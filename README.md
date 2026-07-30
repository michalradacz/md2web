# md2web

**md2web** is a mini CMS system that generates a beautifully designed, fully functional website from a single Markdown file. Write your content in one `.md` file, and md2web takes care of everything else — multi-page structure, navigation, sidebar, themes, and more.

---

## Table of Contents

- [Features](#features)
- [Getting Started](#getting-started)
- [Writing Your Content](#writing-your-content)
  - [Multiple Pages from Sections](#multiple-pages-from-sections)
  - [Two-Level Navigation](#two-level-navigation)
  - [Sidebar](#sidebar)
  - [Internal Links](#internal-links)
  - [Critic Markup — Revision Tracking](#critic-markup--revision-tracking)
- [Advanced Configuration](#advanced-configuration)
- [Multi-Language Support](#multi-language-support)
- [Color Themes](#color-themes)
- [License](#license)

---

## Features

| Feature | Description |
|---|---|
| 📄 **Single Markdown Source** | Your entire website lives in one `.md` file |
| 📑 **Multiple Pages** | Top-level `#` headings automatically become separate pages |
| 🗂️ **Two-Level Navigation** | First and second-level headings form a two-tier navigation menu |
| 🗃️ **Sidebar** | Optional sidebar automatically generated from your content |
| 🔗 **Internal Links** | Link between sections and pages using standard Markdown link syntax |
| ✏️ **Critic Markup** | Visual revision tracking — additions, deletions, and comments rendered inline |
| ⚙️ **Advanced Configuration** | Fine-grained control over site title, layout, metadata, and more |
| 🌍 **Multi-Language** | Built-in i18n support with the ability to add custom translations |
| 🎨 **Color Themes** | Multiple built-in color schemes; easily switch or create your own |

---

## Getting Started

### Requirements

- A web server (Apache, Nginx, or any static file host) **or** just open the file locally in a browser
- No build step, no Node.js, no dependencies to install

### Installation

1. Clone or download this repository:

   ```bash
   git clone https://github.com/michalradacz/md2web.git
   cd md2web
   ```

2. Place your Markdown content file (e.g. `content.md`) in the project root.

3. Open `index.html` in a browser, or deploy the folder to any web host.

---

## Writing Your Content

Everything you need to create a complete website is written inside **a single Markdown file**. md2web reads this file and transforms it into a multi-page, navigable website automatically.

### Multiple Pages from Sections

Each **top-level heading** (`# Heading`) in your Markdown file becomes a **separate page** on the website. Visitors can navigate between pages using the automatically generated navigation menu.

```markdown
# Home

Welcome to my website!

# About

Learn more about us here.

# Contact

Get in touch with us.
```

This example produces three pages: *Home*, *About*, and *Contact*.

### Two-Level Navigation

md2web builds a **two-level navigation menu** automatically:

- **Level 1** — top-level headings (`#`) become the primary navigation items (pages)
- **Level 2** — second-level headings (`##`) within each page become sub-navigation items (sections within a page)

```markdown
# Products

## Software

Our software lineup.

## Hardware

Our hardware lineup.

# Support

## FAQ

Frequently asked questions.

## Contact

How to reach us.
```

The navigation will render *Products* and *Support* as top-level items, each with their own dropdown or sub-menu.

### Sidebar

You can enable an **optional sidebar** that is automatically populated with content from your Markdown file. The sidebar is configurable — you can control which sections appear in it and what it displays (e.g. a table of contents, quick links, or supplementary information).

To include sidebar content, use the designated sidebar section or configuration option (see [Advanced Configuration](#advanced-configuration)).

### Internal Links

You can link to **any heading** on any page using standard Markdown anchor syntax. md2web resolves these links automatically so that they point to the correct page and scroll position, even after the document is split into multiple pages.

```markdown
For more details see [our FAQ](#faq) or the [contact page](#contact).
```

Internal links work across pages — md2web handles the routing so the reader lands on the right page.

### Critic Markup — Revision Tracking

md2web supports **[Critic Markup](http://criticmarkup.com/)**, a lightweight syntax for tracking revisions directly in Markdown. This lets you display additions, deletions, substitutions, highlights, and comments inline on the rendered page.

| Syntax | Meaning |
|---|---|
| `{++ inserted text ++}` | Addition |
| `{-- deleted text --}` | Deletion |
| `{~~ old ~> new ~~}` | Substitution |
| `{== highlighted text ==}` | Highlight |
| `{>> comment <<}` | Comment / annotation |

**Example:**

```markdown
The price is {--$10--}{++$8++} per unit.
Please {==review this section==}{>>needs fact-checking<<}.
```

Rendered output shows the revision visually, making it easy to review changes in documentation or content drafts directly on the web.

---

## Advanced Configuration

md2web supports a **YAML front matter** block at the top of your Markdown file for site-wide and per-page configuration.

```yaml
---
title: My Awesome Site
description: A website built with md2web
language: en
theme: ocean
sidebar: true
author: Jane Doe
---
```

### Configuration Options

| Key | Type | Default | Description |
|---|---|---|---|
| `title` | string | File name | The website title shown in the browser tab and header |
| `description` | string | — | Meta description used for SEO |
| `language` | string | `en` | Interface language code (see [Multi-Language Support](#multi-language-support)) |
| `theme` | string | `default` | Color theme name (see [Color Themes](#color-themes)) |
| `sidebar` | boolean | `false` | Enable or disable the sidebar |
| `author` | string | — | Author name shown in the page footer |
| `nav_depth` | integer | `2` | How many heading levels to include in navigation (1 or 2) |
| `toc` | boolean | `true` | Show or hide the table of contents in the sidebar |
| `date_format` | string | `YYYY-MM-DD` | Date format used throughout the site |

### Per-Page Configuration

You can also set configuration for individual pages by placing a YAML block immediately after the page's `#` heading:

```markdown
# Release Notes

---
sidebar: false
toc: false
---

Content of the release notes page…
```

---

## Multi-Language Support

md2web ships with built-in translations for the site interface (navigation labels, buttons, metadata labels, etc.). The language is set via the `language` key in your front matter.

### Built-In Languages

| Code | Language |
|---|---|
| `en` | English |
| `cs` | Czech |
| `de` | German |
| `fr` | French |
| `sk` | Slovak |

### Custom Translations

To add your own language or override any existing translation string, create a translation file in the `lang/` directory:

```
lang/
├── en.json
├── cs.json
└── my-lang.json   ← your custom language
```

**Format of a translation file** (`lang/my-lang.json`):

```json
{
  "nav.home": "Home",
  "nav.top": "Back to top",
  "search.placeholder": "Search…",
  "toc.title": "Contents",
  "footer.generated": "Generated with md2web",
  "revision.added": "Added",
  "revision.removed": "Removed",
  "revision.comment": "Comment"
}
```

Then reference your language in the front matter:

```yaml
---
language: my-lang
---
```

---

## Color Themes

md2web comes with several built-in color themes. Set the active theme in your front matter using the `theme` key.

### Built-In Themes

| Theme name | Description |
|---|---|
| `default` | Clean light theme with neutral gray tones |
| `ocean` | Blue-green palette inspired by the sea |
| `forest` | Dark greens and earthy tones |
| `sunset` | Warm oranges and reds |
| `night` | Dark mode with deep navy background |
| `minimal` | Pure white with minimal styling |
| `paper` | Beige/sepia tones resembling printed paper |

### Custom Themes

To create your own theme, add a CSS file to the `themes/` directory:

```
themes/
├── default.css
├── ocean.css
└── my-theme.css   ← your custom theme
```

A theme file overrides CSS custom properties:

```css
/* themes/my-theme.css */
:root {
  --color-bg: #fdf6e3;
  --color-text: #333;
  --color-primary: #268bd2;
  --color-secondary: #2aa198;
  --color-accent: #cb4b16;
  --color-nav-bg: #eee8d5;
  --color-nav-text: #657b83;
  --color-sidebar-bg: #fdf6e3;
  --color-code-bg: #eee8d5;
}
```

Then reference it in your front matter:

```yaml
---
theme: my-theme
---
```

---

## License

This project is licensed under the [GNU General Public License v3.0](LICENSE).

---

*Generated with ❤️ using md2web — the single-file Markdown CMS.*
