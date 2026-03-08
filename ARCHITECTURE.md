# LUMIO — Technical Architecture

> This document is for developers who want to contribute code. It explains how LUMIO is structured, why it's built the way it is, and how the pieces connect. Read this before writing any code.

---

## The Core Constraint That Shapes Everything

LUMIO is designed for users on low-end Android devices (2GB RAM, older processors) with intermittent or no internet access. Every architectural decision flows from this constraint.

- **Offline-first** — the app must work completely without internet. Network is a bonus, not a requirement.
- **Low memory** — no heavy libraries, no keeping large data trees in RAM.
- **Low storage** — content is downloaded in grade-sized chunks (~60–90MB each), not all at once.
- **Low-resolution screens** — UI must be sharp and readable on 720p and below.

If a technical decision makes the app heavier, slower, or more network-dependent, it needs a strong justification.

---

## Tech Stack

| Layer | Technology | Why |
|-------|-----------|-----|
| Mobile framework | Flutter (Dart) | Single codebase for Android + iOS. Excellent performance on low-end devices. Strong offline support. |
| State management | Provider + Riverpod | Predictable, testable, minimal boilerplate. |
| Local database | Hive (NoSQL) | Fast, lightweight, works fully offline. No SQL overhead for simple key-value and object storage. |
| Remote database | Firebase Firestore | Sync when connected. Offline persistence built in. |
| Authentication | Firebase Auth (anonymous) | No email required. Device ID as identity. Optional PIN added locally. |
| Animations | Lottie (JSON) + Rive | Lottie for one-shot celebrations. Rive for interactive stateful character animations. |
| Certificates | Blockcerts + IPFS | Blockchain-verified, tamper-proof. Not cryptocurrency — no financial transactions. |
| Audio | Flutter sound (just_audio) | Lightweight audio playback for lesson narration and feedback sounds. |
| Offline content | Custom download manager | Grade content packages downloaded as compressed bundles. Extracted locally. |

---

## Repository Structure

