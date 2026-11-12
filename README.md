# wheel. - Playtest Download & Guide

**wheel.** is a physics-driven backcountry singletrack riding game set in Lake Tahoe, built around surfing dirt, reading natural mountain terrain, and finding downhill flow from alpine timber down to granite slabs and the shoreline.

---

## Download & Install (Windows 10 / 11)

### **[⬇ Download `wheel_installer.exe` (Playtest Installer & Auto-Updater)](https://github.com/play-wheel/wheel-releases/releases/latest/download/wheel_installer.exe)**

1. **Run `wheel_installer.exe`:** Download the lightweight installer above (`~285 KB`) and open it.
   - *Windows SmartScreen tip:* Because this is an independent playtest build, Windows may show *"Windows protected your PC"*. Click **More info** -> **Run anyway**.
2. **Click Install:** The installer streams and verifies the latest game build automatically and creates a **`wheel.`** shortcut on your Desktop and Start Menu (`%LocalAppData%\Programs\wheel` - no administrator rights required).
3. **Automatic Updates:** Whenever you launch **`wheel.`** from your Desktop shortcut, it automatically checks for new playtest releases and updates in one click.

- **[View Latest Patch Notes & Release History](https://github.com/play-wheel/wheel-releases/releases)**

---

## Quick Playtest Tips

- **Controller Strongly Recommended:** Analog stick steering and triggers give full control over lean, carving, and speed scrubbing (Keyboard + Mouse is also supported).
- **In-Game Menu (`Esc` or `Start`):** Switch riders, board colorways, camera framing, time of day (Morning, Noon, Golden Hour, Sunset, Night), and graphics presets (`Low` through `Ultra`).
- **Drop Playtest Pins (`F9`):** Spot something cool or weird on the trail? Press **`F9`** anytime during a ride to drop a spatial playtest note at your exact trail coordinates.

---

## System Requirements (Windows)

| Component | Minimum (`1080p @ 60 FPS`) | Recommended (`1440p / 4K @ 60-144+ FPS`) |
| :--- | :--- | :--- |
| **OS** | Windows 10 64-bit (21H2 or newer) | Windows 11 64-bit (23H2 / 24H2 or newer) |
| **CPU** | 4-Core / 8-Thread (`Core i5-10400` / `Ryzen 5 3600`) | 8-Core / 16-Thread (`Ryzen 7 5800X3D` / `Core i7-13700K`+) |
| **Memory** | `12 GB` RAM | `16 GB+` Dual-Channel RAM |
| **GPU** | `6 GB` VRAM (`GTX 1660 Super` / `RTX 3050` / `RX 6600`) | `10-16 GB+` VRAM (`RTX 3070` / `RTX 4070 Ti` / `RX 7800 XT`+) |
| **Graphics API** | **Direct3D 12** (with automatic **Vulkan 1.2+** fallback) | **Direct3D 12** (Shader Model `6.0`+) |
| **Storage** | `4 GB` SSD space | `4 GB` NVMe SSD space |
| **Input** | Gamepad recommended (or Keyboard) | Controller with Analog Triggers |

---

## Troubleshooting

- **Vulkan Compatibility Mode:** `wheel.` runs on **Direct3D 12** by default and automatically falls back to **Vulkan** if D3D12 startup fails. You can also launch **`wheel. (Vulkan Compatibility)`** directly from your Windows Start Menu (`PlayWheel` folder).
- **Repairing Game Files:** Open **`wheel. Updater`** from the Start Menu (or re-run `wheel_installer.exe`) and click **Verify / Reinstall** to re-verify every file via SHA-256.
- **Intel 13th/14th-Gen `i9-13900K` / `i9-14900K` DX12 Shader Crash:** Ensure your motherboard BIOS is updated (`Intel microcode 0x12B+` with Intel Default Settings) and your NVIDIA/AMD GPU drivers are current.
- **Third-Party Overlays:** If RivaTuner (RTSS), Overwolf, or Discord Overlay hooks D3D12 startup on your PC, update RTSS or disable the overlay for `wheel.exe`.
