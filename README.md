# PepoMote Legacy Android Backport

This fork is an **unofficial Android client backport in progress**. Its goal is to support Android 4.4.4 KitKat (API 19) through Android 7.1.2 Nougat (API 25) on 32-bit `armeabi-v7a` and `x86` devices, while connecting to the **unmodified vanilla PepoMote PC receiver**.

The intended scope is the full Android experience where the legacy platform permits it: QR and manual pairing, LAN discovery, controller/Wiimote, Dolphin, Wii U/GamePad screen, Switch Pro, RetroArch, Nunchuk, and the Android Server. API-26+ facilities must be replaced with API-19–25 equivalents or isolated behind version-specific fallbacks rather than silently dropping features. Hardware-dependent capabilities such as camera, sensors, Wi-Fi multicast and emulator integration must be tested on devices.

## Compatibility status

The upstream Android source is built around Jetpack Compose and modern AndroidX. Those dependencies and UI APIs do not become KitKat-compatible by changing `minSdk`; the UI/dependency migration and API-specific replacements are still required. Do not treat this repository or APK as API 19–25 validated until the Android build workflow and physical-device tests pass. See [the backport audit](ANDROID_API19_25_AUDIT.md) for the file/component review and implementation plan.

## Interoperability

PC-side code and the PMP v1 protocol are not being forked or changed for this Android backport. The Android client must use the existing TCP JSON-lines handshake/pairing and UDP PMP1 packet layouts, including the protocol's capability rules for extended packets. The vanilla receiver remains the compatibility reference; no custom PC receiver or fork-only handshake should be required.

## Build

Build instructions will be finalized once the legacy Android toolchain and UI migration are in place. The intended output is a debug/release APK containing only `armeabi-v7a` and `x86` native ABI payloads, with `minSdk 19` and `targetSdk 25`. The current modern Android build configuration is not yet a verified build recipe for this target range.

## Project status and attribution

This is a community-maintained, unofficial fork of PepoMote, not affiliated with or endorsed by PepoTech. Existing upstream protocol specifications and golden vectors are retained as interoperability references. Other upstream platform sources are not modified as part of the Android backport.
