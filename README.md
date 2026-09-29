<img src="assets/banner.png" align="center" width="100%" />
<p align="center">
    The new All-in-One CFW package for the Nintendo Switch.</br>
    <a href="https://discord.gg/VkaRjYN">
        <img alt="Discord" src="https://img.shields.io/discord/703301751171973190?label=Join%20DeepSea%20on%20Discord&style=flat-square">
    </a> 
    <img alt="GitHub All Releases" src="https://img.shields.io/github/downloads/Team-Neptune/DeepSea/total?label=Total%20downloads&style=flat-square">
    <img alt="GitHub Workflow Status" src="https://img.shields.io/github/actions/workflow/status/Team-Neptune/DeepSea/buildRelease.yml?branch=master&style=flat-square">
</p>

---

## Features

- Background FTP server for filetransfers
- Install NSP & XCI files from Harddrive, WiFi or wired through PC, Smartphone, etc
- Over & Underclocking
- Update OFW & CFW through homebrew
- Find new homebrew through the Appstore
- Savegame management
- Cheating in games (please don't cheat online)
- Emulate Amiibo
- Use all kinds of 3rd party controllers
- Lan play (like Hamachi for your Switch)
- Tesla overlay to control all those features (press L1+DpadDown+RightStick)


**Please check out our [wiki](https://github.com/Team-Neptune/DeepSea/wiki) to learn about the best features**


## How to use
Follow this guide to hack your Switch: https://switch.homebrew.guide

Download the latest release and put it on your SD Card<br />
Send the Hekate payload to your Switch in RCM mode and launch the CFW


## Featuring

| Software | Advanced Package| Normal Package | Minimal Package |
| -------- | :-------------: | :------------: | :------------: |
| [AIO-switch-updater](https://github.com/HamletDuFromage/aio-switch-updater) | ✅ | ✅ |  |
| [Atmosphère](https://github.com/Atmosphere-NX/Atmosphere) | ✅ | ✅ | ✅ |
| [DeepSea Assets](https://github.com/Team-Neptune/DeepSea-Assets) | ✅ | ✅ | ✅ |
| [DeepSea Cleaner](https://github.com/Team-Neptune/DeepSea-Cleaner) | ✅ | ✅ |  |
| [DeepSea CPR](https://github.com/Team-Neptune/CommonProblemResolver) | ✅ | ✅ |  |
| [DeepSea Toolbox](https://github.com/Team-Neptune/DeepSea-Toolbox) | ✅ | ✅ |  |
| [EdiZon-SE](https://github.com/tomvita/EdiZon-SE) | ✅ | ✅ |  |
| [EdiZon-Overlay](https://github.com/proferabg/EdiZon-Overlay) | ✅ | ✅ |  |
| [Emuiibo](https://github.com/XorTroll/emuiibo) | ✅ | ✅ |  |
| [Hekate](https://github.com/CTCaer/hekate) | ✅ | ✅ | ✅ |
| [Homebrew App Store](https://gitlab.com/4TU/hb-appstore) | ✅ | ✅ | ✅ |
| [JKSV](https://github.com/J-D-K/JKSV) | ✅ | ✅ |  |
| [ldn_mitm](https://github.com/spacemeowx2/ldn_mitm) | ✅ |  |  |
| [MissionControl](https://github.com/ndeadly/MissionControl) | ✅ |  |  |
| [nx-ovlloader](https://github.com/WerWolv/nx-ovlloader) | ✅ | ✅ |  |
| [NX-Shell](https://github.com/joel16/NX-Shell) | ✅ |  |  |
| [ovlSysmodules](https://github.com/WerWolv/ovl-sysmodules) | ✅ | ✅ |  |
| [Status Monitor Overlay](https://github.com/masagrator/Status-Monitor-Overlay) | ✅ |  |
| [sys-clk](https://github.com/retronx-team/sys-clk) | ✅ |  |
| [sys-con](https://github.com/cathery/sys-con) | ✅ |  |  |
| [sys-ftpd](https://github.com/cathery/sys-ftpd) | ✅ | ✅ |  |
| [TegraExplorer](https://github.com/joel16/NX-Shell) | ✅ |  |  |
| [Tesla-Menu](https://github.com/WerWolv/Tesla-Menu) | ✅ | ✅ |  |
| [Goldleaf](https://github.com/XorTroll/Goldleaf) | ✅ | ✅ |  |



## Changes from upstream DeepSea

Personal fork of [Team-Neptune/DeepSea](https://github.com/Team-Neptune/DeepSea). The
*Features* and *Featuring* lists above describe upstream DeepSea; this section describes what
this fork actually ships. Only `src/settings.json` differs from upstream - `src/start.py`,
`src/fs.py` and `src/gh.py` are untouched.

### Added modules

| Module | Source | Purpose |
| --- | --- | --- |
| `syspatch` | [borntohonk/sys-patch](https://github.com/borntohonk/sys-patch) | Signature patches for fs/es/ldr/nifm/nim, applied in memory at boot. Upstream ships **no** signature patches, so unsigned NSP/XCI files cannot be installed or started. Independent of the firmware/Atmosphere version and auto-started through `boot2.flag`. |
| `ultrahand` | [ppkantorski/Ultrahand-Overlay](https://github.com/ppkantorski/Ultrahand-Overlay) | Replaces Tesla Menu. Its `sdout.zip` release already bundles `nx-ovlloader`, so the standalone `nxovlloader` module was dropped to avoid two overlay loaders fighting for the same hook. |
| `dbi` | [rashevskyv/DBIPatcher](https://github.com/rashevskyv/DBIPatcher) | DBI 905 (the runtime-translation build) plus the Simplified Chinese table, installed as `/switch/DBI/DBI.nro` and `/switch/DBI/translation.bin`. |
| `sphaira` | [NaGaa95/sphaira](https://github.com/NaGaa95/sphaira) | Homebrew menu, file browser and installer (NSP/XCI/NSZ/XCZ/MSP from SD card, USB, FTP or MTP) with a Chinese UI. |

### Removed modules

`deepseacleaner`, `deepseacpr`, `emuiibo`, `goldleaf`, `ldn_mitm`, `missioncontrol`,
`statusmonitoroverlay`, `syscon`, `sysftpd`, `tegraexplorer`, `nxovlloader`, `teslamenu`

### Changed modules

- `atmosphere`: the stock `hbmenu.nro` is copied to `/switch/hbmenu.nro` before it gets replaced.
- `edizon`: `EdiZon.nro` is moved into `/switch/EdiZon/` instead of being left in the SD card root, so nx-hbmenu can list it.
- `ovlsysmodules`: source changed from `WerWolv/ovl-sysmodules` to the maintained `ppkantorski/ovl-sysmodules`.

### Packages

`normal` was removed and `minimal` is disabled, so a build only produces
`deepsea-advanced_v<releaseVersion>.zip`:

- **minimal** (inactive): `atmosphere`, `hekate`, `deepseaassets`, `syspatch`, `hbappstore`
- **advanced** (active): `atmosphere`, `hekate`, `deepseaassets`, `syspatch`, `hbappstore`, `deepseatoolbox`, `aioupdater`, `edizon`, `edizon-ovl`, `jksv`, `sysclk`, `ovlsysmodules`, `nxshell`, `ultrahand`, `dbi`, `sphaira`

### The Album applet boots Sphaira

The `sphaira` module copies `switch/sphaira/sphaira.nro` over `hbmenu.nro` in the SD card root,
so the Album applet starts Sphaira directly. The original nx-hbmenu is still shipped, as
`/switch/hbmenu.nro`, and can be launched from Sphaira.

- Updating the CFW (for example with AIO-switch-updater) restores the stock `hbmenu.nro`; to
  re-apply, copy `/switch/sphaira/sphaira.nro` to `hbmenu.nro` in the SD card root again.
- To roll back, copy `/switch/hbmenu.nro` to the SD card root as `hbmenu.nro`.

### Keep this module order

Modules are merged into `sd/` in the order they are listed, and later modules overwrite earlier
ones. When editing `src/settings.json`, preserve these invariants:

1. `deepseaassets` after `hekate` - otherwise Hekate's stock `hekate_ipl.ini` and bootlogo win.
2. `sphaira` after `atmosphere` - otherwise the stock `hbmenu.nro` overwrites the Sphaira replacement.
3. `hekate` after `atmosphere` - so `atmosphere/reboot_payload.bin` ends up as Hekate's payload.

### Known issue: DBI can stay Russian

DBI's runtime translation is fragile; upstream reports
([DBIPatcher#12](https://github.com/rashevskyv/DBIPatcher/issues/12)) show it silently skipping
the translation table depending on which launcher started it. If DBI shows Russian, start it
from Sphaira instead, or simply use Sphaira's own installer.

### Build

```sh
cd src
python start.py -gt=<github token>
```

## Credits
* Thanks to all the previous members of Team AtlasNX for laying the groundwork for DeepSea.
* And a huge thanks to all the awesome homebrew developers!
