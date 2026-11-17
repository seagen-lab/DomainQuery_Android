# DomainQ FAQ

- [Why does a result show "Unknown"?](#why-does-a-result-show-unknown)
- [Why do .cn lookups fail on some networks?](#why-do-cn-lookups-fail-on-some-networks)
- [Why does the traffic estimate show "HTTP 403"?](#why-does-the-traffic-estimate-show-http-403)
- [What does "Restricted" mean?](#what-does-restricted-mean)
- [Why is a domain hack like gr.np not suggested?](#why-is-a-domain-hack-like-grnp-not-suggested)
- [Is "Available" a guarantee that I can register it?](#is-available-a-guarantee-that-i-can-register-it)
- [How do background searches and notifications work?](#how-do-background-searches-and-notifications-work)
- [How do reminders decide when to alert me?](#how-do-reminders-decide-when-to-alert-me)
- [Why is the app asking about my clipboard?](#why-is-the-app-asking-about-my-clipboard)
- [Should I turn on DNS precheck?](#should-i-turn-on-dns-precheck)
- [How do I back up or sync my data?](#how-do-i-back-up-or-sync-my-data)
- [How do I install the APK?](#how-do-i-install-the-apk)
- [How do I verify the APK signature?](#how-do-i-verify-the-apk-signature)
- [Is DomainQ open source?](#is-domainq-open-source)

---

### Why does a result show "Unknown"?

DomainQ could not get a clear answer from the registry. The reason is shown next to the tag. Common causes:

- The registry's RDAP or WHOIS server timed out or was unreachable.
- The server rate-limited the request.
- The registry does not publish a public RDAP or WHOIS service, or returns a format that cannot be interpreted reliably.

Try again later, lower **Concurrency** in Settings, or check the domain with the registry or a registrar directly.

### Why do .cn lookups fail on some networks?

The `.cn` registry's lookup server is not reachable, or is very slow, from some networks and regions. When that happens, `.cn` and `com.cn` style domains show as Unknown. Switching networks (for example, from Wi-Fi to mobile data) or retrying later often helps.

### Why does the traffic estimate show "HTTP 403"?

Similarweb sometimes blocks requests from certain networks, IP ranges or regions and responds with HTTP 403 (Forbidden). This is on Similarweb's side and does not affect domain lookups. Tap **Open on Similarweb** to view the estimate in your browser, or turn off **Traffic estimate** in Settings.

### What does "Restricted" mean?

The TLD is not open to everyone. Examples include TLDs that require local presence or residency, TLDs for specific professions or communities, and brand TLDs used only by their owner. A Restricted domain may be unregistered, but you may not be eligible to register it. Check the registry's policy before buying.

### Why is a domain hack like gr.np not suggested?

Domain hacks are only built with TLDs where the public can register a name directly at the second level. DomainQ skips:

- **Brand TLDs** such as `.apple`, which only the brand owner can use.
- **Country TLDs that only allow third-level registrations**, such as `.np`, where names are registered under suffixes like `com.np` rather than directly under `.np`.

A suggestion like `gr.np` would never be registrable, so it is left out.

### Is "Available" a guarantee that I can register it?

No. "Available" means the registry reported no registration at the time of the lookup. A domain can still be reserved, premium-priced, restricted, or registered by someone else a moment later. The registrar's checkout is the final word.

### How do background searches and notifications work?

When a search is running, tap **Run in background**. DomainQ keeps checking while you use other apps and shows a progress notification. When the search completes, you get a **Search finished** notification.

On Android 13 and later you need to allow notifications. Go to **Settings > Notification permission**, or Android's app settings via **Settings > App permissions**. Aggressive battery savers on some devices can delay background work; exempting DomainQ from battery optimization helps.

### How do reminders decide when to alert me?

When **Reminders** are on, DomainQ rechecks your favorites every 6, 12 or 24 hours (your choice) and compares each domain's registry data with what it saw before. It alerts you when a favorite:

- is **30, 7 or 1 days** from its expiry date,
- has **expired**, or
- enters **redemption** or **pending delete** status.

Tap a notification to open that domain. Use **Check now** to recheck immediately; the last check time is shown in Settings. Android may run scheduled checks somewhat later than the exact interval to save battery.

### Why is the app asking about my clipboard?

With **Clipboard suggestions** on, when you return to DomainQ and the clipboard holds something that looks like a domain or keyword, the app offers to search it. Each copied item is offered once. The clipboard is only read when the app comes to the foreground, and its contents are not stored. Turn this off in Settings. See the [Privacy Policy](PRIVACY.md#clipboard).

### Should I turn on DNS precheck?

Usually not. DNS precheck sends each domain name to a third-party public DNS resolver (Cloudflare, Google or AliDNS) before the registry lookup. It can speed up very large searches, but DNS data is less reliable than registry data (a registered domain can have no DNS records). It is off by default, so results come from registry data only.

### How do I back up or sync my data?

- **Android Auto Backup:** if backup is enabled in your system settings, Android backs up DomainQ's data to your Google account and restores it when you reinstall or set up a new device.
- **Google Drive sync:** optional, in **Settings**. Data is stored in the hidden app data folder of your own Google Drive, which only DomainQ can access. This feature depends on setup by the publisher and may not be available in every build.

### How do I install the APK?

1. Download the `.apk` file from the [latest release](https://github.com/seagen-lab/DomainQuery_Android/releases/latest) on your device.
2. Open it from your browser's downloads or a file manager.
3. If Android says installing unknown apps is blocked, tap **Settings** in the prompt and turn on **Allow from this source** for the app you used to open the file (for example, Chrome or Files). Then go back and tap **Install**.
4. You can turn the permission off again after installing.

To update, install the newer APK over the existing app. Your data is kept because it is signed with the same key.

### How do I verify the APK signature?

Use `apksigner` from the Android SDK Build Tools:

```sh
apksigner verify --print-certs DomainQ-x.y.z.apk
```

Check that the output includes:

```
Signer #1 certificate SHA-256 digest: 6aa0a1d4156a0f7bd6b14baf9a8b996560914ab1afc73d0299a36a0ada6d1d7c
```

This is the same value as the colon-separated form:

```
6A:A0:A1:D4:15:6A:0F:7B:D6:B1:4B:AF:9A:8B:99:65:60:91:4A:B1:AF:C7:3D:02:99:A3:6A:0A:DA:6D:1D:7C
```

If the digest does not match, do not install the file. Download it again from the official [releases page](https://github.com/seagen-lab/DomainQuery_Android/releases).

### Is DomainQ open source?

No. This repository contains documentation and release downloads only. See the [License](../LICENSE).

---

Still stuck? Open an issue on [GitHub Issues](https://github.com/seagen-lab/DomainQuery_Android/issues).