```
lumio/
│
├── lib/                          # All Dart application code
│   │
│   ├── main.dart                 # App entry point. Theme, routing, providers initialised here.
│   │
│   ├── core/                     # Shared utilities used across the whole app
│   │   ├── constants/            # Colours, text styles, spacing, route names
│   │   ├── theme/                # Light and dark theme definitions
│   │   ├── utils/                # Formatters, validators, helper functions
│   │   └── extensions/           # Dart extensions on common types
│   │
│   ├── models/                   # Pure data classes — no logic, no Flutter imports
│   │   ├── student.dart          # Student profile, mode, progress snapshot
│   │   ├── lesson.dart           # Lesson content, type, completion state
│   │   ├── question.dart         # Question types, answer options, correct answer
│   │   ├── grade.dart            # Grade metadata, units, download state
│   │   ├── pathway.dart          # Pathway data, levels, career directions
│   │   ├── certificate.dart      # Certificate metadata, blockchain hash, QR data
│   │   └── achievement.dart      # Badge, streak, milestone data
│   │
│   ├── services/                 # Business logic — no UI, no Flutter widgets
│   │   ├── auth_service.dart     # Anonymous auth, device ID, PIN management
│   │   ├── progress_service.dart # Tracking completion, mastery, XP
│   │   ├── download_service.dart # Grade content download, extraction, management
│   │   ├── sync_service.dart     # Offline queue → Firestore sync when connected
│   │   ├── certificate_service.dart  # Blockcerts generation, IPFS storage, QR
│   │   ├── assessment_service.dart   # Placement logic, mastery calculation, retry rules
│   │   └── audio_service.dart    # Lesson audio, feedback sounds, background music
│   │
│   ├── providers/                # Riverpod providers — bridge between services and UI
│   │   ├── student_provider.dart
│   │   ├── progress_provider.dart
│   │   ├── lesson_provider.dart
│   │   └── mode_provider.dart    # Current learner mode (ADHD / Dyslexia / Low Literacy / Standard)
│   │
│   ├── screens/                  # One file per major screen
│   │   ├── onboarding/
│   │   │   ├── welcome_screen.dart
│   │   │   ├── mode_selection_screen.dart    # 8-question visual mode picker
│   │   │   └── placement_screen.dart         # Stage 0 adaptive assessment
│   │   ├── home/
│   │   │   └── home_screen.dart
│   │   ├── map/
│   │   │   └── learning_map_screen.dart      # Full curriculum progress map
│   │   ├── lesson/
│   │   │   ├── lesson_screen.dart            # Lesson content wrapper
│   │   │   ├── question_screen.dart          # Assessment question wrapper
│   │   │   └── simulation_screen.dart        # Interactive simulation wrapper
│   │   ├── pathway/
│   │   │   └── pathway_selection_screen.dart # Choice Point 1
│   │   ├── career/
│   │   │   └── career_direction_screen.dart  # Choice Point 2
│   │   ├── certificates/
│   │   │   └── certificate_screen.dart
│   │   ├── portfolio/
│   │   │   └── portfolio_screen.dart
│   │   └── settings/
│   │       └── settings_screen.dart
│   │
│   └── widgets/                  # Reusable UI components
│       ├── lesson/               # Content blocks — text, image, audio, video
│       ├── questions/            # Multiple choice, tap-to-match, drag-drop, etc.
│       ├── characters/           # LUMI and other character wrappers (Rive)
│       ├── celebrations/         # Lottie celebration overlays
│       ├── map/                  # Map nodes, paths, progress indicators
│       └── common/               # Buttons, cards, modals, badges
│
├── assets/
│   ├── animations/
│   │   ├── lottie/               # .json files — celebrations, feedback
│   │   └── rive/                 # .riv files — LUMI and character rigs
│   ├── images/
│   │   ├── illustrations/        # Lesson illustrations, organised by grade
│   │   ├── icons/                # App icons and UI icons
│   │   └── backgrounds/          # Map backgrounds, screen backgrounds
│   └── audio/
│       ├── feedback/             # Correct, not-yet, level-complete sounds
│       └── music/                # Ambient lesson background music
│
├── curriculum/                   # Lesson content — not compiled into the app
│   ├── grade_1/                  # One folder per grade
│   │   ├── unit_1_1/
│   │   │   ├── lesson_1.json     # Lesson content in structured JSON
│   │   │   ├── lesson_2.json
│   │   │   └── assessment.json   # Questions for this unit
│   │   └── ...
│   └── pathways/
│       ├── technical/
│       ├── business/
│       └── ...
│
├── translations/                 # Localisation files
│   ├── en.json                   # English (base)
│   ├── bn.json                   # Bengali
│   └── [language_code].json      # Added by community contributors
│
├── test/                         # Tests mirror the lib/ structure
│   ├── models/
│   ├── services/
│   └── widgets/
│
├── .github/                      # GitHub-specific files
│   ├── ISSUE_TEMPLATE/
│   └── PULL_REQUEST_TEMPLATE.md
│
├── ARCHITECTURE.md               # This file
├── CONTRIBUTING.md
├── CURRICULUM.md
├── DESIGN_GUIDE.md
├── README.md
├── SECURITY.md
├── SETUP.md
└── pubspec.yaml
```

---

## How Offline Works

This is the most important system in the app. Get familiar with it.

**Content is not bundled in the app binary.** Grade content (lessons, questions, simulations, audio, illustrations) is stored on a CDN and downloaded on demand. This keeps the app install small (~30MB) and lets content be updated without pushing a new app version.

**Download flow:**
```
Student selects a grade to download
  → Download service fetches a manifest (list of files + checksums)
  → Files downloaded in parallel, verified against checksums
  → Extracted into the local Hive database
  → Grade marked as available offline
  → All future access reads from local Hive — zero network calls
```

**Progress is written locally first:**
```
Student completes a lesson
  → Progress written to Hive immediately (synchronous)
  → Added to sync queue (a local list of pending writes)
  → UI updates instantly from local data
  → Background sync service watches for network
  → When connected: flush sync queue to Firestore
  → Firestore confirms write → remove from sync queue
```

**Conflict resolution:** Local data always wins for progress. If the same student logs in on two devices and there's a conflict, we take the higher progress state — never roll a student back.

---

## Learner Modes — How They Work in Code

Four modes. Selected during onboarding. Stored in the student model. Applied via the `mode_provider`.

```dart
enum LearnerMode {
  standard,
  adhd,
  dyslexia,
  lowLiteracy,
}
```

