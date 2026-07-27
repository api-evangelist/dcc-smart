---
name: Verify a DUIS response and strip its signature
description: Validate the XML digital signature and DUIS XSD on a DUIS response or alert received from DCC Boxed, and return the payload without the signature, using the locally hosted DCC Boxed DUIS Signing Tool API.
api: openapi/dcc-boxed-duis-signing-tool-openapi.yml
operations:
  - verifyMessage
generated: '2026-07-27'
method: generated
source: openapi/dcc-boxed-duis-signing-tool-openapi.yml + https://github.com/SmartDCCInnovation/dccboxed-signing-tool
---

# Verify a DUIS response

Use this on anything DCC Boxed sends you — a synchronous reply, an asynchronous device
response, or a device or network alert — before you trust its contents.

## Before you start

- Self-hosted, no authentication, default `http://localhost:8080`. See the sign skill for
  how to start the server.
- You need a listener. DCC Boxed delivers asynchronous DUIS responses and alerts to the
  **Receive Response Service address** you configure on its DUIS Interface (the Node-RED
  integration defaults this path to `/smartdcc/duis`). Nothing polls for you.

## Steps

1. **Capture the signed DUIS XML** that arrived at your Receive Response Service endpoint.

2. **Base64-encode it** and call `verifyMessage` — `POST /verify` with
   `Content-Type: application/json`:

   ```json
   { "message": "<base64 of the signed DUIS XML>" }
   ```

   By default the tool inspects the message to work out which certificate belongs to the
   sender; you do not pass a certificate on the HTTP surface. (The CLI form optionally takes
   a `user.pem`.)

3. **A 200 means two things passed**: the XML digital signature verified against the sender
   certificate, and the document validated against the DUIS XSD. The response is
   `{ "message": "<base64 of the DUIS XML with the signature removed>" }`.

   Treat a non-200 as "do not process this message". Never act on an unverified DUIS payload.

4. **Decode the GBCS payload if present.** Device responses carry a nested Great Britain
   Companion Specification payload, which may be encrypted when it holds sensitive data.
   `@smartdcc/gbcs-parser` parses it; the `dccboxed-receive` Node-RED node decodes and
   decrypts it as part of the same step.

5. **Reconcile the response with the request that caused it.** DUIS has no request-id header
   at the HTTP layer — correlation is done on the DUIS `Originator`/`Target` pair and the
   request id, including the originator counter. Store the original request when you receive
   its `I99` acknowledgement and match the later `I0` response or alert back to it. This is
   exactly what `dccboxed-send` and `dccboxed-receive` implement between them.

6. **Filter by what you care about.** Multiple listeners can be scoped to a single service
   request (for example SRV 4.1.1, read current energy usage) or to device alerts only.

## Errors

Same envelope as signing: `application/json` with `error` and `errorCode`.

| Status | Meaning | What to check |
|---|---|---|
| 400 | Invalid signature or validation error | Body is valid Base64; decoded payload is well-formed XML; the payload actually carries a `Signature` element (a message with no signature is rejected — fixed in tool v2.1.2); the signature verifies against the sender certificate; the document passes DUIS XSD validation |
| 405 | Method not allowed | You used something other than POST |

The CLI equivalent exits `10` when XSD validation or the signature check fails, and `3` when
the certificate needed to verify is missing. Full catalog:
`errors/dcc-smart-problem-types.yml`.
