# Changelog

All notable changes to DomainQ are listed here. Downloads are on the [Releases page](https://github.com/seagen-lab/DomainQuery_Android/releases).

## Unreleased

### Added

- **Expiry and availability reminders for favorites.** Alerts at 30, 7 and 1 days before expiry, when a domain has expired, and when it enters redemption or pending delete. Background recheck every 6, 12 or 24 hours. Tap a notification to open the domain.
- **Background searches** with a progress notification and a "search finished" alert, plus a one-tap **Run in background** button.
- **Clipboard suggestions:** offers to search copied text when you return to the app, asked once per copy.
- **Recent searches** shown as chips on the empty search page.
- **Collapse all / Expand all** for result groups.
- **Interface size** setting.
- French, Italian, German and Russian translations (9 languages in total).
- Links to the system notification settings and app permission settings.

### Changed

- **DNS precheck is now off by default.** Results use registry data only unless you turn it on.

## 0.1.0 (2026-11-17)

Initial release.

- Bulk availability search: a keyword across many TLDs, or a list of full domains.
- All ~1,400 IANA TLDs, second-level suffixes (such as `com.cn`, `co.uk`) and IDN support.
- TLD presets: Common, Popular, Countries, All.
- Direct registry lookups via RDAP with WHOIS fallback, with per-server rate limiting.
- Smart variants: hyphen variants, domain hacks and drop vowels.
- Grouped, collapsible results with an "Available only" filter and status tags.
- Domain details with dates, registrar, status codes, name servers and raw RDAP/WHOIS data.
- Similarweb traffic estimate for registered domains.
- Register guide for available domains, opened in an in-app browser.
- Favorites and History.
- Phone, landscape and two-pane foldable/tablet layouts; dark theme.
- Settings for default TLDs, variants, concurrency, cache duration, language, text size, Google Drive sync and cache clearing.
- Languages: English, Simplified Chinese, Traditional Chinese, Japanese, Korean.
