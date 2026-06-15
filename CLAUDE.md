# CLAUDE.md

## Instruction

Every time you make some change, please record in CHANGE.md the date, what you did, and how you did it. 


## Big picture

This is a Hugo personal website. The goal is to make a quiet, clean, whimsical personal calling-card homepage with deeper material hidden behind buttons.


The homepage should feel like a small room with doors.

It should contain only:

* one picture / portrait / small visual object
* the name
* a short blurb
* a small set of button links

* `research`
* `garden`
* `blog`
* `cv`
* `github`
* `secret`

The visual references are:

* Michael Lan’s site https://mzchael.com/: quiet, clean, mostly just a blurb, with blog hidden away 
* Canis Li’s site https://canis.li: simple portrait + blurb + nice buttons
* clean and cute graphic: https://ben.page
* beautiful: https://everest-pipkin.com
* digital gardens / zettelkasten / Obsidian-like graph as a future direction, but not on the homepage itself

The homepage should feel minimal, slightly soft, and personal. It can have gentle whimsical touches, but it should not become cute, cluttered, or theme-y.

## Technical direction

Use Hugo from scratch with custom layouts and CSS.

Do **not** use a theme like Lynx as the main base. Lynx can be used as inspiration for button styling, but the site should not look like vanilla Lynx.

Do **not** use React for the basic site. Plain Hugo templates, HTML, CSS, and a little JavaScript later are enough. Only use JavaScript for genuinely interactive pieces, such as a fake password page or future garden graph.

Prefer simple static files and clear templates.

## Hugo mental model

Use this separation:

```text
content/_index.md     = homepage metadata and text
layouts/index.html     = homepage structure/layout
static/css/main.css   = styling
static/images/        = images
content/blog/         = blog posts
content/garden/       = garden notes
content/research/     = research pages
```

`content/_index.md` should exist. It should stay small. It is not where the whole homepage layout lives.

A good `content/_index.md` looks like:

```md
---
title: "Gloria Ma"
description: "I work on machine learning, genomes, and small internet objects."
---
```

The actual homepage visual structure should live in `layouts/index.html`.

## Desired file structure

Aim for something like:

```text
.
├── hugo.toml
├── content/
│   ├── _index.md
│   ├── blog/
│   │   └── _index.md
│   ├── garden/
│   │   └── _index.md
│   ├── research/
│   │   └── _index.md
│   └── secret/
│       └── _index.md
├── layouts/
│   ├── index.html
│   ├── page.html
│   └── section.html
└── static/
    ├── css/
    │   └── main.css
    └── images/
        └── me.jpg
```

## Homepage design constraints

The homepage should be centered and calm.

A good initial layout is:

```html
<main class="home">
  <section class="card">
    <img class="portrait" src="/images/me.jpg" alt="Portrait of Gloria Ma">

    <h1>{{ .Title }}</h1>

    <p class="blurb">
      {{ .Description }}
    </p>

    <nav class="buttons" aria-label="Main links">
      <a href="/research/">research</a>
      <a href="/garden/">garden</a>
      <a href="/blog/">blog</a>
      <a href="/cv.pdf">cv</a>
      <a href="https://github.com/gloriama2007">github</a>
      <a href="/secret/">secret</a>
    </nav>
  </section>
</main>
```

The button links are the main navigation. Do not add a visible homepage list underneath them.

## Visual style

Prefer:

* warm off-white or cream background
* dark brown / charcoal text
* soft rounded buttons
* generous whitespace
* serif or elegant readable typography
* subtle hover effects
* paper texture
* gentle, restrained whimsy

Avoid:

* corporate portfolio aesthetic
* blue Bootstrap-like links
* large navbars
* grids of project cards
* aggressive animations
* lots of emoji
* default theme appearance
* excessive borders or shadows

Good CSS direction:

```css
:root {
  --bg: #fbf8f1;
  --text: #2f2a25;
  --muted: #6f675f;
  --border: #ded4c7;
  --button: #fffdf8;
  --button-hover: #f1e8db;
}
```

The homepage should not have any scrolling. 

## Content philosophy

The homepage should not explain everything. It should invite.

Good homepage copy is short, like:

```text
I work on machine learning, genomes, and small internet objects.
Sometimes I write things down.
```

Do not make the homepage sound like a LinkedIn bio.

Avoid phrases like:

```text
Welcome to my portfolio.
I am passionate about...
Here are my selected projects.
Explore my work below.
```

## Garden direction

The `garden` button should eventually lead to a digital garden / zettelkasten-style area.

The garden can have:

* notes
* backlinks
* tags
* a graph or node map
* note statuses like `seed`, `sprout`, `evergreen`
* hover previews
* local graph views
* soft whimsical visual design

But the graph should live at `/garden/`, not on the homepage.

The homepage should only link to the garden.

A future garden note might have front matter like:

```md
---
title: "Gene-level models"
tags: ["ml", "genomics"]
status: "seed"
links: ["STATE", "single-cell eQTLs", "gene networks"]
---
```

Eventually, a script can generate a graph from note links or front matter. Do not build this before the basic site is clean.

## Blog direction

The blog should exist, but it should be hidden behind a button. The homepage should not show recent posts.

Blog pages can be plain and readable. They do not need elaborate design at first.

## Secret page direction

The `secret` page can be a playful fake password / interactive page. It does not need real authentication. It should be treated as an internet toy or easter egg, not a security mechanism.

## Implementation priorities

When changing the site, prioritize in this order:

1. Keep the homepage minimal.
2. Keep the code simple, modular, reusable, understandable.
3. Preserve the “doors” model: homepage buttons lead to deeper areas.
4. Make styling feel custom, soft, and clean.
5. Avoid overbuilding.

When unsure, choose the simpler static Hugo solution.
