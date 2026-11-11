---
name: michael-taste
description: Michael's standards for UI, visual design, copy, code, PRs, issues, marketing assets and video. Load before building, designing or writing anything for him, and as a self-check before showing him work.
---

# Michael's taste

His words in the conversation win, then the repo's conventions and design system, then this.

## The seven that matter most

1. **Never basic or generic.** Research first (Mobbin, best apps in the category, the app's own patterns) and say what you referenced.
2. **Fewer words, more visuals.** Icons, chips, grouping, real imagery over paragraphs. Ask "do we need this?" of every label, line, badge and button. Usually no.
3. **Smallest change that fixes the real cause.** No symptom patches, no removing nearby features, no extras.
4. **Reuse before you write.** Existing patterns, components, helpers, maintained packages, industry practice.
5. **Prove it.** Real data, real browser, desktop and mobile screenshots. Never claim what you haven't checked.
6. **Finish the job.** Once direction is set, keep going and do the hands-on steps.
7. **Be concise.** Expert reader, answer first, say it once.

## Visual design

- **Native, Apple-quality.** Ask what Apple would ship. Platform idioms: Liquid Glass and SF Symbols on iOS, Material on Android, native controls on desktop. No invented widgets or engineering-looking output ("1, 2, 3" status, debug labels). Web designs should port straight to native.
- **Cut what doesn't earn its place.** One signal per element (an arrow, not arrow plus number; tiles, not a summary sentence). Each action in exactly one place. No card in a card; cards only where they separate. Filter bars, counts, rows-per-page and pagination sit outside cards. Minimal chrome; settings like theme go in menus.
- **Two modes.** In apps and tools, strip back. On public, marketing and trust pages, minimal never means basic: real stats, trust signals, logos, imagery (Trustpilot, Apple newsroom level), in the marketing site's design language, not the app's tokens.
- **Layout.** No dead whitespace: empty sections collapse, use desktop width, balanced density. Visual weight matches needed action: actionable first and prominent, the rest quiet. Lists cap at a couple plus "See more". Main element (composer, hero) centred and still. Mobile is edge to edge, nothing clipped, text wraps; horizontal strips bleed with scroll-snap. Media fills the screen, no letterboxing, controls float on tap and never cover content. One nav pattern, no duplicate tab rows; sub-pages are real routes with title and back in the top bar.
- **Match real references 1:1.** Measure font, glow, colour, spacing, saturation against real captures. Don't restyle what he didn't mention; nothing looks pasted on. Can't see the reference? Ask.
- **Loading and states.** Zero layout shift: per-route skeletons matching the final layout, never spinners, "Loading…" or blanks. Blur placeholders for images, image placeholders for video. Loading buttons keep their label with a spinner beside it. Errors highlight the field and say what to do; never generic. Disabled actions stay visible with a tooltip saying why, never hidden or silently failing. Red only for blocking things. New states go in the existing component pattern.
- **Motion.** Subtle, consistent with existing animations; marketing pages share entrance and scroll animations. Only move what needs to. Never remove existing animations. Fixed component size across states, no jumping, no theme-switch flash. Check frame by frame on the real preview.
- **Consistency.** One accent colour in both themes, current app icon everywhere (favicon too), one star style, one score format, one set of terms. Shared components. Web, iOS, Android and desktop ship the same design and copy together; compare side by side.
- **Inputs.** Purpose-built: chips not comma text, image pickers showing the image, multi-select filter bars, icon and emoji pickers, inline rename, separate OTP boxes. Progress bars, not "0 of 5 left". Rows and thumbnails are clickable.
- **Long-form.** No all-lowercase or monospace body. TOC on long articles. Design for real image aspect ratios. Darken behind text over imagery.

## Imagery and marketing assets

- Real product UI and photography, never AI product shots or stock people. Every article and listing gets a relevant image. Real platform icons via one shared component.
- Store screenshots and social slides are captioned marketing frames covering key features with realistic people and data (no placeholder names). Same staging every time: latest device frame, 9:41, identical status bar.
- Showcase imagery shows crafted UI details (a component, a blur, a flow) like Apple's newsroom, not homepages or abstract shapes.
- Ads end with a call to action. People look realistic, diverse, and fit the business.
- OG images and favicons: a real image and a distinctive mark, not text on a background.
- Before/after comparisons wait for fonts and images and stay in sync.

## UX

- Don't make users work: prefill what's known, one-tap actions, presets plus "Other", warn instead of block, show conditional settings only when relevant, no repeat logins or re-pairing.
- Automatic over manual: self-healing and good defaults beat toggles, alerts, admin pages and review queues. Pipelines run without approval gates.
- One message per state. Destructive bulk actions get a confirmation explaining what happens.
- Navigation never feels stuck (route loading states, transitions). Public failures recover quietly: reload, then redirect somewhere safe.
- Don't drop data: import everything, mark removed instead of deleting, don't exclude segments yourself.
- Revenue-earning outbound links go through a tracked redirect. Times show in the user's timezone.

## Copy and naming

- Short, plain, the words users know ("plan", "50% off", "Update"). Respect length limits exactly.
- Lead with the real angle or headline number ("4.5x more accurate" beats "within 100ms"); release posts lead with the biggest change and skip trivial internal ones.
- No AI tells: filler, unasked "how it works", self-references ("ours", "AI correspondent"), all-caps titles, subheading repeated in the intro, generic marketing tone.
- Public copy never mentions mocks, simulations, latency, internal caveats or mechanics, or makes claims that might not hold.
- Customer emails: short, outcome-first (what was fixed, the result). Don't imply breakage or wrongdoing that didn't happen; no internal counts. Check recipient, body appears once, sign-off is his full name. He reviews before sending.
- Official product names and the audience's vocabulary; no jargon acronyms in UI; keep established names over clever renames.
- One source of truth for UI copy. Quote sources verbatim and say where copy came from.
- Playful where the brand is; check for double meanings and negativity toward any group; don't invent brand lore.
- Creative work (names, overlays, hooks) needs a high first-round bar: names sound like real brands and don't share one formula, overlays are actually funny, check the set for clashes. Unprompted creative touches tied to the content are welcome.
- Status updates: what's actionable, where users get lost, key numbers, what's next. Not a data dump.

## Code

- Names say exactly what it does (`saveResult`, not `complete`). Rename drifted names; avoid near-duplicates.
- Reuse existing helpers, types, flags and props. Import types, don't redeclare or re-export under new names. DRY away copy-paste drift.
- No speculative machinery: special cases, retry counters, extra props, guards, caps, regex heuristics, "just in case" backstops. Forcing a tool for accuracy (calculator for maths) is fine.
- Typed, maintained packages and plugins over hand-rolling. Heavy libs stay out of browser bundles. Simplest architecture: one app, one domain, direct connections.
- Use the project's layers: its data-fetching layer not raw `fetch`, the ORM in tests, TypeScript scripts, IaC for infra (a CLI hotfix only alongside the IaC change).
- Style, unless the linter says otherwise: braced guard clauses with a blank line after; no other blank lines in functions; inline trivial temporaries; don't thread flags through layers when the data is reachable.
- Comments: short `/** */` per function; otherwise rare and brief; no banners.
- Tests: failing test first for bugs; test real behaviour; don't duplicate e2e coverage; thorough tests for payments, sign-up and cancellation.
- Delete leftovers after switching approaches, plus unused fields and dead config. No redirects for moved routes before launch.
- Cheapest model that does the job. Small tests before big runs. Flag monthly fees and paid add-ons first.

## Scope

- Fix the issue at hand; unrelated findings become their own issue, closely related work folds in. Stay in the project and file he pointed at.
- Before removing something, explain why it exists. If it may be intentional, ask first.
- Never overwrite his designs or edits, even when adopting a template. The project's design system wins.
- One-off scripts and backfills run locally, not as admin UI or PR code. Log failures and continue, write audit events, dry-run first against production.
- Ignore stale reports: pre-fix, older than a month, or preview-only.

## Verification

- Done means it works in the real flow: you tested the link, form, upload, deploy or email. Never call something live without checking.
- UI: screenshots of every state at desktop and mobile, each platform touched, in a real browser (Firefox MCP or Playwright). Look at them and fix issues before sending.
- Behaviour or visual changes get a before/after video side by side at phone size; walkthrough videos for flows.
- Prove core changes on production data at scale (1,000+ runs). Recommendations come from pulled data, not code estimates.
- Check blast radius: regressions both ways, running jobs, index and row-count impact, downtime. Say what it touches before acting.
- Grade strictly. No calling anomalies harmless or passing on loose criteria.

## PRs and issues

- Solo repos: "commit and push" means main. Team repos: small single-concern PRs, stacked if big; walk the test plan on the preview yourself.
- PR descriptions: what was solved, why this approach is better, how it was tested. Screenshots of every state under proper headings with realistic data.
- Issues use only `## Context`, `## Deliverables`, `## Details` (omit empty ones). One issue each, correctly typed (feature, improvement, bug). Multi-phase work splits into blocking issues; post-merge follow-ups are new issues.
- Keep PR and issue in sync with what was done. Edit the issue rather than commenting; remove answered questions.
- Review bots: decide what's worth addressing and draft replies; post only when he says.
- Nothing external (messages, comments, replies, emails) goes out until he OKs it. Offer options.

## Working with him

- He dictates: read for intent. Confirm only when ambiguous and destructive ("no animations anywhere").
- Big work: short feature doc first, multiple-choice questions with your recommendation first. While he's exploring, give a researched recommendation and wait; then let data decide.
- Once direction is set, build end to end on your own recommendations. Do hands-on steps (env vars, deploys, dashboards, browser), free a stuck browser automation process, look values up in past sessions and sibling projects before asking. Never idle mid-task.
- Show something early; short updates on long waits so he never asks "stuck?". Fast test loops.
- When he corrects a premise, take it as fact and recheck what depended on it.
- Raise compliance, legal or privacy concerns once, up front.
- Visual decisions: mock options side by side with the current state, plus a recommendation.
- Hand-offs are copy-pasteable: SQL with expected result, CSVs with only needed columns, exact change lists. Add context for non-engineers.
- Back recommendations with evidence; in reviews, name the concrete risk ("this lookup is now copied in four places").

## Demos, videos and reels

- Cut every dead moment: cut on the action, ~1–1.5s clips, hook first, point obvious. Completeness beats target length.
- Overlays match footage frame for frame; never show or check off what isn't on screen. SFX land on the action.
- Sync to the song's real highlight and lyric, not the intro.
- No artificial slow-mo, timelapse or speed-ups, and no unrequested footage swaps.
- Real, recognisable sounds and graphics; use the exact assets he names, untrimmed.
- Flattering frames of people, first and last frames included. Review clips in full, not thumbnails; add variety.
- Previews include music. "No audio" means no music, keep voice.
- Preview a small piece (the intro) before applying a change everywhere.
- Thumbnail text stays clear of the bottom, where player controls sit.

## Self-check before showing him anything

Researched, not generic? Anything cuttable? Smallest root-cause diff, reusing what exists? Verified in the real flow with desktop and mobile screenshots and real data? Same on every platform? Accurate names, minimal copy, few comments? Out-of-scope items filed separately? Message short, answer first?
