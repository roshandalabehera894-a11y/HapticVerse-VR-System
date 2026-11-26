# Aetheris: Multiverse VR Reality OS Platform

A living alternate reality platform designed for joyful immersion, high-fidelity spatial computing, and boundless multiverse living. Users can step into hyper-realistic 3D sanctuaries, feel tactile sensations through a multi-frequency haptic feedback engine, share spaces with synchronized avatars, and synthesize new living worlds directly from photos and concept art using advanced Gemini vision AI.

### User Review & Critical Decisions

> [!IMPORTANT]
> Based on your vision, this platform is built not as a small arcade game, but as an expansive **Living Alternate Reality Operating System (Aetheris OS)** with photorealistic procedural 3D environments, tactile haptics, multiplayer social embodiment, and an AI World Synthesis Forge where you can upload any picture to analyze and generate living worlds.

- **Platform Architecture**: Full-featured spatial computing hub offering a high-performance 3D WebXR viewport (supporting Meta Quest, Apple Vision Pro, PC VR headsets, and desktop/mobile spatial navigation with mouse/touch/gamepad).
- **Haptic Feedback Support**: Dual-tier sensory engine combining the W3C Gamepad Haptics API (dual-motor vibration pulses, trigger resistance, frequency sweeps) with the Web Vibration API and synthesized low-frequency psychoacoustic sub-bass haptics for total device immersion.
- **AI Multiverse World Synthesis (Vision & Generation)**:
  - **Vision Analyzer (`gemini-4-argon`)**: Multimodal image understanding that analyzes uploaded photos or concept art to extract physical geography, biome ecology, architectural rules, lighting parameters, atmospheric particle density, spatial audio cues, and living lore.
  - **Texture & Skybox Synthesizer (`gemini-nano-banana-2.1`)**: Text-guided image generator that creates custom equirectangular panoramas, celestial backdrops, and terrain textures to manifest the analyzed worlds.
- **Multiplayer Presence**: Real-time room network with synchronized spatial avatar rigs, proximity voice/audio indicators, shared environmental triggers, and teleport portals between multiverse realms.

---

### 1. Overview & Core Concept

- **What It Does**: Aetheris provides a high-fidelity virtual reality operating environment where people can transcend ordinary gaming to live, explore, meditate, create, and socialize across interconnected living worlds. It includes an integrated **Sensory Telemetry Engine** (customizable haptic frequency profiles: heartbeat, rain impact, wind friction, energy pulses), an **Embodied Avatar Rig**, an **AI Multiverse Portal Forge** that transforms uploaded imagery into explorable 3D realms, and a **Spatial Multiplayer Hub**.
- **Target Audience / Persona**: VR enthusiasts, digital world-builders, creative explorers, and people seeking meaningful, uplifting alternate reality living experiences with next-generation visuals.
- **Key Value**: Bridges the gap between static games and true virtual existence: stunning physical-based 3D graphics (volumetric lighting, day/night atmospheric scattering, water reflections, particles), genuine haptic sensation, and generative AI that creates infinite worlds from images.

---

### 2. User Experience & Visual Design

#### Key User Flows

1. **Reality Portal & Spatial Chamber (Zero State)**:
   - User enters the Aetheris Spatial Chamber: a hyper-detailed architectural pavilion overlooking a dynamic cosmic nebula or bioluminescent archipelago.
   - Immediate toggle for **Enter VR (WebXR)** or **Free-Look Desktop/Touch Exploration**.
   - Subtle tactile welcome pulse calibrates the haptic motors.
2. **AI Multiverse World Forge (Image-to-World Synthesis)**:
   - User opens the World Forge and uploads or drops any picture (e.g. fantasy landscape, cybernetic garden, serene mountain shrine, architectural sketch).
   - `gemini-4-argon` deeply inspects the visual composition, lighting topology, atmospheric particles, materials, and biome physics.
   - The platform generates a living 3D procedural simulation matching the image's aesthetic with procedural geometry, custom lighting, particle systems, and audio soundscape.
   - User can also prompt `gemini-nano-banana-2.1` to generate custom 360-degree skyboxes or ambient textures.
