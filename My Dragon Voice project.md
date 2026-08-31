# My Dragon Voice project.md
**External name:** My Dragon Voice project.md  
**Internal name:** 2026-08-30-2114-my-dragon-voice-project  
**Object type:** project  
**File type:** markdown  
**Type:** Project capture  
**Status:** captured-incomplete-plan  
**Owner:** tripLr  
**Source:** voice / X Grok share paste session  
**Captured:** 2026-08-30  
**Design date on source docs:** 2026-08-31  
**Repo:** tripLr/Train-My-Dragon-AI-2.0  
**AI:** Grok (this window)  

---

## Completeness

| Piece | Status |
|-------|--------|
| Product brief (what / why / decisions) | Complete through section 10 |
| Development plan Phases 0-1 | Captured |
| Development plan Phase 2+ | Cut at ACTION_OPEN_DOCUMENT_TREE |
| X share full thread | Not recoverable from this window (copy-paste only) |

Share links used while stitching (X app cannot export except copy):

- https://x.com/i/grok/share/581ff3e21fac4c8e8d552291560acdac
- https://x.com/i/grok/share/c0382cb686af4e9595715780fc01b555

This file is the public-safe stitch of everything recovered. No API keys. Do not treat later phases as captured.

---

## Product sentence

The keyboard app is the voice pipe into Train-My-Dragon-AI-2.0.
Grok is replaceable. The owned transcript file is not.

---

## Part A - Session Brief

# Session Brief - Voice Keyboard for Dragon
**Created:** 2026-08-31
**Owner:** tripLr
**Purpose:** Durable summary of the design conversation so any AI instance (Grok, Claude, ChatGPT) or human can continue the work without the original chat.

Your AI is replaceable. Your knowledge system is not.
This keyboard is the voice pipe into Train-My-Dragon-AI-2.0.

## 1. How this conversation started

The thread did not begin as a keyboard project.

1. User shared an X post (premtechAI, status 2094084225083531768) listing 50 websites Google does not want you to know about.
2. Asked about the quality of those sites.
3. Asked whether Grok has connectors in the X app.
4. Asked what MCP is.
5. Then the real project appeared: a Grok Voice custom keyboard for Android, for handicapped / hands-free use, with input and output saved to a file, later TTY and braille.
6. Scope narrowed: voice-only keyboard using Grok Voice to send and receive into any app, plus plugins that split the text log onto multiple outbound paths.
7. Added: end-of-speech turn detection, noisy environments (trucking headsets, car, pilot headset, throat mic, space suit), a self-learning layer, Bluetooth/wired device logging, last-3-session profiles, phone speaker vs Bluetooth vs Android Auto detection.
8. Asked for similar projects on the internet and a developer plan.
9. Clarified that SYSTEM events include headset on / Bluetooth on (structured app events, not raw logcat).
10. Added development + journal use: official Grok Voice app loses context and cannot write files; user wants an AI-agnostic agent that saves to user files.
11. Pointed at GitHub tripLr/Train-Your-Dragon-AI (older public method), then corrected to tripLr/Train-My-Dragon-AI-2.0 (live 2.0). Drive copy is slightly ahead of GitHub.
12. Locked the product sentence: the keyboard app is the voice to the Dragon project. Need a complete transcript of every turn, saveable as a file, whether the user is talking to Grok or typing Gmail.
13. Asked what JSONL is.
14. Requested this brief + a first-time-builder development plan.

If a new AI only reads this file, it should treat everything after item 5 as the live project and treat Dragon 2.0 as the knowledge system the keyboard serves.

## 2. Product in one paragraph

Build an Android app that is a hands-free voice IME + accessibility injector + session logger. The user speaks (headset, PTT, or VAD). Speech becomes text. Text can be injected into any app (Gmail, Messages, notes). Every turn is appended to a file the user owns (sessions.jsonl). Optional commands promote lines into journal.md or named notes under Dragon Write Protection. Grok Voice is the first mouth; the file layer and inject layer must work if the model is swapped. Official Grok Voice is insufficient because the session is ephemeral and cannot write the user hoard.

## 3. Who it is for

- tripLr: commercial trucking, voice journaling, Dragon architecture work, GitHub + Google Drive living system.
- People who cannot use their hands (accessibility first).
- Hands-free environments: truck cab, car / Android Auto, noisy headset, later contact/throat mics.
- Developers who want a voice session that does not forget and can dump notes to disk.

## 4. Problems the official apps do not solve

