# Arto Transcriber

**Voice dictation for Windows and Android — with recovery when text delivery fails.**

An independently developed application by **ArtoBuilds**. Speak from a desktop shortcut or an Android recording bubble, transcribe your recording, and deliver the text to a supported editor.

**Status: alpha · Public showcase · Application source and installers are not published here.**

## Why this project

Dictation is more than speech recognition. A useful tool also needs to handle microphone recording, changing windows, unavailable APIs, and editors that do not accept automatic insertion.

Arto Transcriber combines native desktop and mobile interfaces with recoverable recording and text-delivery workflows. Its focus is everyday dictation, including Russian and Ukrainian speech with English terms, rather than meeting summaries or automatic rewriting.

## Two native applications

| | Windows | Android |
| --- | --- | --- |
| Interface | Keyboard/mouse triggers and a compact recording overlay | Draggable recording bubble over supported editors |
| Cloud recognition | ElevenLabs Scribe v2 | ElevenLabs Scribe v2 |
| Local recognition | faster-whisper large-v3, with a configured local runtime and model | Not currently available |
| Delivery | Automatic insertion into the intended application, with recovery controls | Editor integration through Accessibility/InputConnection, with optional clipboard recovery |
| Recovery | Retained recordings for retry and local transcript history | Durable queue, retained results, and retry from history |
| Technology | C# / .NET / WPF | Kotlin / Jetpack Compose |

These describe the current alpha implementation, not a guarantee of compatibility with every application or device.

## How dictation works

1. Focus the field where you want to write, then start a recording.
2. Speak and stop the recording. Audio is saved locally before transcription begins.
3. The selected recognition path produces text. On Windows, configured local recognition can be used when the cloud path is unavailable.
4. Arto attempts to deliver the result to the intended editor.
5. If delivery cannot be completed or confirmed, recovery paths keep the result available instead of treating it as successfully inserted. On Android, automatic clipboard recovery is an opt-in setting.

Switching apps or changing fields can invalidate the original insertion target. Clipboard recovery and history are fallback paths; automatic insertion is not promised after arbitrary focus changes.

## Privacy and setup

- **Cloud mode sends recorded audio to ElevenLabs.** It is not an offline-only workflow. Provider terms, availability, credits, and usage charges apply.
- The current personal alpha uses a user-provided ElevenLabs API key. No shared API credentials are distributed through this repository.
- Windows local recognition requires the local runtime and model to be installed and configured. Performance depends on the computer; Android does not have this local fallback.
- Recordings and transcripts may be retained locally for history and recovery. Treat them as personal data and manage retention accordingly.
- Android recording and insertion depend on microphone, overlay, and accessibility permissions. OS restrictions and editor behavior can affect delivery.

## Current limits

- This is an alpha product, not a generally available commercial release.
- Transcription can be wrong, especially with noise, silence, or mixed-language speech. Review important text before sending it.
- Network delays, exhausted provider credits, and local-model startup can delay recognition.
- Some editors need manual paste. A successful recognition result is not the same as a confirmed insertion.
- Compatibility testing is ongoing; no universal reliability or accuracy benchmark is claimed here.

## Demo and availability

A video walkthrough will be added in a separate update. There is no public download or purchase link at this stage.

This repository is a product showcase, not the application's source repository. Application code, API keys, recordings, transcripts, private diagnostics, and signing material are intentionally excluded. Pricing and distribution terms have not been announced.

## Feedback

Questions and general feedback are welcome in [Issues](https://github.com/Noldor11/Arto-Transcriber/issues). Include the platform and a short description of the scenario. **Do not post API keys, private recordings, personal transcripts, or sensitive screenshots.**

Built by **ArtoBuilds**.

Arto Transcriber is an independent project and is not an official ElevenLabs, Microsoft, or Google product.
