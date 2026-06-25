# sevenlee-claude-code-plugins

A collection of Claude Code plugins providing language server integrations and development tools.

## Plugins

| Plugin | Description | Version |
|--------|-------------|---------|
| [mpx-lsp](./mpx-lsp) | Mpx language server integration for `.mpx` files | 0.1.0 |

## Installation

Install the required language server before installing the Claude Code plugin:

```bash
npm install -g @mpxjs/language-server
which mpx-language-server
```

The `mpx-lsp` plugin starts the `mpx-language-server` executable from your
`PATH`, so the second command must print a path. If it does not, make sure your
npm global binary directory is included in `PATH`.

Then make Claude Code aware of this marketplace:

1. Run `claude`
2. `/plugin marketplace add https://github.com/lidongsevenlee/sevenlee-claude-code-plugins`

Enable the plugins of your choice:

1. Run `claude`
2. Type `/plugins`
3. Tab to `Marketplaces`
4. Enter the `sevenlee-claude-code-plugins` marketplace and choose `Browse plugins`
5. Select the plugins you'd like with the spacebar (e.g. mpx-lsp)
6. Press "i" to install them
7. Restart Claude Code

After restarting, open a project that contains `.mpx` files. Claude Code should
start `mpx-language-server` automatically for those files.

## mpx-lsp

Provides intelligent language features for [Mpx.js](https://github.com/didi/mpx) single-file components in Claude Code.

### Features

- Diagnostics and type checking for `.mpx` files
- TypeScript/JavaScript intellisense
- Go-to-definition, find references, hover
- Auto-completions and code actions

### Requirements

- `@mpxjs/language-server` installed globally, which provides the
  `mpx-language-server` command
- `mpx-language-server` available in `PATH`
- TypeScript available in your project at `node_modules/typescript/lib`

### Plugin Configuration Reference

The following configuration is bundled inside the `mpx-lsp` plugin. Users do
not need to create or copy this file during installation; it is shown here only
for maintainers and troubleshooting.

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

### Troubleshooting

- `mpx-language-server: command not found`: install
  `@mpxjs/language-server` globally and verify `which mpx-language-server`
  prints a path.
- The plugin is installed but `.mpx` files do not get language features:
  restart Claude Code and reopen the project.
- TypeScript-related errors: run `npm install` in the Mpx project so local
  dependencies, including TypeScript, are available.

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
