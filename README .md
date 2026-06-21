# Learning Log

> A working portfolio of everything I'm learning across QA, test automation, cybersecurity, programming and AI — videos, write-ups, code lessons, reading notes and a curated toolbox of GitHub repos.

![Single file](https://img.shields.io/badge/single--file-index.html-E6A95B?style=flat-square)
![No build step](https://img.shields.io/badge/build-none-7BD88F?style=flat-square)
![Hosted on](https://img.shields.io/badge/hosted%20on-GitHub%20Pages-54C9D6?style=flat-square)

**Live site:** https://knurs.github.io/portfolio-learning-log/

---

## About

This is my open learning log. Instead of just listing skills on a CV, I keep the actual material I'm working through and re-explain it in my own words — so recruiters and hiring managers can see exactly where my curiosity is pointed and how I think.

It's a single, dependency-light page: no framework, no build step, no backend. All content lives inside the file, so it's trivial to host for free and easy to maintain.

## Sections

| Section | What's in it |
| --- | --- |
| **Home** | Intro, profile and a snapshot of what's new |
| **Library** | Curated videos I've studied, each with my notes |
| **Write-ups** | Long-form posts that explain a topic from scratch |
| **Code** | Short, line-by-line code lessons with syntax highlighting |
| **Reading** | Books and articles with running notes |
| **Repos** | A searchable toolbox of 100+ useful GitHub repositories |

Everything is colour-coded by domain: **QA & Testing · Cybersecurity · Test Automation · Programming · AI & ML**.

## Built with

- Plain **HTML, CSS and vanilla JavaScript** (hash-based routing, no framework)
- [marked](https://github.com/markedjs/marked) for Markdown rendering
- [highlight.js](https://github.com/highlightjs/highlight.js) for code syntax highlighting
- Google Fonts: Space Grotesk, IBM Plex Sans, IBM Plex Mono

All third-party libraries load from a CDN, so there's nothing to install.

## Run it locally

No tooling required — just open the file:

```bash
# clone, then open in your browser
git clone https://github.com/YOUR-USERNAME/portfolio.git
cd portfolio
open index.html        # macOS  (use "start" on Windows, "xdg-open" on Linux)
```

An internet connection is needed for the fonts, embedded videos and code highlighting (all served from a CDN).

## Adding content

Open `index.html` and look for the line marked `EDIT BELOW THIS LINE`. Content lives in two places:

1. **Markdown blocks** — the text of each write-up, code lesson and book note lives in a `<script type="text/markdown" id="...">` block near the top. Write normal Markdown, including fenced code blocks.
2. **Data lists** — small arrays that wire everything together.

### Add a video (Library)

```js
{ url:"https://www.youtube.com/watch?v=XXXX", title:"Title", domain:"qa",
  note:"One line for the card.", status:"watching",
  takeaways:["Point one.","Point two."], topics:["tag1","tag2"] }
```

### Add a write-up or code lesson

First the body:

```html
<script type="text/markdown" id="md-my-post">
## Heading
Normal text, **bold**, `inline code`.
```js
const x = 1; // code blocks are highlighted automatically
```
</script>
```

Then link it (the `md` field must match the `id` above):

```js
{ slug:"my-post", kind:"writeup", domain:"qa", date:"2026-06-21",
  title:"Title", summary:"One-sentence summary.",
  video:"https://youtube.com/...", md:"md-my-post" }
```

Use `kind:"writeup"` for the Write-ups section or `kind:"code"` for the Code section. Leave `video:""` to skip the embedded player.

### Add a book or article (Reading)

```js
{ slug:"my-book", type:"book", title:"Title", author:"Author",
  status:"reading", rating:5, summary:"Short blurb.", link:"", md:"md-my-notes" }
```

`type` is `book` or `article`; `rating:0` hides the stars.

### Add a repo (Repos)

```js
{ n:"owner/repo", k:"cyber", d:"One-line description." }
```

The link is built automatically from `n`.

**Domain keys** are always one of: `qa`, `cyber`, `auto`, `code`, `ai`. Edit your name and links in the `PROFILE` block, and change the colour palette in the `:root` block at the top.

## Deploy to GitHub Pages

1. Create a new **public** repository (e.g. `portfolio`).
2. Upload `index.html`.
3. Go to **Settings → Pages**, set the source to **Deploy from a branch**, branch **main**, folder **/(root)**, and save.
4. After a minute or two, your site is live at `https://YOUR-USERNAME.github.io/portfolio/`.

To update later, edit `index.html` in the repo and commit — the site rebuilds automatically.

---

Built and maintained by **Kübra Nur Sevilmiş** — QA Engineer · Cybersecurity Student.
