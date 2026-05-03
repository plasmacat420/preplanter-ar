# PrePlanter AR

An immersive **Augmented Reality experience** that brings the PrePlanter brand to life. Point your device at the PrePlanter logo and watch a beautiful 3D plant grow before your eyes with animated branches, leaves, particles, and a glowing aura.

## Overview

**PrePlanter AR** is a web-based AR application that uses **MindAR** for image recognition and **Three.js** for 3D graphics. When you scan the PrePlanter logo, an animated 3D plant blooms with:

- 🌱 Procedurally animated branches growing in sequence
- 🍃 Cascading leaf bloom animations with subtle swaying
- ✨ Particle effects and glowing rings
- 🎨 Elegant green color palette (`#52B788`, `#74C69D`, `#2D6A4F`)
- 🎯 Smooth easing animations and physics-like motion

## Features

### Core Components

- **index.html** - Main AR viewer with MindAR integration and Three.js 3D rendering
- **compile.html** - AR target compiler tool (converts logo images to `.mind` format)
- **targets.mind** - Pre-compiled AR tracking data (recognizes the PrePlanter logo)
- **logo.png** - PrePlanter brand logo asset

### Technical Stack

- **MindAR** v1.2.5 - Image-based AR tracking engine
- **Three.js** v0.150.0 - 3D graphics library
- **WebGL** - GPU-accelerated rendering
- **Vanilla JavaScript** - No framework dependencies

## Getting Started

### Live Demo

🔗 **[View PrePlanter AR Live](https://plasmacat420.github.io/preplanter-ar/)**

Simply visit the link above and allow camera access. Point your device at the PrePlanter logo to trigger the AR experience.

### Local Development

1. **Clone the repository**
   ```bash
   git clone https://github.com/plasmacat420/preplanter-ar.git
   cd preplanter-ar
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Start local server**
   ```bash
   npx serve
   ```

4. **Open in browser**
   - Navigate to `http://localhost:3000`
   - Allow camera permissions
   - Point at the PrePlanter logo to activate AR

### Creating Custom AR Targets

Use the **compile.html** tool to create new AR targets:

1. Open `http://localhost:3000/compile.html`
2. Select your logo/image PNG
3. Click "COMPILE TARGET" to generate `targets.mind`
4. Place the compiled file in the project root

## How It Works

### Animation Timeline

The plant growth animation unfolds over ~4.5 seconds:

| Phase | Duration | Animation |
|-------|----------|-----------|
| 0.3–2.3s | 2.0s | Main trunk grows upward |
| 1.3–2.3s | 1.0s | Left branch emerges |
| 1.6–2.6s | 1.0s | Right arch branch develops |
| 2.0–2.8s | 0.8s | Upper branches flourish |
| 2.6–3.25s | 0.65s | Leaves cascade and bloom |
| 4.0–5.6s | 1.6s | Particles rise and sparkle |

Each element uses custom easing functions (`outCubic`, `outQuart`, `outElastic`) for organic motion.

### Color Palette

```javascript
Trunk Deep:   #1B4332
Trunk Mid:    #2D6A4F
Branch:       #40916C
Leaf A:       #52B788
Leaf B:       #74C69D
Glow Ring:    #95D5B2
Spark:        #D8F3DC
```

## File Structure

```
preplanter-ar/
├── index.html          # Main AR viewer
├── compile.html        # AR target compiler
├── logo.png            # PrePlanter logo asset
├── targets.mind        # Pre-compiled AR tracking data
├── package.json        # Project metadata
├── .gitignore          # Git ignore rules
└── README.md           # This file
```

## Browser Compatibility

- ✅ Chrome/Chromium (recommended)
- ✅ Edge
- ✅ Firefox
- ⚠️ Safari (limited WebGL support)
- ❌ Internet Explorer (not supported)

**Requirements:**
- WebGL support
- Camera access permission
- Modern JavaScript (ES6+)

## Performance Notes

- Optimized for mobile devices (pixel ratio capped at 2x)
- ~80 animated particles + 40+ leaves + 7 branches
- Runs at 60 FPS on modern hardware
- AR tracking: ~30ms per frame

## License

ISC

## About PrePlanter

PrePlanter is a concept project exploring the intersection of nature, technology, and augmented reality. This AR experience brings the brand philosophy—**"Experience Growth"**—to life through immersive digital interaction.

---

**Created by:** [@plasmacat420](https://github.com/plasmacat420)  
**Last Updated:** May 2026
