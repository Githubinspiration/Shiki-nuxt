# nuxt-shiki

<!-- automd:badges -->

[![npm version](https://flat.badgen.net/npm/v/nuxt-shiki)](https://npmjs.com/package/nuxt-shiki)
[![npm downloads](https://flat.badgen.net/npm/dm/nuxt-shiki)](https://npmjs.com/package/nuxt-shiki)

<!-- /automd -->

[Nuxt](https://nuxt.com/) + [Shiki](https://shiki.style/) syntax highlighter!

## Features

- Configurable themes and languages
- Full lazy loading
- Optimized integration with shiki/core

> [!IMPORTANT]
> This module is under development!

## Quick Setup

Add Nuxt module:

```bash
npx nuxi module add nuxt-shiki
```

That's it! You can now use nuxt-shiki in your Nuxt app ✨

## Options

Options can be configured using `shiki` key in `nuxt.config`:

```js
export default defineNuxtConfig({
  modules: ["nuxt-shiki"],
  shiki: {
    theme: "github-light",
    lang: "javascript",
    themes: [],
    langs: [],
  },
});
```

- `themes` and `langs` can be configured to set bundled themes and languages.
- `theme` and `lang` can be configured to set default theme and language.

**Tip:** You can access configurations and defaults in runtime using `shiki.$config` and `shiki.$defaults`.

## Utils

<!-- automd:jsdocs src=./src/runtime/index -->

### `loadShiki()`

Lazy-load shiki instance.

You can use this utility both in `server/` and vue app code.

**Example:**

```vue
<script setup>
const shiki = await loadShiki();
const html = shiki.codeToHtml('const hello = "shiki";', {
  ...$shiki.$defaults,
  lang: "javascript",
});
</script>
```

**Example:**

```ts
// server/api/highlight.ts

export default defineEventHandler(async (event) => {
  const shiki = await loadShiki();
  return shiki.codeToHtml('const hello = "shiki"', { ...$shiki.$defaults });
});
```

### `useHighlighted(code, options)`

Return a lazy highlighted code ref (only usable in Vue)

**Example:**

```vue
const code = ref('const hello = "shiki";');
const highlighted = useHighlighted(code);
</script>
```


<!-- /automd -->

## Development

```bash
# Install dependencies
npm install

# Generate type stubs
npm run dev:prepare

# Develop with the playground
npm run dev

# Build the playground
npm run dev:build

# Run ESLint
npm run lint

# Run Vitest
npm run test
npm run test:watch

# Release new version
npm run release
```
