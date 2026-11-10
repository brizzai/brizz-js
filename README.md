# brizz-js

Release notes for the [Brizz](https://brizz.ai) JavaScript SDKs:

| Package | For | Changelog |
|---|---|---|
| [`@brizz/sdk`](https://www.npmjs.com/package/@brizz/sdk) | Node.js / TypeScript agents | [typescript/CHANGELOG.md](./typescript/CHANGELOG.md) |
| [`@brizz/browser`](https://www.npmjs.com/package/@brizz/browser) | Product events from a web frontend | [browser/CHANGELOG.md](./browser/CHANGELOG.md) |

`typescript/CHANGELOG.md` covers the newest `@brizz/sdk` line (npm tag `latest`). An older line that still gets releases has its own file, `typescript/CHANGELOG-<line>.md`, installed with the npm tag `latest-<line>`: for example [typescript/CHANGELOG-0.1.md](./typescript/CHANGELOG-0.1.md) for `@brizz/sdk@latest-0.1`.

`@brizz/sdk` traces your AI agent — every conversation, LLM call and tool call — and `@brizz/browser` adds product events from your frontend. Both send to Brizz, the product analytics layer for AI agents.

This repo holds the changelogs and a [GitHub release](https://github.com/brizzai/brizz-js/releases) per published version (`sdk-v<version>` for `@brizz/sdk`, `browser-v<version>` for `@brizz/browser`). The SDK source is not published here.

## Install

```bash
npm install @brizz/sdk        # Node.js
npm install @brizz/browser    # browser
```

Full setup: the READMEs on npm, [`@brizz/sdk`](https://www.npmjs.com/package/@brizz/sdk) and [`@brizz/browser`](https://www.npmjs.com/package/@brizz/browser).

## Reporting issues

https://github.com/brizzai/brizz-js/issues

## License

The contents of this repository are Apache-2.0 licensed; see [LICENSE](./LICENSE). The packages on npm are distributed under the license stated in their metadata.
