HapticVerse
HapticVerse VR System
Aetheris — The Multiverse You Can Actually Feel

An open-source VR reality operating system that lets you step inside photographs, feel rain on your skin through haptic motors, and share living worlds with anyone on the planet — all from a browser.




WebXR
Three.js
Gemini AI
Express
PRs Welcome
License: MIT




Live Demo · Read the Spec · Quick Start · Contribute

💡 The Problem

Virtual reality today is fragmented, expensive, and isolating. You need a $500+ headset, platform-locked apps, and you still can't create your own worlds without learning Unity or Unreal. Most "VR" experiences are glorified 360° videos with zero physical feedback.

What if you could:

📸 Take a photo of anything — a mountain, a painting, a napkin sketch — and walk inside it in VR?
🫨 Actually feel the raindrops, the heartbeat, the energy shield impact through your controller, phone, or headphones?
👥 Bring your friends into that world in real-time, with full-body avatars and spatial voice?
🌐 Do all of this from a browser — no app store, no install, no $500 headset required?

That's HapticVerse.

🧠 How It Works (The 60-Second Version)
  📸 You upload a photo
       │
       ▼
  🤖 Gemini AI (gemini-4-argon) deeply analyzes it
     → extracts geography, biome, lighting, materials,
       atmospheric particles, spatial audio cues, and lore
       │
       ▼
  🎨 Gemini AI (gemini-nano-banana-2.1) generates
     → 360° skyboxes, terrain textures, and ambient art
       │
       ▼
  🌍 Three.js procedurally builds a living 3D world
     → PBR materials, volumetric fog, day/night cycle,
       particle weather, water reflections, wildlife
       │
       ▼
  🫨 Haptic Engine makes you FEEL it
     → dual-motor rumble, mobile vibration,
       psychoacoustic sub-bass through your headphones
       │
       ▼
  👥 Multiplayer syncs everyone inside
     → real-time avatars, spatial audio, portal travel

The full implementation spec lives in ARTIFACT.md — it covers every architectural decision, data model, component mapping, and trade-off in detail.

🔥 Why Developers Should Care

This isn't a toy demo. It's an extensible spatial computing platform built on open web standards. Here's what makes the architecture interesting:

1. 🎮 The Dual Rendering Strategy

Most WebXR projects force you to choose: build for VR headsets OR build for desktop. We do both simultaneously with a single Three.js scene graph.

javascript
// Same scene, two rendering paths
if (navigator.xr) {
  // Full 6DOF stereoscopic rendering on Quest/Vision Pro/Index
  session = await navigator.xr.requestSession('immersive-vr');
  renderer.xr.setSession(session);
} else {
  // Pointer-lock + orbit controls for desktop/mobile
  controls = new OrbitControls(camera, renderer.domElement);
}
