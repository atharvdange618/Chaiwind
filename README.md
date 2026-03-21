# chaiwindjs

[![npm](https://img.shields.io/npm/v/chaiwindjs)](https://www.npmjs.com/package/chaiwindjs)

A runtime CSS utility engine - apply Tailwind-style `chai-*` class names as inline styles, with **no build step, no stylesheet, and no configuration**.

Just drop in the script, add classes, done.

---

## Installation

```bash
npm install chaiwindjs
```

Or via CDN:

```html
<script src="https://cdn.jsdelivr.net/npm/chaiwindjs/chai-wind.js"></script>
```

---

## Usage

### CDN / Script tag

```html
<script src="https://cdn.jsdelivr.net/npm/chaiwindjs/chai-wind.js"></script>
<script>
  ChaiWind.init();
</script>
```

### ES Module / bundler

```js
import ChaiWind from "chaiwindjs";
// or: const ChaiWind = require("chaiwindjs");

ChaiWind.init();
```

Then use classes directly in your HTML:

```html
<div
  class="chai-flex chai-items-center chai-gap-4 chai-p-4 chai-bg-white chai-rounded-lg chai-shadow-md"
>
  <p class="chai-text-lg chai-font-semibold chai-text-ink">Hello, ChaiWind!</p>
</div>
```

---

## API

### `ChaiWind.init(options?)`

Scans the DOM, applies all matching `chai-*` classes as inline styles, and starts watching for future DOM changes.

```js
ChaiWind.init();

// With options:
ChaiWind.init({
  debug: true, // logs matches to the console (default: false)
  styles: {
    // extend with custom classes at init time
    "my-card": "border-radius: 12px; padding: 24px; background: #fff",
  },
});
```

### `ChaiWind.register(styles)`

Register additional custom classes at any time after init. Immediately applied to any matching elements already in the DOM.

```js
ChaiWind.register({
  "my-badge":
    "font-size: 12px; background: #f97316; color: #fff; padding: 2px 8px; border-radius: 9999px",
  "my-card": "border-radius: 12px; padding: 24px; background: #fff",
});
```

### `ChaiWind.refresh()`

Re-scans the entire DOM. Useful after surgically modifying HTML outside of React/Vue reactivity.

```js
ChaiWind.refresh();
```

### `ChaiWind.listClasses()`

Prints all registered classes and their styles to the console as a table. Great for debugging.

```js
ChaiWind.listClasses();
```

---

## Built-in Classes

| Category     | Examples                                                                                |
| ------------ | --------------------------------------------------------------------------------------- |
| Spacing      | `chai-p-2`, `chai-px-4`, `chai-m-4`, `chai-mx-auto`                                     |
| Sizing       | `chai-w-full`, `chai-h-screen`, `chai-max-w-xl`                                         |
| Typography   | `chai-text-lg`, `chai-font-bold`, `chai-uppercase`, `chai-text-center`                  |
| Colors       | `chai-text-orange`, `chai-bg-dark`, `chai-text-white`                                   |
| Flexbox      | `chai-flex`, `chai-flex-col`, `chai-items-center`, `chai-justify-between`, `chai-gap-4` |
| Borders      | `chai-border`, `chai-rounded-lg`, `chai-rounded-full`                                   |
| Shadows      | `chai-shadow`, `chai-shadow-md`, `chai-shadow-lg`                                       |
| Display      | `chai-block`, `chai-hidden`, `chai-overflow-hidden`                                     |
| Position     | `chai-relative`, `chai-absolute`, `chai-fixed`                                          |
| Effects      | `chai-transition`, `chai-opacity-50`, `chai-cursor-pointer`                             |
| Neobrutalist | `chai-neo-shadow`, `chai-border-neo`, `chai-bg-cream`, `chai-bg-ink`                    |

---

## License

[MIT](LICENSE)
