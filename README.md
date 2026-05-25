# sevenlee-claude-code-plugins

A collection of Claude Code plugins providing language server integrations and development tools.

## Plugins

| Plugin | Description | Version |
|--------|-------------|---------|
| [mpx-lsp](./mpx-lsp) | Mpx language server integration for `.mpx` files | 0.1.0 |

## Installation

Install them the usual way.  First make CC aware of the marketplace:
1. Run `claude`
2. `/plugin marketplace add https://github.com/lidongsevenlee/sevenlee-claude-code-plugins`

Then enable the plugins of your choice:
1. Run `claude`
2. Type `/plugins`
3. Tab to `Marketplaces`
4. Enter the `sevenlee-claude-code-plugins` marketplace and choose `Browse plugins`
5. Select the plugins you'd like with the spacebar (e.g. mpx-lsp)
6. Press "i" to install them
7. Restart Claude Code

## mpx-lsp

Provides intelligent language features for [Mpx.js](https://github.com/didi/mpx) single-file components in Claude Code.

### Features

- Diagnostics and type checking for `.mpx` files
- TypeScript/JavaScript intellisense
- Go-to-definition, find references, hover
- Auto-completions and code actions

### Requirements

- `mpx-language-server` installed and available in PATH
- TypeScript available in `node_modules/typescript/lib`

### Configuration

Default settings in `.lsp.json`:

```json
{
  "mpx": {
    "command": "mpx-language-server",
    "args": ["--stdio"],
    "transport": "stdio",
    "extensionToLanguage": { ".mpx": "mpx" },
    "maxRestarts": 3
  }
}
```

## Contributing

To add a new plugin, create a directory with its `.lsp.json` config and register it in `.claude-plugin/marketplace.json`.

## License

MIT

## Author

lidongsevenlee (lidongsevenlee@gmail.com)

## Related

- [Mpx.js](https://github.com/didi/mpx)
- [Mpx Language Tools](https://github.com/mpx-ecology/language-tools)
- [Claude Code Documentation](https://docs.anthropic.com/en/docs/claude-code)
