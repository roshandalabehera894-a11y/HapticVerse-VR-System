# Pulse Style Synchronization Selector

Add a compact 3-button **Pulse Style** segmented toggle (`Harmonic`, `Staccato`, `Ethereal`) to the bottom control dock so users can shape how `VRViewport` translates spatial audio (`droneHz`) and haptic activity into bloom luminescence, crystal/obelisk glow, and atmospheric particle drift.

### User Review & Critical Decisions

> [!IMPORTANT]
> Confirmed design choices from clarification:
> - **Confirmed Selector UI**: A compact 3-button segmented toggle (`Harmonic | Staccato | Ethereal`) inside the bottom control dock.
> - **Confirmed Visual Scope**: Switching Pulse Style adapts bloom intensity curves, central crystal and obelisk emissive glow, and atmospheric particle drift speed together.

---

### 1. Overview & Core Concept

- **What It Does**: Gives explorers real-time expressive control over the sensory rhythm of every living realm through three distinct modulation modes:
  - **Harmonic**: Smooth, restorative sine-wave breathing tuned to the active world's `droneHz`, with gentle haptic swells and steady particle motion.
  - **Staccato**: Crisp, tactile-sharp spikes using fast-attack / rapid-decay damping on haptic triggers and rhythmic wave crests, paired with kinetic particle speed surges.
  - **Ethereal**: Layered inharmonic sine-interference waves creating organic, non-repeating dreamy drift across luminescence and floating atmospheric motes.
- **Key Value**: Lets users match the world's visual pulse to their mood—from meditative breathing to kinetic haptic precision or dreamlike ambient drift.

---

### 2. User Experience & Visual Design

- **Key User Flow**:
  1. In the bottom control dock, the user sees the **Pulse Style** segmented control (`Harmonic | Staccato | Ethereal`) styled consistently with the existing `Orbit | Walk` control.
  2. Clicking any mode immediately updates the active visual modulation inside `VRViewport` with zero scene reload or camera interruption.
  3. Triggering **Feel Pulse**, clicking a Sensory Obelisk, or receiving a multiplayer ping reveals the distinct character of the chosen mode (smooth swell vs. sharp tactile flash vs. floating drift).
- **Layout Discipline**:
  - Single-line labels (`whitespace-nowrap shrink-0`) inside a dark segmented pill-free container (`bg-[#06080F] border border-white/10`) with clean active highlight (`bg-white/14 text-white`).
  - Preserves the collapsible bottom dock footprint (`<= 15%` viewport height) and zero `backdrop-filter` over WebGL.

---

### 3. Key Product Decisions & Trade-Offs

- **Decision 1: Stateless Continuous Math + Asymmetric Damping**
  - *Chosen Approach*: Compute **Harmonic** and **Ethereal** envelopes from continuous elapsed-time trigonometric sums (multi-octave inharmonic frequencies for Ethereal), while **Staccato** uses asymmetric exponential damping (fast attack on haptic rise, crisp decay on release) plus power-shaped harmonic crests.
  - *Why*: Avoids abrupt jumps when toggling between modes mid-session and runs with zero heap allocations inside the 60fps render loop.
- **Decision 2: Frame-Synced Ref Propagation**
  - *Chosen Approach*: Pass `pulseStyle` from root app state into `VRViewport` and mirror it into a `useRef` read inside the animation loop.
  - *Why*: Changing Pulse Style never re-initializes the WebGL renderer, `EffectComposer`, or camera state.

---

### 4. Technical Architecture & Data Strategy

```
┌─────────────────────────────────────────────────────────────────────────┐
│                           Bottom Control Dock                           │
│   [ Harmonic | Staccato | Ethereal ]   ──►   Updates pulseStyle state   │
└──────────────────────────────────┬──────────────────────────────────────┘
                                   ▼
┌─────────────────────────────────────────────────────────────────────────┐
│                       VRViewport Animation Loop                         │
│                                                                         │
│  pulseStyleRef + droneHz + hapticAmplitudeRef                           │
│       │                                                                 │
│       ├──► Harmonic : Smooth sin(t * freq) + balanced haptic swell      │
│       ├──► Staccato : Sharp pow(wave, 4) + rapid attack/decay spikes    │
│       └──► Ethereal : Layered 3-frequency drift + soft long-tail glow   │
│                                                                         │
│  Outputs applied per frame (zero GC):                                   │
│       • UnrealBloomPass.strength                                        │
│       • Crystal Core & Obelisk emissiveIntensity                        │
│       • Atmospheric Particles angular/vertical drift rate               │
└─────────────────────────────────────────────────────────────────────────┘
```

#### Interactive Component & State Mapping

- **Shared Type**: `PulseStyle = 'harmonic' | 'staccato' | 'ethereal'`.
- **Root State**: Track `pulseStyle` (default `'harmonic'`) and pass down to both the dock and 3D viewport.
- **Bottom Control Dock**: Render the compact 3-button segmented control with active/inactive states and `aria-pressed` accessibility attributes.
- **VRViewport Render Loop**: Apply the active mode's envelope to `bloomPass.strength`, `crystalCore` & obelisk `emissiveIntensity`, and `particles` motion increment using `delta` time.
