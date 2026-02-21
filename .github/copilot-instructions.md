# Copilot Instructions for SLIM (Structured Low-bandwidth Information Markup)

This repository defines SLIM, a minimal, text-first HTML profile for reliable delivery in low-bandwidth and austere conditions.

When asked to generate HTML, templates, examples, or code that emits HTML, Copilot MUST default to producing **SLIM-compliant output**.

If a user request conflicts with SLIM constraints, Copilot should:
1) explain the conflict briefly, and
2) offer the closest SLIM-compliant alternative.

---

## Source of Truth

- The normative specification source is `spec.bs`.
- If there is any ambiguity, prefer the stricter interpretation that preserves SLIM goals.

---

## SLIM Output Defaults (what to generate)

When generating a SLIM page, Copilot should output:
- A single, self-contained HTML file
- No external resources (no external CSS, JS, images, fonts, analytics)
- Semantic structure (header/main/footer where helpful)
- Clear headings (one `<h1>` per page, meaningful `<h2>`/`<h3>`)

### Required metadata
Every SLIM page MUST include:
- `<meta name="slim-profile" content="SLIM v1.0">`
- `<meta charset="utf-8">`
- `<meta name="viewport" content="width=device-width, initial-scale=1">`

### Mandatory authoring rule
- Every `<input>` MUST include a `type` attribute.

---

## Prohibited content (do not generate)

Copilot MUST NOT generate SLIM “compliant” examples that include:
- Any JavaScript (`<script>`, inline handlers like `onclick=`, or JS URLs)
- Any tracking/analytics/pixels/beacons
- Iframes or embedded contexts (`<iframe>`, `<embed>`, `<object>`)
- Third-party fonts or font CDNs
- External stylesheets (`<link rel="stylesheet" ...>`)
- External media dependencies that create additional fetches

If the user asks for these, provide a SLIM alternative (e.g., plain links, server-rendered pages, or opt-in external tooling outside the SLIM page).

---

## Styling rules (keep it minimal)

- Prefer no CSS unless it improves legibility.
- If inline styles are used, keep them to SLIM-allowed properties only:
  - `color`, `font-family`, `text-align`, `font-weight`, `font-style`
- Do not use layout CSS (no flex/grid/positioning/margins/padding/etc.).
- Color MUST NOT be the only method of conveying meaning (include text labels).

---

## Forms and tables (discouraged)

- Tables and forms SHOULD be avoided unless clearly justified.
- If used:
  - keep them simple and robust
  - do not rely on client-side validation or scripts
  - ensure accessibility (labels, captions, clear text)

---

## Network and deployment guidance (include when asked)

Copilot cannot control HTTP protocol negotiation from within HTML, but when asked about
**deployment/hosting/server configuration**, Copilot SHOULD reflect SLIM’s transport guidance:

- HTTP/3 — SHOULD be preferred where supported by both server and client.
- HTTP/2 — SHOULD be used as a fallback where HTTP/3 is not available.
- HTTP/1.1 — MAY be used only when HTTP/3 and HTTP/2 are unavailable.

Also:
- SLIM content MUST be served over HTTPS.
- Do not recommend solutions that require JavaScript or additional subresource fetches for correctness.

---

## Response format expectations (to help implementors)

When Copilot generates SLIM HTML, it should include:
1) The full HTML document
2) A short **Conformance Checklist** (bullet list) stating key SLIM rules satisfied
3) If any compromises were necessary, a **Non-compliance Notes** section explaining what would violate SLIM and why (keep brief)

---

## Canonical starter template (use this as the baseline)

Copilot should start from this template unless the user provides an existing page to modify:

```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <meta name="slim-profile" content="SLIM v1.0">
  <title>SLIM Page</title>
</head>
<body>
  <header>
    <h1>Page Title</h1>
  </header>

  <main>
    <p>This page is designed to work well on low-bandwidth connections.</p>

    <h2>Section</h2>
    <p>Add content here.</p>

    <p><a href="./">Home</a></p>
  </main>

  <footer>
    <p>Last updated: <time datetime="2026-02-21">February 21, 2026</time></p>
  </footer>
</body>
</html>
