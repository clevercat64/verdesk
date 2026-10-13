# Security Policy

## Reporting a Vulnerability

If you find a security issue in Verdesk, **please do not open a public issue**. Email **support@verdesk.app** with:

- A short description of the vulnerability.
- Steps to reproduce (a proof-of-concept is welcome but not required).
- The Verdesk version (*Settings → Home*) and your Windows version.

You will receive a reply within 72 hours acknowledging receipt. Confirmed issues are patched in the next point release; the reporter is credited in the release notes unless they prefer to stay anonymous.

## Supported Versions

The latest published Release is the only supported version. Older Releases stop receiving security fixes once a newer Release is out.

## Scope

Verdesk runs on the user's machine and sends no usage telemetry. What it does send:

- **License and store service, `pay.verdesk.app`.** With a paid license: a license check (`/lic/check`, fields `token`, `machine`, `nonce`, `v`) and a renewal (`/lic/refresh`, field `token`). `machine` is a 64-character HMAC of the Windows machine GUID; the GUID itself is not kept.
- **Sign-up report.** Once, at the end of the first-run welcome window, to the project's server at `pay.verdesk.app` (`/report/send`), which emails it to the project. Fields: `type` (`onboarding`), `title` (`New Free user` or `New Pro user`), `body` (text with the tier, `email`, `machine`, `version`, and an `error` code only if a license key was rejected), `email`, `app_version` and `machine_id` (a random UUID generated on this PC and kept there). The license key itself is never sent. The server limits how often a PC can send it. Versions before 2.61.2 sent it to a Google Apps Script run by the project owner, with two more fields (`timestamp` and `token`).
- **Reports you or your agent choose to send** (the `send_report` tool): to the project's server at `pay.verdesk.app` (`/report/send`), which emails them to the project, with `type` (`report`), `kind`, `topic`, `message`, `source`, `version` and `host` (the computer name). The server limits their size and how often a PC can send them. Versions before 2.61.2 sent them through a form forwarder (FormSubmit).
- **New releases.** Verdesk asks GitHub for the latest release.

Reports about:

- Local privilege escalation, sandbox escape, RCE via Verdesk itself, or any path that lets a third party connect or act without the user's approval popup → **in scope**.
- The license service (`pay.verdesk.app`): forging or obtaining licenses, getting around the 2-computer limit, or revoking someone else's license → **in scope**; use the same email.
- The payment provider's own systems → out of scope here; report to the provider directly.
- Issues that require the user to install a separate malicious MCP client themselves → out of scope (Verdesk is the server, not the client).
