# Armonía del Ser: Public Landing & Self-Service UI - Agent Guidelines & Workflow Rules

This document specifies mandatory workflows, constraints, and quality gates for AI agents operating in `armonia-landing`.

---

## 1. Core Operating Constraints

- **No Direct Commits to `main`**: Agents must never commit directly to `main`. All work must be developed on descriptive feature, bugfix, or chore branches (`feat/*`, `fix/*`, `chore/*`).
- **No Destructive Git Actions**: Commands such as `git reset --hard`, `git restore <file>`, `git clean -fd`, and force-pushes (`git push --force`) are strictly prohibited without the user's explicit yes.
- **Secret Redaction**: Never print, commit, or log sensitive tokens or API credentials.
- **Session Modes**:
  - `learning`: The user drives and writes the reasoning, the agent asks guiding questions.
  - `delivery`: The agent may draft code and plans, presenting rationale and trade-offs.

---

## 2. Agent Directory & Persona Delegation

- **Anne Droid** (`profile/agents/anne-droid.md`): Senior Frontend Engineer & UX Specialist.
  - **Consult when**: Defining visual tone, typography, color palettes, and emotional resonance.
  - **Delegate when**: Implementing client-facing hero components, booking modals, and responsive flyers on `feat/anne/*` branches.
  - **Aesthetic Manifesto**: Reflect the peaceful, grounded identity of *Armonía del Ser* (warm earth tones, lavender/sage lotus palette from the flyer, clean serif display typography, natural textures) without falling into generic template patterns.

---

## 3. Architecture & Functional Directives

- **Target Persona**: Prospective and recurring clients seeking therapy, meditation, cocoa circles, or retreats.
- **Self-Service Booking Flow**:
  1. *Browse Services*: Clear cards displaying modality (presencial/online), schedule, price in MXN, and benefits.
  2. *Reserve Spot*: Client provides name, phone (WhatsApp), and chooses a slot.
  3. *Payment Clarity*: Instructions showing SPEI CLABE + unique Folio code (`ADS-XXXX`).
  4. *One-Tap WhatsApp Handoff*: Client taps button to open WhatsApp chat with Jazmín and send receipt.
