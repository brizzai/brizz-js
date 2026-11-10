# Changelog

All notable changes to `@brizz/browser` will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project
adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [0.3.3] - 2026-10-28

### Fixed

- More precise PII masking: long numbers that aren't card numbers are left intact.

## [0.3.2] - 2026-09-17

### Changed

- Added `homepage: https://www.brizz.ai` to `package.json` and linked the README to it.

## [0.3.1] - 2026-09-11

### Changed

- Updated OpenTelemetry dependencies.

## [0.3.0] - 2026-05-26

### Added

- Session-replay correlation for Mixpanel and LogRocket.

## [0.2.0] - 2026-05-25

### Added

- FullStory integration: auto-detects FullStory on the page and correlates the Brizz session
  with its FullStory recording. Opt out via `disableFullStory: true`.

## [0.1.0] - 2026-05-21

### Added

- Initial release of `@brizz/browser` — product analytics SDK for browser apps.
- `Brizz.init()` with DSN or explicit `apiKey`/`baseUrl`/`appName`.
- `brizz.track(event, properties?)` emits an OTel log record to the Brizz gateway.
- `brizz.setSessionId(id)` / `setSessionId(null)` — customer-managed default session correlation.
- `brizz.session(id)` — scoped emitter for parallel sessions (e.g. multiple chats on one page); each
  `.track()` stamps the bound id, independent of the default.
- Automatic context decoration under the `brizz.internal.browser.*` namespace: `browser`, `os`,
  `screen_width`/`screen_height`, `locale`, `current_url`, `referrer`, `page_title`, `user_agent`.
- Bearer-prefix validation rejects Server DSNs (`brizz-ing-s-`) with a clear error.
- Flush on `visibilitychange` / `pagehide` via the OTel exporter's `forceFlush()`.
- Built-in PII masking module (regex-based, configurable).
- ESM, CJS, and IIFE (CDN) bundles.
