# LUMIO — Roadmap

This is where the project stands and where it's going. Updated as things change.

If you want to contribute to something on this list, open an issue or comment on an existing one before starting. Coordination saves everyone time.

---

## Current Status

**Phase: Foundation — Documentation and Architecture**
The app itself is not yet built. The curriculum, design system, technical architecture, and contributor infrastructure are being established first — so that when development begins, every contributor is building toward the same thing.

This is intentional. A well-documented foundation built once is faster than a poorly-documented one rebuilt repeatedly as contributors arrive with different assumptions.

---

## Phase 1 — Foundation ✅ In Progress

Getting the project ready for contributors.

- [x] README — project vision and overview
- [x] CURRICULUM.md — complete curriculum framework with research foundations
- [x] CONTRIBUTING.md — how to contribute across all disciplines
- [x] SETUP.md — getting the development environment running
- [x] DESIGN_GUIDE.md — visual identity and design system for contributors
- [x] CHILD_SAFETY_PSYCHOLOGY.md — child safety approach and open invitation to specialists
- [x] ARCHITECTURE.md — technical structure for developer contributors
- [x] ROADMAP.md — this file
- [x] CODE_OF_CONDUCT.md — community standards
- [x] LICENSE — GPL v3 (code) + CC BY-NC-SA 4.0 (curriculum)
- [ ] Issue templates — structured contribution starting points
- [ ] Repository topics and labels — discoverability on GitHub
- [ ] First open issues created — specific, actionable contribution opportunities

---

## Phase 2 — App Skeleton

**Goal:** A Flutter app that opens, runs, and has the correct structure — even if most screens are placeholder.

The foundation every subsequent contributor builds on. Getting this right matters more than getting it fast.

- [ ] Flutter project scaffolded with correct folder structure (see ARCHITECTURE.md)
- [ ] Riverpod state management configured
- [ ] Hive local database configured
- [ ] Firebase project connected (development environment)
- [ ] Four learner modes implemented — theme, font, layout variations
- [ ] Bottom navigation (Home, Map, Explore, Achievements, Profile)
- [ ] Onboarding flow — welcome → mode selection (8 visual questions) → placement
- [ ] Basic routing between screens
- [ ] Translation system configured (English + Bengali)
- [ ] CI pipeline — runs tests on every pull request

**Looking for:** Flutter/Dart developers. See ARCHITECTURE.md for structure detail and open issues for specific tasks.

---

## Phase 3 — Core Learning Engine

**Goal:** A student can take the placement assessment, be placed at a grade level, and complete real lessons with real content from Grade 1.

This is where LUMIO becomes something a real student can use, even in a very limited form.

- [ ] Stage 0 — adaptive placement assessment (5 rounds, adaptive logic)
- [ ] Lesson content renderer — parses lesson JSON, renders text / illustration / audio / interaction blocks
- [ ] Question engine — multiple choice, tap-to-match, drag-drop
- [ ] Mastery assessment logic — 70% threshold, unlimited retakes after review
- [ ] Progress tracking — written to Hive, synced to Firestore when connected
- [ ] Grade 1 content — all 5 units, all lessons, all assessments in JSON format
- [ ] Audio playback — lesson narration, feedback sounds
- [ ] "Not yet" feedback system — gentle, encouraging, non-punitive
- [ ] LUMI character — Rive rig with idle, correct, not-yet, thinking, celebrating states
- [ ] Grade 1 certificate generation — Blockcerts + IPFS

**Looking for:** Flutter developers, curriculum content writers (JSON format), Rive animator for LUMI.

---

## Phase 4 — Offline Architecture

**Goal:** A student can download Grade 1, disconnect entirely from the internet, and complete every lesson, assessment, and simulation with full functionality.

- [ ] Content download manager — manifest, parallel download, checksum verification
- [ ] Local content extraction and Hive storage
- [ ] Offline progress queue — local first, sync when connected
- [ ] Download UI — grade selection, download progress, storage indicator
- [ ] Network state awareness — app behaves correctly whether online or offline
- [ ] Sync conflict resolution
- [ ] Test suite — offline scenarios, sync edge cases

