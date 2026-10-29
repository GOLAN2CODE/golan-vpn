# Golan VPN: feature and use guide

[العربية](GUIDE.ar.md) · [Overview](README.md) · [Downloads and full source](https://github.com/GOLAN2CODE/golan-vpn/releases)

## Purpose and first connection

Version **1.0.1-rc3 / code 4** is an Android VPN client for Android 7/API 24 or newer. It connects the phone to an external VPN server using WireGuard, OpenVPN UDP/TCP or Outline/Shadowsocks. The app needs a valid server configuration; installing it does not create your own VPN server or guarantee that a public server is online.

Download the debug APK and checksum file from Releases. Install it through Android's package installer, allowing installation for the app opening the file if needed. Choose the protocol matching your configuration and enter or import its details: WireGuard configuration text, OpenVPN profile/content, or an Outline access key. Use the dedicated protocol pages/manual slots to keep configurations distinct. Save the configuration, select it and start the connection. Android asks for VPN consent; approve it only when you intend to route traffic through that provider.

## Servers, routing and feedback

Saved server management lets you retain and revisit configurations rather than re-entering them for each connection. Provider discovery can fetch candidate information from VPNBook or VPN Gate; review the resulting server and protocol before connecting. Public endpoints, passwords and availability can change, so a previously working entry may later need refreshing or replacement.

The connection screen and diagnostics report engine state, traffic counters and connection information. Public-IP checks contact ipify or Amazon's check-IP endpoint over the captured VPN route. These outputs help investigate whether a tunnel is working; a connection indicator or one IP result is not a complete anonymity, DNS/IPv6 or leak audit. When using split tunneling, review which apps are included or excluded: that choice affects what traffic uses the VPN.

The foreground VPN service and its notification support connection operation on the phone. Connection lifecycle handling coordinates starting, stopping and network changes, but Android/OEM restrictions and the remote server can still interrupt service. The bundled Outline native library is arm64; other APK ABI entries do not establish Outline functionality on every architecture.

## Configuration protection and backups

Local configuration storage protects saved credentials using Android-backed facilities. The portable server/manual-slot backup flow asks for a passphrase of at least ten characters and creates an encrypted backup file through Android's picker. Keep the file and passphrase safely; restore uses both. A newly built debug APK may have a different signing key. Export what you need before uninstalling, because uninstalling removes local settings.

Internet/network and foreground-service permissions support the tunnel and discovery. Android's VPN approval is separate from installing the APK; notification permission may also be requested. Read [third-party details](THIRD_PARTY.md) for the remaining native dependency audit questions. This preview is not a blanket security certification.

## Costs and computer FAQ

No personal billed API key or payment integration was found in the reviewed production source. VPNBook's shared provider credentials/client key are protocol material, not an API key spending your AI credits. The app uses public or user-configured external servers; mobile data, a paid VPN subscription or hosting your own server can still cost money. It does not require your computer, Codex or this chat to stay running. A server you personally choose to host on a computer would, naturally, need that server to remain reachable.
