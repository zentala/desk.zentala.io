# Open Smart Desk — Tasks

## Next up

- [ ] **Sensor-daemon — packages/daemon — priority #1**
      Oddzielony od apki Electron — crash developmentu nie zatrzymuje zbierania danych.
      Architektura: jeden proces Node.js (bez Electron) który:
        (1) czyta USB Serial z RP2040-Tiny (protokół JSON Lines, 115200 baud)
        (2) loguje do ~/.smart-desk/desk.log (append-only CSV, flush co linię)
        (3) serwuje dane przez WebSocket ws://localhost:3847
      Apka Electron łączy się jako klient WS — nie ma dostępu do portu USB bezpośrednio.
      Startuje automatycznie z systemem: Task Scheduler (Win) / systemd (Linux) / LaunchAgent (macOS).
      Szczegóły: [research/architecture/REPO-ARCHITECTURE.md](research/architecture/REPO-ARCHITECTURE.md)
      → Zbieraj dane od siebie przez 30 dni zanim napiszesz cokolwiek innego.

- [ ] **Design notification algorithm as state machine** — before writing any code.
      Sit with Claude and map: states (sitting/standing/away), transitions, timing rules,
      edge cases (meetings, short stands, night mode).
      → See open questions in [research/SESSION-2026-06-25.md](research/SESSION-2026-06-25.md)

- [ ] **Rewrite Electron app from scratch** — clean v1, not patched experiment.
      Stack: TypeScript + Electron + USB Serial (RP2040-Tiny) + OS notifications.
      Modes: software-only (mouse/keyboard) + hardware (+ VL53L0X height).

- [ ] **Design RP2040-Tiny firmware** — USB Serial, sends height readings as JSON.
      Decide: USB Serial vs HID. Calibration flow.

- [ ] **Design PCB v2** — black PCB, RP2040-Tiny + VL53L0X, I2C traces, USB connector.
      Fab: JLCPCB.

- [ ] **Design enclosure v2** — smoked graphite plexi, laser cut, much smaller than v1.
      New DXF file in `enclosure/v2/`.

## Backlog

- [ ] GitHub release v0.1.0 with binaries (Win + Linux + macOS)
- [ ] Minimal README + notification screenshot
- [ ] Post to r/StandingDesk + r/selfhosted + HA Community
- [ ] `/processize` skill — think through manual hardware kit delivery
- [ ] `/first-customers` skill — when app is live
- [ ] `/pricing` skill — before hardware kit pricing
- [ ] Duolingo-style gamification (streaks, XP) — after 100 active users

## Done

- [x] Validate idea — minimalist-entrepreneur skill session (2026-06-25)
- [x] Community research — real user quotes collected → `research/user-quotes.xml`
- [x] Hardware v2 spec → `research/hardware-v2-spec.md`
- [x] MVP plan defined → `research/SESSION-2026-06-25.md`
- [x] Decision: rewrite from scratch, not patch experiment
- [x] Vision & strategy documented:
  - `research/vision/MISSION.md` — filozofia, misja, target users
  - `research/vision/ECOSYSTEM.md` — model biznesowy, konsorcjum, OEM per-unit
  - `research/vision/ROADMAP.md` — Stage 0→5, Smart Desk→Smart Move→Standard
  - `research/vision/RESEARCH-PLAN.md` — plan badań, PW, granty UE
- [x] Notification algorithm designed → `research/algorithm/NOTIFICATION-ALGORITHM.md`
- [x] Architecture designed (sensor-daemon + WS + Electron) → `research/architecture/REPO-ARCHITECTURE.md`
- [x] Firmware protocol spec → `research/architecture/FIRMWARE-SPEC.md`
- [x] PRD written → `PRD.md`
