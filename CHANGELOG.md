# Changelog

All notable changes to **TarelGo Gate** are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [2.0.0] – 2026-06-18

### Added
- **JWT‑secured access** – protected pages require a valid time‑limited token
- Token is stored in a secure cookie (`Secure`, `SameSite=Strict`, `HttpOnly`)
- Unauthorised requests are automatically redirected to the gate page
- **Demo mode** – manual tier selection (`TarelGoGate.show(10|100|1000)`)
- Dedicated demo page (`gate-demo.html`) for testing individual levels
- `GET /auth` endpoint for JWT verification (internal use)
- `TARELGO_DECIMALS` environment variable for custom token precision
- `JWT_SECRET` environment variable for signing tokens

### Changed
- Backend port changed from `8001` to `8002` to avoid conflicts with other services
- Nginx configuration simplified – `auth_request` replaced with direct FastAPI proxying
- Protected pages are now served by FastAPI instead of Nginx static delivery
- Widget UI updated with version badge ("v2.0") and refined styling

### Fixed
- 422 error when adding a user who is already a member of the Discourse group (legacy)
- 404 error in `auth_request` due to duplicate query string parameters
- 500 error caused by conflicting `location /auth` directives across server blocks

---

## [1.0.0] – 2026-06-16

### Added
- Initial stable release of TarelGo Gate
- Phantom wallet connection and $TARELGO balance check
- Three access tiers based on token balance (10 / 100 / 1000)
- Automatic selection of the highest qualifying tier
- Permanent redirect to the appropriate secret URL
- Dark‑themed widget matching the Tarelgo website style
- Server‑side token balance verification via Solana RPC
- Nginx reverse proxy configuration for production deployment
- Systemd service unit (`tarelgo-gate-xxxxx.service`)
- Configuration via `.env` file (RPC endpoint, mint address, thresholds, URLs)

---

## Types of changes
- `Added` – new features
- `Changed` – changes in existing functionality
- `Deprecated` – soon‑to‑be removed features
- `Removed` – removed features
- `Fixed` – bug fixes
- `Security` – vulnerability fixes

---

[2.0.0]: https://github.com/tarelgo/tarelgo-gate/releases/tag/v2.0.0
[1.0.0]: https://github.com/tarelgo/tarelgo-gate/releases/tag/v1.0.0