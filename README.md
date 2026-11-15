<h1 align="center"><img src="docs/images/app-icon.png" width="56" height="56" align="absmiddle" alt="Shark"> Shark</h1>

<p align="center"><b>Multi-device Android One-Click Temporary Root & Root Manager Switcher</b></p>

<p align="center">
  <a href="https://github.com/darsaliq00/Shark/releases/tag/v2.4.2"><img src="docs/badges/release.svg" alt="Release"></a>
  <a href="LICENSE"><img src="docs/badges/license.svg" alt="License"></a>
  <img src="docs/badges/android.svg" alt="Android">
  <img src="docs/badges/kotlin.svg" alt="Kotlin">
  <img src="docs/badges/compose.svg" alt="Compose">
  <img src="docs/badges/kernel.svg" alt="Kernel">
  <a href="https://gitee.com/puci1/Shark/releases/tag/v2.2.3"><img src="docs/badges/gitee.svg" alt="Gitee"></a>
</p>

> [!NOTE]
> **Credits & Upstream Attribution**:
> This repository is an English translation fork of the original [Shark](https://github.com/Yunnijian/Shark) created by [Yunnijian](https://github.com/Yunnijian).
> All original exploit implementations, kernel modules, and code logic belong to Yunnijian and upstream contributors.
> This fork only translates the user interface, manual, and documentation to English with no copyright claims.

Shark supports OnePlus, OPPO, Realme, iQOO and other devices without unlocking bootloader (BL). Only requires adb shell to start. The app drives the on-device exploit via Stellar or Shizuku, obtains temporary kernel privileges, and loads the LKM corresponding to the selected root manager, providing a KernelSU, KernelSU-Next, BakaSU, SukiSU Ultra, or FinaSU root environment.

## Interface

<table align="center">
  <tr>
    <td align="center"><img src="docs/screenshots/app-home.jpg" width="180" alt="Home"><br><sub><b>Home</b></sub></td>
    <td align="center"><img src="docs/screenshots/app-manager-dropdown.jpg" width="180" alt="ROOT Manager"><br><sub><b>ROOT Manager</b></sub></td>
    <td align="center"><img src="docs/screenshots/app-extras.jpg" width="180" alt="Extras"><br><sub><b>Extras</b></sub></td>
  </tr>
  <tr>
    <td align="center"><img src="docs/screenshots/kernelsu-manager.jpg" width="180" alt="KernelSU Manager"><br><sub><b>KernelSU</b></sub></td>
    <td align="center"><img src="docs/screenshots/bakasu-manager.jpg" width="180" alt="BakaSU Manager"><br><sub><b>BakaSU</b></sub></td>
    <td align="center"><img src="docs/screenshots/sukisu-manager.jpg" width="180" alt="SukiSU Manager"><br><sub><b>SukiSU Ultra</b></sub></td>
  </tr>
</table>

## Supported Devices

| Device | OS | Full Kernel Release |
| --- | --- | --- |
| OnePlus 16 (PYB110) | ColorOS 17 | `6.18.21-android17-5-gf957accaf563-ab15926176-4k`<br>`6.18.21-android17-5-g7fcbffcad3e1-ab16353812-4k` |
| OnePlus 15 (PLK110) | ColorOS 17 | `6.12.69-android16-6-g242e1a07f878-ab15865446-4k`<br>`6.12.69-android16-6-g5fd39602326e-ab16372235-4k` |
| OnePlus 15T (PLZ110) | ColorOS 17 | `6.12.69-android16-6-g242e1a07f878-ab15865446-4k`<br>`6.12.69-android16-6-g5fd39602326e-ab16372235-4k` |
| OnePlus Ace7 Pro (PMS110) | ColorOS 17 | `6.12.69-android16-6-g242e1a07f878-ab15865446-4k`<br>`6.12.69-android16-6-g5fd39602326e-ab16372235-4k` |
| OnePlus Ace7 (PYF110) | ColorOS 17 | `6.12.69-android16-6-g242e1a07f878-ab15865446-4k`<br>`6.12.69-android16-6-g5fd39602326e-ab16372235-4k` |
| OnePlus Ace6T (PLR110) | ColorOS 17 | `6.12.69-android16-6-g242e1a07f878-ab15865446-4k`<br>`6.12.69-android16-6-g5fd39602326e-ab16372235-4k`<br>`6.12.38-android16-5-g844001fb8721-ab14552068-4k` |
| OnePlus Ace6 Ultra (PMB110) | ColorOS 17 | `6.12.69-android16-6-g242e1a07f878-ab15865446-4k`<br>`6.12.69-android16-6-g5fd39602326e-ab16372235-4k` |
| OnePlus Ace6 (PLQ110) | ColorOS 17 | `6.6.118-android15-8-g9bc34d5b0c79-abogki537459655-4k` |
| OnePlus Ace5 Pro (PKR110) | ColorOS 17 | `6.6.118-android15-8-g9bc34d5b0c79-abogki537459655-4k` |
| OnePlus Pad3 Pro (OPD2513) | ColorOS 16/17 | `6.12.69-android16-6-g242e1a07f878-ab15865446-4k`<br>`6.12.69-android16-6-g5fd39602326e-ab16372235-4k`<br>`6.12.58-android16-6-g7704a1ae279b-ab15213644-4k` |
| OnePlus Pad2 Pro (OPD2413) | ColorOS 17 | `6.6.118-android15-8-gc4127a25dcf3-ab15863337-4k` |
| OPPO Find X9 Ultra (PMA110) | ColorOS 17 | `6.12.69-android16-6-g242e1a07f878-ab15865446-4k`<br>`6.12.69-android16-6-g5fd39602326e-ab16372235-4k` |
| OPPO Find X9 Pro (PLG110) | ColorOS 17 | `6.12.69-android16-6-g242e1a07f878-ab15865446-4k`<br>`6.12.69-android16-6-g5fd39602326e-ab16372235-4k` |
| OPPO Find X9 (PLJ110) | ColorOS 17 | `6.12.69-android16-6-g242e1a07f878-ab15865446-4k`<br>`6.12.69-android16-6-g5fd39602326e-ab16372235-4k` |
| OPPO Find X9s Pro (PME110EX) | ColorOS 17 | `6.12.69-android16-6-g242e1a07f878-ab15865446-4k`<br>`6.12.69-android16-6-g5fd39602326e-ab16372235-4k` |
| OPPO Find X10 (PMX110) | ColorOS 17 | `6.12.69-android16-6-g242e1a07f878-ab15865446-4k`<br>`6.12.69-android16-6-g5fd39602326e-ab16372235-4k` |
| OPPO Find X8 Ultra (PKJ110) | ColorOS 17 | `6.6.118-android15-8-g9bc34d5b0c79-abogki537459655-4k` |
| OPPO Find N5 (PKH110) | ColorOS 17 | `6.6.118-android15-8-gc4127a25dcf3-ab15863337-4k` |
| OPPO Pad Mini (OPD2515) | ColorOS 16/17 | `6.12.69-android16-6-g242e1a07f878-ab15865446-4k`<br>`6.12.69-android16-6-g5fd39602326e-ab16372235-4k`<br>`6.12.58-android16-6-g7704a1ae279b-ab15213644-4k` |
| OPPO Pad 5 Pro (OPD2511) | ColorOS 17 | `6.12.69-android16-6-g242e1a07f878-ab15865446-4k`<br>`6.12.69-android16-6-g5fd39602326e-ab16372235-4k` |
| OPPO Pad4 Pro (OPD2409) | ColorOS 17 | `6.6.118-android15-8-gc4127a25dcf3-ab15863337-4k` |
| Realme GT8 Pro (RMX5200) | ColorOS 17 | `6.12.69-android16-6-g242e1a07f878-ab15865446-4k`<br>`6.12.69-android16-6-g5fd39602326e-ab16372235-4k` |
| Realme GT8 (RMX6699) | ColorOS 17 | `6.6.118-android15-8-g9bc34d5b0c79-abogki537459655-4k` |
| OPPO K13 Turbo Pro (PLE110) | ColorOS 17 | `6.6.118-android15-8-g9bc34d5b0c79-abogki537459655-4k` |
| Realme Neo8 (RMX8899) | ColorOS 16/17 | `6.12.38-android16-5-g844001fb8721-ab14552068-4k`<br>`6.12.69-android16-6-g242e1a07f878-ab15865446-4k`<br>`6.12.69-android16-6-g5fd39602326e-ab16372235-4k` |
| vivo / iQOO Models | OriginOS 6/7 | `6.12.58-android16-6-g690108013dcc-abogki576129896-4k`<br>`6.12.58-android16-6-g0a092cc0037a-abogki521987229-4k`<br>`6.12.58-android16-6-gdd6fd5c98918-abogki543627742-4k`<br>`6.12.23-android16-5-g41f4cb1fa7c7-abogki465038634-4k`<br>`6.6.127-android15-8-gd489d4ad2a70-abogki567717946-4k` |

## Supported Managers

KernelSU, KernelSU-Next, BakaSU, SukiSU Ultra, and FinaSU.

Manager APKs are not distributed with Shark. Standard mode directly utilizes `ksud` inside the installed manager APK, so **install whichever manager you intend to use beforehand**.

## Features

- **One-Click Temporary Root**: No manual exploit selection required. Automatically matches the 7 exploit chains (6.18.21 / 6.12.69 / 6.12.38 / 6.12.58 / 6.12.23 / 6.6.118 / 6.6.127) based on `uname -r`. Tap "One-Click Jailbreak" to perform privilege escalation, `ksud late-load`, module install, and manager launch. Temporary root disappears upon reboot.
- **Five Root Managers Available**: Select KernelSU, KernelSU-Next, BakaSU, SukiSU Ultra, or FinaSU directly from the dropdown. Not tied to a single manager; standard mode uses `ksud` and LKM directly from your installed APK.
- **Hot-switch Root Manager**: Supported on 6.18 and 6.12 kernels. Select `Dynamic Switching` on clean boot to load the universal KSU LKM (initial: KernelSU), then switch to any target manager under Extras -> "Hot-switch Root Manager". Synchronizes version, features, private ioctl, primary manager, and restarts target manager without rebooting. Also supports **Custom / Spoofed Package Names** via `/proc/kernelsu_manager`.
- **Extras**: Load VFS provider on 6.18; load SUSFS on 6.12 / V2505A; toggle security prompt suppression, soft reboot after jailbreak, and unload kernel security guards. Independent toggles won't break root if one fails.
- **Logs & History**: Real-time streaming logs during execution. Every run saves a full `.log` in History tab. View, delete, or swipe right to export and share.
- **Online Updates**: Checks Gitee Releases first, falls back to GitHub. In-app download verifies SHA-256 and APK signature before delegating to system package installer.
- **Droidspaces Support**: On 6.18, fetch latest `droidspaces_lkm` release, download zip to `Download/Shark/`, and flash via KernelSU Manager.

## Two Root Modes

### Standard Mode

Select a manager in the dropdown. The app uses `ksud` bundled in that manager's APK to load its own LKM. This is the native root environment for that manager.

Switching managers in standard mode requires a device reboot.

### Dynamic Switching Mode

Select `Dynamic Switching` in the ROOT Manager dropdown. The app loads the universal KSU LKM using bundled `libksud_universal.so` (initial manager is KernelSU).

After loading, "Hot-switch Root Manager" appears in Extras. Pick any target manager from the dropdown to switch instantly. Modifies only the in-kernel manager profile without unloading modules or rebooting.

Because universal KO shares hook symbols with stock KSU, it must be loaded on a clean boot without existing KSU loaded.

## Usage

1. Install target root manager APK(s). If using Dynamic Switching, installing all five is recommended.
2. Launch Stellar or Shizuku and grant permission to Shark.
3. Select your manager or `Dynamic Switching` in ROOT Manager dropdown.
4. Toggle optional features in Extras as desired.
5. Tap "One-Click Jailbreak" and wait for `DONE` in logs.
6. In Standard Mode, open your manager to grant root. In Dynamic Switching, select target manager in Extras to switch and open.

## Architecture

Shark consists of an Android App, on-device exploit runners, and optional kernel modules.

```text
Shark/
├── app/                         Android App (Gradle Project)
│   ├── app/src/main/java/com/shark/kty/
│   │   ├── MainActivity.kt      Tabs, flow control, manager & extras state
│   │   ├── UpdateChecker.kt     Gitee / GitHub update checker
│   │   ├── HistoryStore.kt      Log persistence, run history
│   │   └── DroidspacesModule.kt Droidspaces module download
│   ├── app/src/main/jniLibs/arm64-v8a/
│   │   ├── libk61821.so         6.18.21 runner
│   │   ├── libk61269.so         6.12.69 runner
│   │   ├── libk61238.so         6.12.38 runner
│   │   ├── libk61258.so         6.12.58 runner
│   │   ├── libk61223.so         6.12.23 runner
│   │   ├── libk66118.so         6.6.118 runner
│   │   ├── libk66127.so         6.6.127 runner
│   │   ├── libksud_universal.so Dual KMI universal loader
│   │   ├── libsusfs_guard_lkm.so
│   │   ├── libsusfs_guard_lkm_612.so
│   │   └── libhybridmount.so
│   ├── app/src/main/assets/     manual.md, licenses, donation QR
│   └── gradle/, keystore/
├── exploit/
│   ├── rust-k61821/             6.18.21 Rust runner
│   ├── rust-kplant/             6.12 / 6.6 Rust runner (features select K source)
│   └── src/                     plant_core.inc + K<version>_plant.c (per kernel)
├── lkm/
│   ├── susfs4ksu-lkm/           SUSFS guard source
│   ├── hybridmount/             VFS provider source
│   └── susfs-tools/             SUSFS rules tools
├── docs/screenshots/            README screenshots
├── ports/v2505a/                V2505A notes and verification records
├── ports/coloros-61269/         6.12.69 dual OTA build notes & recovery tools
├── ports/pkj110-66118/          PKJ110 6.6.118 notes and verification records
├── ports/pd2454-66127/          vivo 6.6.127 notes and verification records
├── third_party/                 Third-party licenses and materials
├── NOTICE / LICENSE
└── README.md
```

**Component Responsibilities**

- `app/`: Kotlin/Compose UI, Shizuku/Stellar calls, exploit selection, feature toggles, logging, and OTA update checking.
- `exploit/`: Rust runner and C plant, privilege escalation, fake creds, `ksud late-load`, and post-cleanup.
- `lkm/`: SUSFS guard and Hybrid Mount VFS provider source and build scripts.
- `ports/`: Device/kernel-specific notes, constants, and verification tools.
- `third_party/`: Third-party licenses and reference implementations.

**Tech Stack**

- App: Kotlin, Jetpack Compose, COUI-Kit, Shizuku / Stellar API.
- On-device: Rust + C, Android NDK arm64.
- Kernel side: C / GPL-2.0 LKM; Universal KSU KO in standalone project [KSU-Universal](https://github.com/Yunnijian/KSU-Universal).
- Build: Gradle Kotlin DSL, Cargo, Android SDK/NDK, Docker DDK.

## Compilation

App:

```bash
cd app
./gradlew :app:assembleRelease
```

On-device runners (one `libk<version>.so` per kernel, packaged into jniLibs):

```bash
export ANDROID_NDK_HOME=/path/to/ndk
./exploit/build-all.sh
```

Single target build:

```bash
cd exploit/rust-kplant
cargo build --release --target aarch64-linux-android \
    --no-default-features --features k66118
```

Available features: `k61269`, `k61238`, `k61258`, `k61223`, `k66118`; 6.18.21 built independently via `rust-k61821`.

Universal KO and dual KMI loader are built in [KSU-Universal](https://github.com/Yunnijian/KSU-Universal); Shark includes the precompiled `libksud_universal.so`.

## Disclaimers & Notice

- Dynamic Switching must run initially on a clean boot; subsequent switches do not require reboot.
- Standard mode requires pre-installing the chosen manager APK.
- KPM is not yet enabled.
- CVE-2026-98260 is a race-condition UAF; any run could cause a kernel panic or reboot.
- For research on owned devices only. Use at your own risk.

## Credits, Source & Licenses

- **Original Author**: [Yunnijian](https://github.com/Yunnijian) ([Yunnijian/Shark](https://github.com/Yunnijian/Shark))
- **English Translation Fork**: Maintained by [darsaliq00](https://github.com/darsaliq00). This fork only translates UI strings, user manual, and documentation to English with zero copyright claim over original code or assets.
- Shark original code licensed under GPL-3.0 (see `LICENSE`); third-party components listed in `NOTICE`.
- Universal KSU LKM based on SukiSU Ultra (GPL-3.0).
- SUSFS guard and Hybrid Mount are GPL-2.0.
- CVE-2026-98260 design references AzirX1337's public implementation (MIT).
- UI utilizes COUI-Kit (MPL-2.0), remote execution uses Shizuku API (Apache-2.0).

## Releases

- GitHub: https://github.com/darsaliq00/Shark/releases/tag/v2.4.3
- Upstream: https://github.com/Yunnijian/Shark/releases/tag/v2.2.3
- App: v2.4.3 (102)

Universal Kernel Releases:

- https://github.com/Yunnijian/KSU-Universal/releases/tag/v1.1.0
- `ksu_universal-android16-6.12.ko`
- `ksu_universal-android17-6.18.ko`
- `ksud_universal`
