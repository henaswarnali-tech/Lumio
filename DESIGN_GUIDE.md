<!--
LUMIO Design Guide
Creative Commons Attribution-NonCommercial-ShareAlike 4.0 (CC BY-NC-SA 4.0)
Original publication: github.com/henaswarnali-tech/Lumio — March 2026
-->

# LUMIO Design Guide
### For Designers, Animators, and UI/UX Contributors

---

## Hello, Designer

If you're reading this, you're thinking about contributing creative work to LUMIO — illustrations, animations, UI components, icons, or UX thinking. This guide is everything you need to make sure your work fits into the project and actually ships.

A quick word before the specs: design is one of the places where LUMIO can be exceptional or mediocre, and the difference matters enormously. The children and adults using this app have often been failed by systems that treated them as an afterthought. They have almost certainly never had a piece of software designed with them specifically in mind. Every illustration that reflects their world rather than a Western default, every animation that makes learning feel like play rather than punishment, every UI decision that works on a low-end phone with a cracked screen — those choices accumulate into something that either feels like it was made for this person, or something that doesn't.

That's what we're going for. This guide will help you get there.

---

## What We're Building — Design Context

LUMIO is a mobile learning app, primarily Android, designed for:
- Low-end smartphones (2GB RAM, older processors)
- Intermittent or no internet connection
- Users with limited digital literacy
- Neurodivergent users (ADHD, dyslexia, low literacy modes)
- Children from around age 7 through to adults

Every design decision should pass one question: **does this work for someone using a three-year-old Android phone, possibly with a cracked screen, possibly with limited reading ability, who has never used an app quite like this before?**

If yes — it works for everyone.

---

## The Brand in One Sentence

LUMIO feels like a wise, warm older sibling — never a teacher, never a charity, never a corporation.

That feeling should come through in every visual, every animation, every layout choice. Warm but not childish. Simple but not dumbed down. Joyful because learning genuinely is.

---

## Brand Name

**LUMIO** — derived from *lumen*, Latin for light. Light for every learner.

**Pronunciation:** LOO-mee-oh

**In your designs:**
- Headlines and logos: **LUMIO** (all caps)
- Body text and descriptions: Lumio (title case)
- Never: lumio, LUMIO App, The Lumio App

---

## Colour System

These colours are the core of every screen, illustration, and animation in the project.

### Primary Colours

**Sunrise Orange — the heart of LUMIO**
```
Hex:  #FF6B35
RGB:  255, 107, 53
```
This is the first colour anyone associates with LUMIO. Use it for primary buttons, the logo accent, key highlights, and anywhere you want to draw the eye. It reads as warm, energetic, and hopeful — a sunrise, not a warning sign.

**Sky Teal — the second voice**
```
Hex:  #4ECDC4
RGB:  78, 205, 196
```
Secondary elements, progress indicators, success states, and anything that needs to feel calm and clear. Works beautifully alongside Sunrise Orange — they have enough contrast to be interesting and enough warmth to feel cohesive.

**Night — the dark base**
```
Hex:  #1A1A2E
RGB:  26, 26, 46
```
Dark mode backgrounds, text on light surfaces. This is not black — it has a blue warmth to it that feels like a night sky, not a void. Dark mode is the default in the app because many users have AMOLED screens and battery matters when you're learning on a phone that might only charge once a day.

**Cream — the light base**
```
Hex:  #FFF8F0
RGB:  255, 248, 240
```
Light mode backgrounds and cards. Warmer than white — pure white creates visual stress for many readers, especially those with dyslexia. This is the lightest surface in the app.

**Two rules that matter:**
- Never use `#000000` (pure black) — use Night instead
- Never use `#FFFFFF` (pure white) — use Cream instead

### Supporting Colours

```
Success:         #2ECC71  — correct answers, completed lessons, streaks
Gentle Warning:  #F39C12  — "almost there" states, reminders (never for wrong answers)
Achievement:     #9B59B6  — special achievements, certificates
```

**Important:** LUMIO never uses red or harsh colours to signal wrong answers. A student getting something wrong is not a failure — it's a step in the process. The visual language should reflect that.

### Pathway Accent Colours

Each learning pathway has its own accent colour that runs through its UI:

