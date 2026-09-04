[README.md](https://github.com/user-attachments/files/31827707/README.md)
# THALASSA — One Window, Two Worlds

> An immersive WebGL ocean cross-section experiment where a fixed sea, a scrolling document, and a changing sky share the same viewport.

THALASSA is a single-page creative coding prototype built around a **half-above / half-underwater ocean view**.  
Instead of treating the ocean as a background image, the page renders the sea as a live visual system: waves, refraction, underwater light, weather, particles, and the day cycle all react as the user scrolls.

## 🌊 Live Demo

**GitHub Pages:**  

**[Open THALASSA](https://throne-kari.github.io/thalassa-ocean/)**

---

## ✨ Highlights

- **Real-time ocean cross-section** with the camera positioned around the waterline
- **Scroll-driven day cycle** from evening through night to the following noon
- **Analytic wave field** shared across the sea surface, waterline, refraction, and particle interactions
- **Screen-space refraction** for UI elements crossing the waterline
- **Underwater optics** with depth attenuation, haze, shafts, caustics, and spectral absorption
- **Dynamic weather system** with storm clouds, rain, wind, whitecaps, and lightning
- **Rain-to-ocean interaction** with surface impacts and ripple/crown effects
- **Environmental motion** including bubbles, fish schools, birds, spray, and meteors
- **Responsive layout** with mobile-aware rendering choices
- Support for **`prefers-reduced-motion`**

---

## 🎨 Concept

The entire browser window is treated as a vertical slice through the ocean.

The sea remains fixed to the viewport while the document scrolls through it. Elements can pass through the waterline, becoming visually submerged and refracted instead of simply disappearing behind a CSS layer.

The result is a website that behaves less like a conventional page and more like a small interactive environment.

---

## 🧠 Rendering Approach

THALASSA combines DOM UI with a WebGL rendering pipeline.

### 1. Ocean render pass

The ocean scene renders:

- sky
- sun and moon
- clouds and stars
- sea surface
- underwater column
- glitter and reflections
- light shafts and caustics
- bubbles and fish

into a `WebGLRenderTarget`.

### 2. Waterline / UI mask

A low-resolution 2D mask tracks DOM elements that intersect the live waterline.

The mask stores information about:

- UI coverage
- submersion depth
- transition intensity

### 3. Composite / refraction pass

The final shader composites the scene and reprojects the submerged parts of UI through the same wave field used to draw the sea.

This keeps the visible waterline, refraction, and wave motion synchronized.

---

## 🛠 Tech Stack

- **HTML5**
- **CSS3**
- **JavaScript / ES Modules**
- **Three.js**
- **GLSL**
- **GSAP**
- **ScrollTrigger**
- **WebGL2**

The current prototype is intentionally contained in a single `index.html` file and loads its external libraries from CDNs.

---

## 🕹 Interaction

### Scroll

Scroll through the page to move through the time-of-day sequence and the different sections of the experience.

### Weather

Use the **Weather** button in the navigation bar to switch between clear conditions and the storm system.

### Optional query parameters

Start directly in storm mode:

```text
?storm=1
```

Disable ecology effects such as birds, meteors, spray, and bubbles:

```text
?noecology=1
```

Example:

```text
https://throne-kari.github.io/thalassa-ocean/?storm=1
```

---

## 🚀 Run Locally

Because the project uses ES modules and CDN imports, it should be opened through a local HTTP server rather than directly with `file://`.

### Python

```bash
python -m http.server 5174
```

Then open:

```text
http://localhost:5174
```

### Node.js

You can also use a lightweight static server:

```bash
npx serve .
```

---

## 🌐 Deploy with GitHub Pages

1. Rename the main file to:

```text
index.html
```

2. Upload it to the root of your GitHub repository.

3. Open:

```text
Settings → Pages
```

4. Set:

```text
Source: Deploy from a branch
Branch: main
Folder: / (root)
```

5. Save and wait for GitHub Pages to finish building.

Your site will normally be available at:

```text
https://throne-kari.github.io/thalassa-ocean/
```

---

## 📁 Project Structure

```text
.
├── index.html
└── README.md
```

The current version is deliberately self-contained, with the main visual systems, shaders, styles, and interactions living inside `index.html`.

---

## 💻 Browser Notes

A modern browser with **WebGL2** support is recommended.

For the intended experience, desktop Chromium-based browsers generally provide the best combination of WebGL performance and visual fidelity.

Performance may vary depending on GPU capability, viewport size, and browser rendering settings.

---

## 🌌 Design Direction

THALASSA explores the idea that a webpage does not need to place content *on top of* a scene.

Instead, the content can become part of the scene itself:

> **The interface is a website. The ocean is a shader.**

---

## 📄 License

No license is included by default.

If you want other people to freely reuse or modify the project, add a license such as MIT.  
If you prefer to keep reuse restricted, leave the repository without an open-source license until you decide.

---

**THALASSA · Ocean Optics Lab**  
*One window, two worlds.*
