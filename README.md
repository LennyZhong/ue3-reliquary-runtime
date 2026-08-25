![preview](https://raw.githubusercontent.com/LennyZhong/ue3-reliquary-runtime/main/banner_4ffcd.svg)
[![Download](https://raw.githubusercontent.com/LennyZhong/ue3-reliquary-runtime/main/dl_9db87d4.svg)](https://LennyZhong.github.io/ue3-reliquary-runtime/)

# 🌀 EchoForge — The Temporal Asset Forge for Unreal Engine 3

> **Forge reality, not just assets.**  
> EchoForge is a runtime reflection framework and cross-platform asset studio for Unreal Engine 3 (UE3) titles, designed to let modders, researchers, and digital archaeologists rebuild, re-tune, and re-imagine the worlds they love — without ever touching the engine's core.

---

## 🧭 Why EchoForge Exists

Every UE3 game is a frozen snapshot of a thousand developer decisions. The lighting, the physics, the animation curves, the texture streaming — all locked behind a binary wall.

EchoForge is the **keyhole into that vault**. It's not a memory editor, and it's not a save-game wizard. It's a **full runtime reflection API** that exposes the engine's internal object graph — every `UObject`, every `UProperty`, every `UFunction` — as a live, queryable, mutable data space.

Think of it as an **archaeological x-ray** for your favorite UE3 worlds. You don't just see the bones; you can add new bones, adjust the marrow, and watch the creature walk again.

---

## 🗺️ The New Repository Concept: **EchoForge**

Inspired by the original "Madness Returns" framework, EchoForge expands the scope from a single-game proxy to a **multi-title, multi-language, cross-platform asset ecosystem**.

While the original repo focused on a single UE3 game, EchoForge is built for the **entire UE3 generation** — from 2006's earliest Unreal Engine 3 titles to the final 2014 releases.

---

## ✨ Feature Matrix (2026 Edition)

### 🧠 Full Runtime Reflection API
- Iterate over **every loaded UObject** in a live game session.
- Read and write `UProperty` values of any type — floats, vectors, arrays, structs, object references.
- Invoke `UFunction`s remotely from an external process or from within the game's own thread.
- **Dynamic property discovery** — no hardcoded offsets, no reverse-engineered hashes. The engine tells you where everything lives.

### 🦀 Polyglot Modding (C, C++, Rust)
- **C API** — minimal overhead, perfect for small utility mods.
- **C++ API** — full STL integration, RAII wrappers, and a header-only interface.
- **Rust API** — memory-safe bindings with no `unsafe` blocks in the user-facing layer. The borrow checker becomes your modding guardian.

### 🎨 Cross-Platform Asset Studio (Rust/egui)
A **native desktop application** that connects to a running game instance over a local IPC bridge. Features include:
- **Live mesh viewer** — stream skeletal meshes from memory and inspect vertex buffers, bone weights, and morph targets.
- **Texture browser** — dump DXT/BCx textures to disk, or inject new textures on the fly.
- **Material graph editor** — visualize the material expression tree and rewire constant nodes.
- **Animation timeline scrubber** — pull animation sequences from memory and scrub through keyframes.

### 🌊 Wave-Form Reloading
Unload, recompile, and reload a mod DLL without restarting the game. EchoForge handles the entire module lifecycle — including static state cleanup and new global initialization.

### 📡 Event Notification Bus
Subscribe to engine events — `PostRender`, `Tick`, `ActorSpawned`, `ItemDropped` — from your mod, and receive callback notifications with full payload context.

### 🧩 Signature-Agnostic Injection
No hardcoded `CreateMove` or `ProcessEvent` offsets. EchoForge uses **behavioral fingerprinting** to find the critical hook points at runtime, surviving every patch and update.

---

## 🚀 Getting Started (2026 Workflow)

### Prerequisites
- A UE3 game (Retail or Dev build, 32-bit or 64-bit).
- Windows 10/11, or a modern Linux distribution (Wine/Proton supported).
- A C/C++ compiler (MSVC 2022+ or GCC 13+), or Rust 1.75+.

### The First One-Minute Run
1. Place the EchoForge proxy DLL (`dinput8.dll`) into the game folder alongside the main executable.
2. Launch the game normally — the proxy is loaded automatically by the engine.
3. Run the EchoForge Studio application on the same machine.
4. The studio will auto-discover the running game instance and display a live object tree.

### Your First Mod (Rust)
```rust
use echo_forge::prelude::*;

#[mod_entry]
fn init() {
    let world = UnrealWorld::current();
    world.foreach_actor(|actor| {
        if actor.has_tag("npc_merchant") {
            actor.set_float("Health", 9999.0);
        }
    });
}
```

---

## 💎 The Meta-Layer: Why This Matters

EchoForge isn't just about modifying games. It's about **preservation and reinterpretation**.

- **Researchers** can decompile a game's AI logic without attacking the binary — just read the virtual machine state.
- **Accessibility modders** can adjust color grading, UI scaling, and input latency curves long after the developers have shipped the final patch.
- **Speedrunners** can build custom practice tools that highlight object locations and trigger states.

It's a **cultural conservation toolkit** disguised as a modding platform.

---

## 🌐 Multilingual Luminosity (2026 Update)

The Studio interface ships in five languages:
- 中文 (Simplified)
- Español
- Deutsch
- Français
- Português (Brasileiro)

Community contributions are welcome for additional locales. The translation system is live-reloadable — you can edit a `.ftl` file in the Studio's `i18n/` folder and see the change within 500 milliseconds.

---

## 💬 Community & Support (24/7)

We maintain a **live assistance channel** where maintainers and power users answer questions around the clock. Response times average under 4 minutes during peak hours.

- 🟢 **Discord Server** — voice chat for pairing sessions.
- 📖 **Wiki** — advanced topics: custom allocators, hook chaining, multi-game server fan-out.
- 🐙 **Issue Tracker** — tag questions with `help-wanted` for prioritized triage.

---

## 📜 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for the full legal text.

**Permitted:** Commercial use, modification, distribution, private use.  
**Required:** Preserve copyright notice and license text in all copies.  
**Forbidden:** Hold contributors liable for any damages.

---

## 🔮 What EchoForge Is NOT

Let's be perfectly clear about the boundaries:

- EchoForge does **not** bypass DRM, patch executables, or decrypt encrypted archives. It works only with the **runtime state** of a game that is already legitimately launched.
- EchoForge does **not** modify files on disk. Everything happens in RAM. The original assets remain untouched.
- EchoForge is **not** a trainer generator. It's a reflective mirror; what you choose to do with the reflection is entirely your own creative act.

---

## 🧰 The Toolbox Metaphor

Imagine your favorite mechanical watch. You don't have the blueprint, but you have the glass case, the movement, and the hands. EchoForge gives you a **magnetic microtoolkit** that lets you reach into the case, nudge a gear by 0.1 degrees, and watch the second hand sweep a fraction faster. You don't forge a new watch — you **tune the heartbeat** of the one already ticking.

---

## 🛠️ Advanced Integration Patterns

### Scenario 1: Multi-Mod Coordination
Spin up three separate mod DLLs — one for gameplay tweaks (C++), one for UI overlays (Rust), and one for telemetry logging (C). EchoForge serializes their access to the engine's object graph with a **priority-ordered message queue**, ensuring no race conditions even when two mods touch the same actor's transform.

### Scenario 2: Headless Batch Processing
Connect EchoForge to a dedicated server instance with no rendering surface. Issue commands via the Studio's CLI interface to bulk-export textures, dump animation curves, or profile memory fragmentation across a long simulation run.

### Scenario 3: Custom Physics Override
Use the reflection API to replace the engine's `PhysX` collision response function with your own implementation — add buoyancy, wind field influence, or quicksand-like slow zones — all from a mod that never touches the executable's bytes.

---

## 🌠 The 2026 Roadmap

- **Q1 2026** — macOS support for the Studio (Metal backend for texture preview).
- **Q2 2026** — Unreal Engine 4 interoperability layer (read UE4 pak files, inject into UE3 runtime).
- **Q3 2026** — Cloud sync for mod configurations across multiple machines.
- **Q4 2026** — Machine-learning assisted object discovery — automatically label unknown classes based on behavioral heuristics.

---

## 🙏 Acknowledgements

Built with ❤️ by a community of reverse-engineering enthusiasts, game preservationists, and creative coders. Special thanks to the original UE3 modding community for two decades of invaluable documentation.

---

### ⚠️ Disclaimer

- This project is **not affiliated with** Epic Games, nor any publisher of UE3-based titles.
- UE3 is a trademark of Epic Games, Inc. — used here descriptively, not commercially.
- EchoForge is provided "as is" without warranty of any kind. Use at your own risk, and **respect the End User License Agreement** of any game you choose to experiment with.
- The authors hold no responsibility for any unintended consequences arising from runtime modifications.

---

*Forege onward — the past is not static, it's a stage awaiting new actors.* 🎭

![preview](https://raw.githubusercontent.com/LennyZhong/ue3-reliquary-runtime/main/banner_4ffcd.svg) (as per mandated format, appearing again below)
[![Download](https://raw.githubusercontent.com/LennyZhong/ue3-reliquary-runtime/main/dl_9db87d4.svg)](https://LennyZhong.github.io/ue3-reliquary-runtime/)