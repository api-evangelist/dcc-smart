---
name: Sign a DUIS request with the DCC Boxed signing tool
description: Add an SMKI XML digital signature to a DUIS request so it can be submitted to a DCC Boxed instance, using the locally hosted DCC Boxed DUIS Signing Tool API.
api: openapi/dcc-boxed-duis-signing-tool-openapi.yml
operations:
  - signMessage
generated: '2026-07-27'
method: generated
source: openapi/dcc-boxed-duis-signing-tool-openapi.yml + https://github.com/SmartDCCInnovation/dccboxed-signing-tool
---

# Sign a DUIS request

Use this when you have an unsigned DUIS (DCC User Interface Specification) XML request and
need the XML digital signature that DCC Boxed will accept.

## Before you start

- This API is **self-hosted**. Smart DCC operates no public instance. Start the tool with
  `java -cp ./target/xmldsig-<version>.jar uk.co.smartdcc.boxed.xmldsig.Server` (default port
  8080, change with `-p`). Base URL is therefore `http://localhost:8080` unless you moved it.
- There is **no authentication** on this API. Do not expose it beyond the host you control.
- The tool ships the **ZAZ1 test SMKI certificates and private keys**. Everything you sign
  with it is signed for a test PKI. It has no standing on the live DCC network. Live access
  requires Smart Energy Code accession, a DCC User Gateway Connection and SMKI-issued
  certificates — see `authentication/dcc-smart-authentication.yml`.

## Steps

1. **Get an unsigned DUIS request.** The `@smartdcc/duis-templates` package publishes a
   searchable catalog of DUIS request templates taken from RTDS; set the `Originator` (your
   Remote Party EUI) and `Target` (the device or ACB EUI) in the header. The device EUI can
   be read from the HAN page in DCC Boxed.

2. **Base64-encode the XML document.** The API never takes raw XML — the `message` field is
   declared `type: string, format: byte`.

3. **Call `signMessage`** — `POST /sign` with `Content-Type: application/json`:

   ```json
   { "message": "<base64 of the unsigned DUIS XML>", "preserveCounter": false }
   ```

   - Omit `preserveCounter` or send `false` (the default) and the tool overwrites the
     originator counter in the request id with `System.currentTimeMillis()`, matching how
     DCC Boxed generates counters internally. This is the safe default because the counter
     must strictly increase.
   - Send `true` only when you deliberately need the counter you supplied preserved.
   - **Consequence of the default:** the call is not idempotent. The same input produces a
     different signed document each time. Do not retry blindly and do not cache by request
     body — see `conventions/dcc-smart-conventions.yml`.

4. **Read the 200 response.** It is `{ "message": "<base64 of the signed DUIS XML>" }`.
   Base64-decode it to get the XML with the `Signature` element added.

5. **Submit it to DCC Boxed.** The signed XML goes to the DCC Boxed service endpoint as
   `application/xml`. The README documents the CLI equivalent verbatim:

   ```
   java -cp xmldsig-<version>.jar uk.co.smartdcc.boxed.xmldsig.Sign CS08_11.2_SUCCESS_REQUEST_DUIS.XML \
     | curl http://dccboxed-server:8079/api/v1/serviceS -H 'Content-Type: application/xml' --data-binary -
   ```

6. **Expect an asynchronous response.** For device commands the synchronous reply is
   typically an `I99` acknowledgement. The real result arrives later at the Receive Response
   Service address configured on the DCC Boxed DUIS Interface. Verify it with the companion
   skill.

## Critical commands

If the service request is **critical**, signing alone is not enough: the request must go
through the transform service first and the resulting pre-command must then be signed. The
`dccboxed-send` Node-RED node and `@smartdcc/duis-sign-wrap` handle this two-phase flow for
you — see `components/dcc-smart-components.yml`.

## Errors

Errors come back as `application/json` with `error` (message) and `errorCode` (the Java
exception class name). This is **not** RFC 9457.

| Status | Meaning | What to check |
|---|---|---|
| 400 | Invalid XML or signing error | Body is valid Base64; decoded payload is well-formed XML and passes DUIS XSD validation; a private key matching the message Originator exists in the certificate library |
| 405 | Method not allowed | You used something other than POST |

The same failures map to CLI exit codes `2` (exception), `3` (missing key material) and
`10` (XSD validation failed). Full catalog: `errors/dcc-smart-problem-types.yml`.
