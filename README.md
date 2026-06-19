# dpsalvatierra.github.io

Personal GitHub Pages site for Daniel Salvatierra, built with [Jekyll](https://jekyllrb.com/) and a customized dark, Midnight-based theme.

The homepage is **front-matter driven**: the content lives as variables in [`index.md`](index.md), the structure lives in [`_layouts/default.html`](_layouts/default.html), and the look lives in [`assets/css/style.scss`](assets/css/style.scss). Editing content rarely requires touching HTML or CSS.

## Project structure

| Path | What it controls |
| --- | --- |
| [`index.md`](index.md) | All homepage text/content (front matter variables). **Edit this for most updates.** |
| [`_layouts/default.html`](_layouts/default.html) | Page structure and where each front matter variable is rendered. |
| [`assets/css/style.scss`](assets/css/style.scss) | Styling, colors, and responsive layout. |
| [`assets/img/`](assets/img/) | Images: `logo.png` (brand/favicon) and `console-lab.png` (hero background). |
| [`_config.yml`](_config.yml) | Site title, URL, theme, and plugins. |
| `_site/` | Generated build output — **do not edit**, ignored by Git. |

## Local development

```bash
bundle install
bundle exec jekyll serve
```

Then open <http://localhost:4000/>. With the server running, saved changes rebuild automatically — refresh the browser to see them.

### First-time setup (Ubuntu)

```bash
sudo apt update
sudo apt install ruby-full build-essential zlib1g-dev
echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
gem install bundler
cd /path/to/your/jekyll-site
bundle install
bundle exec jekyll serve
```

### First-time setup (PowerShell)

```powershell
gem install bundler
cd C:\path\to\your\jekyll-site
bundle install
bundle exec jekyll serve
```

## Updating the site content

Almost every content change is made by editing the front matter at the top of [`index.md`](index.md) (everything between the two `---` lines). After editing, save and refresh the local preview to confirm.

| To change... | Edit this front matter key in `index.md` |
| --- | --- |
| Page/browser title | `title` |
| Hero eyebrow line | `eyebrow` |
| Hero headline | `headline` |
| Hero intro paragraph | `intro` |
| Main GitHub button link | `github_url` |
| Site repository link | `repo_url` |
| Brand/logo image | `logo_path` |
| Creative brand name & pitch | `creative_brand`, `creative_brand_pitch` |
| Social/media buttons | `media_links` (list of `label` + `url`) |
| "What I do" story blocks | `story_sections` (list of `title` + `body`) |
| "What I build" focus cards | `focus_areas` (list of `title` + `description`) |
| Selected work entries | `selected_work` (list of `title`, `description`, `tags`) |
| Principles list | `principles` (list of strings) |
| Topics list | `site_topics` (list of strings) |

### Adding or removing list items

Lists (e.g. `focus_areas`, `selected_work`, `media_links`) render automatically — add or delete an item and the layout updates. Keep the indentation consistent with the existing entries. Example:

```yaml
focus_areas:
  - title: New Focus Area
    description: A short description of this focus area.
```

### Changing images

Replace the files in [`assets/img/`](assets/img/) (keep the same filenames), or add a new image and update the matching path (`logo_path` in `index.md`, or the `background-image` for the hero in `assets/css/style.scss`).

### Adding a new section

1. Add the content as a new front matter variable (or list) in [`index.md`](index.md).
2. Render it by adding a matching `<section>` and Liquid markup in [`_layouts/default.html`](_layouts/default.html).
3. If it should appear in the top navigation, add an anchor link in the `<nav>` of the layout that matches the new section's `id`.

## Styling notes

- The theme is dark and Midnight-based. Reuse the existing CSS variables (`--bg`, `--text`, `--gold`, `--teal`, `--rust`, etc.) defined at the top of [`assets/css/style.scss`](assets/css/style.scss) instead of hardcoding new colors.
- The layout is responsive with breakpoints at 1080px, 820px, and 520px.
- `assets/css/style.scss` **must** keep the empty Jekyll front matter (the two `---` lines at the very top) so the theme `@import` is processed.
- **Theme gotcha:** `jekyll-theme-midnight` applies `section { max-width: 650px }` to every `<section>`. Because this layout's blocks are all `<section>` elements, the stylesheet includes a `main > section { max-width: none; ... }` reset right after the `@import`. Do not remove it, or the hero and content will collapse into a narrow 650px column.

## Publishing changes

The site is hosted on GitHub Pages, which rebuilds automatically on every push to the `main` branch:

```bash
git add .
git commit -m "Update site content"
git push origin main
```

Wait a moment for GitHub Pages to build, then check the live site. Build artifacts (`_site/`, caches, local bundler folders) are excluded via [`.gitignore`](.gitignore) and should never be committed.

## Configuration

Site-wide settings (title, description, URL, theme, plugins) live in [`_config.yml`](_config.yml). Note that changes to `_config.yml` require restarting `bundle exec jekyll serve` to take effect locally.