The mode provider is consumed by:
- `lesson_screen.dart` — controls session length and break timing
- `question_screen.dart` — controls reward frequency
- `core/theme/` — controls font, spacing, background colour
- All widgets that contain text — controls whether text or icon leads

**ADHD Mode specifics:**
- Sessions auto-pause at 3 minutes with a break prompt
- Reward animation fires every 2 questions (not just at lesson end)
- Maximum 3 meaningful elements visible on screen at once
- Progress displayed as character movement, not percentages

**Dyslexia Mode specifics:**
- OpenDyslexic font loaded via custom font asset
- Line height forced to 1.8× (vs 1.5× standard)
- Background colour forced to Cream (#FFF8F0) regardless of dark/light setting
- Audio highlight follows word-by-word during text reading (requires audio sync metadata in lesson JSON)

**Low Literacy Mode specifics:**
- Navigation uses icons only — text labels hidden
- All instructions delivered via audio before interaction
- Interaction pattern: audio plays on tap before answer is expected

The mode can be changed at any time from settings. Changing mode does not affect progress or certificates.

---

## Assessment Logic

LUMIO's assessment is mastery-based, not time-based. Here's the logic:

**Placement assessment (Stage 0):**
```
5 rounds of questions, increasing difficulty
Each round: 3 questions
Threshold: 2/3 correct → advance to next round
Below threshold → placement found

Result: student placed at the start of the appropriate grade
No score shown to student. No label. Just a starting point.
```

**In-grade assessment:**
```
End of each unit: assessment questions
Threshold: 70% correct to advance
Below 70%: relevant lesson content replayed
Student can retry after review — unlimited retakes
No time limit. No penalty for retaking.

Feedback language:
  Correct:  "Yes! That's it." / celebration animation
  Wrong:    "Not quite — let's look at that again." / gentle animation
  Never:    "Wrong" / "Incorrect" / "Failed" / percentage scores shown mid-assessment
```

**Mastery is stored as:**
```dart
class UnitProgress {
  final String unitId;
  final int attemptsCount;
  final double highestScore;    // 0.0 to 1.0
  final bool mastered;          // true when highestScore >= 0.7
  final DateTime? masteredAt;
}
```

---

## Certificate Generation

Certificates use Blockcerts — an open standard for blockchain-verified credentials. This is not cryptocurrency. No financial transactions. No wallet required.

**Flow:**
```
Student achieves mastery of a grade or pathway level
  → certificate_service generates a Blockcerts JSON document
  → Document contains: student pseudonym, grade/level, date, mastery evidence
  → Document hashed and anchored to a public blockchain (we use Ethereum mainnet)
  → Hash + certificate JSON stored on IPFS (permanent, decentralised)
  → IPFS content ID stored in Firestore against student record
  → QR code generated pointing to the IPFS document
  → Certificate shown in app with QR for verification
```

**Privacy:** Certificates use a student pseudonym (not their real name, which LUMIO doesn't collect). The student controls whether to share the certificate and QR with anyone.

---

## Content Format — Lesson JSON

Lesson content is structured JSON, not hardcoded in Flutter. This lets curriculum contributors add and edit content without touching Dart code.

```json
{
  "lesson_id": "g1_u1_l1",
  "grade": 1,
  "unit": 1,
  "lesson": 1,
  "title": {
    "en": "Sounds and Letters",
    "bn": "শব্দ এবং অক্ষর"
  },
  "mode_variants": {
    "low_literacy": true,
    "adhd_chunk_after": 2
  },
  "blocks": [
    {
      "type": "text",
      "content": { "en": "Every word is made of sounds.", "bn": "..." },
      "audio": "audio/en/g1_u1_l1_block1.mp3"
    },
    {
      "type": "illustration",
      "asset": "images/illustrations/grade1/sounds_intro.png",
      "alt": { "en": "A child listening to sounds in nature", "bn": "..." }
    },
    {
      "type": "interaction",
      "interaction_type": "tap_to_reveal",
      "prompt": { "en": "Tap each picture to hear its sound", "bn": "..." },
      "items": [...]
    }
  ]
}
```

**Content types currently planned:**
- `text` — paragraph content with optional audio
- `illustration` — static image with alt text
- `audio` — audio-only block
- `interaction` — tap-to-match, drag-drop, tap-to-reveal, ordering
- `simulation` — links to a specific simulation widget by ID
- `journal_prompt` — private journal offer (no data collected)

---

## Translation System

All user-facing strings live in translation files, never hardcoded in Dart.

```
translations/
├── en.json    ← base file, must be complete
├── bn.json    ← Bengali
└── ...
```

All translations use Flutter's built-in `intl` package via `flutter_localizations`. The `en.json` file is the source of truth. Any key missing from a translation file falls back to English — the app never shows an empty string.

**For translators:** You don't need to touch Dart. Edit the JSON file for your language. See [CONTRIBUTING.md](CONTRIBUTING.md) for the full process.

---

## State Management Pattern

We use **Riverpod** for global state and **local StatefulWidget** state for isolated UI interactions.

**Rule of thumb:**
- Data that multiple screens need → Riverpod provider
- Data that only one widget needs → `StatefulWidget` local state
- Never use `setState` for data that has to survive navigation

**Key providers:**
```dart
// Student identity and mode
final studentProvider = StateNotifierProvider<StudentNotifier, Student>

// Current lesson progress
final progressProvider = StateNotifierProvider<ProgressNotifier, ProgressState>

// Active learner mode
final modeProvider = StateProvider<LearnerMode>

// Download state per grade
final downloadProvider = StateNotifierProvider<DownloadNotifier, Map<String, DownloadState>>

// Network status
final connectivityProvider = StreamProvider<ConnectivityStatus>
```

---

## Naming Conventions

Consistency matters when multiple contributors are writing code.

**Files:** `snake_case.dart` — always

**Classes:** `PascalCase` — always

**Variables and functions:** `camelCase` — always

**Constants:** `kConstantName` — prefix with `k`

**Providers:** `entityNameProvider` — suffix with `Provider`

**Assets:** `grade1_unit2_lesson3_block1.png` — descriptive, no spaces

**Translation keys:** `grade1.unit1.lesson1.title` — dot notation, hierarchical

---

## Performance Rules

These apply to every pull request touching UI or data:

1. **No synchronous reads from Firestore in the UI layer.** All Firestore reads go through the sync service. UI reads from Hive only.

2. **Images must be compressed.** Illustrations max 200KB. Icons max 10KB. Use WebP format for illustrations.

3. **Lottie files max 50KB.** If your animation JSON is larger, simplify it.

4. **No `setState` inside `build()`.** Ever.

5. **Lazy load lesson content.** Don't load the entire grade into memory. Load one unit at a time.

6. **Test on a low-end device before submitting.** If you only test on a high-spec emulator, you will miss performance problems that real users will hit. The [Android Emulator supports low-RAM configurations](https://developer.android.com/studio/run/managing-avds).

---

## Testing

Every service should have unit tests. Every widget that contains meaningful logic should have widget tests.

```
test/
├── services/
│   ├── assessment_service_test.dart   ← mastery logic especially
│   ├── download_service_test.dart
│   └── sync_service_test.dart
├── models/
│   └── progress_test.dart
└── widgets/
    └── question_widget_test.dart
```

Run tests: `flutter test`

Run with coverage: `flutter test --coverage`

**Before submitting a PR:** All existing tests must pass. New logic needs new tests.

---

## What We Need From Developers Right Now

In rough priority order:

1. **Offline download manager** — the content download, extraction, and local storage system
2. **Assessment engine** — placement logic and mastery-based progression
3. **Learner mode system** — the four modes and how they affect every screen
4. **Lesson content renderer** — parsing lesson JSON and rendering the correct block type
5. **Learning map screen** — the visual curriculum progress map
6. **Certificate generation** — Blockcerts + IPFS integration
7. **Sync service** — offline queue to Firestore
8. **LUMI character integration** — Rive rig wired to app events

If you want to pick something up, open an issue or comment on an existing one. Coordinate before building — we don't want two people building the same thing differently.

---

## Questions

Open a GitHub Issue tagged `architecture-question` and describe what you're trying to understand. Someone will answer in the issue so the explanation is findable by future contributors.

---

*LUMIO Technical Architecture v1.0*
*github.com/henaswarnali-tech/Lumio*
