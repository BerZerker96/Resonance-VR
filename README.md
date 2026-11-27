
<img width="2047" height="1152" alt="apt" src="https://github.com/user-attachments/assets/f3c568d2-f17e-48e4-81d7-1d88d047b81e" />

<div align="center">

# 🗡️ Resonance VR

**VR for Resonance: A Plague Tale Legacy on PC**

Stereo 3D · stereo reconstruction · head and position tracking · first person · in-headset settings panel · any OpenXR headset

![version](https://img.shields.io/badge/version-0.2.0--alpha-c0392b) ![game](https://img.shields.io/badge/game-Resonance%3A%20A%20Plague%20Tale%20Legacy-222) ![xr](https://img.shields.io/badge/OpenXR-SteamVR%20%7C%20Pimax%20%7C%20Quest%20%7C%20VDXR%20%7C%20WMR-555)

<img width="6320" height="1198" alt="ResonanceVR_20261127_201506_875_left" src="https://github.com/user-attachments/assets/62e8a059-2216-4d85-b6c0-1fc5eaaca26d" />




</div>

---

## 📦 Install

1. Copy everything inside the `mod` folder next to the game's exe.

   | File | What it is |
   |---|---|
   | `dxgi.dll` | The mod |
   | `resonancevr_config.txt` | Your settings (made by itself if it is missing) |

   Not sure where the exe is? Search the game folder for `Resonance.exe`. The mod goes next to it.

2. Start your VR software (SteamVR, Pimax Play, Virtual Desktop, Oculus …), then start the game. VR starts by itself.

Works with any store version (Steam, Epic, Xbox app). On the Xbox app the game folder must be writable (turn on *Advanced management features* when you install). To uninstall, delete the copied files and the `ResonanceVR` folder.

Using a no-intro mod (`ResonanceNoIntro.asi`) and its ASI loader (`dinput8.dll`)? Delete both: the mod skips the intro logos itself.

Another mod already named `dxgi.dll` (ReShade, an ASI loader …)? Rename that one to `dxgi_chain.dll`; the mod loads it and passes every call on. `alternative\winmm.dll` and `alternative\ResonanceVR.asi` are the same mod under other names.

---

## ⚠️ Read this before playing or reporting

These rules hold for every mod on this VR framework. Setups that break them are not supported, and reports from them are answered with this list.

- **Motion smoothing must be OFF.** Oculus ASW, SteamVR Motion Smoothing and Virtual Desktop SSW halve the frame rate and invent every other frame: motion warps and the world seems to change scale when you turn. Oculus: `Ctrl + Numpad 1` while the game runs, or Oculus Debug Tool → ASW Off. SteamVR: per-app Motion Smoothing off. Virtual Desktop: SSW off.
- **Use Resonance VR alone, installed once.** No other mods for this game at the same time: FOV / ultrawide patchers, other VR mods, ASI loaders with other plugins, ReShade, camera tools. The mod already sets the field of view and the picture shape itself.
- **No OpenXR layers or FOV cropping.** OpenXR Toolkit, VectorXR and other API layers, and the Oculus Debug Tool FOV-Tangent Multiplier, change the field of view, resolution or frame rate the mod is given. Switch them off.
- **No frame generation.** DLSS Frame Generation and FSR Frame Generation in the game's options must be off. Picture problems: test without upscaling (DLSS / FSR) and at render scale 1.0 first.
- **Reports:** `ResonanceVR\resonancevr.log` and `ResonanceVR\xrhost.log` from the same run (they are rewritten at every start), the mod version, your headset and VR software, and what you did when it went wrong.
- **The setup check:** search the log for `SETUP` (the problems are framed in `=====` lines); the VR panel's status line shows `SETUP: n problems`. Fix every SETUP problem before reporting.

---

## 🎮 Controls

| Keyboard | Gamepad | Action |
|---|---|---|
| `Insert` | hold `L3 + R3` | Open / close the VR panel |
| `Space` or `F9` | – | Recentre the view |
| `End` | – | First person on / off |
| `Delete` | – | Screenshot |
| `F6` | – | Flat screen on / off |
| `F7` | – | HUD on / off |
| `F8` | – | Switch stereo method (reconstruction / synchronized / alternate eye / head-tracked mono / flat screen) |

Every key can be changed or cleared in the panel's **Hotkeys** tab, for the keyboard and the gamepad.

---

## 🥽 Your headset is set up automatically

The mod reads your headset's field of view and recommended resolution. It sets the shape and resolution of the game's picture to match, so the picture fills your view at the sharpness your VR software asks for. If you change your VR software's resolution or supersampling setting, the mod follows it.

- The game's resolution menu doesn't matter in VR: the mod sets the game's render size itself, together with the window.
- The first time you use a new headset, the mod measures it and saves the result. Everything is exact from the next launch.
- The game's field of view is replaced by your headset's, so nothing is cut off at the edges and nothing pops in as you turn your head.
- The game normally keeps its picture between 1.6 and 2.33 wide per 1 high. A headset eye is narrower, so the mod keeps that limit open: no black bars in your eyes.
- Want it sharper? Raise **View > VR resolution** in the VR panel (for example 1.25) and press **Apply VR resolution** - it changes in game, no restart, and is saved at once. Want more fps? Lower it. **Headset default resolution** goes back to x 1.00.
- **Display > Render resolution = Game setting** uses the resolution from the game's own graphics menu instead.

---

## 👀 Stereo methods

Pick the method you like in **View > Stereo method**. You can switch while playing.

| Method | What it does |
|---|---|
| **Stereo reconstruction** | The game draws one view from the middle of your head every frame, and both eyes are rebuilt from its picture and depth. Both eyes are new every frame, at full frame rate, from the same moment, and the game's own anti-aliasing keeps working. The gaps beside close objects are filled with real background pixels remembered from earlier frames, or matched from the background around them (View > Stereo, *Reconstruction: quality preset* performance (default) / balanced / quality). The default draws a view about one eye wide (the outer edge of each eye repeats the rim of the picture); *drawn view size* in Advanced can make it wide or headset size. Slower, finer options are in Advanced > *Stereo reconstruction (costs more)*. |
| **Synchronized** | The game draws the eyes in turn, and its clock waits for the second eye, so both eyes always show the same moment. Exact geometry. Moving things update at half the frame rate. |
| **Alternate eye (AER)** | The default. The game draws the eyes in turn: left, right, left, right, and runs exactly as normal. Exact geometry; the eyes are one frame apart. |
| **Head-tracked mono** | One head-tracked picture for both eyes (no 3D). The fastest. |
| **Flat screen** | The game on a big virtual screen. |

**More fps per eye (synchronized / alternate eye):** turn on **View > Both eyes every refresh**. Each eye then gets the full headset rate, if your PC can render twice that fps.

**Cloth and hair in synchronized:** the second eye of a pair is drawn on a game tick that still advances part of a step (Stereo tab, *Synchronized: step kept*, `sync_hold`, default 0.35). If cloth or hair still jitters, raise it; if the two eyes differ on fast-moving things, lower it.

**Anti-aliasing:** the game's TAA, DLSS and FSR blend each frame with the frames before it. With synchronized and alternate eye those are the other eye's: you may see ghosting. Stereo reconstruction does not have this problem.

---

## ✨ What you get

- **Real 3D with head tracking.** Your head moves the game's own render camera, so the game draws everything you look at, with no pop-in.
- **Full field of view** with wide culling: nothing is cut off or pops in at the sides, with a soft fill at the very edges. Only the culling is widened; the picture is not rendered any bigger.
- **A HUD you can read:** the game lays its HUD out smaller and on your line of sight, at a comfortable depth (**HUD > UI scale**, **UI depth**), with text that stays sharp. Hide it with `F7`.
- **Built-in first person** (`End`): your eye at the character the camera follows, with adjustable eye height and position. Cutscenes keep the game's camera.
- **Decoupled pitch:** the camera stays level and you look up and down with your head (less motion sickness).
- **Comfort filters:** camera shake filter and idle sway lock for the game camera; your own head is never filtered.
- **Head aim** (on by default): the sling and crossbow aim where you look; the view does not turn. For exact aim, turn the game's aim assist off in its accessibility options.
- **No lens effects in your eyes:** lens distortion, chromatic fringe and vignette off (film grain, lens dirt and lens flare optional).
- **Sharp cutscenes:** the game's depth-of-field blur is switched off while a cutscene or scripted camera is shown (in a headset your eyes focus themselves). **Display > Depth of field**: cutscenes, off or the game's.
- **No intro logos:** the start-up logos are skipped (built in, no separate no-intro mod). Turn it off with **Display > Skip intro logos**.
- **No black bars**, and the game keeps full speed when its window has no focus.
- **Smooth frame pacing:** a frame cap at your headset's refresh rate if you want it, a short GPU queue for low lag, fixed foveated rendering (VRS) as an option, and no Windows throttling.
- **Menus, pause screens and videos** on a flat virtual screen. Photo mode stays in 3D.
- **The game never feels your head:** after each eye is drawn the game gets its own camera back, so nothing drifts or spins.
- **A VR panel in the game's style:** black, old gold and blood red, readable at arm's length (`Insert` or hold `L3 + R3`).
- **Setup check:** frame generation, temporal anti-aliasing in the wrong stereo method, other mods and FOV patchers are found and named in the log.
- **Safe with speed hacks:** they change only the game, never the VR timing.

---

## 🧰 VR panel (`Insert` / `L3 + R3`)

| Page | What's there |
|---|---|
| **View** | Stereo method and its settings, world scale, performance (frame limit, uncapped, both eyes every refresh, foveated rendering, render scale), recentre, mark an issue, make a report folder |
| **Camera** | Head aim, decoupled pitch, shake filter, idle sway lock, give the game its camera back, camera offsets, first person (eye position, head bob filter, cutscene distance) |
| **HUD** | HUD size, depth and height, hide the HUD, how the UI is placed (engine or draws) |
| **Graphics** | Lens distortion, chromatic fringe, vignette, film grain, lens dirt, lens flare, sharpening, no black bars |
| **Screen** | Flat screen size and distance, panel size, desktop window, start-up |
| **Advanced** | Foveation zones, picture and frustum, eye alignment, render size and timing |
| **Hotkeys** | Every mod function on any key or gamepad button combination |

Settings are saved in `resonancevr_config.txt` next to the game exe. Delete that file to get the defaults back.

---

## ❓ Problems?

- **No picture in the headset:** start your VR software before the game, and make sure it is the active OpenXR runtime.
- **Low fps or stutter:** lower **View > VR resolution** and press Apply (0.8 helps a lot), try **Head-tracked mono**, or turn on foveated rendering.
- **The world looks too big or too small:** change **View > World scale**.
- **Ghosting or double images in synchronized / alternate eye:** use stereo reconstruction, or set the game's anti-aliasing to its lowest setting.
- **The picture or the HUD looks wrong:** turn off every other mod and FOV / ultrawide patcher, and frame generation in the game's options.
- **The HUD is not scaled:** set **HUD > UI placed by** to **D3D12 draws** and send the log.
- **Anything else:** the mod writes a log in the `ResonanceVR` folder next to the game (`resonancevr.log` and `xrhost.log`). Send both with your report, or press **View > Make a report folder** and send that folder. Every 10 seconds the log records fps, frame times, hitches and what limits the frame rate.

---

- **Crash at start, or after a game update:** set `safe_mode = true` in `resonancevr_config.txt` - every optional game hook (video, post effects, UI scaling, first person) stays off and VR still runs. The log's `COMPAT:` line says which game functions a patch moved.

## 🏗️ Building

The `source` folder holds the full source. Build with MinGW-w64:

- `OXR=<OpenXR-SDK built for MinGW> scripts/build_mingw.sh` builds `dxgi.dll`, `winmm.dll` and `ResonanceVR.asi`.
- `scripts/build_tests.sh` builds the tests; `python3 tools/verify_signatures.py <Resonance.exe>` checks every signature of the mod against any build of the game.

Technical details are in `NOTES.md`, and the history is in `CHANGELOG.md`.

---

## 🙏 Credits

| Who | What |
|---|---|
| **mark-mon** | The VR framework this mod is built on: XrBridge OpenXR host, vrkit VR panel, proxy loader, and its D3D12 compositor, stereo reconstruction and foveated rendering |
| **sKuhLight** | Resonance 32:9 & FOV patcher: confirmed the picture-shape clamp and the gameplay FOV load |
| **praydog / UEVR** | The synchronized-sequential idea behind the synchronized method |
| **Tsuda Kageyu** | MinHook (BSD 2-Clause) |
| **Omar Cornut** | Dear ImGui (MIT) |
| **Khronos Group** | OpenXR (Apache 2.0) |

<sub>Resonance: A Plague Tale Legacy is a trademark of Focus Entertainment and Asobo Studio. This is an unofficial fan mod with no game files included. You need your own copy of the game.</sub>
