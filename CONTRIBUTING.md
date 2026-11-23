# Contributing a Theme to massCode

Thank you for contributing a theme to the massCode community!

## How to Submit a Theme

1. Fork this repository.
2. Add your theme JSON file to `themes/<your-theme-id>.json`.
   - Use **kebab-case** for the filename (`a-z`, `0-9`, `-`), e.g. `tokyo-night.json`.
   - Reserved IDs (`light`, `dark`, `auto`) are not allowed.
3. Test your theme locally in massCode by placing it in `~/.massCode/themes/`.
4. Run validation locally:
   ```bash
   node scripts/build-registry.mjs --check
   ```
5. Open a Pull Request. Do **not** edit `registry.json` — GitHub Actions will automatically regenerate it after merge.

## Theme JSON Format

```json
{
  "name": "My Theme",
  "author": "your-handle",
  "authorUrl": "https://github.com/your-handle",
  "type": "dark",
  "colors": {
    "primary": "hsl(220, 90%, 66%)",
    "primary-foreground": "hsl(0, 0%, 100%)",
    "background": "hsl(232, 23%, 14%)",
    "foreground": "hsl(227, 68%, 88%)",
    "accent": "hsl(234, 22%, 22%)",
    "accent-hover": "hsl(234, 22%, 26%)",
    "accent-foreground": "hsl(227, 68%, 88%)",
    "muted": "hsl(233, 22%, 19%)",
    "muted-foreground": "hsl(228, 24%, 56%)",
    "card": "hsl(233, 24%, 17%)",
    "popover": "hsl(233, 24%, 17%)",
    "popover-foreground": "hsl(227, 68%, 88%)",
    "border": "hsl(233, 22%, 24%)",
    "scrollbar": "hsla(228, 24%, 56%, 0.35)"
  },
  "editorColors": {
    "editor-keyword": "hsl(267, 84%, 81%)",
    "editor-string": "hsl(115, 54%, 76%)",
    "editor-comment": "hsl(228, 24%, 50%)",
    "editor-number": "hsl(23, 92%, 75%)",
    "editor-atom": "hsl(23, 92%, 75%)",
    "editor-variable": "hsl(227, 68%, 88%)",
    "editor-def": "hsl(217, 92%, 76%)",
    "editor-property": "hsl(189, 71%, 73%)",
    "editor-tag": "hsl(343, 81%, 75%)",
    "editor-attribute": "hsl(217, 92%, 76%)",
    "editor-operator": "hsl(189, 71%, 73%)",
    "editor-bracket": "hsl(228, 24%, 64%)"
  }
}
```

## Validation Rules

- Required fields: `name`, `type` (`"light"` or `"dark"`), `colors` (minimum: `background`, `foreground`, `primary`, `card`, `border`).
- Optional fields: `author`, `authorUrl` (`https://github.com/...`), `editorColors` (keys must start with `editor-`).
- Supported CSS color formats: `#hex`, `rgb(...)`, `rgba(...)`, `hsl(...)`, `hsla(...)`, `oklch(...)`.
- Legacy `color-*` tokens (such as `color-bg`, `color-primary`) are not allowed.