**Looking for:** Flutter developers with experience in offline-first architecture.

---

## Phase 5 — Full Foundation (Grades 1–5)

**Goal:** All five foundation grades fully playable offline, with certificates, the learning map, and the full placement system.

- [ ] Grades 2–5 content (curriculum JSON, illustrations, audio)
- [ ] Learning map screen — visual curriculum progress, locked/current/completed states
- [ ] Simulations — interactive scenarios (The Neighbourhood, The Village Challenge, The Nature Lab, etc.)
- [ ] Full certificate system — one per grade, blockchain verified
- [ ] Portfolio foundation — collecting and storing student work from lessons
- [ ] Private journal — device-only, never synced
- [ ] Choice Point 1 — pathway selection screen at end of Grade 5
- [ ] Language: Bengali translation of all Grade 1–5 content

**Looking for:** Flutter developers, curriculum content writers, illustrators (diverse characters and lesson scenes), Bengali translators.

---

## Phase 6 — Pathways

**Goal:** At least one pathway fully playable end-to-end, with Choice Point 2 and career direction preparation.

We will build one pathway first — most likely Technical — to prove the pathway architecture before scaling to all six.

- [ ] Pathway architecture — levels, career directions, portfolio outputs
- [ ] Technical pathway — all 5 levels, content, assessments, simulations
- [ ] Choice Point 2 — career direction selection screen
- [ ] Pathway-level certificates (blockchain verified)
- [ ] Merged pathway specialisation logic (Technical + Creative = Digital Product Designer)
- [ ] Pathway UI — distinct visual identity per pathway (pathway accent colours)

Then progressively:
- [ ] Business pathway
- [ ] Creative pathway
- [ ] Health pathway (requires expert review of first aid content before deployment)
- [ ] Agriculture pathway
- [ ] Education pathway

---

## Phase 7 — Stage 3 and Graduation

**Goal:** A student can complete the full journey from zero literacy to graduation with a verified transcript and portfolio.

- [ ] Stage 3 professional skill courses — at least 3 per pathway
- [ ] Graduate transcript generation — full record, formatted for employers and universities
- [ ] Graduate portfolio page — permanent, linked to certificates
- [ ] Graduation screen — the moment the journey completes
- [ ] Employment readiness tools — CV builder, cover letter templates

---

## Phase 8 — Educator Accounts and Community Deployment

**Goal:** A teacher, NGO worker, or community facilitator can manage a group of LUMIO students and monitor progress.

- [ ] Educator account system (separate from student accounts)
- [ ] Group dashboard — student progress at a glance
- [ ] Alerts for students who haven't opened the app recently
- [ ] Certificate download and printing for supervised students
- [ ] Simple group progress reports
- [ ] Community deployment infrastructure — custom language, custom community branding

---

## Longer Term — No Fixed Timeline

Things we know we want but haven't scoped in detail yet:

**More languages** — every language added by community contributors opens LUMIO to a new population. We'll build the translation system in Phase 2 so adding languages is as easy as adding a JSON file.

**Simulation depth** — the current roadmap includes basic simulations. Deeper, more interactive simulations — particularly for the Health and Agriculture pathways — need dedicated design and development effort.

**Scholarship module** — guided scholarship discovery and application preparation for students who complete Grade 5+.

**Neurodivergent mode refinement** — the four modes are a starting point. We want to iterate based on real user testing with neurodivergent learners.

**Voice input** — for learners who struggle with text entry, voice-based responses in assessments.

**GitHub Sponsors** — once the app is far enough along to demonstrate what it is and what it does. Not before.

---

## How This Roadmap Works

This isn't a fixed schedule. It's a shared understanding of direction and priority.

Things get added when they're clearly needed. Things get moved when real-world learning changes the priority. Things get marked done when they're actually done — not when they're started.

If you think something is missing, wrong, or should be prioritised differently — open an issue and make the case. This roadmap is a living document and it belongs to the community.

---

*Last updated: March 2026*
*github.com/henaswarnali-tech/Lumio*
