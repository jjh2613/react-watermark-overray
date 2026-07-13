# react-watermark-overlay

[![npm version](https://img.shields.io/npm/v/react-watermark-overlay.svg)](https://www.npmjs.com/package/react-watermark-overlay)
[![npm downloads](https://img.shields.io/npm/dm/react-watermark-overlay.svg)](https://www.npmjs.com/package/react-watermark-overlay)
[![license](https://img.shields.io/npm/l/react-watermark-overlay.svg)](./LICENSE)

A lightweight, zero-dependency React component that overlays a slanted, repeated text watermark (like `TEST`) across a container or the whole viewport. Ideal for marking **staging / test / confidential** environments so screenshots and shared screens are clearly identified as non-production.

👉 **[Live demo & docs](https://jjh2613.github.io/react-watermark-overlay/)**

## ✨ Features

- 🔁 Diagonal, repeated watermark pattern
- 🖼️ Two modes: `box` (fill a container) or `overlay` (cover the full viewport)
- 🖱️ Click-through — `pointer-events: none`, never blocks interaction
- 📐 Responsive — auto-recomputes on resize via `ResizeObserver`
- 🎛️ Customizable text, opacity, font size, rotation, and cell spacing
- 📦 Zero runtime dependencies, TypeScript types included

## 📦 Installation

```bash
npm install react-watermark-overlay
```

```bash
yarn add react-watermark-overlay
```

```bash
pnpm add react-watermark-overlay
```

> **Peer dependency:** React 17 or 18.

## 🚀 Usage

### Overlay mode — cover the whole viewport

Perfect for globally marking a staging/test build. Render it once, near the root of your app.

```tsx
import { Watermark } from "react-watermark-overlay";

export default function App() {
  return (
    <>
      <YourApp />
      <Watermark text="STAGING" type="overlay" />
    </>
  );
}
```

### Box mode — mark a single container

Applies the watermark to a specific section (e.g. a document preview). The parent element should be `position: relative`.

```tsx
import { Watermark } from "react-watermark-overlay";

export default function DocumentPreview() {
  return (
    <div style={{ position: "relative", width: 320, height: 240 }}>
      <Watermark
        text="CONFIDENTIAL"
        type="box"
        opacity={0.3}
        fontSize="1.2rem"
        rotate={-30}
        watermarkCellSize={80}
      />
      <div style={{ position: "relative", zIndex: 1, padding: 16 }}>
        <h2>Document Preview</h2>
        <p>This area is marked as confidential.</p>
      </div>
    </div>
  );
}
```

## 🎛️ Props

| Prop                     | Type                                   | Default     | Description                                                                                 |
| ------------------------ | -------------------------------------- | ----------- | ------------------------------------------------------------------------------------------- |
| `text`                   | `string`                               | `"TEST"`    | The watermark text to repeat.                                                               |
| `opacity`                | `number`                               | `0.2`       | Opacity of the watermark text (`0`–`1`).                                                     |
| `fontSize`               | `string`                               | `"5rem"`    | CSS font size of the watermark text.                                                        |
| `type`                   | `"box" \| "overlay"`                   | `"box"`     | `box` fills the parent container; `overlay` covers the whole viewport (`position: fixed`).  |
| `rotate`                 | `number`                               | `-45`       | Rotation angle of the pattern, in degrees.                                                  |
| `watermarkCellSize`      | `number`                               | `160`       | Spacing (px) of each repeated cell — smaller = denser pattern.                              |
| `containerDivAttributes` | `React.HTMLAttributes<HTMLDivElement>` | `undefined` | Extra props spread onto the container `div` (e.g. `style`, `className`, `id`).              |

## 💡 Notes

- The component renders `aria-hidden="true"` and is fully click-through, so it never interferes with accessibility or user interaction.
- In `box` mode, give the parent element `position: relative` and render your content with a higher `z-index` so it sits above the watermark.
- In `overlay` mode the watermark is `position: fixed` and always fills the viewport regardless of the parent.

## 🧑‍💻 Development

The repository is organized as two folders:

- [`package/`](https://github.com/jjh2613/react-watermark-overlay/tree/main/package) — the published component source.
- [`example/`](https://github.com/jjh2613/react-watermark-overlay/tree/main/example) — a Vite demo app used for the live docs.

```bash
# build the package
cd package
npm install
npm run build
```

## 📄 License

[MIT](./LICENSE) © jjh2613
