# The Diabetes Link at Queen's — website

The whole site is one file, `index.html`. No build step, no frameworks, no
dependencies to install. Open it in a text editor, save, refresh the browser.

## Files

```
index.html     the entire site: content, styling and scripts
photos/        the rolling photo strip (01.jpg, 02.jpg, ...)
```

## Running it on your own machine

From this folder:

```bash
python3 -m http.server 8000
```

Then open http://localhost:8000. (Double-clicking `index.html` mostly works
too, but the photo strip needs a server to load the images.)

## The two things you'll actually edit

Both live in the settings block at the top of the `<script>` near the bottom
of `index.html`.

**1. The blog.** Once the Substack publication exists, put its address here:

```js
const SUBSTACK = "https://queensdiabeteslink.substack.com";
```

The three newest posts then load automatically, with title, date, header
image and summary. Leave it as `""` and the section shows a "Read our posts"
button instead — nothing breaks either way.

Note this is the *publication* address ending in `.substack.com`, not the
reader profile at `substack.com/@queensdiabeteslink`. Only publications have
the RSS feed the site reads.

**2. The photos.** Add JPGs to `photos/` named `05.jpg`, `06.jpg` and so on,
up to `10.jpg`. The strip detects which ones exist, so missing numbers are
skipped and no code change is needed. If the folder is empty the whole
section hides itself.

To go past `10.jpg`, extend the list in `const PHOTOS`.

## Other things worth knowing

- **The glucose graph is simulated.** It is not real data from any person.
  A new curve is generated from the current date, so it is the same for every
  visitor all day and changes at midnight. The physiology is in the `cgm`
  function: baseline, dawn phenomenon, three meals, occasional lows.
- **Colours** are CSS variables on `:root` at the top of the file, taken from
  the chapter logo. Change one there and it updates everywhere.
- **The team and roles sections** are plain HTML — search for `class="person"`
  or `class="role"` and copy an existing block to add someone.
- The site is responsive, keyboard-navigable, and respects
  `prefers-reduced-motion`. Worth keeping that way.

## Publishing

Hosted on GitHub Pages. To update:

```bash
git add .
git commit -m "describe what changed"
git push
```

Changes are live about a minute later.
