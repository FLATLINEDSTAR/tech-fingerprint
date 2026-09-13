# tech-fingerprint

## Project Purpose
The **tech-fingerprint** repository extracts technology‑level fingerprints from raw observations (HTML, HTTP headers, TLS certificates, etc.) and produces structured `Technology` entities.

## Current Status
**Planning** – repository only contains a placeholder README.

## Why It Exists
A dedicated fingerprinting service allows the rest of the pipeline to work with high‑level technology identifiers (e.g., web server, CMS, framework) without each component re‑implementing detection logic.

## Architecture Role
- **Library** – imported by `entity-extractor` and `change-detector`.
- Exposes a Go package `github.com/FLATLINEDSTAR/tech-fingerprint` with a function:
  ```go
  func Fingerprint(obs OnionObservation) ([]Technology, error)
  ```

## Planned Features (MVP)
1. Header‑based detection (Server, X‑Powered‑By).
2. TLS‑certificate analysis (issuer, key length).
3. HTML meta‑tag and script‑src heuristics.
4. Simple rule‑engine driven by a YAML fingerprint database.

## Installation / Usage (placeholder)
```bash
# Go (primary)
go get github.com/FLATLINEDSTAR/tech-fingerprint
```
*Package will be released after MVP is complete.*

## Development
- Language: **Go**.
- Follow organization‑wide contribution guidelines.

## Testing
- Unit tests for each detection rule.
- Integration tests covering real‑world `.onion` services (using mock data).

## Contributing
See the organization‑wide `CONTRIBUTING.md` in the `.github` repository.

## Roadmap
- **Phase 1** – Define `Technology` struct in `onion-sdk` and populate a basic fingerprint rule set.
- **Phase 2** – Implement detection logic and CI pipeline for rule updates.
- **Phase 3** – Expose Python/TS bindings via the SDK.

## Relationship to FLATLINEDSTAR Ecosystem
`tech-fingerprint` enriches raw observations, feeding `entity-extractor` and `change-detector`, which subsequently provide data to `onion-intelligence`.

## License
MIT – see LICENSE in the repository root.