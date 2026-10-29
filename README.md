# Golan VPN

[Feature and use guide](GUIDE.md) · [دليل الاستخدام العربي](GUIDE.ar.md) · [Releases: APK and complete source](https://github.com/GOLAN2CODE/golan-vpn/releases)

[العربية](README.ar.md)

Android VPN client preview **1.0.1-rc3 / code 4**, package `com.ibngolan.vpn`. Android 7/API 24 or newer; compile SDK 35, target SDK 34. This repository is a sanitized snapshot of the current application source and existing tests.

## Features

- Separate WireGuard, OpenVPN UDP/TCP and Outline/Shadowsocks protocol engines and configuration screens.
- Import and manage user-provided tunnel configurations; dedicated manual protocol slots and saved server management.
- Provider/server fetch and review, connection diagnostics, tunnel traffic counters, split tunneling and connection lifecycle handling.
- Android VPN consent, foreground tunnel service and Arabic/English resources with GOLAN branding.
- Secure local configuration storage and portable backup/restore code are included. A working configuration and reachable server are required.

## Install and use

The existing delivery is a **debug-signed preview**, not a store release. The APK is unchanged from the delivered build. Enable installation for the app opening the APK, install, add a valid configuration and approve Android's VPN dialog. A different signing certificate prevents an in-place update; uninstalling removes local settings, so preserve an exported backup first.

The native dependency/source audit remains incomplete; see the exact known provenance and remaining questions in [THIRD_PARTY.md](THIRD_PARTY.md). This preparation does not establish production security acceptance or live server availability.

## Full source and build

The complete sanitized source is packaged as `golan-vpn-1.0.1-rc3-source.zip` for the release assets. Download and extract the ZIP before opening or building the project; a README-only repository view is not the application source. It contains application code, existing unit/instrumentation tests, Gradle wrapper, resources, local Outline JAR and native library. No signing keys or machine-local SDK configuration are included.

Install JDK 17 and Android SDK 35, set `ANDROID_HOME`/`ANDROID_SDK_ROOT` or create your own untracked `local.properties` with `sdk.dir`, then run from the extracted root:

```powershell
.\gradlew.bat :app:assembleDebug
```

On Linux/macOS: `chmod +x gradlew && ./gradlew :app:assembleDebug`. Gradle downloads declared Maven dependencies. Existing build configuration places generated outputs under the system temporary directory, in `GolanVPN-build/<project-path-hash>/app/outputs/apk/debug/`. Tests are supplied but were not rerun for this packaging operation. The native Outline binary included in source is arm64; the APK advertises other ABIs because other dependencies contain them, which does not establish Outline support on each ABI.

## Limits and privacy

Protocol implementations and server import code are present; connectivity, performance, DNS/IPv6 behavior and every device/protocol combination were not freshly tested here. Public VPN provider passwords and endpoints change. A connected UI alone does not prove anonymity, a working route or protection against every leak. Source declares Internet/network permissions, and server discovery/IP diagnostics contact external services. Review the selected provider and configuration before use.

The snapshot excludes local profiles, user backups, scraped server payloads, device logs, screenshots, build caches and historical development evidence. The application source itself is preserved, including existing tests and network behavior. No new project-wide license was assigned. See [LICENSE-STATUS.md](LICENSE-STATUS.md).
