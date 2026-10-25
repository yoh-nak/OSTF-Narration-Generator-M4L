# OSTF Narration Generator / JA Male

**Japanese Text-to-Speech Narration for Ableton Live**

OSTF Narration Generator / JA Male is a Max for Live Audio Effect that generates Japanese narration from text or lyrics imported from Open Song Timeline Format (OSTF).

Unlike the experimental OSTF Vocal Generator, which synthesizes singing voices from phonetic samples, this device uses the **Windows Japanese text-to-speech (TTS) system** to generate spoken narration.

It is designed for voiceovers, spoken-word production, narration, music introductions, and other audio projects requiring Japanese speech inside Ableton Live.

The device demonstrates how OSTF can be used beyond conventional music playback, connecting structured song information with speech synthesis and DAW audio workflows.

## About Open Song Timeline Format (OSTF)

**Open Song Timeline Format (OSTF)** is an open music data format designed to separate musical information from the software used to create, edit, or perform it.

Its central philosophy is:

**Music data should be independent of the applications that interpret it.**

OSTF supports the exchange of structured musical information, including song metadata, sections, tempo, time signatures, chords, melodies, lyrics, pronunciation information, and arrangement data, depending on the format version.

This allows different applications to use the same song information for different purposes.

For example, OSTF lyrics can be interpreted by a singing synthesizer, narration generator, lyric editor, or other text-based audio application.

OSTF Narration Generator demonstrates this flexibility by interpreting song lyrics as spoken Japanese rather than singing them according to melody notes.

**Open Song Timeline Format 3.0:**

https://github.com/yoh-nak/Open-Song-Timeline-Format-3.0

## Main Features

### Japanese Text-to-Speech

- Japanese narration using Windows TTS
- Japanese male voice selection through the installed TTS system
- Direct input of Japanese text
- Support for Japanese text containing kanji, hiragana, and katakana
- Optional pronunciation corrections
- Text-based narration without MIDI melody notes
- Automatic audio generation before playback

### OSTF Integration

- Import lyrics from compatible OSTF song files
- Use OSTF lyrics as narration text
- Interpret available pronunciation information
- Narrate song lyrics without following their original melody
- Preserve the original OSTF file without modification

### Narration Timing

- Adjustable narration playback speed
- Target-duration adjustment with FIT TOTAL
- Automatic recalculation of narration length
- Timing adjustment without intentionally truncating the text
- Playback duration display

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

1. Place the device on an audio track in Ableton Live.
2. Enter or paste Japanese text into the TEXT area.
3. Use READING if pronunciation correction is required.
4. Adjust the narration speed or target duration.
5. Click PLAY to generate and play the narration.
6. The generated narration is recorded and displayed as a waveform.
7. Click EXPORT WAV to save the recorded audio.
8. Alternatively, click WRITE CLIP to place the recording on the same audio track.
9. Use CLEAR to remove the current recording.

### Narrating Lyrics from OSTF

1. Click LOAD OSTF.
2. Select a compatible OSTF song file.
3. The device extracts available lyrics and pronunciation information.
4. Edit the narration text or reading if necessary.
5. Adjust playback speed and timing.
6. Click PLAY to generate spoken narration.

Unlike a singing synthesizer, this device does not require the original song melody to read the lyrics aloud.

### Speed and Target Duration

The device provides two approaches to controlling narration length.

**SPEED**

Adjust the speaking speed of the narration.

**FIT TOTAL**

Specify a target duration in seconds.

The device attempts to adjust the narration speed to fit the requested duration.

When the requested duration cannot be achieved within the supported speed range, the device may report a limitation or use additional silence rather than truncate the narration.

## Audio Export and Clip Writing

**EXPORT WAV** saves the recorded narration as a WAV audio file.

**WRITE CLIP** automatically saves the recording internally and attempts to create an Arrangement audio clip on the same audio track containing the device.

**CLEAR** removes the current recording buffer without intentionally deleting previously exported audio files or created clips.

The device is intended for use on a regular audio track rather than a MIDI track.

## Technical Approach

This device uses the Japanese speech synthesis functionality available through Windows.

Unlike sample-based singing synthesis, narration is generated from text using the installed TTS voice and its pronunciation processing.

This approach eliminates the need to embed a large Japanese singing voice sample bank inside the Max for Live device.

It also allows the TTS engine to interpret Japanese sentences, including many kanji expressions, rather than requiring every syllable to be manually assembled.

The implementation uses Node for Max to coordinate speech generation with the device's playback, recording, and export workflows.

## Requirements

- Ableton Live with Max for Live support
- Windows
- A compatible Windows Japanese male TTS voice
- A functioning Node for Max environment

The device relies on locally available Windows speech synthesis capabilities.

Voice availability, pronunciation, synthesis quality, and compatibility may vary depending on the Windows installation and installed speech voices.

An external cloud speech synthesis account is not required for the intended local workflow.

## Limitations

This is an early reference implementation of OSTF-based narration generation.

Known limitations include:

- Windows-specific speech synthesis dependencies
- Voice quality determined by available Windows TTS voices
- Possible pronunciation errors for uncommon names or specialized terminology
- Limited emotional expression and voice customization
- Target-duration accuracy dependent on the TTS engine
- Limited synchronization with complex tempo and time-signature automation
- Compatibility dependent on the structure of imported OSTF files

The device is not intended to replace professional narration recording or advanced neural text-to-speech systems.

It is also not a singing synthesizer.

## For Developers and the Community

This project is shared as an example of how OSTF can be used with text-to-speech technology and Ableton Live.

Developers are encouraged to explore alternative narration engines and extend the concept.

Possible improvements include:

- More natural Japanese neural TTS
- Improved Japanese pronunciation and accent analysis
- Multiple speakers and voice styles
- Emotional narration controls
- More accurate target-duration adjustment
- Sentence-level timeline editing
- Advanced synchronization with Ableton Live
- Cross-platform speech synthesis
- Multilingual narration
- Standalone OSTF-based narration software

The goal is not necessarily to extend this particular Max for Live device.

Developers are also encouraged to create independent applications using OSTF as a common format for musical timelines, lyrics, speech, and related information.

Any reuse or redistribution should follow the applicable software and dependency licenses.

## Project Philosophy

OSTF is a data format, not a speech synthesis engine.

This project demonstrates one possible interpretation of OSTF lyrics using Japanese text-to-speech technology.

By separating structured song information from the application that processes it, OSTF can support many different kinds of creative software.

A song's lyrics might be sung by one application, narrated by another, and edited by a third, without requiring each application to use the same synthesis engine.

This interoperability and extensibility are central to the OSTF concept.

## Project Information

- **Version:** 1.0
- **Status:** Initial Release / Reference Implementation
- **Platform:** Ableton Live / Max for Live / Windows
- **Device Type:** Max Audio Effect
- **Language:** Japanese
- **Voice:** Windows Japanese Male TTS
- **Primary Functions:** Text-to-Speech, OSTF Lyric Narration, Recording, WAV Export, Audio Clip Writing

## Links

**Open Song Timeline Format 3.0**

https://github.com/yoh-nak/Open-Song-Timeline-Format-3.0

**Developer — yoh-nak**

https://github.com/yoh-nak

---

*An OSTF-based Japanese narration experiment connecting text-to-speech technology with music production workflows in Ableton Live.*
