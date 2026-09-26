# Jacob Shkrob: academic website

Live at **https://shkroby.github.io/**

Built with [Hugo](https://gohugo.io). Every push to `master` rebuilds and
publishes the site through GitHub Actions (`.github/workflows/hugo.yml`).

## Where things live

| To change | Edit |
|---|---|
| Intro paragraph | `content/_index.md` |
| Name, email, links, research interests, education, address | `hugo.yaml` (under `params`) |
| Papers and working papers | `data/papers.yaml` |
| Writings (expository notes, etc.) | `data/writings.yaml`, PDFs in `static/writings/` |
| Shelf (favorite quotes, books, websites, people) | `data/shelf.yaml` (page subtitle: `content/shelf/_index.md`) |
| CV | replace `static/cv.pdf` |
| Profile photos (one is picked at random per visit) | `static/images/`, listed in `hugo.yaml` under `portraits` |
| Colors and layout | `assets/css/main.css` (blog: `assets/css/tufte.css`) |

## Writing a blog post

```sh
hugo new content blog/my-post-title.md
```

This creates a draft. Write in Markdown, set `draft: false`, commit, push.
To include images, make a folder instead (`content/blog/my-post/index.md`)
and put the images next to `index.md`.

LaTeX works as in a paper: `$...$` inline, `$$...$$` for display, and
environments like `align` and `equation` (numbered, citable with `\eqref`).
Use `\$` for a literal dollar sign. Custom macros live in
`layouts/partials/mathjax.html`.

Tufte features, via shortcodes:

```
{{</* sidenote */>}}Numbered note in the margin.{{</* /sidenote */>}}
{{</* marginnote */>}}Unnumbered note.{{</* /marginnote */>}}
{{</* newthought */>}}Small-caps opening{{</* /newthought */>}}
{{</* marginfigure src="plot.svg" alt="..." caption="..." */>}}
{{</* figure src="plot.png" alt="..." caption="..." */>}}   (add fullwidth="true" to span the page)
{{</* epigraph author="..." source="..." */>}}Quotation{{</* /epigraph */>}}
```

(In a real post, drop the `/*` and `*/`.) The post "How this blog works"
demonstrates all of them. Delete it, or set `draft: true`, once you publish
a real post.

## Previewing locally

Install Hugo extended, v0.158 or newer (on a Mac: `brew install hugo`), then:

```sh
hugo server -D
```

and open http://localhost:1313/.

## Credits

Blog typography adapted from [Tufte CSS](https://github.com/edwardtufte/tufte-css)
with the ET Book typeface (both MIT licensed; see `static/fonts/et-book/`).
