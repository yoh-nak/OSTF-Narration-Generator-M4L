# OSTF Narration Generator

**Multilingual Text-to-Speech Narration for Ableton Live**

OSTF Narration Generator is a Max for Live Audio Effect that generates spoken narration from text or lyrics imported from Open Song Timeline Format (OSTF).

The device uses the **operating system's built-in text-to-speech (TTS) capabilities**, automatically selecting the appropriate speech synthesis backend for Windows or macOS.

Unlike the experimental OSTF Vocal Generator, which synthesizes singing voices from phonetic samples, OSTF Narration Generator is dedicated to spoken narration.

It supports multiple languages, male and female voices, adjustable speaking speed, target-duration control, DAW synchronization, audio recording, WAV export, and audio clip writing.

**Important: Available languages, voices, pronunciation quality, and synthesis capabilities depend on the operating system and the speech voices installed on the user's computer.**

## About Open Song Timeline Format (OSTF)

**Open Song Timeline Format (OSTF)** is an open music data format designed to separate musical information from the software used to create, edit, or perform it.

Its central philosophy is:

**Music data should be independent of the applications that interpret it.**

Depending on the format version, OSTF can represent:

- Song metadata and musical structure
- Tempo, time signatures, and timeline positions
- Chord progressions
- Melody and note information
- Lyrics and pronunciation information
- Arrangement information
- Application-specific extensions

OSTF allows different applications to interpret the information relevant to their purposes.

For example, the same OSTF song information may be used by a chord editor, lyric editor, vocal synthesizer, narration generator, or other music application.

OSTF Narration Generator demonstrates this flexibility by interpreting song lyrics as spoken narration rather than singing them according to melody notes.

**Open Song Timeline Format 3.0:**

https://github.com/yoh-nak/Open-Song-Timeline-Format-3.0

## Main Features

### Multilingual Text-to-Speech

- Text-to-speech narration using operating system speech engines
- Automatic Windows / macOS detection
- Automatic selection of the corresponding TTS backend
- Language selection based on installed voices
- Male, female, and other available voice classifications
- Individual voice selection
- Automatic voice discovery and rescan
- Direct text input and editing
- Optional pronunciation corrections
- Support for languages and writing systems handled by the selected TTS engine
- Automatic speech generation before playback

The device does not include a fixed list of supported languages or a large internal voice library.

Instead, it discovers the speech voices available through the operating system.

### Voice Selection

The device provides the following settings:

**LANGUAGE**

Select the language or locale of the narration voice.

**GENDER**

Filter available voices by their reported gender.

**VOICE**

Select a specific installed voice or use automatic selection within the requested language and gender.

**RESCAN**

Refresh the available voice list after installing or removing operating system speech voices.

Voice information is obtained from the operating system.

A voice with unknown gender is not automatically classified as male or female.

If the requested language, gender, or voice is unavailable, the device reports an error and stops speech generation rather than silently switching to an unrelated voice.

### OSTF Integration

- Import lyrics from compatible OSTF song files
- Use imported lyrics as narration text
- Interpret available pronunciation information
- Narrate lyrics without requiring melody notes
- Preserve the original OSTF file without modification

The device uses OSTF as a source of structured song and lyric information, not as a singing synthesis engine.

### Narration Timing

- Adjustable narration speaking speed
- Target-duration adjustment with FIT TOTAL
- Automatic recalculation of narration length
- Timing adjustments without intentionally truncating the text
- Playback duration display

Actual timing depends on the selected voice and operating system synthesis engine.

### Ableton Live Integration

- Max for Live Audio Effect
- Internal narration playback
- DAW transport synchronization
- Adjustable synchronization offset
- Recording of actual playback audio
- Recorded waveform display
- WAV export
- Audio clip writing to the same audio track
- Recording buffer clear function

## How to Use

### Basic Text Narration

1. Place the device on a regular audio track in Ableton Live.
2. Select the desired LANGUAGE.
3. Select the GENDER and VOICE.
4. Enter or paste text into the TEXT area.
5. Use READING if pronunciation corrections are required.
6. Adjust the speaking speed or target duration.
7. Click PLAY to generate and play the narration.
8. The playback output is recorded and displayed as a waveform.
9. Click EXPORT WAV to save the recording.
10. Alternatively, click WRITE CLIP to place the recording on the same audio track.
11. Use CLEAR to remove the current recording.

### Narrating Lyrics from OSTF

1. Select the desired narration language and voice.
2. Click LOAD OSTF.
3. Select a compatible OSTF song file.
4. The device extracts available lyrics and pronunciation information.
5. Edit the narration text or reading if necessary.
6. Adjust the speed and timing.
7. Click PLAY to generate spoken narration.

Unlike a singing synthesizer, the device does not require the original song melody to read lyrics aloud.

### Speed and Target Duration

**SPEED**

Adjust the speaking speed using the selected operating system speech engine.

**FIT TOTAL**

Specify a target narration duration in seconds.

The device attempts to adjust the speaking speed to match the requested duration.

If the requested duration cannot be achieved within the available speed range, it may report a limitation or use additional silence rather than truncate the narration.

Different voices and operating systems may produce different durations, even when using the same speed setting.

## Operating System Dependencies

**OSTF Narration Generator relies on speech synthesis capabilities provided by the host operating system.**

It does not bundle its own multilingual speech models.

This design keeps the device relatively lightweight and allows it to take advantage of speech voices already installed on the computer.

However, it also means that narration capabilities are determined by the operating system.

### Windows

