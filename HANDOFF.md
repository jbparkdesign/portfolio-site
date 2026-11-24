# Portfolio handoff — November 24, 2026

Continue on the `simplified` branch. These updates build on `a2bb56d`.

## Current implementation

- Buildless site: `index.html`, `style.css`, existing fonts and assets.
- Home has the revised Rivian introduction in a narrower four-column desktop measure.
- Name starts as JP on load, pauses briefly, expands to Jeffrey Park and stays expanded. No hover collapse; project rail remains JP.
- Fragment URLs open projects directly and survive refresh; Back/Forward, closing, and Next Project use the existing transitions. Routes: `#rivian-assistant`, `#joyful-utilities`, `#security-access`, `#energy-charging`, `#earlier-work`, `#about`.
- Rivian Assistant metadata is **Role / Lead IC**. Calendar demo is on the left; real-world video fills the right media height. Its play/stop control and label overlay the bottom-left with 24px insets; clicking anywhere on that card toggles the same behavior.
- Assistant section heading: **Voice and screen, in sync.** Body copy uses standard feature columns.
- Only Assistant has the contact strip. It has a 160px spacer before it, 40px vertical padding, and no extra bottom border. Next Project remains beneath it.
- Security & Access and Energy & Charging also have 160px before Next Project.
- About tenure paragraph is removed. Current role reads **Product Design @ Rivian**, links to Rivian, has no underline, and uses the existing external-link arrow with a tight gap and baseline alignment.
- Rail Info, LinkedIn, and email controls have circular outlines. Info uses a straight-stem icon and remains filled/selected while About is open.
- About headline spacing expands on taller desktop viewports; no scroll verified at 1542×950 and 1280×720.

## Preserve

Existing typography, colors, spacing and grid tokens. Figma 55 Roman means Regular. Preserve media dimensions, bezels and padding unless requested. Preserve About photo cropping, scale and existing filters. Do not add contact strips to other projects without a request.

Figma: https://www.figma.com/design/ypWldGLdAEj8rbNYLBxjzR
Exploration page: `59832:419`; Home: `59832:421`; Assistant: `59832:505`.
The local implementation includes subsequent browser-comment refinements beyond those frames.

## Preview and validation

Run from the repository:

```sh
python3 -m http.server 8000 --bind 127.0.0.1
```

Open http://127.0.0.1:8000/ . No dependency installation or build step is needed.

Browser checks covered desktop and 390px mobile layouts, project routes, refresh, Back/Forward, close, Next Project and video toggles. Inline JavaScript syntax and `git diff --check` passed. The final Role / Lead IC change was a text-only edit after those browser checks.
