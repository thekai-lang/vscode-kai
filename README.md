# Kai Language Support

A [VS Code](https://code.visualstudio.com/) extension for the [Kai](https://github.com/thekai-lang) programming language — a complete language extension whose TextMate grammar mirrors the [tree-sitter-kai](https://github.com/thekai-lang/tree-sitter-kai) grammar (`grammar.js`) and its highlight queries:

| Contribution | File | What it does |
|---|---|---|
| `languages` | `package.json` | Registers the `kai` language: `.kai` extension, aliases, and a language icon so files get the Kai icon **automatically** |
| `grammars` | `syntaxes/kai.tmLanguage.json` | TextMate grammar (`source.kai`) — syntax highlighting |
| `languages[].configuration` | `language-configuration.json` | Comment toggling (`//`), bracket matching, auto-closing pairs |
| `iconThemes` | `icon-theme.json` | Optional **Kai File Icons** theme (`workbench.iconTheme` = `kai-icons`) |

```
icons/kai.svg              File icon (16×16, ocean-blue wave)
syntaxes/kai.tmLanguage.json  TextMate grammar
language-configuration.json   Brackets / comments / auto-closing
icon-theme.json            File icon theme definition
package.json               Extension manifest
```

## Install

No `node_modules` setup is required — this is a static extension.

### Option A — Install the extension folder (simplest)

1. Copy this folder to your extensions directory:
   - Linux: `~/.vscode/extensions/kai-lang.kai/`
   - macOS: `~/.vscode/extensions/kai-lang.kai/`
   - Windows: `%USERPROFILE%\.vscode\extensions\kai-lang.kai\`
2. Reload VS Code (`Developer: Reload Window`).

### Option B — Package as `.vsix`

```sh
npm install -g @vscode/vsce
# run from this folder:
vsce package
# → kai-0.1.0.vsix
```

Then install via the Extensions view → `...` → `Install from VSIX...`.

### Option C — Development (F5)

Open this folder in VS Code and press `F5` to launch an Extension Development Host.

## What to expect

- `.kai` files open as the **Kai** language with syntax highlighting.
- The Kai file icon shows automatically (via `languages[].icon`).
- The dedicated icon theme is optional — select **Kai File Icons** for `workbench.iconTheme`, or add `"workbench.iconTheme": "kai-icons"` to `settings.json`.

> Note: file icon themes take precedence over `languages[].icon`, so if the active theme defines its own `.kai` icon, it wins.

## Known outstanding work

- **Language configuration** is minimal; add more `autoClosingPairs`/`surroundingPairs` as the language stabilizes.
- **Semantic highlighting** — a future LSP/resolver can feed semantic tokens on top of the TextMate layer.
- This TextMate grammar is hand-written to match the [tree-sitter-kai](https://github.com/thekai-lang/tree-sitter-kai) grammar; keep it in sync whenever `grammar.js` changes (validate with `tree-sitter test` upstream).

## Requirements

- VS Code >= 1.75.0.