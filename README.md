# ImmortalWrt APK Mirror (aarch64_cortex-a53)

A complete mirror of all **ImmortalWrt 25.12.2** Alpine `.apk` packages for the `aarch64_cortex-a53` architecture, hosted on GitHub so you can install them even when `downloads.immortalwrt.org` is blocked or unreachable (e.g. behind aggressive DPI).

## Contents

| Category | Packages |
|----------|----------|
| base     | 597      |
| packages | 4635     |
| **Total** | **5232** |

All files are standard Alpine `.apk` (ADB format), ready for `apk add`.

## How to use

Add this repository to your router's `/etc/apk/repositories`:

```
https://raw.githubusercontent.com/I1obody/immortalwrt-mirror/main/aarch64_cortex-a53/
```

Then install packages normally:

```sh
apk update
apk add <package-name>
```

For example, to install the NFQUEUE kernel module needed by `zapret`:

```sh
apk add iptables-mod-nfqueue
```

## Repository layout

```
aarch64_cortex-a53/
├── APKINDEX          # plain-text package index (all 5232 packages)
├── APKINDEX.tar.gz   # compressed index (what apk fetches)
└── *.apk             # all package files
```

## Notes

- Built from `https://downloads.immortalwrt.org/releases/25.12.2/packages/aarch64_cortex-a53/`
- Only the `base` and `packages` categories are included (covers ~all common packages).
- The `luci`, `routing`, and `telephony` categories are not mirrored here — add them separately if needed.
- Packages are unsigned by ImmortalWrt's key; if you get an "UNTRUSTED signature" error, use `apk add --allow-untrusted <pkg>` or import the signing key first.
