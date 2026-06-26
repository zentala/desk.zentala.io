# CLAUDE.md — Agent Guidance for desk.zentala.io

## What this repo is

This is the **research, vision and website repo** for the **Open Smart Desk** project —
an open-source hardware + software system that helps knowledge workers build
a habit of alternating between sitting and standing at their desk.

**This is NOT a desk product. It is a nudge/motivation system.**
The desk raises manually — the user presses the button themselves.
The system detects posture and sends non-annoying, Duolingo-style notifications.

Read the vision before touching anything: [research/vision/MISSION.md](research/vision/MISSION.md)

---

## Current state of the repo

| What | Where | Status |
|---|---|---|
| Website (landing page) | `index.html` + `style.css` | Live at desk.zentala.io — outdated, needs update |
| Hardware v2 spec | `research/hardware-v2-spec.md` | Done |
| Vision & strategy | `research/vision/` | Done |
| Notification algorithm | `research/algorithm/` | Designed, not coded yet |
| App architecture | `research/architecture/` | Designed, not coded yet |
| Session handoff | `research/SESSION-2026-06-25.md` | Read this to catch up |
| Task list | `TASKS.md` | Read this for next steps |
| User research quotes | `research/user-quotes.xml` | 26 real quotes from forums |

---

## Read these first (priority order)

1. **[TASKS.md](TASKS.md)** — what needs to be done, in order
2. **[research/SESSION-2026-06-25.md](research/SESSION-2026-06-25.md)** — full session handoff, open questions
3. **[research/vision/MISSION.md](research/vision/MISSION.md)** — philosophy, why this exists, who it's for
4. **[research/vision/ROADMAP.md](research/vision/ROADMAP.md)** — Stage 0→5, what gets built when
5. **[research/algorithm/NOTIFICATION-ALGORITHM.md](research/algorithm/NOTIFICATION-ALGORITHM.md)** — state machine, read before touching notification logic

---

## Research & Vision tree

```
research/
├── SESSION-2026-06-25.md        ← session handoff, open questions, next steps
├── user-quotes.xml              ← 26 real user quotes from forums (market validation)
├── hardware-v2-spec.md          ← RP2040-Tiny + VL53L0X spec, BOM, wiring
│
├── vision/
│   ├── MISSION.md               ← philosophy, personas, what we are NOT building
│   ├── ECOSYSTEM.md             ← OEM per-unit model, consortium, flywheel
│   ├── ROADMAP.md               ← Stage 0→5: MVP → Habit Engine → Standard
│   ├── RESEARCH-PLAN.md         ← academic partnership (PW), validation metrics
│   └── LONG-TERM-VISION.md      ← Smart Move, Smart Life, AI health companion
│
├── algorithm/
│   └── NOTIFICATION-ALGORITHM.md  ← state machine (AWAY/SITTING/STANDING/ALERT/SNOOZED)
│
└── architecture/
    ├── REPO-ARCHITECTURE.md     ← monorepo structure, tech stack, build order
    └── FIRMWARE-SPEC.md         ← USB Serial protocol, MicroPython skeleton, I2C wiring
```

---

## Product summary (for context)

**Hardware v2:** RP2040-Tiny (~20 PLN) + VL53L0X laser sensor (~20 PLN) → USB to PC

**Two data sources:**
- Desk height from laser → knows if sitting or standing
- Mouse + keyboard OS events → knows if user is at computer

**App:** Electron tray app (TypeScript), OS-native notifications

**Core differentiator:** Knows if you ACTUALLY stood up (not just ignored the notification).
All other reminder apps are blind to whether you acted. We have the sensor.

**Business model:** Open source software + OEM sensor kit sold to desk manufacturers
per unit (recurring revenue). See [research/vision/ECOSYSTEM.md](research/vision/ECOSYSTEM.md).

---

## What to build next

**Immediate (before any code):**
1. Review [research/algorithm/NOTIFICATION-ALGORITHM.md](research/algorithm/NOTIFICATION-ALGORITHM.md) with the creator
2. Agree on sitting threshold, snooze duration, max repeats

**Then (in order):**
1. New repo: `smart-desk` (monorepo — firmware + shared + app)
2. Start with `packages/shared/src/types.ts` (shared TypeScript types)
3. Then `packages/app/src/engine/state-machine.ts` (pure logic, write tests first)
4. See full build order: [research/architecture/REPO-ARCHITECTURE.md](research/architecture/REPO-ARCHITECTURE.md)

---

## Website (desk.zentala.io)

Currently: static HTML (`index.html` + `style.css`), Bootstrap 5, GitHub Pages.
Old CLAUDE.md referenced Astro — that was a planned migration that did not happen.

The website needs a content update to reflect the actual product vision
(currently describes v1 hardware with relay board — outdated).
Not a priority until app is released.
