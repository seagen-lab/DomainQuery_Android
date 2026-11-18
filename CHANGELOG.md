# Changelog

All notable changes to DomainQ are listed here. Downloads are on the [Releases page](https://github.com/seagen-lab/DomainQuery_Android/releases).

## 0.3.0 (2026-11-18)

### Added

- **Price comparison** in the detail screen: first-year, renewal and transfer prices from registrars' official public price lists (Porkbun, OVHcloud), sorted by renewal price, converted with ECB reference rates; choose the display currency in Settings.
- **Words with spaces** form one name: `nano banana` checks `nanobanana` plus hyphen combinations such as `nano-banana` (setting: Spaces join words).
- **Full domains also try other TLDs:** `coolapp.io` checks `coolapp.io` first, then `coolapp.com`, `coolapp.ai`… (setting: Also try other TLDs).
- **Web addresses are cleaned** in the search box and clipboard suggestions: `https://www.example.com/page?x=1` becomes `example.com`.
- **Share with friends** (Settings → About): send a ready-made message with the download link, or a branded image with a QR code, both written in the app's current language.

## 0.2.0 (2026-11-17)

### Added

- **Expiry and availability reminders for favorites.** Alerts at 30, 7 and 1 days before expiry, when a domain has expired, and when it enters redemption or pending delete. Background recheck every 6, 12 or 24 hours. Tap a notification to open the domain.
- **Background searches** keep running when you leave the app, with a progress notification, a "search finished" alert and a one-tap **Run in background** button. A running search also appears at the top of **History** with **View** and **Stop**.
- **Export** results as CSV, Excel (.xlsx), PDF or a long image styled like the app; share to other apps or save to a file.
- **Full-screen TLD manager:** search by suffix or country name, category tabs, quick sets, custom suffixes (e.g. `com.cn`) and bulk edit.
- **Update check:** once a day (can be turned off) DomainQ looks for a newer release on GitHub and offers to download it. Version number and **Check for updates now** are under Settings → About.
- **Light theme**, with System / Light / Dark under Settings → Display.
- **Clipboard suggestions:** offers to search copied text when you return to the app, asked once per copy.
- **Recent searches** as chips on the empty search page, and **Collapse all / Expand all** for result groups.
- **Animations:** collapsing groups, filtering, live counters, a progress bar under the search box, tab and detail transitions.
- **Interface size** setting.
- French, Italian, German and Russian (9 languages in total).
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