Grok Android Voice talks to Grok but loses context when the socket dies, cannot write user files, and is not a keyboard.
Gboard / Samsung / SwiftKey dictate into a field with no complete owned transcript.
FUTO / Sayboard / Outspoke are private STT IMEs but still words-in-the-box, not a durable IN/OUT/SYSTEM log.
GroqBoard / VoxPen / rustemar voice-keyboard are fast Whisper IMEs without headset-adaptive VAD or Dragon objects.
Google Voice Access taps buttons by voice; it is not a transcript hoard.
Talon Voice is desktop only.
xAI Voice Android sample is a Grok realtime WebSocket demo, not IME + files + profiles.

The gap: Grok (or any) voice + inject into any app + complete saveable transcript + per-device listening profiles + Dragon consent rules.

## 5. Decisions already made

### 5.1 Shape of the app
Voice-only first, not a full QWERTY clone.
Invisible / minimal IME plus AccessibilityService so text can enter apps that do not accept a custom keyboard well.
Foreground service while a session is live (mic).
Modes: Off / PTT / Listening.
PTT is the default in noisy or safety-critical places (truck, car speaker, Android Auto).

### 5.2 Transcript bus
Every event is a TextEvent:
- IN: user speech (raw transcript). Never overwrite this.
- OUT: Grok speech or text inserted into an app.
- SYSTEM: device and session facts the app already understands.

SYSTEM includes: headset connected/disconnected, route changed (input+output pair), Android Auto on, speakerphone on, profile loaded, PTT/listening/paused, VAD false-start, VAD cutoff, audio dropout, sink error, journal appended.
SYSTEM does not include raw Android logcat.
Always write SYSTEM to the file. Do not paste Bluetooth status into Gmail or WhatsApp. Optional short spoken status: Trucker headset. Using last settings.

### 5.3 Files the user owns
Storage Access Framework: user picks a folder once (ACTION_OPEN_DOCUMENT_TREE). Persist that tree URI.

Suggested layout:
My-Dragon/ or Documents/GrokHands/
  sessions.jsonl   complete machine transcript (always on)
  journal.md       human diary; only on command + consent
  notes/           save as named notes
  sandbox/         ephemeral drafts before durable writes

App-private storage is only a crash backup. User files are first.

### 5.4 JSONL
JSON Lines: one JSON object per line, append-only.
Example fields: at, dir (IN/OUT/SYSTEM), text, app, device, dest, event, package.
Why JSONL: crash-safe append, grep-able, load only the tail into a new Grok session, Drive/Syncthing friendly.
Human journal is a second sink (markdown).

### 5.5 Voice backends (AI-agnostic)
Interface idea: VoiceBackend with Grok Realtime first, later OpenAI Realtime or local STT+LLM.
Tools stay in the app: type_text, append_journal, write_note, read_tail, list_notes.
Do not embed a long-lived xAI API key in the APK. Use ephemeral tokens from a tiny backend, or a key stored only on-device in settings for personal testing.

### 5.6 End of turn
Grok Realtime server_vad with tunable threshold, silence_duration_ms (start long: 1000-1500 ms), prefix_padding_ms.
PTT can skip VAD entirely: button down = listen, button up = end turn.

### 5.7 Device routing and last-3 profiles
Detect with AudioManager / AudioDeviceCallback:
- Bluetooth SCO/HFP vs A2DP
- Wired / USB headset
- Built-in mic + phone speaker
- Android Auto (UiModeManager car mode)
Profile key = (inputId, outputId).
On connect, load median of last 3 sessions for that key.
After each turn, count false starts, cutoffs, dropouts. Nudge one knob per about 10 turns. Cap ranges. Voice command: reset listening.
Open-cabin rule: phone mic + loudspeaker or Android Auto -> PTT or high threshold. Never always-on into a speaker that the mic can hear.

### 5.8 Plugins / sinks
Sink interface: wants(event), emit(event).
v1 sinks: File (required), Field inject.
Later: Journal, Http/webhook, Braille display, RTT/TTY.
Router can split one turn onto many sinks.

