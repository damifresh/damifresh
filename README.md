# damifresh

**Local-first media engineer.** I build AI video tools, desktop applications, and adaptive playback systems that keep working without cloud services — then verify them against real renders, real devices, and real constraints.

Open to opportunities in AI/video engineering, full-stack desktop apps, media streaming, and systems debugging.

## What I work on

- **AI video tooling** — local generation and auto-clipping pipelines built around FFmpeg, whisper.cpp, and deterministic scoring rather than opaque cloud calls.
- **Full-stack desktop apps** — Python/FastAPI backends, React + TypeScript interfaces, Electron shells, SQLite state, and signed macOS packages.
- **Adaptive streaming** — HLS/fMP4 rendition ladders, segment/keyframe cadence, codec and HDR metadata, and playback on constrained hardware.
- **Hard debugging** — reproducing intermittent failures, separating network/buffer problems from decode/display problems, and verifying each narrow change before moving on.

## Selected work

### [AI Social Video Studio](https://github.com/damifresh/ai-social-video-studio)

A fully local macOS desktop app with two engines: a prompt-to-video creator (720p H.264/AAC, 1–5 minutes, script → storyboard → narration → captions → mix → render) and an auto-clip studio (local ASR or SRT/VTT import, transcript-grounded highlight scoring, native-resolution exports, one-clip assembly, multi-source combines).

- **Verified:** 16 PASS / 0 FAIL / 0 NOT_RUN in the Engine B acceptance harness; 51 unit tests and 25/25 Electron UI smoke checks reported for the latest features.
- **Measured:** 5-minute 720p render in 329.1 s, 21.44 MB, peak 746 MB; long-source harness exercised synthetic sources up to 60 minutes.
- **Honest limitations:** synthetic TTS fixtures, Apple M2 / 8 GB target, animated stills by default rather than assumed diffusion footage. All measurement tables and failure notes are in the repo docs.

### [Adaptive HLS on a constrained TV — case study](https://github.com/damifresh/open-screen-hls-case-study)

Source-free engineering write-up about eliminating recurring playback freezes on a Hisense Android/VIDAA TV.

- Built a same-origin adaptive HLS path with vendored hls.js, one FFmpeg process per viewer, and finite VOD playlists.
- Used live segment-request logs, NAL-level bitstream checks, and container atom inspection to rule out bandwidth, buffer starvation, HDR SEI, and bitrate as sole causes.
- Final build moved from 2 s to 4 s segments and forced one IDR per segment; the TV owner reported the freeze gone.
- The private source repository remains private; the case study contains method and measurements only.

## How I work

1. **Measure before changing.** I look at request timing, byte counts, keyframe placement, and decoded frame evidence instead of guessing.
2. **Change one thing per build.** Each iteration is narrow, tested, and reversible.
3. **Preserve the product.** UI/UX, existing APIs, and device compatibility stay intact while internals are fixed.
4. **Publish the caveats.** Test fixtures, hardware limits, and unproven causal claims are documented next to the results.

## Stack

Python · FastAPI · React · TypeScript · Electron · SQLite · FFmpeg · hls.js · HLS/fMP4 · whisper.cpp · pytest · macOS packaging

---

This profile uses the `damifresh` handle only: no real name, location, or external contact link by choice.
