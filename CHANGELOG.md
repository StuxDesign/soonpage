# Changelog

All notable changes to Soonpage are documented here.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Date Versioning](https://datevers.ing) since v26.10.23 (`YY.MM.DD`, the UTC release date, with `-1`, `-2`… for later releases the same day); earlier releases used [Semantic Versioning](https://semver.org/).

## v26.10.26

### Security

- The CI workflow runs on Node.js 24 instead of the end-of-life Node.js 20, which has no fix for the Brotli decoder vulnerability CVE-2026-111497

## v26.10.23-1

### Added

- A full icon set from the brand's own icon: `favicon.ico` (16, 32 and 48px) and `apple-touch-icon.png` at the site root, and a `site.webmanifest` with 192px, 512px and maskable icons, so the page has a proper icon in browser tabs, bookmarks and on phone home screens (the home-screen icons sit on a white background, as iOS would otherwise fill the icon's transparent corners with black). Every page lists the same icons, served from this site instead of the media host
- Discord link previews: sharing any page in Discord shows a custom preview in the Stux.Design brand colour, with the page's name, what it is and a few links (Stux.Design, Services on the coming-soon page; the legal pages link back to Boring Legal Stuff). Names and descriptions show as plain text, and the 404 page has none. They're pre-built into each page by `python scripts/build-discord-embeds.py`, which `scripts/build-sitemap.py` now runs too
- `tests/site.sh`, which checks that every preview is valid JSON under Discord's 3,000-byte limit and none is on the 404 page, that the icon files have the right sizes, and that every page's `<head>` carries the same icon tags. CI runs it

## v26.10.23

### Added

- `tests/version.sh`, which checks that `VERSION.md` is a valid Date Version, a real calendar date not in the future, and the same as the newest entry in this changelog

### Changed

- Switched from Semantic Versioning to [Date Versioning](https://datevers.ing): releases are numbered by their UTC release date as `YY.MM.DD`, with `-1`, `-2`… for later releases the same day. This release follows v1.0.3
- `commit.sh` and `commit.bat` refuse a `VERSION.md` that isn't a valid Date Version or is dated in the future (UTC), and warn when it's dated before today
- `README.md` and `CONTRIBUTING.md` describe Date Versioning and the release steps

## v1.0.3

### Changed

- The favicon follows the browser's light or dark theme: the deep icon (`icon-dark.png`) on light and the bright one (`icon-light.png`) on dark, straight from the brand's media host, so a brand colour change is just a new file there
- The logos and icons in the Markdown docs (README and the like) follow GitHub's light or dark theme, using each brand's `logo-light`/`logo-dark` and `icon-light`/`icon-dark` files

## v1.0.2

### Changed

- The favicon follows the browser's light or dark theme: the deep icon (`icon-dark.png`) on light and the bright one (`icon-light.png`) on dark, straight from the brand's media host, so a brand colour change is just a new file there
- The logos and icons in the Markdown docs (README and the like) follow GitHub's light or dark theme, using each brand's `logo-light`/`logo-dark` and `icon-light`/`icon-dark` files

## v1.0.1

### Added

- The home page's footer has a copyright line ("© 2026 Stux.Design. All rights reserved."), like the legal pages, with the years kept current automatically

### Fixed

- The legal, changelog and sitemap footers name Stux.Design in the copyright line instead of Stux.Group, and no longer say Stux.Design is operated by Stux Group Ltd: that belongs on the Imprint only, which still says it

## v1.0.0

### Added

- The coming-soon page for Stux.Design (soonpage.stux.design), built like the other Stux.Group page templates in Stux.Design magenta (`#e71081`), with light and dark themes
- The Stux.Design artboard: the page sits on a faint layout grid with rulers along the top and left edges, the headline's highlighted words get a selection box with handles and a "Draft" tag, and the card has crop marks at its corners
- The Boring Legal Stuff hub with its six pages, a changelog page that renders `CHANGELOG.md`, a sitemap and a 404 page
- `dev-server.sh`/`.bat` that serve the site the way GitHub Pages does with DEV_MODE on (dev banner), and `--no-dev-mode` to see it as production does