### 5.9 Dragon 2.0 rules the keyboard must obey
Public method: https://github.com/tripLr/Train-My-Dragon-AI-2.0
Older method repo: https://github.com/tripLr/Train-Your-Dragon-AI
Living data: Google Drive My-Dragon / (ahead of GitHub).
Creed: Agency First, External Continuity, Challenge to Improve, Trust, Versioned Knowledge.
Write Protection: sandbox -> review + exact destination -> explicit permission -> write -> verify.
Do not let voice silently rewrite README.md or Shard.md.
Boot for a voice session (short): README Dragon Stack, Shard live rules, newest ORB tail, last N lines of sessions.jsonl / journal.
Voice commands: Load dragon; Journal that; Save as ...; Type that; Don't write.
File headers when promoting to a durable Object should include Source = voice.
Origin: Dragon began with voice journaling during commercial trucking.

### 5.10 Accessibility and safety
AccessibilityService used to inject/read the focused field, not to scrape the whole phone.
Coexist with TalkBack and Voice Access.
Driving: PTT, no surprising auto-send, no always-on open speaker.
Aviation / space / underwater radios are headsets into this app, not this app becoming those radios.

## 6. Similar projects named in the thread
Voice IMEs: Sayboard (Vosk), FUTO Keyboard / FUTO Voice Input, Outspoke (Parakeet + Silero VAD), VoxPen, rustemar/voice-keyboard, GroqBoard, GroqAndroid, Phone Whisper, KoIME, Hashtype/hush-type.
Agents / a11y control: Google Voice Access, Sanna, CellClaw, VoiceDroid, Gotcha, DeVA, Hark, Zafiro.
Grok samples:
- https://github.com/xai-org/xai-cookbook/tree/main/Android/VoiceApiAndroidExample
- https://github.com/rmh78/grok-voice-api-android-showcase
Desktop reference: Talon Voice (no Android).

## 7. Tooling the owner already has
GitHub, xAI / Grok Voice, Claude for Kotlin scaffolding, ChatGPT as extra explainer.
Never paste xAI API keys into chats.
Keyboard tools are a small local MCP-like surface, not a full desktop MCP host in v1.

## 8. What was explicitly deferred
Full screen-tapping agent.
On-device Whisper plus Grok Voice in v1.
Play Store until accessibility purpose is documented.
Certified aviation / EVA / hydrophone stacks.
Auto-updating graph Edges on Dragon system Objects.
Encrypt-at-rest (v1 = user Documents/Drive folder).

## 9. Success tests agreed in spirit
Truck headset + PTT: lines appear in sessions.jsonl.
Type that lands in Messages or Gmail.
Unplug headset / plug speaker: profile changes; open-cabin does not always-on listen.
Save to journal asks or uses a locked destination and appends markdown.
Kill the app, reopen, load tail of JSONL; Grok knows the last turns.
A new AI given this brief + Dragon README can continue without the original thread.

## Part B - Development Plan (as captured)

Working name: Dragon Voice / GrokHands
Date: 2026-08-31

Four jobs: Listen, Talk to a model (xAI Grok Voice first), Type into the focused app, Remember by appending sessions.jsonl.

Ignore keyboard-theme tutorials. Need mic + WebSocket + log + inject.

### Setup
Accounts: GitHub, xAI console key for personal test only, Google Drive.
Software: Git, Android Studio, real phone with USB debugging.
Example app repo later: tripLr/dragon-voice-keyboard
gitignore: local.properties, apk, .idea, build
First code: run official xAI Voice Android sample before writing an IME.

### Architecture to grow into
app/voice, route, adapt, bus, inject, files, dragon (read-only boot tail in v1), ui
Data flow: Mic -> Grok Voice -> IN/OUT transcripts to Router to JSONL; assistant audio to headset; type_text to IME or Accessibility; headset events to SYSTEM + profile load; Journal that to sandbox/journal with consent.

### Phased build captured
Phase 0: paper and permissions (RECORD_AUDIO, foreground mic service, notifications, BLUETOOTH_CONNECT, Accessibility focused-field only, SAF folder grant).
Phase 1: voice loop, about 1 week. Foreground service, Off/PTT/Listening, server VAD silence 1000-1500 ms. Pass: one minute conversation on trucker headset.
Phase 2: JSONL log + SAF folder, 3-5 days. Goal: every IN/OUT/SYSTEM line in a user-picked file. First run: ACTION_OPEN_DOCUMENT_TREE.

Remainder of Phase 2 and later phases were not in the recovered paste. Do not invent them here.

## Capture notes
Stitched 2026-08-30 from X Grok copy-paste blocks.
Brief decisions 5.1-5.10 are the binding product rules.
Voice commands: Load dragon / Journal that / Save as ... / Type that / Don't write.
First code to run is the official xAI Voice Android sample, not a custom IME.

End of 2026-08-30-2114-my-dragon-voice-project
