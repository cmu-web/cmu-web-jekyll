---
nav_order: 1
---

# Writing Pages

Write ordinary Markdown. These are the pieces that change on the way to the
page.

## Which Files Become Pages

GitHub Pages builds from your repository's root or its `/docs` folder; choose
which in the repository's Pages settings. Use `/docs` when the repository holds
anything besides the docs: only what's in that folder becomes the site.
Put a `README.md` in it for the home page: GitHub shows the same file when
someone browses the folder, so it serves as the docs' index in both places,
while the repository's own README stays the front door for people working on
the code.

Building from the root, every `.md` file becomes a page. Leave files and
folders out with `exclude` in `_config.yml`:

```yaml
exclude: [CONTRIBUTING.md, tools/]
```

To leave out a single page, give it `published: false` in its front matter.

## Navigation

Every page with a title appears in the site's navigation, in the header and
the menu. To order them, give a page `nav_order` in its front matter; to build
a page without listing it, such as one you link to from another page, give it
`nav_exclude: true`.

```yaml
---
nav_order: 2
---
```

To list the navigation in one place instead, name the pages in order in
`_config.yml`; the list replaces `nav_order` and `nav_exclude`:

```yaml
cmu:
  nav: [writing.md, setup.md, faq.md]
```

To list other sites after your pages, such as a channel or a related site,
add them as `nav_links`. They appear as external links, above the link to
your repository:

```yaml
cmu:
  nav_links:
    - title: Your Office on YouTube
      url: https://www.youtube.com/@your-office
```

If your site belongs to a larger office, name it as the `parent`. It comes
first in the breadcrumbs, and the line under your site's name links to it:

```yaml
cmu:
  parent:
    title: Your Department
    url: https://www.cmu.edu/your-department/
```

## Footer

The footer starts with your office's name and Carnegie Mellon's address. Set
your own in `_config.yml`; every line is optional:

```yaml
cmu:
  footer:
    office: Your Office
    address: [Carnegie Mellon University, 5000 Forbes Avenue, Pittsburgh, PA 15213]
    phone: 412-268-0000
    email: your-office@andrew.cmu.edu
    links:
      - title: Your Office's Main Site
        url: https://www.cmu.edu/your-office/
```

The email becomes a Contact Us link, and the links join Legal Info and
www.cmu.edu.

## Tables

Tables are striped and fill the page's width.

| Setting       | What It Does                             | Default    |
| ------------- | ---------------------------------------- | ---------- |
| `title`       | Your site's name, in the header and footer | Required |
| `description` | A line under the name                    | None       |
| `cmu.roof`    | The strip across the top: `red`, `gray` or `white` | `red` |
| `cmu.footer`  | The footer's office, address, phone, email and links | `title` and CMU's address |
| `cmu.nav`     | The pages in the navigation, in order    | Every page with a title |
| `cmu.nav_links` | Other sites, after the pages in the navigation | None |
| `cmu.parent`  | The office your site belongs to, first in the breadcrumbs | None |
| `cmu.kit`     | The web kit release to load              | `0.1.0`    |

## Code

Each code block gets a box with a copy icon in its corner, as on GitHub.

```bash
git add docs/writing.md
git commit -m "docs: add Writing Pages"
```

## Callouts

GitHub's alert syntax becomes a labeled callout:

> [!NOTE]
> Pages publish a minute or two after you push.

> [!TIP]
> Start each page with a `#` heading; it becomes the page's title.

> [!IMPORTANT]
> Use made-up names and data in examples, never real people's.

> [!WARNING]
> Anything in a public repository's Pages site is public.

> [!CAUTION]
> Don't put passwords or keys in your docs.

Any other block quote becomes a plain note.

> This is a note: a quiet aside among the other content.

## Full-Width Pages

Markdown pages go in one column. For a page with full-width sections, such
as a home page with a hero, color bands and cards, or a page with a sidebar,
use the `sections` layout and write the page in HTML with the template's
sections and the kit's components. It keeps your site's header, navigation
and footer:

```html
---
layout: sections
title: Borrow a Camera
description: Reserve a camera in about a minute.
---
<div class="content">
  <div>
    <h1>Borrow a Camera</h1>
    <p class="cmu-lead">Reserve one in about a minute.</p>
  </div>
</div>
```

The [example page](example.html) shows a few sections together. In the
front matter, `breadcrumbs: false` leaves the breadcrumbs off, and
`carousel: true` loads the template's slideshow script for a
`js-flickityCustom` section. On any page, a `description` becomes what
search engines show.
