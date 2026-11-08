# ImmortalWrt APK Mirror (aarch64_cortex-a53)

A complete mirror of all **ImmortalWrt 25.12.2** Alpine `.apk` packages for the `aarch64_cortex-a53` architecture, hosted on GitHub so you can install them even when `downloads.immortalwrt.org` is blocked or unreachable (e.g. behind aggressive DPI).

## Contents

| Category | Packages | Location |
|----------|----------|----------|
| base + packages (target feed) | 5329 | `aarch64_cortex-a53/*.apk` |
| kernel modules, kernel 6.12.103 (mediatek/filogic) | 1121 | `aarch64_cortex-a53/kmod-*.apk` |
| generic "packages" feed (coreutils, gzip, …) | 4865 | `packages/aarch64_cortex-a53/packages/*.apk` |
| **Total** | **~11.3k files** | |

All files are standard Alpine `.apk`, ready for `apk add`. Every index is signed with the official ImmortalWrt key (`openwrt-keyring` ships in the system), so `--allow-untrusted` is **not** needed.

## How to use

Point `/etc/apk/repositories` at the index files of this repository (direct file URLs — not a directory, see Notes):

```
https://raw.githubusercontent.com/I1obody/immortalwrt-mirror/main/aarch64_cortex-a53/packages.adb
https://raw.githubusercontent.com/I1obody/immortalwrt-mirror/main/aarch64_cortex-a53/packages-kmods.adb
https://raw.githubusercontent.com/I1obody/immortalwrt-mirror/main/packages/aarch64_cortex-a53/packages/packages.adb
```

Then install packages normally — `apk` fetches the `.apk` files from raw.githubusercontent.com:

```sh
apk update
apk add <package-name>        # e.g. coreutils, gzip
apk add kmod-tun              # kernel modules for 6.12.103 (zapret/nfqueue etc.)
```

## Repository layout

```
aarch64_cortex-a53/
├── packages.adb / packages.adb.sig     # signed index of the target feed
├── packages-kmods.adb / .sig           # signed index of kernel modules (1121)
├── APKINDEX / APKINDEX.tar.gz          # original combined plain-text index (unsigned)
└── *.apk                               # base + packages + kmod-* files

packages/aarch64_cortex-a53/packages/   # generic feed, own signed index inside
├── packages.adb / .sig
└── *.apk                               # 4865 packages (coreutils-*, gzip, …)
```

## Notes

- **Use direct `.adb` file URLs in `/etc/apk/repositories`, not a directory URL.** apk-tools then appends `<arch>/APKINDEX.tar.gz` to directories, which does not exist here and fails with "unexpected end of file".
- Built from `https://downloads.immortalwrt.org/releases/25.12.2/packages/aarch64_cortex-a53/`, `.../targets/mediatek/filogic/packages/` and `.../targets/mediatek/filogic/kmods/6.12.103-1-b5b7729ffbba3ecdd83f339de8fadfb8/`.
- The `luci`, `routing` and `telephony` categories are not mirrored — add them separately if needed.
- Tagged per ImmortalWrt release (`v25.12.2`). New kernel version → new kmods set; the tag tells you which one is inside.
