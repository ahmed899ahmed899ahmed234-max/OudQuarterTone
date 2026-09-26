# Oud QuarterTone

VST3/Standalone effect plugin (JUCE + CMake) that converts a guitar signal into an
oud-like (Karplus-Strong plucked-string) sound, tracked note-by-note by a YIN pitch
detector, then remapped to Arabic maqam quarter-tone intonation (Rast, Bayati, Sikah,
or a fully custom 12-step cents table), or snapped freely to any 24-TET quarter tone.

## Parameters
- Mode: Maqam Map / Quarter-Tone Snap / Free Follow
- Maqam: Off / Rast / Bayati / Sikah / Custom (12 per-semitone cents knobs)
- Tonic: which guitar note is the maqam's root
- Bend Follow, Input Gate, Sustain, Tone, Pick Brightness, Course Detune,
  Note Overlap, Body Resonance, Oud Level, Dry Guitar Level

## Build (Windows, for FL Studio)
Requires Visual Studio 2022 (Desktop C++ workload) and CMake 3.22+.

    cmake -B build -G "Visual Studio 17 2022" -A x64
    cmake --build build --config Release --target OudQuarterTone_VST3

Output: build/OudQuarterTone_artefacts/Release/VST3/Oud QuarterTone.vst3
Copy that .vst3 folder into: C:\Program Files\Common Files\VST3\
then rescan plugins in FL Studio.

## Build via GitHub Actions (no local toolchain needed)
Push this folder to a new GitHub repo. The included
`.github/workflows/build-windows.yml` builds it on GitHub's Windows runners
automatically and uploads the .vst3 as a downloadable artifact — no need to
install Visual Studio yourself.

## Build (macOS, for AU/VST3)
    cmake -B build -G Xcode
    cmake --build build --config Release --target OudQuarterTone_VST3
