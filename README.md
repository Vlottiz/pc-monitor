# PC Monitor

> A real-time hardware monitoring dashboard for Windows — built with C# + WebView2 + pure HTML/CSS/JS.

<div align="center">

[![Release](https://img.shields.io/github/v/release/Vlottiz/pc-monitor?style=flat-square&color=ffcc00)](https://github.com/Vlottiz/pc-monitor/releases/latest)
[![License](https://img.shields.io/badge/license-MIT-blue?style=flat-square)](LICENSE)
[![Platform](https://img.shields.io/badge/platform-Windows%2010%2F11-lightgrey?style=flat-square&logo=windows)]()
[![Coffee](https://img.shields.io/badge/Buy%20Me%20a%20Coffee-reyobu-ffdd00?style=flat-square&logo=buy-me-a-coffee&logoColor=black)](https://buymeacoffee.com/reyobu)

</div>

---

## Features

| Feature | Details |
|---|---|
| **CPU Monitoring** | Per-core clock speeds, temperatures, CCD temps (AMD), package power |
| **GPU Monitoring** | Temperature, clock speed, voltage, power draw, VRAM |
| **Fan Control** | Auto / Manual / Custom curve editor with drag-and-drop points |
| **Temperature History** | Min / Max / Avg for every thermal sensor on the system |
| **RGB Control** | OpenRGB integration (500+ devices) |
| **Multi-window** | Pop out any page to a separate window — run fans on one monitor, temps on another |
| **Themes** | 8 built-in color presets + full per-color customization + 3 saved profiles |
| **Hardware Auto-detect** | CPU, GPU, RAM, socket type all detected and displayed automatically |
| **AMD Full Support** | Per-core clocks, CCD0/CCD1 temps, Ryzen SMU sensors |
| **Intel Support** | All-core clock via Windows Performance Counters, 16-core P/E display |
| **Auto-updater** | Checks GitHub releases on startup |

---

## Screenshots

> *Coming soon — drop screenshots in `/docs/screenshots/` and update these links*

| Home | Performance | Fan Control |
|---|---|---|
| ![Home](docs/screenshots/home.png) | ![Performance](docs/screenshots/performance.png) | ![Fans](docs/screenshots/fans.png) |

| Temperatures | RGB | Settings |
|---|---|---|
| ![Temps](docs/screenshots/temps.png) | ![RGB](docs/screenshots/rgb.png) | ![Settings](docs/screenshots/settings.png) |

---

## Installation

### Option A — Installer (Recommended)

1. Download **`PCMonitor-Setup.exe`** from the [latest release](https://github.com/Vlottiz/pc-monitor/releases/latest)
2. Run it — click Next → Next → Install → Finish
3. PC Monitor launches automatically

The installer:
- Places the app in `Program Files\PCMonitor`
- Creates a Desktop and Start Menu shortcut
- Adds Windows Defender exclusions automatically
- Appears in Add/Remove Programs for clean uninstall

### Option B — Manual

1. Download and extract `PCMonitor-portable.zip` from releases
2. Run `Pcmonitor2.0.exe` as Administrator

---

## Requirements

- **Windows 10 or 11** (64-bit)
- **Administrator privileges** — required for hardware sensor access (the app auto-elevates)
- **Internet** on first launch — downloads the hardware sensor driver (~14KB)
- **WebView2** — pre-installed on Windows 11; Windows 10 users may need to install it from [Microsoft](https://developer.microsoft.com/en-us/microsoft-edge/webview2/)

### Intel CPU Note

Intel CPUs require a kernel-mode driver (`WinRing0`) to read per-core temperatures and clock speeds. On most modern Windows 11 systems this driver is blocked by the **Vulnerable Driver Blocklist** (a Windows security feature).

**What you get on Intel without the driver:**
- ✅ All-core average clock speed (accurate, reflects Turbo Boost)
- ✅ CPU load percentage
- ✅ GPU temperature, clock, power
- ✅ RAM, fans, all other sensors
- ❌ Per-core individual temps/clocks

**To unlock full Intel sensor support:**
> Windows Security → Device Security → Core Isolation → Microsoft Vulnerable Driver Blocklist → **OFF** → Restart

This is the same setting required by HWiNFO, CPU-Z, and MSI Afterburner.

---

## Fan Curve Editor

The fan curve editor supports:
- **Click** the graph to add a point (up to 8)
- **Drag** points to adjust
- **Right-click** a point to delete it
- **Temp source** — drive the curve from CPU, GPU, CCD0, or CCD1
- **Save** persists the curve — it activates automatically on next launch
- **Health Check** — ramps the fan through 30/60/100% and reports if it's responding correctly

---

## RGB Control

RGB requires [OpenRGB](https://openrgb.org) to be running with the SDK server enabled:

1. Open OpenRGB → Settings → SDK Server → **Start Server** (port 6742)
2. Open PC Monitor → RGB tab → Connect

Supports 500+ devices including MSI motherboards, AMD/Nvidia GPUs, Corsair iCUE, and more.

---

## Building from Source

```powershell
# Prerequisites
# - .NET 8 SDK: https://dotnet.microsoft.com/download
# - NSIS (for installer): https://nsis.sourceforge.io

git clone https://github.com/Vlottiz/pc-monitor.git
cd pc-monitor

# Run in development (admin PowerShell)
dotnet run

# Build installer
.\build-installer.bat
```

---

## Credits & Attributions

| Project | Use | License |
|---|---|---|
| [LibreHardwareMonitor](https://github.com/LibreHardwareMonitor/LibreHardwareMonitor) | All hardware sensor reading | MIT |
| [Microsoft WebView2](https://developer.microsoft.com/en-us/microsoft-edge/webview2/) | Embedded browser for the UI | Free |
| [System.Management](https://www.nuget.org/packages/System.Management) | WMI — CPU load, RAM, Intel fallback | MIT |
| [NSIS](https://nsis.sourceforge.io) | Windows installer | zLib |
| [Claude — Anthropic](https://claude.ai) | AI assistant for accelerating development | — |

All ideas, feature design, and project direction by **[Vlottiz](https://github.com/Vlottiz)**.  
Claude assisted with implementation speed, debugging, and boilerplate. Every feature was conceived and directed by the author.

---

## Support

If PC Monitor has been useful to you, consider buying me a coffee:

[![Buy Me A Coffee](https://img.shields.io/badge/Buy%20Me%20a%20Coffee-%E2%98%95-ffdd00?style=for-the-badge&logo=buy-me-a-coffee&logoColor=black)](https://buymeacoffee.com/reyobu)

---

## License

MIT — see [LICENSE](LICENSE) for details.

This project uses open source components. See the Credits section above for individual licenses.
