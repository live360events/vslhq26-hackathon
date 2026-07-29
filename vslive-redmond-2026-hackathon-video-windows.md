# Recording Your Demo Video on Windows 11

Part of the [VSLive! Redmond 2026 Hackathon GitHub guide](vslive-redmond-2026-hackathon-github-tnt.md). See [Section 8](vslive-redmond-2026-hackathon-github-tnt.md#8-your-demo-video-and-submitting-your-repo) for what makes a good demo video. This page is the mechanics.

macOS user? See [Recording your demo video on macOS](vslive-redmond-2026-hackathon-video-macos.md).

**What you need to produce:** an MP4 (H.264), roughly 1080p, 3 minutes, **under 100 MB**, committed to `./demo/demo.mp4` in your repo.

**Good news:** every tool on this page is free, and two of the three are already on your machine. You do not need to buy Camtasia tonight.

---

## Pick your tool

| Tool | Where it comes from | Records mic | Records system audio | Best for |
| ---- | ------------------- | ----------- | -------------------- | -------- |
| **Snipping Tool** | Built into Windows 11 | Yes | Yes (current builds) | The default. Fastest path to a working MP4. |
| **ZoomIt** | Free download (Sysinternals or PowerToys) | Yes | Yes | Demos where you need to zoom, annotate, or blur secrets while recording. |
| **Xbox Game Bar** | Built into Windows 11 | Yes | Yes, automatically | Fallback if the other two misbehave. Won't capture File Explorer or the desktop. |

If you have no strong opinion, use **Snipping Tool**. If you're demoing something with small text or fiddly UI detail, use **ZoomIt** — its live zoom is genuinely the best thing on this list for technical demos.

---

## Before you record (all tools)

Run through this once. It takes two minutes and prevents most re-records.

1. **Set your display to 1920×1080** if you can, or at least record a 1080p-sized region. Recording a 4K display and scaling down makes text mushy and files huge.
2. **Turn on Do Not Disturb.** Settings → System → Notifications → Do not disturb. Teams, Outlook, and Discord will absolutely interrupt you otherwise.
3. **Increase font sizes.** Visual Studio / VS Code: bump the editor font a few points. Terminal: same. Browser: Ctrl+`+` a couple of times.
4. **Clean the screen.** Close unrelated tabs and windows. Check your bookmarks bar and taskbar for anything you don't want in the video.
5. **Scan for secrets.** API keys in `.env` or `appsettings.json`, tokens in terminal scrollback, keys visible in an Azure portal tab, your email in an account menu. Clear the terminal (`cls`) before you start.
6. **Warm everything up.** Start your app, run any first-time compile, log in, load your test data. Record the second run, not the cold start.
7. **Do a ten-second test recording and play it back.** Confirm you got the right screen and the audio you expected. This single step catches most disasters.

---

## Option A: Snipping Tool (built in)

### Recording

1. Press **Win + Shift + R** to go straight to the recording overlay. (**Win + Shift + S** opens the capture bar for screenshots; you can switch to the video/camcorder icon from there. **Win + S** is Search — not what you want.)
2. Drag to select the rectangular region you want to record.
3. Before clicking Start, set your audio (next section).
4. Click **Start**. You get a three-second countdown.
5. Do your demo.
6. Click **Stop** in the floating toolbar.
7. The recording opens in the Snipping Tool editor. Press **Ctrl + S** to save.

Recordings save as MP4 to **Videos → Screen Recordings** by default.

### Audio: with voice, without voice, or both

The recording toolbar has two independent audio toggles — a **microphone** icon and a **system audio / speaker** icon.

- **Silent video (no narration):** leave both muted. Mute is the default for the microphone, so if you do nothing, you get a silent recording. That's a valid submission — add text callouts in editing.
- **Narrated:** click the microphone icon, pick your input device from the dropdown, and **make sure it's unmuted**. Selecting the right mic is not the same as unmuting it, and this is the most common reason people end up with a silent recording they thought was narrated.
- **App sound too** (your demo plays audio, or you're showing a video call): enable the system audio toggle as well. Both can run at once.

You can set the default in **⋯ → Settings → Include microphone input by default when a screen recording starts**, so you don't have to remember every time.

### Editing

Snipping Tool's editor does basic trimming. For anything more — text overlays, captions, joining takes — see [Clipchamp](#editing-and-captions-clipchamp) below.

---

## Option B: ZoomIt (best for technical demos)

ZoomIt is Mark Russinovich's presentation tool, and it's built for exactly what you're doing. The standalone version is **v12.1** as of June 2026.

**Get it:** [Sysinternals ZoomIt](https://learn.microsoft.com/en-us/sysinternals/downloads/zoomit) (standalone, ~24 MB, no install — just run it) or via [PowerToys](https://learn.microsoft.com/en-us/windows/powertoys/zoomit). The standalone version sometimes gets features first. You can also [run it from Sysinternals Live](https://live.sysinternals.com/ZoomIt.exe) without downloading anything.

### Set it up first

Open ZoomIt's options and go to the **Record** tab:

| Setting | Recommendation |
| ------- | -------------- |
| Format | **MP4** (GIF is also supported, but you want MP4) |
| Scaling | `1.0` unless you need to shrink the output |
| Lock region selection to 16:9 | **On** — keeps your framing clean |
| Capture system audio | On only if your demo makes noise you want heard |
| Capture audio input | **On for narration, off for a silent video.** Off by default. |
| Microphone | Pick your actual headset, not "Default", if you have several devices |
| Show webcam overlay | Optional — puts a picture-in-picture of you in a corner. Fine, not required. |

### Recording hotkeys

| Action | Hotkey |
| ------ | ------ |
| Record full screen | **Ctrl + 5** |
| Record a selected region | **Ctrl + Shift + 5** |
| Record the window under the cursor | **Ctrl + Alt + 5** |
| Stop recording | Same hotkey again |

### The demo features that make ZoomIt worth it

These all work *while you're recording*, and they end up in the video:

| Action | Hotkey |
| ------ | ------ |
| Zoom (freezes screen, magnifies) | **Ctrl + 1** |
| **Live Zoom** (magnifies live, moving content) | **Ctrl + 4** |
| Draw on screen without zooming | **Ctrl + 2** |
| **Blur pen** — Gaussian-blur a region | **X** (while drawing) |
| Arrow | Hold **Ctrl + Shift** while dragging |
| Rectangle / Ellipse | Hold **Ctrl** / hold **Tab** |
| Type text on screen | **T** |
| Erase all drawings | **E** |
| Exit drawing mode | **Esc** |

Two of these matter a lot for you:

- **Live Zoom (Ctrl + 4)** lets you magnify a running app so a judge can actually read your log output or a small UI control. This is the killer feature for a technical demo.
- **The blur pen (X)** lets you obscure an API key, email address, or connection string mid-demo instead of re-recording.

There's also **DemoType (Ctrl + 7)**, which types a pre-written snippet from a file at a configurable speed — useful if you need to "type" a prompt or a code block without fumbling it on camera.

### The trim editor

When you stop recording, ZoomIt opens a trim editor before saving. You can shorten the clip, **append additional clips**, and add transitions between them. That means you can record your demo in three separate takes and stitch them into one file without ever opening a video editor — which is a very good deal at 11pm on Night 2.

---

## Option C: Xbox Game Bar (fallback)

Use this if the other two are giving you trouble.

1. **Win + G** opens Game Bar. **Win + Alt + R** starts and stops recording directly.
2. It captures the app window that has focus.
3. System audio is captured automatically. Toggle the mic with **Win + Alt + M**.
4. Audio settings: Settings → Gaming → Captures → Audio to record.
5. Files land in **Videos → Captures**.

**Limitation:** Game Bar will not record File Explorer or the desktop itself. If your demo involves either, use Snipping Tool or ZoomIt.

---

## Editing and captions: Clipchamp

Clipchamp ships with Windows 11 and is enough for everything you need.

- **Trim dead air** — cut the compile, the cold start, the part where you looked for the right window
- **Text overlays** — essential if you're going silent. Add a title card at the start and short callouts over each demo step.
- **Auto-captions** — if you narrated, generate captions. Free, and it makes the video watchable with the sound off.
- **Join takes** — drop multiple recordings on the timeline in order

Export at **1080p**. Clipchamp outputs MP4/H.264, which is exactly what you want.

If you'd rather not use Clipchamp, the Snipping Tool editor trims, and ZoomIt's trim editor trims and appends.

---

## Getting under 100 MB

GitHub rejects any single file over 100 MB without Git LFS. Check your file first:

```powershell
(Get-Item .\demo\demo.mp4).Length / 1MB
```

**If you're over,** re-encode with ffmpeg. Install it once:

```powershell
winget install Gyan.FFmpeg
```

Then:

```powershell
# Good general-purpose re-encode: 1080p, H.264, web-optimized
ffmpeg -i input.mp4 -c:v libx264 -preset slow -crf 24 -vf "scale=1920:-2" -c:a aac -b:a 128k -movflags +faststart demo.mp4
```

Knobs, in the order you should reach for them:

- **`-crf`** — quality. Higher number, smaller file. `24` is a good start; `28` is still perfectly watchable for a screen recording; past `30` text starts to smear.
- **`-vf "scale=1280:-2"`** — drop to 720p. Screen recordings compress well and 720p is fine if your fonts are large.
- **`-an`** — strip audio entirely. Only if you're going silent anyway.
- **Trim it.** If you're 40% over the limit, you probably also have 40% of the video that isn't earning its place.

Rough sanity check: a 3-minute 1080p screen recording at CRF 24 typically lands well under 50 MB. If yours is 400 MB, you almost certainly recorded at 4K or at a very high bitrate — re-encoding will fix it.

---

## Committing the video

```bash
# Confirm .gitignore isn't silently excluding it
git check-ignore -v demo/demo.mp4
# No output = you're fine.

git add demo/demo.mp4
git commit -m "Add demo video"
git push
```

If `git check-ignore` prints a line, some pattern (`*.mp4`, `demo/`, `media/`) is excluding your video. Fix `.gitignore` first — see Section 7 of the main guide.

---

## Troubleshooting

| Symptom | Fix |
| ------- | --- |
| Recording is silent, but I wanted narration | The mic was muted. It's muted by default in Snipping Tool, and "Capture audio input" is off by default in ZoomIt. Test-record ten seconds next time. |
| Mic is unmuted but still no audio | Settings → Privacy & security → Microphone. Confirm the app has access. Check you picked the right input device — the built-in array mic and your headset are different entries. |
| App sound isn't in the recording | Enable the system audio toggle (Snipping Tool) or "Capture system audio" (ZoomIt). Game Bar does it automatically. |
| Captured the wrong monitor | Select a region or a specific window rather than "full screen" on a multi-monitor setup. |
| No video/record option in Snipping Tool | Update it: Microsoft Store → Library → Get updates. Then Settings → Windows Update. |
| Game Bar won't record my window | It doesn't record File Explorer or the desktop. Use Snipping Tool or ZoomIt. |
| File is way over 100 MB | Re-encode with ffmpeg (above), or record at 1080p instead of 4K next time. |
| A notification popped up mid-demo | Turn on Do Not Disturb, then re-record. |

---

Questions during the event? Find any of the moderators at the moderator table.
