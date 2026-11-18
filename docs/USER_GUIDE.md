# DomainQ User Guide

This guide covers every feature of DomainQ. Some features (reminders, background searches, clipboard suggestions, recent searches, interface size, and some languages) are newer than v0.1.0; see the [Changelog](../CHANGELOG.md) for which version introduced what.

- [Installing](#installing)
- [Searching](#searching)
- [Choosing TLDs](#choosing-tlds)
- [Smart variants](#smart-variants)
- [Reading the results](#reading-the-results)
- [Domain details](#domain-details)
- [Background searches](#background-searches)
- [Clipboard suggestions](#clipboard-suggestions)
- [Favorites and reminders](#favorites-and-reminders)
- [History and recent searches](#history-and-recent-searches)
- [Settings](#settings)
- [Layouts](#layouts)

## Installing

1. Download the APK from the [latest release](https://github.com/seagen-lab/DomainQuery_Android/releases/latest).
2. Open it on your device. If Android asks, allow your browser or file manager to install unknown apps.
3. Optional: [verify the signature](FAQ.md#how-do-i-verify-the-apk-signature) before installing.

DomainQ needs Android 8.0 or later.

## Searching

Type into the search box on the **Search** tab and press search. There are two kinds of input:

- **A keyword**, such as `coolapp`. DomainQ checks it against every selected TLD (`coolapp.com`, `coolapp.io`, ...).
- **Words with spaces**, such as `nano banana`. They are treated as one name: DomainQ checks `nanobanana` and the hyphen combinations (`nano-banana`; with three words also `nano-bananapro`, `nanobanana-pro`, `nano-banana-pro`). Turn this off with **Settings > Spaces join words** to make spaces separate keywords again.
- **One or more full domains**, such as `coolapp.io` or `example.com example.net`. Separate them with spaces, new lines or commas. The domain you typed is checked first, then the same name with your other selected TLDs (`coolapp.com`, `coolapp.ai`, ...). Turn this off with **Settings > Also try other TLDs** to check only what you typed.
- **A web address**, such as `https://www.example.com/page?x=1`. The protocol, `www.`, port, path and parameters are removed and `example.com` is checked.

New lines, commas and semicolons always separate entries.

You can also enter:

- Second-level suffixes such as `example.com.cn` or `example.co.uk`.
- Internationalized domain names (IDN) in their native script. They are converted to Punycode for the lookup.

### How lookups work

DomainQ asks each TLD's registry directly:

1. **RDAP** first, using the server list from the IANA RDAP bootstrap.
2. **WHOIS** (port 43) as a fallback when a TLD has no RDAP server, using the server listed at `whois.iana.org`.

Requests are rate-limited per server so registries are not flooded. You can tune how many lookups run in parallel with **Concurrency** in Settings.

An optional **DNS precheck** (off by default) queries public DNS-over-HTTPS resolvers first. See [Settings](#settings).

## Choosing TLDs

Tap the **tune icon** inside the search box. The badge on it shows how many TLDs are currently selected.

- **Presets:** Common, Popular, Countries, All. All covers the ~1,400 TLDs in the IANA root zone.
- Select or deselect individual TLDs to build your own set.
- Your default set is configured under **Settings > Default TLDs**.

TLDs only apply to keyword searches. Full domains are checked as entered.

## Smart variants

For keyword searches, DomainQ can also check related names. Each kind can be turned on or off in Settings.

| Variant | Example | Notes |
| --- | --- | --- |
| Hyphen variants | `nanobanana3` → `nano-banana-3`, `nano-banana3`, `nanobanana-3` | Word boundaries come from an on-device English word list. |
| Domain hacks | `coolapp` → `cool.app`, `coo.la` | Uses the end of the keyword as the TLD. |
| Drop vowels | `greenapple` → `grnp.pl` | Removes vowels, then looks for a matching domain hack. |

Domain hacks only use TLDs where anyone can register a second-level name. Brand TLDs (such as `.apple`) and country TLDs that only allow third-level registrations (such as `.np`) are skipped. See the [FAQ](FAQ.md#why-is-a-domain-hack-like-grnp-not-suggested).

## Reading the results

Results are grouped by name. Hyphen variants are grouped with their base name; domain hacks and no-vowel variants get their own groups.

- Tap a group header to collapse or expand it. Use **Collapse all / Expand all** to toggle every group.
- Turn on **Available only** to hide registered domains. Rows that are still being checked stay visible until they resolve.

Each row shows a status and may show tags:

| Tag | Meaning |
| --- | --- |
| Year (e.g. `2009`) or `Nd ago` | When the domain was registered. Recent registrations show days ago. |
| For sale | The name servers point to a known domain parking service. |
| Expiry countdown | The domain expires soon. |
| Restricted | The TLD has registration requirements (for example, residency or a trademark) or is not open to the public. |
| Unknown | The lookup did not give a clear answer. The reason (for example, a timeout or an unreachable server) is shown. |

Tap any row to open its details.

## Domain details

For a **registered** domain:

- Registered, expiry and updated dates
- Registrar
- Status codes (for example `clientTransferProhibited`, `redemptionPeriod`)
- Name servers
- The raw RDAP or WHOIS response
- **Traffic estimate** from Similarweb: monthly visits, global and country rank, bounce rate, pages per visit, average visit duration, traffic sources and top countries. On some networks Similarweb blocks the request; use **Open on Similarweb** to view it in a browser instead. This can be turned off in Settings.
- **Preview site** opens the website in an in-app browser.

For an **available** domain:

- A **Register** guide with links to Cloudflare, Spaceship, NameSilo, Namecheap and Porkbun. Links open in a half-screen in-app browser (Custom Tab), so you can compare prices and return to DomainQ quickly.

From the detail screen you can also add the domain to **Favorites**.

## Background searches

Large searches (for example, a keyword against All TLDs) can take a while.

- Tap **Run in background** to keep the search going while you use other apps.
- A pinned progress notification shows how far the search has got (for example `29 / 66 checked`) and has a **Stop** button. It stays until the search ends and can't be swiped away.
- When it finishes, you get a **Search finished** notification.

Notifications require the notification permission on Android 13 and later. See [Settings > Notifications](#notifications-and-permissions).

## Clipboard suggestions

When you return to DomainQ and the clipboard contains something that looks like a domain or keyword, DomainQ offers to search it.

- Web addresses are cleaned first: `https://www.example.com/a/b?x=1` is offered as `example.com`.
- Each copied item is offered only once.
- The clipboard is read only when the app comes to the foreground.
- Turn this off with **Settings > Clipboard suggestions**.

See the [Privacy Policy](PRIVACY.md#clipboard) for details.

## Price comparison

The detail screen shows what registrars charge for the domain's TLD, sorted by **renewal price** — the price you keep paying every year.

- For an **available** domain: first-year and renewal price per registrar; the lowest renewal is highlighted. Tap a row to open that registrar's order page.
- For a **registered** domain: transfer and renewal prices, useful when it is about to expire; in redemption, the restore price where available.
- Prices come from the registrars' own official public price lists (currently Porkbun and OVHcloud) and are converted to your display currency with the European Central Bank's daily reference rates. They exclude taxes, coupons and premium-name pricing, so always confirm at checkout.
- Price lists are downloaded at most once a day. No domain names are sent — only the full price lists are fetched.
- Turn this off, or change the display currency, under **Settings**.

## Favorites and reminders

Add a domain to **Favorites** with the star on its result row or in its detail screen.

When **Reminders** are on, DomainQ rechecks your favorites in the background and notifies you when:

- A registered domain expires in **30, 7 or 1 days**
- A domain has **expired**
- A domain enters **redemption** or **pending delete**, which often means it may soon become available

Rechecks run every **6, 12 or 24 hours** (set in Settings). Use **Check now** to run one immediately; the last check time is shown below it. Tap a reminder notification to open that domain.

## History and recent searches

- **History** keeps one entry per query and TLD set. Tap an entry to run it again. Use **Clear all** to remove every entry.
- When the search box is empty, the Search screen shows **recent searches** as chips. Tap one to rerun it.

## Settings

### Search

| Setting | Description |
| --- | --- |
| Default TLDs | The TLD set selected for new searches. |
| Spaces join words | Treat `nano banana` as one name (`nanobanana`, `nano-banana`). When off, spaces separate keywords. |
| Also try other TLDs | For a full domain such as `coolapp.io`, also check `coolapp` with your other selected TLDs. |
| Hyphen variants | Check hyphenated versions of keywords. |
| Domain hacks | Check names that use part of the keyword as the TLD. |
| Drop vowels | Check vowel-less domain hacks. |
| Traffic estimate | Fetch Similarweb estimates on the detail screen for registered domains. |
| Price comparison | Show registrar prices on the detail screen. On by default. |
| Display currency | USD, EUR, CNY, GBP or JPY for price comparison. |
| Clipboard suggestions | Offer to search copied text when you return to the app. |
| DNS precheck (third-party) | Query Cloudflare, Google or AliDNS public DNS before the registry. Off by default; when off, only registry data is used. |
| Concurrency | Number of parallel lookups, 1 to 8. |
| Cache duration | How long lookup results are reused: Off, 1 h, 6 h, 24 h or 3 days. |

### Reminders

| Setting | Description |
| --- | --- |
| Reminders | Turn background rechecks of favorites on or off. |
| Interval | Every 6, 12 or 24 hours. |
| Check now | Run a recheck immediately. Shows the last check time. |

### Notifications and permissions

- **Notification permission** shows whether notifications are allowed and opens the system notification settings for DomainQ.
- **App permissions** opens DomainQ's page in Android's app settings.

### Appearance

| Setting | Description |
| --- | --- |
| Theme | System, Light or Dark. |
| Language | System default, English, Français, Italiano, Deutsch, Русский, Simplified Chinese, Traditional Chinese, Japanese, Korean. |
| Interface size | Scales the whole UI, 80% to 120%. |
| Text size | Scales text, 80% to 140%. |

### About

- **Share with friends** opens a sheet with two choices:
  - **Text link:** a short message with the download link. Copy it or share it to any app.
  - **QR code image:** a card in DomainQ's style with a QR code that opens the download page. Save it or share it.
  Both are written in the app's current language.
- **Version**, **Check for updates automatically** (once a day, from GitHub Releases) and **Check for updates now**.

### Data

| Setting | Description |
| --- | --- |
| Google Drive sync | Optional. Syncs your app data to the hidden app data folder in your own Google Drive. Some builds may not include it. |
| Clear lookup cache | Deletes cached lookup results. Favorites and history are kept. |
| Android Auto Backup | Android can back up the app's data to your Google account and restore it on a new device. Managed in your system backup settings. |

## Layouts

- **Phone (portrait):** single-pane layout.
- **Landscape:** a navigation rail on the side.
- **Foldables and tablets:** two panes, with the result list on one side and domain details on the other.

Light and dark themes are available; by default DomainQ follows the system setting.

---

Questions not covered here? Check the [FAQ](FAQ.md) or open an issue on [GitHub Issues](https://github.com/seagen-lab/DomainQuery_Android/issues).
