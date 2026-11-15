# Shark User Manual

Shark drives the on-device 98260 exploit as shell via Stellar or Shizuku, and loads the selected root manager LKM. On first use, grant permission, then tap One-Click Jailbreak.

> Shark currently supports Oplus devices with 6.18.21, 6.12.69, 6.12.38, 6.12.58, 6.12.23, 6.6.118, and 6.6.127 kernels, matched exactly against `uname -r`. Unmatched devices will report unsupported.

## Quick Start

1. Install your chosen ROOT manager first (KernelSU / FinaSU / KernelSU Next / BakaSU / SukiSU Ultra). **CI builds of KernelSU Next are currently not supported**.
2. Start and activate **Stellar (Recommended)** or **Shizuku** via **wireless debugging or adb**, and grant permission to Shark.
3. Return to Shark home and tap "One-Click Jailbreak", then wait for success logs: confirmed by `DONE`, `SU_ID_RC=0`, and `uid=0(root)`.
4. After success, the manager launches automatically. If enabled, it also disables security prompts and loads **SUSFS** (6.18/6.12 series; 6.12 uses `libsusfs_guard_lkm_612.so`) or **VFS** (6.18.21 only).
5. If the log shows **MODULE NOT LOADED**, no reboot is required; simply tap Jailbreak again.
6. Updates are checked automatically on launch (Gitee Releases prioritized, GitHub fallback). New versions show an update dialog to download and install directly. You can also manually check in the "About" tab.

## Permissions & Preparation

- **Stellar first, Shizuku fallback**: When both exist, Stellar is used; falls back to Shizuku if Stellar is unavailable.
- **Root manager must be pre-installed**: `ksud` is not bundled inside Shark; it executes directly from the installed manager APK's `lib/arm64`.
- **Clean boot recommended**: 6.18.21, 6.12.69, 6.12.38, 6.12.58, 6.12.23, 6.6.118, and 6.6.127 each have independent entry points; the app matches exact `uname -r`.

## Jailbreak Workflow

**preflight** (kernel release / trace channel) → **98260 UAF** (fake cred / SELinux zero write) → **cred child process one-shot ksud late-load** → wait for module & su → **post-cleanup** (ksud install, unload kernel guards, SUSFS, VFS, screenshot restore, launch manager).

Each kernel version has independent K source and `libk<version>.so`; shared engine in `plant_core.inc`. vivo devices (6.12.23 / 6.12.58 vivo build / 6.6.127) zero out tracepoint func slots used by `vr.ko` before waking root child process; 6.6.127 also clears `sched_process_exit` slot. 6.12.58 OS7 (`gdd6fd5c98918`) and 6.6.127 also bypass `hooks_defend` load gate: locate module, one-shot zero unlock, publish khs whitelist, then load KO in-process.

- **Fast path** plant takes ~2–3 sec, total flow ~4–9 sec; non-cache-hit reclaim takes a few extra seconds.
- **On chain failure**: Pages held by plant transfer to holder, can retry directly within the same boot; do not manually kill or reap holder.

## Features

- **Home**: ROOT Manager dropdown, toggles (VFS shown only on 6.18; vivo V2505A hides anti-root options; 6.6.118 / 6.6.127 hide SUSFS/VFS/Hot Switch; 6.12.58 OS7 hides SUSFS but keeps Hot Switch); info card shows kernel version and auto-selected exploit.
- **Logs**: Real-time streaming log of current run.
- **History**: Each run saves a `.log`; tap to view, swipe left for "Export" button to share.
- **About**: Version, Check Updates, Source Code / Join Community / Issue Tracker, AboutLibraries dependency list (versions, licenses, details), and offline bundled open-source license texts (GPL-3.0, NOTICE, Apache-2.0, MIT, GPL-2.0, MPL-2.0).
- **Extras → Droidspaces Support** (6.18.21 only): "Download Module" fetches latest release of `Droidspaces-LKM` from GitHub, saves zip to `Download/Shark/`. Flash via KernelSU Manager → Modules → Install.
- **ROOT Manager → Dynamic Switching** (6.18.21 / 6.12.69 / 6.12.38 / 6.12.58 / 6.12.23; not 6.6.118): Run once on clean boot; `libksud_universal.so` loads universal KSU LKM (initial KernelSU, embeds 6.18/6.12 dual KMI KO). Adds "Manager Hot Switch" in Extras to switch between KernelSU / KernelSU-Next / BakaSU / SukiSU / FinaSU on the fly without rebooting.

## Troubleshooting

| Log | Action |
| --- | --- |
| `PROBE_FAIL` / `kernel mismatch` | Current kernel not in support list (matches exact `uname -r` for 6.18.21 / 6.12.69 / 6.12.38 / 6.12.58 / 6.12.23 / 6.6.118 / 6.6.127). |
| `MANAGER` / `KSUD_MISSING` | Install the required root manager APK first. |
| `STALE_PLANT` | Previous plant still running; retry once it becomes holder. |
| `PLANT_FAIL` | Plant preserves holder and exits; retry directly in same boot. |
| `LATE_LOAD_FAIL` | Module did not appear in time; check ksud output in logs and retry. |
| Kernel crash / reboot | Inherent race condition risk of 98260; reboot and retry. |

## Execution Details

- **6.18.21** → `libk61821.so`; **6.12.69** → `libk61269.so` (two OTA builds select call site by uname).
- **6.12.38 (PLR110)** → `libk61238.so`; **6.12.58 (PLZ110 / V2505A OS6/OS7)** → `libk61258.so`; **6.12.23 (V2505A)** → `libk61223.so`.
- **6.6.118 (PKJ110 / PKH110 / Pad, etc.)** → `libk66118.so` (two OTA builds select call site by uname); KMI android15-6.6.
- **6.6.127 (vivo X200 Ultra / PD2454)** → `libk66127.so`; KMI android15-6.6, uses vivo hooks_defend bypass.
- All matched by **exact `uname -r`**; unmatched kernels immediately report unsupported.
- All entry points run in-place from native library dir (`nativeLibraryDir`), cwd/HOME/TMPDIR set to app filesDir, no files deployed to `/data/local/tmp`. `ksud` executes in-place from installed manager APK. SUSFS supported on 6.18/6.12 (6.12 uses `libsusfs_guard_lkm_612.so`); VFS open only for 6.18.
- For research on owned devices only.
