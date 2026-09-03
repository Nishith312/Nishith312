# Profile README Restructure — Design

Date: 2026-09-03
Repo: Nishith312/Nishith312 (GitHub profile README)

## Goal

Align the profile README with the portfolio (nishith.yunawise.com): Flutter-first
positioning, real project outcomes, only widgets that reliably render.

## Problems in current README

- Activity graph endpoint (github-readme-activity-graph.vercel.app) returns HTTP 402. Broken image.
- Streak stats served from herokuapp. Historically unreliable.
- "3D Contribution Graph" heading has a stray variation-selector char before the text.
- Fun-fact bullet duplicates the footer quote.
- Positioning says "Flutter | Backend & AI Engineer" with C++/PyTorch badges; portfolio says
  "Lead Flutter Engineer, Ahmedabad, 60fps on cheap hardware, Node + Express backend".
- Featured projects are badge links only, no outcomes.
- Unused assets: `assets/banner.png`, `assets/profile_picture.png`.
- Two email badges (personal + business).
- Workflow uses `actions/checkout@v3`.

## Target structure (top to bottom)

1. **Banner** — `assets/banner_short.png`, width 100%.
2. **Typing SVG** — two lines: "Lead Flutter Engineer · Ships to both stores" and
   "60fps on cheap hardware · Ahmedabad, IST". Links to portfolio. Portfolio badge below.
3. **About** — short paragraph: Lead Flutter Developer at Yunawise Technologies; cross-platform
   apps for parking, fintech, healthcare, sports; 100k+ combined downloads. Bullets:
   currently working on, learning, ask me about, based in, open to. No fun fact.
4. **Tech stack** — three flat centered badge rows (no `<details>`):
   - Mobile: Flutter, Dart, GetX, Bloc
   - Backend & data: Node.js, Express, Python, Firebase, Supabase, PostgreSQL
   - Web & tooling: React, TypeScript, Next.js, Docker, GitHub Actions, Figma
   Removed: C++, JavaScript, SQL, FastAPI, TensorFlow, PyTorch, Tailwind, Git, VS Code,
   Postman, Android Studio, Xcode.
5. **Featured apps** — markdown table with columns App | What it does | Outcome | Store.
   Rows (copy sourced from portfolio case studies):
   - Draftsy — AI-assisted fantasy sports drafting — 73% less drafting time, 40% better retention — App Store
   - Vyavhar — field-force management, GPS attendance, Supabase sync — 200+ pan-India staff — App Store
   - ParkBuzz — smart parking: plate scanning, offline tickets, payments, booking — App Store + Play
   - Animal Voice — on-device TFLite sound classification — 94% accuracy at stable 60fps, 100k+ downloads — Play
6. **GitHub stats** — github-readme-stats card and top-langs side by side (49% / 42% widths as now).
   Then 3D contribution graph via `<picture>` from `output` branch, heading fixed.
   Activity graph and streak removed.
7. **Connect** — one line: "Open to contract or full-time · remote anywhere · IST hours".
   Badges: Portfolio, LinkedIn, Email (nishith.prajapati@yunawise.com). Business email dropped.
8. **Footer** — capsule-render wave + quote "Great software is indistinguishable from magic."
   Star-request line dropped.

## Other changes

- Delete `assets/banner.png` and `assets/profile_picture.png`.
- `.github/workflows/3d-contrib.yml`: `actions/checkout@v3` → `@v4`. No other change.
- GitHub profile metadata via `gh api -X PATCH /user`: bio "Lead Flutter Engineer @ Yunawise · ships to both stores",
  location "Ahmedabad, India", blog "https://nishith.yunawise.com". Requires token with `user` scope;
  if missing, report and skip.

## Verification

- Every `<img src>` and link in the README returns HTTP 200 (curl check).
- README renders without broken images (preview via `gh` / GitHub after push).
- Heading text has no stray invisible characters (`grep -P '\xEF\xB8\x8F'` on headings).
- `gh api users/Nishith312` reflects new bio/location/blog if scope allowed.

## Out of scope

- New banner artwork.
- Additional workflows (snake animation, metrics).
- Adding FoodBoss Rider, Aakar Exhibition, Parkman, or other apps to the table.
