# Nistha's Galaxy

A portfolio of hand-built websites, presented as a solar system. Each planet
opens one sample site. Live at <https://nisthasgalaxy.netlify.app>.

Plain HTML, CSS and JavaScript. No framework, no build step, no dependencies
to install. Every page is a single self-contained file.

## What is in here

| Path         | Page                    | What it is                                                        |
|--------------|-------------------------|-------------------------------------------------------------------|
| `index.html` | Nistha's Galaxy         | The entry page and the 3D solar system, built with Three.js        |
| `cv-1/`      | CV Portfolio Style 1    | CV layout on marbled endpapers, drawn live with a WebGL shader     |
| `cv-2/`      | CV Portfolio Style 2    | CV layout in a red editorial style, with an interactive letter field |
| `cafe/`      | Nistha's Brownie Points | A bakery site drawn in biro on ruled paper, with two small games   |
| `tech/`      | Mothwing                | A fictional tech startup: a CRT boot screen into a scrolling 3D tunnel |
| `exam/`      | Aldermoor               | A UGC NET English Literature revision tool set in a 3D castle      |
| `quiz/`      | NET practice bank       | A timed question bank with a blunder book that remembers misses    |

The two CV pages are **samples**. The person on them, Ira Menon, is invented,
and so is every project, number and credential. They exist to show the layout
without using anyone's real details. Both pages say so on screen.

## Running it locally

Opening `index.html` by double-clicking mostly works, but browsers block some
things on `file://` URLs. A local server is more reliable:

```bash
cd nisthas-galaxy
python3 -m http.server 8000
```

Then open <http://localhost:8000>.

## Editing the text

The two CV samples keep **all** of their words in one block near the top of
the file, marked:

```
EVERYTHING YOU CAN EDIT LIVES IN THIS ONE BLOCK
```

Change the text between the quote marks and the page rebuilds around it. Keep
the quote marks, commas and square brackets where they are. To add a job or a
piece of writing, copy one `{ ... }` block, paste it after the last one, and
put a comma between them. Everything below the divider line is layout code you
should not need to touch.

To add or remove a planet, edit the `SYSTEM` array near the top of the script
in `index.html`. Each planet is one entry. `orbit` is its distance from the
sun, `size` its radius, and `colour` its hex colour.

## Deploying

Connected to Netlify from GitHub, every push to the default branch deploys
automatically. `netlify.toml` already tells Netlify there is no build step and
to publish this folder as it stands.

To deploy by hand instead, drag the whole folder onto <https://app.netlify.com/drop>.
Always drag the entire folder, never one file: a deploy replaces everything.

## Known limitations

- The galaxy and three of the sample pages need WebGL. Each one falls back to
  a readable text version when WebGL is unavailable, but the 3D is the point.
- The CV samples build their text with JavaScript, which is what makes the
  single editable block possible. With JavaScript disabled those two pages
  come up blank.
- `quiz/` is 2.3 MB and `exam/` is 1 MB, both single files with everything
  inlined. They are slow on a first load over a weak mobile connection.
- The question text in `quiz/` was drawn from solved-paper PDFs. Check the
  rights on that before promoting the page publicly.