3. **Multiverse Living Realms**:
   - Seamless portal travel to curated living realms (e.g., *Elysian Canopy*, *Luminescent Abyss*, *Hyper-Solarium*, *Aetherian Sky-Sanctuary*).
   - Interactive world elements: physical touch spheres with reactive haptics, ambient weather modulation, day/night cycles, living wildlife/particle dynamics.
4. **Haptic Feedback & Sensory Calibration Center**:
   - Visual waveform monitor showing dual-motor frequency, amplitude, and pattern duration.
   - Interactive haptic testbeds: *Raindrop Droplets*, *Heartbeat Resonator*, *Kinetic Impact*, *Gravitational Drift*, and *Energy Shield Surge*.
   - Works across VR controllers, standard gamepads (DualSense/Xbox), and mobile vibration hardware.
5. **Immersive Multiplayer Realm**:
   - Instant room connection with unique Multiverse Room IDs.
   - Synchronized 3D avatars with head and hand orientation, walking physics, interactive greeting gestures, and spatial audio beacon pings.

#### Visual Identity & Theme

- **Aesthetic Direction**: High-end spatial luxury and futuristic biocentric minimalism. Translucent glassmorphic surfaces, hairline titanium edges, deep void backgrounds, and vibrant bioluminescent lighting accents.
- **Color Palette & Mood**:
  - Canvas / Void: Deep Obsidian (`#06080F`), Dark Space Navy (`#0C101F`)
  - Structural Surfaces: Frosted Obsidian Glass (`rgba(15, 23, 42, 0.75)`), Hairline Borders (`rgba(255, 255, 255, 0.08)`)
  - Energy Accents: Prismatic Cyan (`#06B6D4`), Hyper Violet (`#8B5CF6`), Radiant Emerald (`#10B981`), Solar Amber (`#F59E0B`)
  - Typography: Pure White (`#FFFFFF`) with Muted Starlight Slate (`#94A3B8`)
- **Typography & Hierarchy**:
  - Display / Hero Wordmark: `Outfit` & `Plus Jakarta Sans` for clean, forward-looking architectural authority.
  - Data / Telemetry / HUD: `JetBrains Mono` with `tabular-nums` for precise spatial metrics, frequency readings, and coordinates.
- **Interactive Feedback & Motion**:
  - Micro-interactions settle smoothly under 180ms with custom cubic-bezier dampening.
  - Spatial audio synthesizer built with Web Audio API for tactile clicks, ambient drone resonance, and positional cues.

---

### 3. Key Product Decisions & Trade-Offs

- **Decision 1: Dual WebXR and Interactive 3D Canvas Engine**
  - *Chosen Approach*: Build on Three.js with full WebXR session management (`navigator.xr.requestSession('immersive-vr')`) alongside rich desktop/mobile pointer-lock, orbit, and virtual joystick controls.
  - *Why*: Allows anyone without an expensive VR headset to fully experience the high-graphical multiverse platform right now, while providing native 6DOF stereoscopic VR to headset owners.
  - *Alternatives Considered*: Native WebXR-only (would lock out users testing on standard desktop browsers or phones).
- **Decision 2: Comprehensive Multi-Device Haptic Engine**
  - *Chosen Approach*: Triple-path haptic architecture:
    1. Gamepad Haptics API (`gamepad.vibrationActuator.playEffect('dual-rumble')`) for Quest/Vive/Index VR controllers and console gamepads.
    2. Navigator Vibration API (`navigator.vibrate()`) for mobile devices.
    3. Web Audio Sub-Frequency Psychoacoustic synthesizer (30Hz–80Hz resonance burst) for audio-tactile rumble on headphones/speakers.
  - *Why*: Guarantees every user feels physical feedback regardless of their connected peripheral.
- **Decision 3: Server-Side Gemini API Proxy with Structured Output**
  - *Chosen Approach*: Route image analysis through `/api/gemini/analyze-world` using `gemini-4-argon` and image generation through `/api/gemini/create-image` using `gemini-nano-banana-2.1` via `@google/genai`.
  - *Why*: Protects API credentials, complies with environment constraints, and formats vision analysis directly into executable 3D world parameters (lighting color, fog density, terrain elevation, particle speed, sound frequencies).