On Windows, the device uses available Windows speech synthesis interfaces.

The available languages, voices, and voice characteristics depend on the installed Windows TTS voices.

A Japanese Windows display language is not required to generate Japanese narration, provided that a compatible Japanese TTS voice is installed and accessible.

Similarly, English or other language narration requires a corresponding compatible voice.

Not every voice listed in Windows accessibility or Narrator settings is necessarily available through the speech interfaces used by this device.

### macOS

On macOS, the device uses available macOS speech synthesis capabilities.

Available narration languages and voices depend on the speech voices installed and accessible on that Mac.

Additional voices may be available through macOS speech or accessibility settings.

The voice selection and audio generation behavior may differ from Windows.

**macOS support has been implemented but has not yet been verified on a physical Mac with Ableton Live. Community testing is welcome.**

### Voice Availability

The device automatically detects the operating system and discovers available voices.

However:

- OS display language does not determine the only supported narration language.
- A compatible speech voice must be installed for the selected language.
- Male and female voices may not exist for every language.
- Gender information may be unavailable for certain voices.
- The same voice models are not necessarily available on Windows and macOS.
- Speech quality, pronunciation, and timing may differ between operating systems.
- Some OS-level premium or natural voices may not be accessible through the APIs used by the device.

**If a selected voice is unavailable, the device stops generation and displays an error instead of silently choosing another language or gender.**

### Performance

The device does not need to load a large bundled voice bank.

Speech generation is performed using the selected operating system TTS engine.

Once generated, audio can be played and recorded through the device's existing audio workflow.

However, speech generation is not computationally free.

Long text, repeated target-duration calculations, or more advanced operating system voices may require additional processing time or memory.

## Audio Export and Clip Writing

**EXPORT WAV** saves the recorded narration as a WAV audio file.

**WRITE CLIP** automatically saves the recording internally and creates an Arrangement audio clip on the same audio track containing the device.

**CLEAR** removes the current recording buffer without intentionally deleting previously exported WAV files or created clips.

The device is designed for use on a regular audio track, not a MIDI track.

## Technical Approach

OSTF Narration Generator uses a platform-dependent speech synthesis backend.

**Windows:** Windows speech synthesis interfaces.

**macOS:** macOS speech synthesis interfaces.

Node for Max coordinates operating system detection, voice discovery, text-to-speech generation, and communication with the Max for Live device.

The generated audio is then handled by the shared playback, recording, waveform, and export workflow.

This approach separates the speech synthesis engine from the musical timeline and DAW integration.

It also avoids embedding separate voice sample libraries for every language and gender.

## Requirements

- Ableton Live with Max for Live support
- Windows or macOS
- A functioning Node for Max environment
- At least one compatible operating system TTS voice
- A compatible speech voice for the selected language and gender

An external cloud speech synthesis subscription is not required for the intended local workflow.

**The device's audio generation capabilities depend on the operating system and installed speech voices.**

## Limitations

OSTF Narration Generator is a reference implementation of OSTF-based narration technology.

Known limitations include:

- Platform-dependent TTS voices and speech quality
- Different voice availability on Windows and macOS
- No guarantee of identical narration output across operating systems
- Possible pronunciation errors for names or specialized terminology
- Voice gender information may be missing or incomplete
- Limited emotional expression compared with advanced neural TTS systems
- Target-duration accuracy depending on the selected speech engine
- Limited synchronization with complex tempo and time-signature automation
- Compatibility depending on the structure of imported OSTF files
- macOS implementation awaiting real-world testing

The device is not a speech translation tool.

Selecting a language changes the narration voice; it does not translate the original text into that language.

It is also not a singing synthesizer.

## For Developers and the Community

This project demonstrates how OSTF can be combined with operating system text-to-speech technology and Ableton Live.

Developers are encouraged to explore alternative speech synthesis engines and extend the concept.

Possible improvements include:

- More natural neural TTS
- Additional voice providers
- Improved pronunciation and accent processing
- More expressive voice styles
- Multiple speakers within a single narration
- More accurate target-duration adjustment
- Advanced narration timeline editing
- Improved DAW synchronization
- Cross-platform compatibility testing
- More consistent voice behavior across operating systems
- Standalone OSTF-based narration applications

The goal is not necessarily to extend this exact Max for Live device.

Independent applications using OSTF as a common format for musical timelines, lyrics, and speech are also welcome.

Any reuse or redistribution should follow the applicable software and dependency licenses.

## Project Philosophy

OSTF is a data format, not a speech synthesis engine.

OSTF Narration Generator demonstrates one possible use of structured OSTF lyrics with operating system speech synthesis technology.

By separating musical data from the application that processes it, OSTF can support a variety of creative workflows.

The same song information may be edited in one application, sung by another, and narrated by a third.

This independence and interoperability are central to the OSTF concept.

## Project Information

- **Version:** 2.0
- **Status:** Multilingual Reference Implementation
- **Platform:** Ableton Live / Max for Live / Windows / macOS
- **Device Type:** Max Audio Effect
- **Languages:** Determined by installed operating system TTS voices
- **Voices:** Selected from available system voices
- **Speech Engine:** Automatically selected according to the operating system
- **macOS Testing:** Implementation available; real-world validation pending

## Links

**Open Song Timeline Format 3.0**

https://github.com/yoh-nak/Open-Song-Timeline-Format-3.0

**Developer — yoh-nak**

https://github.com/yoh-nak

---

*An OSTF-based multilingual narration experiment connecting operating system speech synthesis with music production workflows in Ableton Live.*
