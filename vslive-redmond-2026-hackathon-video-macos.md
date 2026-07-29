# Recording Your Demo Video on macOS

Part of the [VSLive! Redmond 2026 Hackathon GitHub guide](vslive-redmond-2026-hackathon-github-tnt.md). See [Section 8](vslive-redmond-2026-hackathon-github-tnt.md#8-your-demo-video-and-submitting-your-repo) for what makes a good demo video. This page is the mechanics.

Windows user? See [Recording your demo video on Windows 11](vslive-redmond-2026-hackathon-video-windows.md).

**What you need to produce:** a screen recording, roughly 1080p, 3 minutes, **under 100 MB**, committed to `./demo/demo.mp4` in your repo. MP4 is preferred, but the `.mov` that macOS gives you is accepted as-is — commit it as `./demo/demo.mov` and reference that path in your README.

**Three things to know up front, because they surprise people:**

1. **QuickTime Player and ⌘⇧5 are the same recorder.** Choosing File → New Screen Recording in QuickTime just launches the Screenshot toolbar. One engine, two doors. Use whichever you like; the capabilities are identical.
2. **macOS does not record system audio.** The built-in recorder captures your microphone only. This is a deliberate privacy boundary, not a bug, and it's still true in macOS 26 Tahoe. If your demo makes sounds you need heard, see [Recording system audio](#recording-system-audio) below.
3. **You do not need to convert to MP4.** macOS saves screen recordings as `.mov`, and that's fine — we can play it. Skip the conversion and spend the time on your demo instead. The 100 MB limit still applies either way, so see [Compressing](#compressing-and-optional-conversion).

---

## Before you record

Run through this once. It takes two minutes and prevents most re-records.

1. **Turn on Do Not Disturb.** Control Center → Focus → Do Not Disturb. Slack and Messages will interrupt you otherwise.
2. **Check permissions now, not mid-demo.** System Settings → Privacy & Security → **Screen & System Audio Recording**, and → **Microphone**. Make sure the app you're using is enabled. macOS updates sometimes reset these.
3. **Increase font sizes.** Editor, terminal, browser (⌘ + `+`). What's readable on a Retina display at arm's length is unreadable in a shrunk-down video player.
4. **Clean the screen.** Close unrelated windows and tabs. Check your menu bar and Dock for anything you don't want visible. Consider hiding the Dock (⌥⌘D).
5. **Scan for secrets.** API keys in `.env`, tokens in terminal scrollback, connection strings, keys in an Azure or AWS console tab, your email in an account menu. Clear the terminal (⌘K) before you start.
6. **Warm everything up.** Start your app, run the first compile, log in, load test data. Record the second run.
7. **Do a ten-second test recording and play it back.** Confirm the right screen was captured and the audio you wanted is actually there. This catches most disasters.

---

## Option A: The Screenshot toolbar (⌘⇧5) — the default

This is built into every Mac you're realistically using. It's also the engine behind QuickTime's screen recording.

### Recording

1. Press **⌘ + Shift + 5**. A floating toolbar appears near the bottom of the screen. The left icons are stills; the right icons are video.
2. Choose a recording mode:
   - **Record Entire Screen**
   - **Record Selected Portion** — drag to define a rectangle
   - **Record Selected Window** — new in macOS 26 Tahoe, and the best option for a demo. It captures one app window cleanly, without your desktop or a stray notification bleeding in.
3. Click **Options** and configure (see below).
4. Click **Record**.
5. Stop with **⌘ + Control + Esc**, or click the stop button in the menu bar.
6. A thumbnail appears in the corner. Click it to trim, or let it save.

Recordings save as **`.mov`** to wherever you set Save To (Desktop by default).

### The Options menu

| Option | What to set |
| ------ | ----------- |
| **Microphone** | **This is the one that matters.** Defaults to **None**. Leave it on None for a silent video; pick your input for narration. |
| Save to | Desktop, Documents, or a folder of your choosing |
| Timer | 5 or 10 seconds — gives you time to arrange windows after clicking Record |
| Show Mouse Clicks | **Turn this on.** It draws a circle around each click, which makes a silent demo far easier to follow. |
| Capture Format (Tahoe 26+) | **SDR.** HDR looks nicer on your Mac and worse everywhere else. Pick SDR / H.264 for compatibility. |

### Audio: with voice or without

- **Silent video (no narration):** leave **Microphone: None**. That's the default, so doing nothing gets you a silent recording. Perfectly valid — add text callouts in editing.
- **Narrated:** Options → Microphone → select your input. Use a headset or a USB mic if you have one; the built-in mic picks up the whole hotel bar.

**Watch out:** macOS does not reliably remember the microphone selection between sessions or between capture modes. A workflow that recorded audio last week can silently produce a silent file today. Check the Options menu every single time, and test-record ten seconds.

---

## Option B: QuickTime Player

Same recorder, different door — but QuickTime is genuinely useful for the *editing* step.

**To record:** QuickTime Player → File → New Screen Recording. This opens the ⌘⇧5 toolbar. Everything above applies.

**To trim:** open the `.mov` in QuickTime → **Edit → Trim (⌘T)** → drag the yellow handles → Trim → save. Fast and good enough for cutting dead air off the front and back.

**To split and rejoin:** ⌘Y splits the clip at the playhead, and you can drag a second clip in from Finder to append. Clunky but functional for stitching two takes.

QuickTime's **File → Export As** produces H.264 in a `.mov` container. That's a perfectly acceptable submission — no further conversion needed. Export at **1080p** and check the file size.

---

## Option C: ZoomIt for Mac

Microsoft now ships a native macOS port of the Sysinternals ZoomIt presentation tool, and it's the most capable free option on this list for a *technical* demo. It's newer than the Windows version, so treat it as the interesting option rather than the safe one — but it does things the built-in recorder can't.

**Install:**

```bash
brew install --cask microsoft/sysinternalstap/zoomit
```

Or grab it from [github.com/microsoft/ZoomitForMac](https://github.com/microsoft/ZoomitForMac).

**What it gives you over ⌘⇧5:**

- MP4 recording of the full screen or a selected region — **with optional system audio, microphone audio, and a webcam picture-in-picture**. That system audio support is the big one; it solves the macOS limitation without a virtual audio driver.
- **Live zoom** on running content, so a judge can actually read your log output
- Pen, arrow, rectangle, highlighter, and a **blur pen** for hiding an API key mid-demo
- A post-recording editor with trim, append, fades, and export

It'll prompt for Screen Recording, Microphone, and Camera permissions on first run. Grant what you need in System Settings → Privacy & Security.

If you're demoing something with small UI detail, this is worth the five minutes to install.

---

## Recording system audio

If your demo produces sound that matters — audio generation, a voice agent, a video call — the built-in recorder will not capture it. Options, in order of least hassle:

1. **Just narrate over it.** Say "and here it's generating the audio track" instead of playing it. Fastest fix, and honestly fine for a hackathon demo.
2. **Use ZoomIt for Mac** (above), which captures system audio directly.
3. **Install BlackHole**, a free open-source virtual audio driver:
   - Install BlackHole (2ch is enough) from [existential.audio](https://existential.audio/blackhole/)
   - Open **Audio MIDI Setup** → **+** → **Create Multi-Output Device**
   - Check both **BlackHole 2ch** and your real speakers/headphones, with your real output listed first so you can still hear
   - Set the Multi-Output Device as your output in System Settings → Sound
   - In ⌘⇧5 → Options → Microphone, select **BlackHole 2ch**

   **Tradeoff:** there's only one microphone slot, so you get system audio *instead of* your voice, not alongside it. If you need both, record system audio and narration separately and mix them in iMovie.

Set your audio output back afterward, or you'll wonder why your headphones are quiet for the rest of the event.

---

## Editing and captions: iMovie

iMovie is free from the App Store and does everything you need.

- **Trim dead air** — cut the compile, the cold start, the fumbling
- **Titles** — essential if you're going silent. Add a title card at the start (project, team, category) and short text callouts over each demo step.
- **Join takes** — drop clips on the timeline in order
- **Export** — Share → Export File → 1080p, Quality: High. iMovie outputs `.mp4` if you'd prefer that container.

If iMovie feels heavy for what you need, QuickTime's ⌘T trim plus a title card made in Keynote and screen-recorded for five seconds is a perfectly legitimate hack.

---

## Compressing (and optional conversion)

**You do not need to convert to MP4.** Commit the `.mov` as-is if it's small enough. The only hard requirement is **under 100 MB**. Check first:

```bash
ls -lh demo/demo.mov
```

Under 100 MB? You're done — skip to [Committing the video](#committing-the-video).

Over 100 MB? Re-encode. Install ffmpeg once:

```bash
brew install ffmpeg
```

This shrinks the file and converts to MP4 in the same pass. If you'd rather keep the `.mov` container, just change the output extension to `.mov` — the encoding settings are identical either way:

```bash
ffmpeg -i recording.mov -c:v libx264 -preset slow -crf 24 -vf "scale=1920:-2" -c:a aac -b:a 128k -movflags +faststart demo.mp4
```

Knobs, in the order you should reach for them:

- **`-crf`** — quality. Higher number, smaller file. `24` is a good start; `28` is still perfectly watchable for a screen recording; past `30` text starts to smear.
- **`-vf "scale=1280:-2"`** — drop to 720p. Screen recordings compress well and 720p is fine if your fonts are large.
- **`-an`** — strip audio entirely. Only if you're going silent anyway.
- **Trim it.** If you're 40% over the limit, you probably also have 40% of the video that isn't earning its place.

**Recording on an M-series Mac?** Hardware-accelerated encoding is much faster, at slightly larger file sizes:

```bash
ffmpeg -i recording.mov -c:v h264_videotoolbox -b:v 4M -vf "scale=1920:-2" -c:a aac -b:a 128k -movflags +faststart demo.mp4
```

Drop `-b:v` to `2M` if you're still over the limit.

Rough sanity check: a 3-minute 1080p screen recording at CRF 24 typically lands well under 50 MB. If yours is 400 MB, you recorded a Retina display at native resolution — re-encoding will fix it.

No ffmpeg? [HandBrake](https://handbrake.fr/) is free, graphical, and its "Fast 1080p30" preset will get you an MP4 in the right ballpark.

---

## Committing the video

```bash
# Confirm .gitignore isn't silently excluding it (use your actual extension)
git check-ignore -v demo/demo.mov
# No output = you're fine.

git add demo/demo.mov
git commit -m "Add demo video"
git push
```

`.mov` is more likely than `.mp4` to be caught by a stray ignore rule, so don't skip this check.

If `git check-ignore` prints a line, some pattern (`*.mp4`, `*.mov`, `demo/`, `media/`) is excluding your video. Fix `.gitignore` first — see Section 7 of the main guide.

---

## Troubleshooting

| Symptom | Fix |
| ------- | --- |
| Recording is silent, but I wanted narration | Microphone was set to **None**. It's the default and macOS doesn't reliably remember your choice. ⌘⇧5 → Options → Microphone. Test-record ten seconds next time. |
| Mic is selected but still no audio | System Settings → Privacy & Security → Microphone. Confirm the recording app is enabled. |
| App/system sound isn't in the recording | Expected — macOS never captures it natively. See [Recording system audio](#recording-system-audio). |
| Recording shows a black screen | Either the app lacks Screen Recording permission (System Settings → Privacy & Security → Screen & System Audio Recording), or the content is DRM-protected (Apple TV, some streaming). DRM cannot be worked around. |
| I have a `.mov`, not an MP4 | That's fine — `.mov` is accepted. Only convert if you want to. |
| File is way over 100 MB | You recorded a Retina display at native resolution. Re-encode with ffmpeg. |
| Can't stop the recording | **⌘ + Control + Esc** stops any active screen recording instantly. |
| A notification popped up mid-demo | Do Not Disturb, then re-record. |

---

Questions during the event? Find any of the moderators at the moderator table.
