# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [1.3.1] - 2026-09-27

### Added

- `S3_PROXY_PUBLIC_FILES` to serve avatars and background images through the server from a private bucket
- Helm chart

### Changed

- Docker image runs as uid/gid 1000 and is published to ghcr.io

### Security

- Check source board authorization on duplicate
- Upgrade server dependencies with known vulnerabilities (bcrypt 6, nodemailer 10, sharp 0.35, express, socket.io, ws, lodash, validator)
- Upgrade client dependencies with known vulnerabilities (axios, js-cookie, lodash, nanoid, react-router-dom, js-yaml)
- Fix stored XSS via attacker-chosen attachment extension

## [1.3.0] - 2026-05-28

### Added

- Export boards data to CSV
- Include active filters in URL (shareable filter state)
- Folder deletion
- Configurable organization ID claim for OIDC project auto-assignment

### Fixed

- Display issue with long board names
- Duplicated user in share modal
- Cmd+Enter incorrectly opening card on Mac
- Notifications read button
- Comments not rendered as markdown

### Changed

- Harmonised board actions UI
- Improved drag-and-drop and rendering performance

## [1.2.0] - 2026-02-06

### Added

- Count badge on list headers
- Automatically assign filtered members and labels to created cards
- Display all activities by default and make them hideable

### Fixed

- Various interactions on the card modal

### Changed

- UI kit fixes

## [1.1.0] - 2026-02-03

### Added

- Kit UI v2 migration
- User search on-demand for better performance and privacy

### Fixed

- Shared boards display in left menu
- XSS vulnerability from react-photoswipe-gallery
- User emails now masked on public boards when not logged in
- Node upgrade issues
- Attachment popup removed
- ESLint config extending from another package.json

### Changed

- Removed pnpm in favor of npm for simplicity
- Aligned node versions across environments
- Cleaned up package-lock.json and added async overrides

## [1.0.1] - 2025-11-25

### Added

- ✨ (frontend) add no member/label option in filters

### Fixed

- 💄 (frontend) Improve filters UI
- 🐛(frontend) Switched to pointer collision strategy
- 🐛 (header) fix posthog identification by using window.posthog
- ✨ (frontend) add i18n support to Cunningham

### Changed

- 📝 Update README
