# HTTP Header Analyzer

Paste a raw HTTP response or request header block and get a per-header explanation plus a security posture summary. It parses text only, makes no requests, and runs entirely in your browser with no external dependencies. Works offline.

## Live demo

https://0xelitesystem.github.io/http-header-analyzer/

## Features

- Parses the status line (`HTTP/2 200`) or request line (`GET /path HTTP/1.1`) and every `Header-Name: value` line.
- One-line explanation for each recognized header (60-plus common headers built in).
- Security flags for the important headers: `Strict-Transport-Security`, `Content-Security-Policy`, `X-Frame-Options`, `X-Content-Type-Options`, `Referrer-Policy`, `Permissions-Policy`, and `Set-Cookie` flags (`HttpOnly`, `Secure`, `SameSite`).
- Flags weak configurations, such as short HSTS `max-age`, `unsafe-inline` in CSP, `SameSite=None` without `Secure`, and version-leaking `Server` or `X-Powered-By`.
- Security posture summary that lists recommended security headers absent from the pasted set, with a short reason for each.
- Handles folded header continuation lines and blank lines.
- Load a realistic example, light and dark themes, keyboard-friendly (Ctrl or Cmd plus Enter).

## How it works

The pasted text is split into lines. The first line matching a status or request pattern becomes the status line; the rest are parsed as `name: value` pairs, with leading-whitespace continuation lines folded into the previous header. Each header is looked up in a built-in description table, and security-relevant headers are run through value checks that produce safe, weak, or missing flags. The posture section compares the set of present headers against a recommended baseline and reports what is absent.

## Privacy

Everything runs in your browser as plain text parsing. The tool never fetches a URL or sends your headers anywhere. There are no analytics and no external scripts. Confirm with the DevTools network tab that no requests are made.

## License

MIT. Copyright 0xelitesystem 2026.
