# `wheel.` — System Requirements & Hardware Compatibility Guide

This guide covers minimum and recommended hardware specs for `wheel.`, how the engine selects and falls back between native graphics APIs (**Direct3D 12**, **Metal**, and **Vulkan**), and quick troubleshooting steps for high-end Intel 13th/14th-Gen systems.

---

## 1. Windows System Requirements

| Component | Minimum (`1080p @ 60 FPS` — Medium/Low Auto-Tier) | Recommended (`1440p / 4K @ 60–144+ FPS` — High/Ultra Auto-Tier) |
| :--- | :--- | :--- |
| **OS** | Windows 10 64-bit (Version 21H2 or newer) | Windows 11 64-bit (23H2 / 24H2 or newer) |
| **CPU** | 4-Core / 8-Thread (`Intel Core i5-10400` / `AMD Ryzen 5 3600`) | 8-Core / 16-Thread (`AMD Ryzen 7 5800X3D` / `Intel Core i7-13700K` or newer) |
| **Memory** | `12 GB` RAM | `16 GB+` Dual-Channel RAM |
| **GPU** | `6 GB` VRAM (`NVIDIA GTX 1660 Super` / `RTX 3050`, `AMD RX 6600`, or `AMD Radeon 780M` / Steam Deck APU) | `10–16 GB+` VRAM (`NVIDIA RTX 3070` / `RTX 4070 Ti` / `RTX 4080`, `AMD RX 7800 XT` / `RX 7900 XT`) |
| **Graphics API** | **Direct3D 12** (Feature Level `12_0`+) with automatic **Vulkan 1.2+** fallback | **Direct3D 12** (Agility SDK / Shader Model `6.0`+) |
| **Storage** | `2.5 GB` available SSD space | `2.5 GB` NVMe SSD space |
| **Input** | Gamepad strongly recommended (dual-stick + analog triggers) or Keyboard | Dual-stick Controller with Analog Triggers (`LT` / `RT` / `LS` / `RS`) |

---

## 2. macOS System Requirements (Apple Silicon)

| Component | Minimum (`1080p @ 60 FPS`) | Recommended (`1440p+ @ 60–120 FPS`) |
| :--- | :--- | :--- |
| **OS** | macOS 13 Ventura or newer | macOS 14 Sonoma / macOS 15 Sequoia |
| **Chip** | Apple `M1` / `M2` (`8-Core GPU`) | Apple `M2 Pro` / `M3 Pro` / `M4 Pro` or `Max` |
| **Unified Memory** | `16 GB` Unified Memory | `16–32 GB+` Unified Memory |
| **Graphics API** | **Apple Metal 3** (Native) | **Apple Metal 3** (Native) |

---

## 3. Native Graphics API Selection & Automatic Fallback Architecture

`wheel.` is configured in `project.godot` to use each operating system's fastest native rendering backend first, with automatic engine and launcher fallback if a driver or overlay issue occurs:

1. **Per-Platform Native API Defaults (`project.godot`):**
   - **Windows Override (`rendering_device/driver.windows = "d3d12"`):** Runs natively on **Direct3D 12** for maximum Windows frame pacing, low-overhead command submission, and Windows Flip Model presentation.
   - **macOS Override (`rendering_device/driver.macos = "metal"`):** Runs natively on **Apple Metal** without translation-layer overhead.
   - **Global Baseline & Automatic Fallback (`rendering_device/driver = "vulkan"`, `fallback_to_vulkan = true`):** Serves as the cross-platform baseline (Linux / SteamOS / Steam Deck) and the automatic fallback API if `Direct3D 12` device initialization fails on Windows.
2. **Staged Cold-Start Boot & Crash-Recovery Watchdog:**
   - Shader cache Zstd decompression is disabled (`shader_cache/use_zstd_compression = false`), 3D foliage MultiMesh instancing is staged to frame 2, and `ReflectionProbe` cubemap rendering is staged to frame 4 so the window opens and responds immediately without a single-frame GPU timeout (TDR).
   - If a system crashes or hangs before completing 3 rendered frames (`user://boot_in_progress.lock`), the next launch automatically triggers **Safe Recovery Mode** and the smart launcher (`wheel_installer.exe`) automatically retries with `--rendering-driver vulkan`.

---

## 4. Troubleshooting & Driver Checklist (Especially Intel 13th/14th-Gen `i9-13900K` / `i9-14900K` + RTX 40-Series)

If the game fails to open or closes during initial shader compilation on a high-end PC (such as an **Intel Core i9-14900K / 14900KF** on an **MSI Z790** motherboard with an **NVIDIA RTX 4070 Ti / 4080 / 4090**):

1. **Update Motherboard BIOS (Crucial for Intel i9-13900K / i9-14900K):**
   - Intel 13th/14th-Gen `i9` CPUs have a well-known voltage/clock transient issue during heavy **Direct3D 12 DXIL shader compilation** at game launch. Updating your MSI/ASUS/Gigabyte BIOS to the latest version (containing **Intel microcode `0x12B` or newer** and enabling the **Intel Default Settings** power profile) permanently fixes DX12 startup crashes across all modern games.
2. **Update GPU & Chipset Drivers:**
   - Install the latest **NVIDIA Game Ready Driver** (`566.xx` or newer) or **AMD Software: Adrenalin Edition**, plus the latest **Intel Chipset & Management Engine (ME)** drivers from your motherboard support page.
3. **One-Click Vulkan Compatibility Shortcut (Immediate Workaround):**
   - The installer automatically adds **`wheel. (Vulkan Compatibility)`** to your Windows Start Menu (`PlayWheel` folder), or you can pass `--rendering-driver vulkan` to `wheel.exe`. This bypasses the Windows DirectX 12 DXIL compiler entirely and runs at full native speed on NVIDIA/AMD Vulkan drivers.
4. **Disable Third-Party DX12 Hooking Overlays if Needed:**
   - Outdated versions of **RivaTuner Statistics Server (RTSS)**, **MSI Afterburner**, **Overwolf**, or **Discord Overlay** can hook `D3D12CreateDevice` and block window creation. Updating RTSS or closing the overlay resolves the conflict.
