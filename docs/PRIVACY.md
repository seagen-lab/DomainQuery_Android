# DomainQ Privacy Policy

**Effective date:** 2026-11-17

This policy explains what data the DomainQ Android app (package `app.seagenlab.domainquery`, published by seagen-lab) handles and where it goes.

## Summary

- No account or sign-in is required.
- No analytics, crash reporting, advertising or tracking SDKs.
- Your searches, favorites, history and settings are stored on your device.
- The app sends domain names to third parties only as needed to look them up, as described below.
- We (the publisher) do not operate any server that receives your data.

## Data stored on your device

DomainQ stores the following locally in its private app storage:

- Favorites and their last known status
- Search history and recent searches
- Cached lookup results (you can clear them in Settings, or set the cache duration to Off)
- Settings and preferences
- Clipboard fingerprints (see [Clipboard](#clipboard))

This data stays on your device unless you use Android Auto Backup or Google Drive sync (see below). Uninstalling the app deletes it.

## Network requests

DomainQ connects directly from your device to the following services. Each service receives your IP address and standard connection information as part of any internet request, and handles it under its own privacy policy.

| Recipient | When | What is sent |
| --- | --- | --- |
| **IANA** (iana.org servers, including `whois.iana.org`) | To download the TLD list, the RDAP bootstrap file, and to find a TLD's WHOIS server | Requests for public lists; a TLD name when looking up its WHOIS server |
| **TLD registries' RDAP and WHOIS servers** (as listed by IANA) | Every domain lookup | The domain name being checked |
| **Public DNS resolvers**: Cloudflare, Google, AliDNS (DNS-over-HTTPS) | Only if you turn on **DNS precheck**. **Off by default.** | The domain name being checked |
| **Similarweb** | When you open the detail screen of a registered domain and **Traffic estimate** is on. Can be turned off in Settings. | The domain name |
| **Google Drive** (your own account) | Only if you turn on **Google Drive sync** | Your DomainQ data, stored in your Drive's hidden app data folder (`appDataFolder`), which is only accessible to DomainQ |
| **GitHub** (`api.github.com`) | At most once a day when **Check for updates automatically** is on (on by default), or when you tap **Check for updates now** | A request for the latest public release of DomainQ; no personal data |
| **Websites you choose to open** | When you tap **Preview site**, **Open on Similarweb**, or a registrar link in the Register guide | Opened in an in-app browser tab (Custom Tab) provided by your browser, subject to that browser's and website's policies |

Registrar links in the Register guide (Cloudflare, Spaceship, NameSilo, Namecheap, Porkbun) are ordinary links. DomainQ does not share any data with these registrars beyond opening their page.

## Clipboard

If **Clipboard suggestions** is on (it can be turned off in Settings):

- DomainQ reads the clipboard **only when the app comes to the foreground** (on resume), to offer a search for copied text that looks like a domain or keyword.
- Each copied item is checked once. To avoid asking twice about the same item, DomainQ stores only a fingerprint: the clipboard item's timestamp and a hash. The clipboard text itself is not stored or sent anywhere.
- Clipboard contents are only searched if you accept the suggestion.

## Notifications

DomainQ asks for the notification permission (Android 13 and later) to show:

- Progress and "search finished" notifications for background searches
- Reminders about your favorites (upcoming expiry, expired, redemption or pending delete)

Notifications are generated on your device. You can deny or revoke the permission at any time in Android settings; the rest of the app keeps working.

## Background work

When reminders are on, DomainQ periodically rechecks your favorites in the background (every 6, 12 or 24 hours). These rechecks make the same registry requests described above, for your favorite domains only.

## Backups

- **Android Auto Backup:** if backup is enabled on your device, Android may back up DomainQ's app data to your Google account under Google's policies, and restore it on reinstall or a new device. You control this in your system settings.
- **Google Drive sync:** optional and off unless you enable it. It requires you to sign in to Google and grant access to the app data folder only. DomainQ does not access any other files in your Drive. This feature may be unavailable in some builds.

## Children

DomainQ is a general-purpose utility, not directed at children, and does not knowingly collect personal information from anyone.

## Data sharing and sale

We do not sell, rent or share your data. We do not receive your data at all, except what you choose to include when contacting us through GitHub Issues.

## Your choices

- Turn off **Traffic estimate**, **Clipboard suggestions**, **DNS precheck**, **Reminders** or **Google Drive sync** in Settings.
- Clear the lookup cache or history at any time.
- Delete all data by clearing the app's storage or uninstalling it.

## Changes

If this policy changes, the updated version will be published in this repository with a new effective date.

## Contact

For questions about this policy, open an issue on [GitHub Issues](https://github.com/seagen-lab/DomainQuery_Android/issues).
