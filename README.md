# Secure Dev Tools

Single-file, offline, fully client-side developer tools — JSON formatter, Markdown viewer, diff, encode/decode & JSONPath. **Your data never leaves the browser.**

**[▶ Live demo](https://anilejder.github.io/secure-dev-tools/)**

---

## Why?

Developers routinely paste JSON, config files, tokens, and logs into online "formatter" / "beautifier" sites to clean them up. The problem: that content — often containing **API keys, passwords, customer records, and internal configuration** — is sent to a third-party server you don't control.

This isn't hypothetical. In late 2025, [watchTowr Labs](https://labs.watchtowr.com/stop-putting-your-passwords-into-random-websites-yes-seriously-you-are-the-problem/) collected **80,000+ files (~5 GB)** of secrets leaked through JSONFormatter and CodeBeautify — thousands of credentials, AWS keys, database connection strings, and PII — simply because those sites store pasted content behind predictable, publicly browsable links. Test canary credentials were abused by attackers **within 48 hours**.

**The fix is simple: never let the data leave the device.** This tool does all processing in the browser. There is no backend, no network request, no storage.

## Features

- **JSON Formatter / Validator** — beautify, minify, validate, and an interactive collapsible **tree view** with syntax coloring.
- **Markdown Viewer** — live preview with **syntax-highlighted code blocks** (language label per block) and **synchronized scrolling** between editor and preview.
- **Diff / Compare** — LCS-based line diff with optional JSON normalization.
- **Encode / Decode** — Base64, Base64URL, URL component, and **JWT decoding** (header/payload + human-readable timestamps).
- **JSONPath** — query engine supporting `..`, `[*]`, slices, and filter expressions like `[?(@.price < 10)]`.
- **Sensitive-data detector** — locally scans pasted content for API keys, private keys, JWTs, connection strings, credit cards (Luhn-validated), and PII, and warns you. The data still never leaves the page — this is an awareness layer.
- **Panel view modes** — show both panels, or give a single panel (input or output) the full screen for large content like tables.

## Security guarantees

- 🚫 **Data never leaves your device** — all processing happens in your browser. Nothing is sent to any server, including ours.
- 🗑️ **No storage / no history** — no cookies, no `localStorage`, no server logs. Closing the tab discards everything.
- ✈️ **Works offline** — fully functional with no internet connection. That's the practical proof your data isn't going anywhere.
- 📦 **Zero third-party code** — no external libraries, CDNs, fonts, or analytics. A single HTML file; all logic is self-contained.
- 🔐 **Browser-level lock** — a `Content-Security-Policy` with `connect-src 'none'` prevents the page from opening any network connection, even by accident.

## Usage

**Option 1 — Live demo:** open the [hosted version](https://anilejder.github.io/secure-dev-tools/).

**Option 2 — Local (recommended for sensitive data):**

1. Download [`index.html`](index.html) (or clone this repo).
2. Double-click it to open in any modern browser.

That's it — no build step, no dependencies, no server.

## Verify it yourself

- **Turn off Wi-Fi** and use the tool — everything keeps working. Nothing is leaving.
- Open **DevTools → Network** and use the tool — you'll see zero network requests.
- Open the file in a text editor and search for `fetch` or `http` — you won't find them.

## License

[MIT](LICENSE) © 2026 Anıl Ejder
