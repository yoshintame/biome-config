# @yoshintame/biome-config

Personal shared [Biome](https://biomejs.dev) configuration.

## Install

```sh
bun add -D -E @yoshintame/biome-config @biomejs/biome
```

Requires `@biomejs/biome ^2.0.0`.

## Usage

Reference a preset via `extends` in your `biome.json`:

### Base (Node / generic TS)

```json
{
  "$schema": "https://biomejs.dev/schemas/2.4.12/schema.json",
  "extends": ["@yoshintame/biome-config/base"]
}
```

### React / Tailwind

```json
{
  "$schema": "https://biomejs.dev/schemas/2.4.12/schema.json",
  "extends": ["@yoshintame/biome-config/react"]
}
```

Includes `base` + `useSelfClosingElements` + `useSortedClasses` (for `cn`, `clsx`, `cva`, `tw`).

### FSD (Feature-Sliced Design)

Composable — add on top of `react` or `base`:

```json
{
  "$schema": "https://biomejs.dev/schemas/2.4.12/schema.json",
  "extends": [
    "@yoshintame/biome-config/react",
    "@yoshintame/biome-config/fsd"
  ]
}
```

Overrides `organizeImports.groups` to add a dedicated `@/shared/**` block.

## Presets

| Preset | Purpose |
| --- | --- |
| `/base` | Formatter (space, single quotes, no semi), strict style rules, kebab-case filenames, tsconfig comments allowed, generic `organizeImports` groups |
| `/react` | Extends `/base`, adds JSX/Tailwind rules |
| `/fsd` | Overrides `organizeImports` with an `@/shared/**` group |

## Overrides

Local `biome.json` always wins. Downgrade or disable rules per project:

```json
{
  "extends": ["@yoshintame/biome-config/react"],
  "linter": {
    "rules": {
      "a11y": { "useKeyWithClickEvents": "warn" },
      "style": { "noNonNullAssertion": "off" }
    }
  }
}
```

## License

MIT
