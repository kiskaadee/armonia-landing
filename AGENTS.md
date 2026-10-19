# Repository Technical Blueprint: `armonia-landing`

This file defines the local toolchain, frontend implementation rules, aesthetic boundaries, and self-service reservation flow for `armonia-landing`. For cross-repo Git branching rules, TDD lifecycle, or Gitea (`tea`) issue tracking, consult the workspace root [`../AGENTS.md`](../AGENTS.md).

---

## 1. Local Toolchain & Nix Environment (`flake.nix` + `pnpm` + `Vite+` + `Biome`)

This repository is provisioned via a declarative Nix `devShell` (`flake.nix` + `.envrc`) and uses `pnpm`, `Vite+` (`vp`), and `Biome`.
- **Nix DevShell:** Ensure commands run inside the Nix environment (`direnv` activates automatically on `cd`, or prefix with `nix develop -c <cmd>`).
- **Package Manager:** Use `pnpm` exclusively (`pnpm install`, `pnpm add`). Never use `npm` or `yarn` (do not generate `package-lock.json` or `yarn.lock`).
- **Verification Gates (Pre-Commit Checklist):**
  Before proposing or executing any commit, run and pass all checks with zero warnings or errors:
  ```bash
  pnpm exec biome check .
  pnpm exec vp check
  pnpm exec vp test
  ```

---

## 2. Frontend Architecture & Aesthetic Direction

### Anne Droid Delegation (`profile/agents/anne-droid.md`)
- **Consult when:** Defining visual tone, typography, color palettes, emotional resonance, and mobile booking ergonomics.
- **Delegate when:** Implementing client-facing hero sections, service catalog cards, booking flows, and frontend tests on `feat/anne/*` branches.

### Aesthetic & UX Invariants
- **Grounded Holistic Identity:** Reflect the peaceful, warm identity of *Armonía del Ser* (referencing [`../armonia-flyer.jpg`](../armonia-flyer.jpg): warm earth tones, lavender/sage lotus palette, clean serif display typography, and natural textures) without generic SaaS template tropes.
- **5-State Resilient UI:** Every dynamic catalog and booking component must handle *Empty* (no slots available), *Loading*, *Error* (e.g., `409 Conflict` slot collision), *Partial*, and *Success* states cleanly.
- **Public Security Boundary:** Consumes only public `armonia-api` endpoints (`GET /services`, `POST /bookings`). Never expose administrative routes or credentials.

---

## 3. Self-Service Client Reservation Flow

1. **Browse Service Catalog:** Clear cards displaying modality (`PRESENCIAL` in Tulancingo vs. `ONLINE`), schedule, duration, price in MXN, and holistic benefits.
2. **Claim Slot:** Client selects a service and time slot and enters their name and WhatsApp phone number (or redeems an active multi-session package).
3. **SPEI Payment Instructions:** Displays SPEI bank details, CLABE, and the generated reservation folio (`ADS-XXXX`).
4. **One-Tap WhatsApp Handoff:** Opens a pre-filled `wa.me` chat with Jasmin/assistant so the client can send their transfer receipt immediately.
