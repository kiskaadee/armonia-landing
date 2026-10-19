# Armonía del Ser: Client Landing & Self-Service UI (`armonia-landing`)

Client-facing landing page and self-service appointment reservation application for **Armonía del Ser**.

> *"Cada día, un espacio para volver a ti."*  
> Espacios para reconectar contigo, calmar tu mente y armonizar tu cuerpo y tu energía.

---

## Capabilities & Vision

`armonia-landing` translates Jazmín's physical service flyer and Instagram outreach into a welcoming digital experience:
- **Service Catalog**: Clean breakdown of weekly recurring circles (*Círculos de Cacao*, *Meditación con cuencos*, *Constelaciones Familiares*) and individual psychotherapy (*Atención Psicológica*).
- **Self-Service Reservation**: Allows clients to select a service, specify their attendance modality (Presencial in Mexico or Online via Google Meet/Zoom), and claim a spot.
- **Frictionless SPEI Instructions**: Displays Jazmín's CLABE and bank details with an auto-generated reservation folio (`ADS-XXXX`).
- **WhatsApp Direct Connect**: Instant button to send payment receipt directly to Jazmín's WhatsApp.

---

## Design & Aesthetics

Guided by **Anne Droid**:
- Soft, grounded aesthetic matching the flyer: lavender, sage, warm stone, and lotus accents.
- Responsive for mobile clients coming from Instagram/WhatsApp stories.
- Complete 5-state resilience (handling empty slots, loading states, and instant confirmation feedback).

---

## Local Development Quickstart

### Prerequisites
- NixOS / Nix Flakes (`direnv` recommended) or Node.js 22+ & `pnpm`

### 1. Enter Nix DevShell & Setup Environment
```bash
direnv allow # or: nix develop
cp .env.example .env
```
Set `VITE_API_BASE_URL=http://localhost:8000` to connect to `armonia-api`.

### 2. Install Dependencies
```bash
pnpm install
```

### 3. Run Dev Server (`Vite+`)
```bash
pnpm exec vp dev
```
Open `http://localhost:5173` in your browser.

### 4. Verification Gates
```bash
pnpm exec biome check .
pnpm exec vp check
pnpm exec vp test
```