# react-watermark-overlay

[![npm version](https://img.shields.io/npm/v/react-watermark-overlay.svg)](https://www.npmjs.com/package/react-watermark-overlay)
[![license](https://img.shields.io/npm/l/react-watermark-overlay.svg)](./LICENSE)

A lightweight, zero-dependency React component that overlays a slanted, repeated text watermark across a container or the whole viewport — perfect for marking **staging / test / confidential** environments.

👉 **[Live demo & docs](https://jjh2613.github.io/react-watermark-overlay/)**

```bash
npm install react-watermark-overlay
```

```tsx
import { Watermark } from "react-watermark-overlay";

<Watermark text="STAGING" type="overlay" />;
```

## Repository layout

| Folder                     | Description                                                    |
| -------------------------- | ------------------------------------------------------------- |
| [`package/`](./package)    | The published npm component — see its [README](./package/README.md) for the full API. |
| [`example/`](./example)    | A Vite demo app that powers the live documentation site.      |

## Local development

```bash
# build the package
cd package && npm install && npm run build

# run the demo app
cd example && npm install && npm run dev
```

## License

[MIT](./LICENSE) © jjh2613