---

### 4. Technical Architecture & Data Strategy

```
┌────────────────────────────────────────────────────────────────────────┐
│                        Aetheris VR Platform UI                         │
│  ┌───────────────────────┐  ┌────────────────┐  ┌───────────────────┐  │
│  │ Top Navigation Bar    │  │ VR / 3D Canvas │  │ World Forge Modal │  │
│  │ (Living Realms / HUD) │  │ (Full Viewport)│  │ (Image Analyzer)  │  │
│  └───────────┬───────────┘  └───────┬────────┘  └─────────┬─────────┘  │
└──────────────┼──────────────────────┼─────────────────────┼────────────┘
               ▼                      ▼                     ▼
┌────────────────────────────────────────────────────────────────────────┐
│                     Core Spatial & Runtime Engines                     │
│  ┌───────────────────────────┐         ┌────────────────────────────┐  │
│  │ Three.js 3D Engine        │         │ Haptics & Sensory Engine   │  │
│  │ • PBR Materials & Shaders │         │ • Gamepad Haptics API      │  │
│  │ • Procedural Landscapes   │◄───────►│ • Web Vibration API        │  │
│  │ • WebXR Session Rig       │         │ • Sub-Bass Audio Haptics   │  │
│  │ • Particle & Atmosphere   │         └────────────────────────────┘  │
│  └───────────┬───────────────┘                                         │
│              ▼                                                         │
│  ┌───────────────────────────┐         ┌────────────────────────────┐  │
│  │ Multiplayer Presence Hub  │         │ AI Multiverse World Forge  │  │
│  │ • Avatar Kinematics       │         │ • gemini-4-argon (Vision)  │  │
│  │ • Room State & Pings      │◄───────►│ • gemini-nano-banana-2.1   │  │
│  │ • Spatial Proximity Mesh  │         │ • Dynamic Parameter Parser │  │
│  └───────────────────────────┘         └──────────────┬─────────────┘  │
└───────────────────────────────────────────────────────┼────────────────┘
                                                        ▼
┌────────────────────────────────────────────────────────────────────────┐
│                        Express Proxy Server (/api)                     │
│  • POST /api/gemini/analyze-world   (Multimodal Vision Analyzer)       │
│  • POST /api/gemini/create-image    (Skybox & Texture Generation)      │
└────────────────────────────────────────────────────────────────────────┘
```

#### Data Model & State

- **World Environment State**:
  - `id`, `name`, `theme`, `lore`, `skyColor`, `groundColor`, `fogDensity`, `ambientIntensity`, `sunPosition`, `particles` (count, velocity, color), `soundScape` (preset, droneFrequency), `sourceImage` (if created via AI).
- **Haptic Telemetry**:
  - `activeEffects`, `motorIntensity` (0.0 to 1.0), `subBassEnabled`, `hapticLog`, `hapticProfile` (Tactile, Soft, Heavy, Resonant).
- **Multiplayer Avatar State**:
  - `userId`, `username`, `color`, `position` `[x, y, z]`, `rotation` `[x, y, z]`, `handLeft` `[x, y, z]`, `handRight` `[x, y, z]`, `status`, `ping`.
- **AI World Generation State**:
  - `analyzingImage` (boolean), `generatedWorldConfig`, `imagePrompt`, `aiInsights` (architectural style, emotional tone, atmospheric composition).

#### Interactive Component & State Mapping

- **VR Reality Viewport (`VRCanvas`)**: Fullscreen WebXR canvas with PBR pipeline, dynamic day/night orbit, floating celestial bodies, interactive sensory obelisks, and camera controls.
- **Multiverse Navigator**: Instant switching between 4 core realms + user-generated AI realms.
- **Haptic Feedback Deck**: Tactile triggers for testing motor rumble, frequency sweeps, and environmental impact simulation.
- **AI World Forge Panel**: File upload / camera snapshot input, instant preview, `gemini-4-argon` multi-dimensional analysis, and 1-click "Materialize World in VR" action.
- **Multiplayer Sanctuary Drawer**: Room code generation, connected avatar list, spatial emote pings, and presence radar.
