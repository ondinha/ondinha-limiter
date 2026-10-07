# Ondinha Limiter

**True-peak brickwall limiter for mastering, with an optional oversampled clipper. 8x true-peak detection, clean auto release, streaming-safe ceilings.**

A VST3 and Audio Unit plug-in from [Ondinha](https://github.com/ondinha), a DAW 2.0: native AI tools combined with traditional sound engineering tools.

The last plug-in on your master. It makes the track louder and guarantees the peaks never go over the ceiling, including the peaks **between** the samples that a DAC or an MP3 / AAC encoder will see.

An optional clipper shaves the fastest drum peaks first, so the limiter has less to do and pumps less.

## What it's good for

- Streaming master: ceiling -1 dBTP, auto release, push **Gain** until it's loud enough.
- Loud genres: switch on the clipper at 2 dB to keep drums punchy at higher levels.
- Safety on a bus or a bounce: set the ceiling and forget it.

## Controls

| Control | Range | What it does |
|---|---|---|
| Gain | 0-24 dB | Drive into the limiter. |
| Ceiling | -12 to 0 dBTP | True-peak maximum of the output. |
| Release | 5-1000 ms | Or **Auto release**: fast after short peaks, slow under sustained limiting. |
| Lookahead | 0.5-10 ms | Longer is smoother, shorter keeps more snap. |
| Clipper | Off / On | Soft clip before the limiter. |
| Clip above | 0-6 dB | How far above the ceiling the clipper starts. |

## Presets

Built in as host programs (your DAW's preset menu):

- Transparent (-1 dBTP)
- Loud: clip 2 dB, limit
- Streaming safe (-1 dBTP, slow)

## Download and install

Builds will be on the [Releases](../../releases) page.

**macOS:** copy `Ondinha Limiter.vst3` to `~/Library/Audio/Plug-Ins/VST3` and `Ondinha Limiter.component` to `~/Library/Audio/Plug-Ins/Components`, then rescan plug-ins in your DAW.

| Format | Platform |
|---|---|
| VST3 | macOS |
| Audio Unit (AU) | macOS |

Works in any VST3 or AU host: Ableton Live, Logic Pro, Reaper, Bitwig Studio, Cubase, Studio One, FL Studio and others.

## How it works

True peaks are found 8x oversampled with a Kaiser-windowed sinc (finer than the 4x in ITU-R BS.1770, which can miss up to ~0.5 dB). The needed gain is held at its minimum over the lookahead and averaged over the same window, so it's already down when the peak arrives and never moves faster than the window: no clicks, no overshoot. A short second true-peak stage and a sample-peak guard catch the rest. The clipper is 4x oversampled and linear-phase with a 20 kHz low-pass after it. **Under the ceiling, with the clipper off, the limiter is bit-transparent.** Stereo linked; latency reported to the host.

## More Ondinha plug-ins

- [Ondinha Bus Comp](https://github.com/ondinha/ondinha-bus-comp): Console-style glue compressor for the mix bus and groups.
- [Ondinha Split EQ](https://github.com/ondinha/ondinha-split-eq): Transient / tonal split EQ: separate gain for the attack and the sustain in every band.
- [Ondinha Unmask](https://github.com/ondinha/ondinha-unmask): Spectral side-chain ducking: dips a track only at the frequencies where the key is loud, only while it plays.
- [Ondinha Resonance](https://github.com/ondinha/ondinha-resonance): Dynamic resonance tamer for harsh mixes, vocals and guitars: pulls down narrow peaks only while they ring and leaves the broad tone alone.
- [Ondinha Imager](https://github.com/ondinha/ondinha-imager): Multiband stereo imager with mono low end: width for lows, mids and highs on phase-matched Linkwitz-Riley crossovers.
- [Ondinha Delay](https://github.com/ondinha/ondinha-delay): Tempo-synced stereo / ping-pong delay with filtered, saturated feedback and ducking, so the echoes stay out of the way of the vocal.
- [Ondinha Graphic EQ](https://github.com/ondinha/ondinha-graphic-eq): 10-band octave graphic EQ with analog-matched bells (31 Hz - 16 kHz, +-12 dB).
- [Ondinha Tube Air](https://github.com/ondinha/ondinha-tube-air): High-frequency exciter with a tube stage: adds warm even or bright odd harmonics above a frequency, under the untouched signal.

## Feedback

Found a bug or a host where it misbehaves? [Open an issue](../../issues) with your DAW, its version and your OS.
