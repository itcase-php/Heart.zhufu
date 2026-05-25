# Blessing Generator

An interactive, multilingual blessing/greeting card generator with voice recognition, emotional TTS, canvas particle effects, and recording capabilities. Open `heart.html` directly in a browser — no build system, no dependencies.

## Features

### Voice Recognition Gate
- Speech recognition passphrase gate requiring spoken "爱你一万年" to access the page
- Fuzzy matching algorithm tolerating speech imprecision
- Text input fallback for browsers without SpeechRecognition API
- iOS Safari user gesture handling

### Intro Sequence
- Sequential popup welcome messages with random positioning
- Two-phase intro: initial curiosity prompts and heartfelt messages
- Exit confirmation flow with gentle persuasion

### Blessing Cards
- Tap anywhere to generate random blessing cards
- 5 mood categories: Birthday, Joyful, Comfort, Strength, Fortune
- 5 languages: English, Chinese, Japanese, German, Korean
- 150 unique blessings across all languages and moods
- Cards auto-dismiss after 9 seconds, max 6 active cards

### Text-to-Speech (TTS)
- Emotional speech synthesis with mood-adaptive prosody
- Per-language rate, pitch, volume, and pause configuration
- Female voice preference with smart voice selection scoring
- Sentence segmentation with per-segment pause scheduling
- Natural speech patterns with randomized pitch/rate micro-variations

### Recording (Chinese voice)
- MediaRecorder API with Web Audio WAV fallback
- Record, playback, re-record workflow per card
- 60-second max recording with live timer
- Cross-browser MIME type negotiation (WebM/OGG/MP4/AAC/WAV)

### Visual Effects
- Canvas heart particle system with gravity, rotation, and fade
- DOM sparkle effects with CSS animations on card spawn
- Heart trail following mouse/touch movement
- Canvas fireworks engine with multi-pattern explosions (ring, star, burst, willow)
- Glass-morphism cards with backdrop blur
- Animated starfield background with SVG noise texture

### UI/UX
- Responsive design with fluid typography (clamp)
- Touch-optimized with passive event listeners
- Accessibility: ARIA roles, live regions, screen reader support
- Voice detection badge showing active TTS voice
- Blessing counter tracking total shares

## Technologies

| Technology | Usage |
|---|---|
| HTML5 | Semantic markup, Canvas API, Web Speech API |
| CSS3 | Glass-morphism, animations, custom properties, backdrop-filter |
| Vanilla JavaScript | All logic in a single IIFE, no frameworks |
| Web Speech API | SpeechRecognition (voice gate) + SpeechSynthesis (TTS) |
| MediaRecorder API | Audio recording with getUserMedia |
| Web Audio API | WAV encoding fallback for recording |
| Canvas 2D API | Heart particles and fireworks rendering |
| Google Fonts | Cormorant Garamond (display) + DM Sans (body) |

## Browser Support

| Feature | Chrome | Safari | Firefox | Edge |
|---|---|---|---|---|
| Voice Gate | Full | iOS button | Text fallback | Full |
| TTS | Full | Full | Full | Full |
| Recording | Full | Full | WAV only | Full |
| Canvas Effects | Full | Full | Full | Full |

## Getting Started

1. Clone the repository
2. Open `heart.html` in any modern browser
3. Speak the passphrase "爱你一万年" (or type it in the fallback input)
4. Tap anywhere to receive blessings

## Project Structure

```
Heart.zhufu/
├── heart.html          # Single-file application (~2500 lines)
├── CLAUDE.md           # Development documentation
├── .gitignore
└── README.md
```

## License

Personal project — not licensed for redistribution.