| Pathway | Colour | Hex |
|---------|--------|-----|
| 🔧 Technical | Electric Blue | `#3498DB` |
| 💼 Business | Gold | `#F1C40F` |
| 🎨 Creative | Violet | `#9B59B6` |
| 🏥 Health | Soft Red | `#E74C3C` |
| 🌱 Agriculture | Leaf Green | `#27AE60` |
| 👩‍🏫 Education | Warm Orange | `#E67E22` |

### Accessibility

All text must meet **WCAG AA contrast ratio: 4.5:1 minimum.** This is not optional — many LUMIO users have varying visual ability, and low contrast makes the app genuinely harder to use.

Check your colour combinations before finalising. Tools like [Colour Contrast Checker](https://colourcontrast.cc/) make this quick.

---

## Typography

Both fonts are free on Google Fonts. No licensing issues, no costs.

### Nunito — Headlines and Display

**Use for:** Grade completion headlines, screen titles, the logo, anything big and prominent
**Weights:** 800 (ExtraBold) for main headlines · 700 (Bold) for sub-headlines

Nunito's rounded letterforms are the reason it's here. It reads as friendly and approachable without being juvenile — important when your users range from a seven-year-old in their first day of learning to a thirty-year-old adult who never finished school.

### Inter — Everything Else

**Use for:** All lesson content, UI labels, body text, captions
**Weights:** 400 (Regular) for body · 600 (SemiBold) for labels and captions

Inter was designed specifically for screen readability at small sizes in multiple languages. It is exceptionally clear on low-resolution screens.

### Type Scale (Flutter `sp` units)

```
Display   32sp   Nunito 800    Grade completion, big moments
H1        24sp   Nunito 700    Screen titles
H2        20sp   Nunito 700    Section headers
H3        18sp   Inter 600     Card titles
Body      16sp   Inter 400     All lesson text
Caption   14sp   Inter 400     Secondary information
Small     12sp   Inter 400     Labels, badges
```

**Minimum body text: 16sp.** Below this, the app becomes difficult to read for users with low vision or learning on a small or cracked screen.

**Line height:** 1.5× font size for body text.

**Text alignment:** Always left-aligned. Justified text creates uneven word spacing that makes reading significantly harder, particularly for dyslexic readers.

**Characters per line:** Aim for 60 maximum. Longer lines make it harder to track back to the start of the next line.

---

## The Mascot — LUMI

LUMI is LUMIO's mascot. A small glowing creature somewhere between a firefly, a sun, and an owl. Wise but playful. Genderless. No specific ethnicity. Universally lovable.

LUMI appears on the loading screen, when celebrating achievements, when encouraging a student after a wrong answer, as the narrator in story-based lessons, and on the app icon.

**LUMI's personality:** Curious, warm, never sarcastic, always patient. LUMI celebrates effort, not just success. If a student gets something wrong three times in a row, LUMI responds with the same patience as the first time — because that's what this student needs.

**Expressions to design:**
- Happy / celebrating — wide eyes, arms up, glow bright
- Thinking — slight chin tilt, one eye a little squinted
- Encouraging — gentle smile, soft thumbs up or forward lean
- Excited — bouncing, small stars or sparkles around it
- Calm / idle — slow gentle glow pulse, natural breathing movement

**What LUMI is not:** A robot, a generic mascot, anything that reads as Western or ethnically specific. LUMI should feel like it belongs to every learner who meets it.

---

## Illustration Style

This is where your skills as an artist matter most. The LUMIO illustration style is **warm, diverse, flat-style characters with soft gradient fills** — globally recognisable without defaulting to any one culture.

### Characters

- **Diverse representation is the baseline, not a bonus.** Various skin tones, facial features, hair types, body types, and clothing. The app is designed for learners across South and Southeast Asia, sub-Saharan Africa, the Middle East, and beyond. Every student who opens LUMIO should see someone who could be from their world.
- **Thick outlines** (3–4px) so characters read clearly on small, low-resolution screens.
- **Expressive faces** — large eyes, clear and readable emotions. Students need to understand what characters are feeling without reading text.
- **Simple backgrounds** — characters are always the focus. Backgrounds set context without competing.
- **Avoid the Western default** in objects and environments. Show rice, not hamburgers. Rivers and wells, not swimming pools. Markets, not shopping malls. The world most LUMIO students live in.

### Fills and Colour

- Soft gradients over flat colour — feels warmer and more alive on screen.
- Pathway accent colours can inform illustration palettes in pathway-specific content.

### What to Avoid

- Clipart style
- Heavy Western cartoon influence (think characters that look like they belong in a Hollywood animated film — that's not our audience's world)
- Stereotypical or tokenistic representation — a student in a rural village wearing traditional dress is fine; a student in a rural village wearing traditional dress to represent an entire continent is not
- Overly complex illustrations — they slow down the app on low-end devices and distract from the lesson

---

## Animation Guidelines

LUMIO uses two tools for animation. They have different purposes.

### Lottie — Celebrations and Decorative Animation

Lottie plays pre-rendered animations exported from After Effects or similar. Use it for:
- Confetti burst on grade completion
- Star pulse on correct answer
- Coin or XP reward shower
- Ambient background movement (very subtle)

**File size:** Under 50KB per animation. This is strict — many users download content once and learn offline. Every kilobyte matters.

**Duration:** 1–3 seconds for celebrations. Under 1 second for feedback (correct/incorrect).

**Looping:** Only for ambient and idle animations. Celebration animations play once — a celebration that loops is no longer a celebration, it's a distraction.

### Rive — Interactive Character Animation

Rive handles character states and interactive animations driven by the app's logic. LUMI and other characters need Rive rigs.

**States every character needs:**
- Idle (default) — gentle, alive, breathing or slow glow pulse
- Correct — bright, celebratory, clear joy
- Incorrect / not yet — soft, encouraging, not defeated
- Thinking — engaged, curious
- Celebrating — big energy for grade completions and achievements

**Transitions:** 0.2s blend between states. Abrupt cuts feel wrong.

**Complexity:** Keep rigs simple. A complex rig that takes 3 seconds to load on a low-end phone loses the moment. LUMI should feel responsive — appearing immediately when the student needs encouragement.

### Animation Principles (The Relevant Ones)

You probably know these. A reminder of the ones that matter most for LUMIO:

**Ease in/ease out** — nothing moves at constant speed in the real world. Nothing should in LUMIO either.

**Squash and stretch** — makes things feel physical and alive rather than digital.

**Anticipation** — a small wind-up before a big action makes the action feel satisfying.

**Timing signals emotion** — celebrations should feel fast and energetic. Thinking should feel slow and calm. The same animation at different speeds communicates completely different feelings.

---

## UI Components

### Cards

- Background: Night for dark mode · Cream for light mode
- Border radius: **16px** — rounded and friendly
- Shadow: `0px 4px 20px rgba(0,0,0,0.15)` — present but soft
- Padding: 16px minimum on all sides

### Buttons

- **Primary:** Sunrise Orange background · white Nunito text · 12px border radius · 52px height minimum (touch target accessibility)
- **Secondary:** Transparent · 2px Sunrise Orange border · Sunrise Orange text
- **Destructive / cancel:** Transparent · grey border — never red for cancellation
- **Disabled:** 40% opacity of primary

### Progress Indicators

- Height: 8px
- Rounded ends always
- Fill: gradient from pathway accent colour to a lighter version
- Background: dark grey (dark mode) or light grey (light mode)

### Lesson Cards on the Learning Map

- **Completed:** Full colour, tick icon
- **Current:** Pulsing animation, full colour — the student knows exactly where they are
- **Locked:** Greyscale, lock icon — not sad, just waiting
- **Map path between cards:** Dashed line that curves naturally, feels like a path through a landscape

### Iconography

**Style:** Rounded, outlined — 2px stroke weight, rounded line ends and corners

**Library:** [Lucide Icons](https://lucide.dev/) — open source, rounded, consistent. Use these as the base. If you create custom icons, match this style exactly.

**Grid:** Design all icons on a 24×24 grid.

**Rule:** Every icon must be meaningful without a label. But always include a label anyway — for accessibility and for users with low visual literacy.

One style throughout: don't mix filled and outlined icons.

---

## App Screen Architecture — For Reference

Understanding the overall structure helps you design components that fit into the right context.

**Bottom Navigation (5 tabs):**
1. Home — daily lesson and current streak
2. Map — full curriculum progress map
3. Explore — browse all content
4. Achievements — badges, certificates, XP history
5. Profile — settings, language, downloaded content

**Home Screen:**
- Top: Greeting with student's name, current streak
- Centre: Today's lesson (large, inviting, the main action)
- Below: Continue where you left off
- Bottom: Quick stats — XP this week, lessons completed

---

## Neurodivergent Mode Design Considerations

LUMIO has four learner modes. When designing any component, consider how it will behave in each:

**ADHD Mode** reduces screen elements to a maximum of 3. Any component you design should work in a simplified layout. Avoid layouts that depend on peripheral visual information.

**Dyslexia Mode** switches to OpenDyslexic font, uses the Cream background, and increases letter and line spacing. Design layouts that accommodate these changes without breaking — don't rely on pixel-perfect text fitting.

**Low Literacy Mode** puts icons first. If your design uses text labels, they must be accompanied by icons that communicate the same thing independently.

If you're designing a new component, consider all four modes before calling it done.

---

## Sound — Brief Notes for Designers Working on Interactive Animations

If your animation involves sound triggers, here are the specs:

| Moment | Sound Character | Duration |
|--------|----------------|----------|
| Correct answer | Bright, ascending | 0.3s |
| Not yet / incorrect | Soft, two-tone, never harsh | 0.3s |
| Level complete | Short triumphant fanfare | 1.5s |
| Streak milestone | Extended celebration | varies |
| Button tap | Barely audible soft click | instant |
| Lesson complete | Warm melodic chime | 2s |

All sounds are stored locally — the app works fully offline, and every audio file contributes to the download size of each grade. Keep audio files efficient.

---

## A Few Things LUMIO Doesn't Look Like

**It doesn't look like a charity app.** Sad children, muted colours, hand-outstretched imagery — that framing reduces learners to recipients. LUMIO's learners are capable people with agency. The design should reflect that.

**It doesn't look like a corporate EdTech product.** Blue gradients, stock photography of diverse children at laptops, motivational quote overlays. Those designs communicate "we built this for you" from the outside. LUMIO was built from the inside.

**It doesn't look like a children's toy.** Aggressively bright primaries and cartoonish letterforms infantilise the adults who use LUMIO and fail to respect that this app serves learners from age 7 to 40+. Friendly is not the same as childish.

---

## Getting Started

**To contribute design work:**

1. Read [CONTRIBUTING.md](CONTRIBUTING.md) for the full contribution process
2. Check the open issues for design tasks that need doing
3. If you have an idea that's not an open issue, open one and describe it before investing significant work — we want to coordinate, not duplicate
4. Post work-in-progress in your issue or pull request. Iteration is welcome and expected.
5. Export Lottie files as JSON, Rive files in their native format. Include source files wherever possible so future contributors can build on your work.

**What we really need right now:**
- LUMI mascot design (Rive rig with all expression states)
- Illustration library: diverse characters in grade-level lesson contexts
- Correct / not yet answer feedback animations (Lottie)
- Grade completion celebration (Lottie)
- Icon set expansion (Lucide-style, custom LUMIO-specific icons)
- Pathway card designs for the learning map

**Questions?** Open an issue tagged `design-question`. Someone will respond.

---

## Core Brand Rules — The Non-Negotiables

Some things you can adapt. Some things must stay consistent for LUMIO to be recognisable as LUMIO across every language and every contributor.

These must not change:
- The name: LUMIO
- Primary colours: Sunrise Orange, Sky Teal, Night, Cream
- Fonts: Nunito (headlines) and Inter (body)
- LUMI mascot's core character and genderless identity
- The warm, non-condescending tone

These can be adapted by regional contributors with cultural sensitivity:
- Illustration content — show the learner's world, not a generic global default
- Examples and scenarios in lesson art — localise to what makes sense
- Supporting illustration style details — as long as the core warmth is preserved

---

*LUMIO Design Guide v1.0*
*CC BY-NC-SA 4.0 — adapt freely for non-commercial use, credit LUMIO, share alike*
*github.com/henaswarnali-tech/Lumio*
