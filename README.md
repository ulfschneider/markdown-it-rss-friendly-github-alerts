# markdown-it-rss-friendly-github-alerts

This plugin is forked from [markdown-it-github-alerts](https://github.com/antfu/markdown-it-github-alerts) by Anthony Fu.

My fork is addressing the following issues: In case your content is delivered through a RSS feed (it should) where you do not have control about the styling, the formatting is not ideal. E.g. there is no space between the icon and the title, the color of the icon does not adapt to the text color, and the rendering as a `div` might not help for reading, a `blockquote` would be better in my view for this case.

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
  <p class="markdown-alert-title" style="display: flex; align-items: center;">
    <svg class="octicon octicon-info" fill="currentColor" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="M0 8a8 8 0 1 1 16 0A8 8 0 0 1 0 8Zm8-6.5a6.5 6.5 0 1 0 0 13 6.5 6.5 0 0 0 0-13ZM6.5 7.75A.75.75 0 0 1 7.25 7h1a.75.75 0 0 1 .75.75v2.75h.25a.75.75 0 0 1 0 1.5h-2a.75.75 0 0 1 0-1.5h.25v-2h-.25a.75.75 0 0 1-.75-.75ZM8 6a1 1 0 1 1 0-2 1 1 0 0 1 0 2Z"></path></svg>&nbsp;Note</p>
  <p>Highlights information that users should take into account, even when skimming.</p>
</blockquote>
```

>[!IMPORTANT]
>This output is *not* identical with GitHub's output, because the alert is rendered as a `blockquote` and not as a `div`.
>There is also an `&nbsp;` between the svg icon the marker text and svg has the setting `fill="currentColor`, which GitHub wouldn´t render.

### Styling

You can write custom styles for your alerts, and there is some CSS extracted from GitHub's styles for you to use.

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
