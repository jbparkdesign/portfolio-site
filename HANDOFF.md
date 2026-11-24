# Portfolio handoff — November 24, 2026

Continue on the `simplified` branch. The latest refinements build on `5c5a28f`.

## Current implementation

- Buildless site: `index.html`, `style.css`, existing fonts and assets.
- Home has the revised Rivian introduction in a narrower four-column desktop measure.
- Name starts as JP on load, pauses briefly, expands to Jeffrey Park and stays expanded. No hover collapse; project rail remains JP.
- Fragment URLs open projects directly and survive refresh; Back/Forward, closing, and Next Project use the existing transitions. Routes: `#rivian-assistant`, `#joyful-utilities`, `#security-access`, `#energy-charging`, `#earlier-work`, `#about`.
- Rivian Assistant metadata is **Role / Lead IC**. Calendar demo is on the left; real-world video fills the right media height. Its play/stop control and label overlay the bottom-left with 24px insets; clicking anywhere on that card toggles the same behavior.
- Assistant section heading: **An exercise in restraint.** Body copy uses standard feature columns.
- Only Assistant has the contact strip. It has a 160px spacer before it, 40px vertical padding, and no extra bottom border. Next Project remains beneath it.
- Security & Access and Energy & Charging also have 160px before Next Project.
- Home introduction: “I joined before the first vehicle shipped. Since then, I’ve shaped experiences across the vehicle, app, charging network, and AI assistant.” Home and About link only Rivian plus its arrow, with Rivian Yellow hover/focus; About role reads Product Design at Rivian.
- Navigation says About on Home and A in the rail, retaining its selected state. Icons remain compact during rail expansion on close; text fades in after the width transition completes. Interrupted transitions have a fallback and reopening clears the temporary state.
- Close control has a dark translucent backing, 18px glyph and reduced rotation; it animates only on Home/project entry, avoiding project-switch flicker.
- All decorative rules and control borders use the shared divider color and 1px weight. Assistant contact invitation uses muted text, with Get in touch as the bright mail link.
- About facts are left-aligned metadata rows, bottom-aligned to the rail list divider on desktop. Photos scale together with proportional overlap and vertical stagger to remain predictable across viewport sizes. The random-photo canvas extends into left negative space and slightly into the headline, avoiding facts and the camera button. The pill camera button sits centered below the photos at 25% of its container width.
- Energy uses a seven-column centered phone stage and five-column square home reference photo, preserving phone scale. Added The Rivian Adventure Network and Charging at home titles.
- Earlier Work caption has a fixed line break before “like”.
- Responsive breakpoints: 600px (About photo canvas), 768px (mobile layout and Assistant media stacking), 1024px (rail visibility). Redundant About overrides removed.
- Project reveals follow visual position rather than DOM order. Newly visible batches share a stagger schedule; Role/Scope/Released inherit the group delay and retain 80ms row stagger. Entrance delays are cleared after transitions; reduced-motion skips reveal movement.

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

Browser checks covered desktop and 390px mobile layouts, responsive boundaries, project routes, refresh, Back/Forward, close, Next Project, video toggles, random-photo placement, reveal timing and rail expansion timing. Inline JavaScript syntax and `git diff --check` passed before this push.
