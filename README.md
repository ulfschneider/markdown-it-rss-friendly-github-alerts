# markdown-it-rss-friendly-github-alerts

This plugin is forked from [markdown-it-github-alerts](https://github.com/antfu/markdown-it-github-alerts) by Anthony Fu.

[![npm version][npm-version-src]][npm-version-href]
[![npm downloads][npm-downloads-src]][npm-downloads-href]
[![bundle][bundle-src]][bundle-href]
[![JSDocs][jsdocs-src]][jsdocs-href]
[![License][license-src]][license-href]

Support [GitHub-style alerts](https://github.com/orgs/community/discussions/16925) for [markdown-it](https://github.com/markdown-it/markdown-it).

> [!NOTE]
> Highlights information that users should take into account, even when skimming.

> [!TIP]
> Optional information to help a user be more successful.

> [!IMPORTANT]
> Crucial information necessary for users to succeed.

> [!WARNING]
> Critical content demanding immediate user attention due to potential risks.

> [!CAUTION]
> Negative potential consequences of an action.

```
> [!NOTE]
> Highlights information that users should take into account, even when skimming.

> [!TIP]
> Optional information to help a user be more successful.

> [!IMPORTANT]
> Crucial information necessary for users to succeed.

> [!WARNING]
> Critical content demanding immediate user attention due to potential risks.

> [!CAUTION]
> Negative potential consequences of an action.
```

## Usage

```bash
npm i markdown-it-rss-friendly-github-alerts
```

```js
import MarkdownIt from 'markdown-it'
import MarkdownItRSSFriendlyGitHubAlerts from 'markdown-it-rss-friendly-github-alerts'

const md = MarkdownIt()

md.use(MarkdownItRSSFriendlyGitHubAlerts, /* Options */)

const html = md.render(/* ... */)
```

For the options available, please refer to [the jsdoc](./src/index.ts).

## Functionality

This plugin transforms the following markdown:

```markdown
> [!NOTE]
> Highlights information that users should take into account, even when skimming.
```

to the following HTML:

```html
<blockquote class="markdown-alert markdown-alert-note">
  <p class="markdown-alert-title" dir="auto"><!-- svg icon-->&nbsp;Note</p><p>
  Highlights information that users should take into account, even when skimming.</p>
</blockquote>
```

>[!IMPORTANT]
>This output is *not* identical with GitHub's output, because the alert is rendered as a `<blockquote>` and not as a `<div>`. GitHub will render as a `<div>`!
>There is also an `&nbsp;` between the svg icon the marker text, which GitHub wouldn´t render.

### Styling

You can write your custom styles for your alerts.

We also provide some CSS extracted from GitHub's styles for you to use.

```js
import 'markdown-it-rss-friendly-github-alerts/styles/github-colors-light.css'
import 'markdown-it-rss-friendly-github-alerts/styles/github-colors-dark-media.css'
import 'markdown-it-rss-friendly-github-alerts/styles/github-base.css'
```

You might change `github-colors-dark-media.css` to `github-colors-dark-class.css` if you are using class-based (`.dark`) dark mode.

Refer to the [source code](./styles) for more details.

### Customization

In order to also support [Obsidian callouts syntax](https://help.obsidian.md/Editing+and+formatting/Callouts) it is possible to allow any type of markers with the following setting:

```js
md.use(MarkdownItRSSFriendlyGitHubAlerts, {
  markers: '*'
})
```
Alternative titles are also supported, by appending it to the marker like this:

```markdown
> [!note] Nota bene
> The custom title will replace the regular title.
```

## License

[MIT](./LICENSE) License

<!-- Badges -->

[npm-version-src]: https://img.shields.io/npm/v/markdown-it-rss-friendly-github-alerts?style=flat&colorA=080f12&colorB=1fa669
[npm-version-href]: https://npmjs.com/package/markdown-it-rss-friendly-github-alerts
[npm-downloads-src]: https://img.shields.io/npm/dm/markdown-it-rss-friendly-github-alerts?style=flat&colorA=080f12&colorB=1fa669
[npm-downloads-href]: https://npmjs.com/package/markdown-it-rss-friendly-github-alerts
[bundle-src]: https://img.shields.io/bundlephobia/minzip/markdown-it-rss-friendly-github-alerts?style=flat&colorA=080f12&colorB=1fa669&label=minzip
[bundle-href]: https://bundlephobia.com/result?p=markdown-it-rss-friendly-github-alerts
[license-src]: https://img.shields.io/github/license/antfu/markdown-it-github-alerts.svg?style=flat&colorA=080f12&colorB=1fa669
[license-href]: https://github.com/antfu/markdown-it-github-alerts/blob/main/LICENSE
[jsdocs-src]: https://img.shields.io/badge/jsdocs-reference-080f12?style=flat&colorA=080f12&colorB=1fa669
[jsdocs-href]: https://www.jsdocs.io/package/markdown-it-rss-friendly-github-alerts
