# SLIM: Structured Low-bandwidth Information Markup

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.16790879.svg)](https://doi.org/10.5281/zenodo.16790879)
[![Build Status](https://github.com/cqueern/slim-spec/actions/workflows/release-build.yml/badge.svg)](https://github.com/cqueern/slim-spec/actions/workflows/release-build.yml)
[![License: MIT](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)

**SLIM** is a minimal, text-first HTML authoring profile for delivering reliable, accessible information in low-bandwidth and austere network conditions.

SLIM v1.0 defines strict authoring rules to ensure:
- **Text-only content** (no images, video, or audio)
- **Single-request load model** (one HTTPS request to render the page)
- **Mandatory TLS encryption**
- **No scripts, tracking, or third-party fonts**
- **Inline styles only** (with a limited property set)
- **No iframes or embedded contexts**
- **Strong CSP enforcement (recommended)**

The specification is authored in [Bikeshed](https://tabatkins.github.io/bikeshed/) format and builds into a W3C-style HTML document for distribution.

## Status

- **Current version:** v1.0 *(Unofficial Draft)*
- **Editor:** Caleb Queern ([ORCID](https://orcid.org/0009-0009-4440-8941))
- **License:** [MIT License](LICENSE)

## Repository Contents

- `spec.bs` — Bikeshed source for the SLIM specification
- `.github/workflows/release-build.yml` — GitHub Actions workflow to build HTML/PDF on release
- `.zenodo.json` & `CITATION.cff` — Metadata for DOI citation via Zenodo
- `LICENSE` — MIT License

## Building the Spec Locally

```bash
pipx install bikeshed
bikeshed update
bikeshed spec spec.bs index.html
```

## Contributing
SLIM is intended as an open, evolving profile.
* **Feedback**: [Open a GitHub Issue](https://github.com/cqueern/slim-spec/issues)
* **Changes**: Fork and submit a Pull Request

## Citation
If citing SLIM in academic or technical work, please use the DOI from the latest release:

```Queern, C. (2025). SLIM: Structured Low-bandwidth Information Markup v1.0. Zenodo. https://doi.org/10.5281/zenodo.XXXXXXX```

**ORCID:** [0009-0009-4440-8941](https://orcid.org/0009-0009-4440-8941)

## Links
* [Bikeshed Documentation](https://speced.github.io/bikeshed/)
* [MIT License](https://opensource.org/license/mit/)
* [Zenodo](https://zenodo.org/)


