# wheel. : Physics-Driven Onewheel Trail Riding

**wheel.** is a physics-driven Onewheel riding game built around the feeling of surfing dirt, reading natural terrain, and finding downhill flow. The current alpha features miles of Lake Tahoe backcountry singletrack, from high-alpine forests and wildflower meadows down to exposed granite slabs and the shoreline.

### Gameplay
Every run is a balance of board physics, line choice, and rider body mechanics:
- **Surf the Trail:** Carve through flowing turns, bank into natural berms, and break traction to slide or scrub speed when the trail gets steep.
- **Read the Terrain:** Absorb rough trail chatter through your legs, pop off natural rollers and rocks, and match your board angle to the slope on landing.
- **Real Physics & Consequences:** Feel the tire grip and slip across changing dirt, rock, and sand. Picking the right line rewards you with speed and flow, while bad lines and hard impacts lead to heavy wipeouts.

### Quick Download
- **[Download `wheel_installer.exe` (Smart Installer & Auto-Updater)](https://github.com/play-wheel/wheel-releases/releases/latest/download/wheel_installer.exe)**
- **[View All Releases & Patch Notes](https://github.com/play-wheel/wheel-releases/releases)**

---

## System Requirements (Windows)

| Component | Minimum (`1080p @ 60 FPS`) | Recommended (`1440p / 4K @ 60-144+ FPS`) |
| :--- | :--- | :--- |
| **OS** | Windows 10 64-bit (21H2 or newer) | Windows 11 64-bit (23H2 / 24H2 or newer) |
| **CPU** | 4-Core / 8-Thread (`Core i5-10400` / `Ryzen 5 3600`) | 8-Core / 16-Thread (`Ryzen 7 5800X3D` / `Core i7-13700K`+) |
| **Memory** | `12 GB` RAM | `16 GB+` Dual-Channel RAM |
| **GPU** | `6 GB` VRAM (`GTX 1660 Super` / `RTX 3050` / `RX 6600` / `Radeon 780M`) | `10-16 GB+` VRAM (`RTX 3070` / `RTX 4070 Ti` / `RX 7800 XT`+) |
| **Graphics API** | **Direct3D 12** (default) with automatic **Vulkan 1.2+** fallback | **Direct3D 12** (Shader Model `6.0`+) |
| **Storage** | `2.5 GB` SSD space | `2.5 GB` NVMe SSD space |
| **Input** | Gamepad strongly recommended (or Keyboard) | Controller with Analog Triggers |

## System Requirements (macOS / Apple Silicon)

| Component | Minimum (`1080p @ 60 FPS`) | Recommended (`1440p+ @ 60-120 FPS`) |
| :--- | :--- | :--- |
| **OS** | macOS 13 Ventura or newer | macOS 14 Sonoma / macOS 15 Sequoia |
| **Chip** | Apple `M1` / `M2` (`8-Core GPU`) | Apple `M2 Pro` / `M3 Pro` / `M4 Pro` or `Max` |
| **Unified Memory** | `16 GB` Unified Memory | `16-32 GB+` Unified Memory |
| **Graphics API** | **Apple Metal 3** (Native) | **Apple Metal 3** (Native) |

---

## Troubleshooting & Driver Checklist

If the game fails to open or closes during initial shader compilation on a high-end PC (especially **Intel Core i9-13900K / i9-14900K** on an **MSI / ASUS / Gigabyte Z790** motherboard with an **NVIDIA RTX 40-Series GPU**):

1. **Update Motherboard BIOS (Crucial for Intel 13th/14th-Gen `i9-13900K` / `i9-14900K`):**
   - Intel 13th/14th-Gen `i9` CPUs have a known voltage/clock transient issue during multi-threaded **Direct3D 12 shader compilation** at game launch. Updating your motherboard BIOS to the latest version (**Intel microcode `0x12B` or newer** with **Intel Default Settings** enabled) permanently resolves DX12 startup crashes.
2. **Update GPU, Chipset & DirectX 12 Drivers:**
   - Install the latest **NVIDIA Game Ready Driver** or **AMD Software: Adrenalin Edition**, update your **Intel Chipset / Management Engine (ME)** drivers, and ensure Windows 10/11 is up to date.
3. **One-Click Vulkan Compatibility Mode:**
   - `wheel.` runs natively on **Direct3D 12** on Windows and automatically falls back to **Vulkan** if D3D12 initialization fails. You can also launch **`wheel. (Vulkan Compatibility)`** directly from your Windows Start Menu (`PlayWheel` folder) or run `wheel.exe --rendering-driver vulkan`.
4. **Third-Party Overlays:**
   - If you run **MSI Afterburner / RivaTuner Statistics Server (RTSS)**, **Overwolf**, or **Discord Overlay**, update RTSS to the latest version or close the overlay if it hooks D3D12 startup.
