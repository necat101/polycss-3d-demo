# PolyCSS 3D Demo

A self-contained HTML demo showcasing [PolyCSS](https://polycss.com/) - a pure CSS 3D engine that renders 3D meshes using DOM elements and CSS transforms (no WebGL or Canvas required).

## 🎯 What is This?

This demo creates an interactive 3D scene where:
- Each polygon is a **real DOM element**
- Positioned with `transform: matrix3d(...)`
- Rendered by the browser's CSS compositor
- Fully inspectable in DevTools
- No WebGL context, no `<canvas>` element

## 🚀 Quick Start

Simply open `index.html` in a modern browser - no build step, no dependencies, no server required!

```bash
# Option 1: Direct open
open index.html

# Option 2: Local server (recommended)
python3 -m http.server 8000
# Then visit http://localhost:8000
```

## 🎨 Features Demonstrated

- **Multiple 3D primitives**: Icosahedron, boxes, octahedrons
- **Interactive controls**: Drag to rotate, scroll to zoom
- **Lighting**: Ambient + directional lights
- **Materials**: Solid colors with opacity
- **Animation**: Auto-rotating center piece
- **Hover effects**: Polygons highlight on mouseover
- **Responsive design**: Works on desktop and mobile

## 🛠️ Technical Details

### How PolyCSS Works
1. Loads 3D mesh data (or creates primitives)
2. Each triangle becomes a `<div>` element
3. Positions it with CSS `transform: matrix3d()`
4. Browser's compositor handles 3D layering and rendering
5. Results in a tree of ~500 DOM elements for this demo

### Architecture
```
<poly-camera>          // Camera with projection
  └─ <poly-scene>      // Scene with lighting
      ├─ <poly-orbit-controls>  // Mouse interaction
      ├─ <poly-ambient-light>
      ├─ <poly-directional-light>
      ├─ <poly-icosahedron>      // Each becomes ~80 polygons
      ├─ <poly-box>              // Each becomes 12 polygons
      └─ <poly-octahedron>       // Each becomes 16 polygons
```

### Browser Compatibility
- ✅ Chrome/Edge 90+
- ✅ Firefox 88+
- ✅ Safari 14+
- ⚠️ Mobile browsers may have performance limitations

## 📊 Performance

This demo renders approximately **500 DOM elements** simultaneously:
- Each polygon is individually addressable
- Can attach event listeners to polygons
- Style with CSS classes
- Animate with CSS transitions
- Inspect in DevTools → Elements panel

**Performance characteristics:**
- Good for: Low-poly scenes, data visualization, interactive diagrams
- Not ideal for: High-poly models, games requiring 60fps, complex scenes

## 🎓 Learning Resources

- [PolyCSS Documentation](https://polycss.com/)
- [How It Works](https://polycss.com/core-concepts)
- [API Reference](https://polycss.com/api/headless)
- [Gallery](https://polycss.com/gallery)

## 🔗 Related Projects

This demo was inspired by:
- [CSSQuake](https://cssquake.com/) - Quake rendered with CSS
- [CSS Doom](https://cssdoom.wtf/) - DOOM rendered with CSS
- Hacker News discussion on CSS 3D capabilities

## 📝 License

MIT - Feel free to use for learning and experimentation!

## 🤝 Contributing

Found a bug or have an improvement? PRs welcome!

---

**Note**: This is a demonstration of CSS 3D capabilities, not a production game engine. For serious 3D work, use WebGL (Three.js, Babylon.js) or WebGPU.
