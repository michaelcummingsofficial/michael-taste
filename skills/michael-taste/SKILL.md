---
name: michael-taste
description: Michael's taste and standards for building apps, UI and visual design, copy, code changes, PRs and issues, marketing assets, demos and videos. Load before building, designing or writing anything for Michael (a page, screen, component, feature, fix, PR, issue, email, store listing, demo, video, dashboard) so the first version lands close to what he wants instead of needing rounds of feedback. Also use it as a self-review checklist before showing him work.
---

# Michael's taste

Mined from about 4,100 of Michael's messages to Claude Code across roughly 30 projects (Oct–Nov 2026): solo consumer apps and websites, plus a team codebase. Each rule is something he corrected or asked for more than once. Where the reason is known it's included, so you can extend the rule to cases not listed here.

Precedence: his words in the current conversation come first, then the repo's own conventions and design system, then this skill.

## The seven that matter most

1. **Never basic, never generic.** Research before building: pull references from Mobbin and from the best apps in the category, and follow the app's existing patterns. Un-researched first drafts get called "super basic" or "slop". Say what you referenced.
2. **Fewer words, more visuals.** Separate things with icons, chips, grouping and real imagery, not paragraphs. Ask "do we need this?" of every label, line, badge and button. He almost always says no.
3. **The smallest change that fixes the real cause.** He has thrown away whole implementations because the diff was bigger than the problem. Fix causes, never symptoms. Don't remove nearby features or add things nobody asked for.
4. **Reuse before you write.** Use existing patterns, components, helpers and well-maintained packages, and follow industry practice. "We aren't reinventing the wheel here."
5. **Prove it.** Use real data, a real browser, and screenshots at desktop and mobile widths. Never state something about the code or product you haven't checked; he will ask "did you hallucinate that?"
6. **Finish the job.** Once a direction is set, keep going and do the hands-on steps yourself. "What are you stopping for? Finish this."
7. **Be concise.** Assume an expert reader, put the answer first, give context once, and don't repeat yourself.

## Visual design

**Native and Apple-quality.** Ask what Apple would ship. Use each platform's own idioms: Liquid Glass and SF Symbols on iOS, Material on Android, native controls on Mac and Windows. Avoid invented widgets and anything that looks like engineering output (step-by-step "1, 2, 3" status, debug labels). Design web so it carries straight over to native.

**Cut what doesn't earn its place.**
- One signal per element: an arrow, not an arrow plus a number. Tiles, not a summary sentence.
- No duplicate controls. Each action lives in exactly one place.
- No card inside a card, and use card styling only where it separates something.
- Filter bars never go inside cards. Count, rows-per-page and pagination sit outside the table card.
- Keep headers and chrome minimal. Settings-type controls (theme) go in menus, not top-level chrome.

**Two modes, one principle.** Inside an app or tool, strip the UI back. On public, marketing and trust pages, "minimal" must never mean "basic": add real substance, such as trust signals, real stats, logos and imagery, at the level of Trustpilot or Apple's newsroom. Marketing pages follow the marketing site's design language, not the app's tokens. In both modes: fewer words, more visuals, no filler.

**Layout.**
- No dead whitespace. Empty sections collapse instead of reserving space, content uses the desktop width, and density is balanced, never cramped.
- Visual weight matches how much action something needs. Things needing action go first and stand out; things needing nothing stay quiet. Cap lists at a couple of items plus "See more". Keep the main element (the composer, the hero) centred and unmoved.
- Mobile is edge to edge, with nothing clipped and text that wraps. Horizontal strips bleed to the edge with scroll-snap.
- Media products give content the whole screen: no letterboxing or pillarboxing, and controls float, appear on tap, and never cover the picture.
- One navigation pattern app-wide, with no duplicate tab rows. Sub-pages are real routes with the title and back button in the top bar.

**When a design or reference depicts something real, match it 1:1.** Measure against real captures: font, glow, colour, spacing, saturation. Don't restyle or "improve" pieces he didn't mention, and nothing should look pasted on. If you can't see the reference, ask for it.

**Loading and states.**
- Zero layout shift. Each route gets a skeleton that matches the final layout pixel for pixel, never a spinner, "Loading…" text or blank space. Images get a blur placeholder; videos get an image placeholder until they load.
- Loading buttons keep their label, with the spinner beside it.
- Errors are visible: the field highlights, the form turns red, and the message says what to do. Generic "something went wrong" or empty answers are unacceptable.
- Disabled actions show as disabled, with a tooltip saying why. Never hide them, and never let them fail silently.
- Red means blocking. Use red pills ("Action needed") only for things that block the user.
- New states and warnings go into the existing component pattern, not a one-off message.

**Motion.** Keep it subtle, professional and consistent with the site's existing animations. Marketing pages share the same entrance and scroll animations. Only move what needs to move. Never remove existing animations, and never make them obnoxious. Components keep a fixed size across variants and states, with no jumping. Theme switches don't flash. Check motion frame by frame on the real preview.

**Consistency.** One accent colour in both themes, the current app icon everywhere (favicon included), one star style, one score shown the same everywhere, and one set of terms. Shared components mean a fix reaches every copy. Web, iOS, Android and desktop ship the same design and copy together; compare them side by side before showing him.

**Inputs.** Use purpose-built inputs:
- chips, not comma-separated text
- image pickers that show the image
- multi-select filter bars
- icon and emoji pickers
- inline rename, not a popup
- separate OTP digit boxes

Show progress as a bar, not "0 of 5 left". Rows and thumbnails are clickable.

**Readable long-form.** No all-lowercase or monospace body text. Long articles get a table of contents. Design for the real image aspect ratio. Darken the background behind text that sits over imagery.

## Imagery and marketing assets

- **Real, not generated.** Use real product UI and real photography. Never use AI-generated product photos or stock people in place of the real thing. Every article and listing gets a relevant image. Use the real platform icons, as one shared component.
- **Store screenshots and social slides** are captioned marketing frames, not bare phone captures. They cover the key features with realistic people and data (never a placeholder like "Screenshots" as the user's name). Stage them the same way every time: the latest device frame, 9:41, and identical status bar.
- **Showcase imagery** shows specific crafted UI details (a component, a blur, a flow), the way Apple's newsroom shows features. Not homepages or abstract shapes.
- **Ads end with a call to action**, not just a name and URL.
- **People in imagery** look realistic and diverse, and fit the real business.
- **OG images and favicons:** a real image, not text on a background; a distinctive mark, not a generic one.
- **Before/after comparisons** wait for fonts and images to load, and keep both sides in sync.

## UX

- **Don't make users decide or work.** Prefill from what's already known. Prefer one-tap actions and preset options with an "Other" field. Warn instead of block. Show conditional settings only when they apply. No repeated logins or re-pairing.
- **Automatic over manual.** Self-healing behaviour and sensible defaults beat toggles, alerts, admin pages and human review queues. Automated pipelines run without human approval gates.
- **One message per state.** Don't stack redundant notices.
- **Destructive bulk actions** get a confirmation that explains what's about to happen.
- **Navigation never feels stuck.** Use route loading states and transitions.
- **Public-facing failures recover quietly.** No error message for visitors: reload, then redirect to a safe page.
- **Don't drop data.** Import everything, keep records (mark them removed rather than deleting), and don't exclude segments on your own.
- **Track what matters.** Outbound links that earn revenue go through a tracked redirect. Times show in the user's local timezone.

## Copy and naming

- **Short, plain, human.** Use the words users already know ("plan", "50% off", "Update"). Respect stated length limits exactly.
- **Lead with the real angle or the headline number.** For example, "4.5x more accurate" beats "within 100ms", and a release post leads with the biggest change, not a minor tweak. Leave trivial internal changes out of release notes.
- **No AI tells:**
  - filler phrases
  - "how it works" or process explanations nobody asked for
  - self-references ("ours", "we wrote this", "AI correspondent")
  - all-caps titles
  - a subheading repeated in the intro
  - generic marketing tone
- **Public copy never mentions mocks, simulations, latency, internal caveats or mechanics.** It contains no claims that might not hold.
- **Customer emails and replies** are short and outcome-first: what was fixed, plus the result. Don't imply something was broken, and don't imply past wrongdoing that didn't happen. Leave out internal counts and rankings. Check the recipient, that the body appears exactly once, and the sign-off (his full name, not a nickname). He reviews before anything external is sent.
- **Domain-correct terms.** Use the product's official names and the audience's vocabulary. No jargon acronyms in user-facing UI. Keep established names users know rather than clever renames.
- **One source of truth for UI copy.** Quote sources verbatim, and say where any copy came from.
- **On-brand and playful where the brand is.** Check for double meanings and for negativity toward any group. Don't invent brand lore.
- **Creative work** (names, overlay text, hooks) needs a much higher bar on the first round. Names sound like real brands, are distinct from each other, and don't all follow one formula. Overlays should actually be funny. Check the whole set for clashes. Unprompted creative touches tied to the content are exactly what he wants.
- **Status updates** cover what's actionable, where users are lost, the key numbers, and what's next. Not a data dump.

## Code

- **Names say exactly what the thing does.** A function that saves a result is `saveResult`, not `complete`. Rename anything whose name has drifted from its behaviour, and avoid near-duplicate names.
- **Reuse before you write.** Look for an existing helper, type, flag or prop first. Import types instead of redeclaring or re-exporting them under new names. DRY away copy-paste drift.
- **No speculative machinery.** No special cases, retry counters, extra props, guards, caps, regex heuristics or scheduled backstops "just in case". Forcing a tool for accuracy (a calculator for maths) is fine.
- **Packages over hand-rolling.** Use well-maintained packages with types, and plugins over home-grown versions. Keep heavy libraries out of browser bundles. Prefer the simplest architecture: one app, one domain, direct connections.
- **Use the project's own layers.** Fetch through its data-fetching layer, not raw `fetch`. Use the ORM in tests, not raw queries. Write scripts in TypeScript. Infra changes go through infrastructure-as-code; a CLI hotfix is acceptable only alongside the matching IaC change.
- **Style** (unless the repo's linter says otherwise):
  - Guard clauses get braces and a blank line after the early return.
  - No other blank lines inside functions.
  - Inline trivial temporaries.
  - Don't thread flags through layers when the data is reachable directly.
- **Comments:**
  - A short `/** */` on each function saying what it does.
  - Otherwise comment rarely and briefly, and never on self-explanatory lines.
  - No decorative banner comments.
- **Tests:** for bugs, write a failing test first. Test real behaviour, not trivial assertions. Don't duplicate existing end-to-end coverage. Payments, sign-up and cancellation get thorough tests.
- **Cleanup:** delete leftover code after switching approaches, and remove unused fields and dead config. No redirects for moved routes before launch.
- **Cost:** use the cheapest model that does the job well. Run small tests before big runs. Flag fixed monthly fees and paid add-ons before adding them.

## Scope

- **Fix the issue at hand and file the rest.** Unrelated findings become their own issue; closely related work folds into the current one. Stay in the project and the file he pointed at.
- **Before removing something, explain why it exists** (Chesterton's fence). If something may be intentional design, ask before "fixing" it.
- **Never overwrite his existing designs or edits,** including when adopting a template. The project's own design system wins.
- **One-off scripts and backfills** run locally, not as admin UI or as code in the PR. They log failures and keep going, write audit events, and dry-run first when they touch production.
- **Ignore stale reports**: anything from before the fix, older than a month, or preview-only.

## Verification and evidence

- **"Done" means it works in the real flow.** You tested the link, form, upload, deploy or email yourself. Never say something is running or live without checking.
- **UI:** take screenshots of every state, at desktop and mobile widths, on each platform touched. Look at them yourself and fix what you see before sending. Use a real browser (Firefox MCP or Playwright), not a test runner's screenshots.
- **Behaviour or visual changes** get a video: before and after, side by side, at phone size. A short walkthrough video works well for flows.
- **Prove fixes with real data at scale.** Replay against production data, with 1,000+ runs rather than a small sample, before changing or removing core behaviour. Base recommendations on data you pulled, not estimates from code.
- **Check the blast radius.** Look for regressions both ways (new false positives, and cases that were never flagged), running jobs that might be interrupted, index and row-count impact, and downtime. Say what it touches and what downtime to expect before acting.
- **Grade strictly.** Don't call anomalies harmless or report a pass on loose criteria.

## PRs and issues

- **Follow the repo's flow.** In solo repos, "commit and push" means push to main so it deploys. In team repos, keep PRs small with one concern each, stacked if big, and verify on the preview build yourself by walking the test plan.
- **PR descriptions** say what was solved, why the new approach is better, and how it was tested or replayed. Screenshots cover every state, under proper headings, with realistic data. No vague lines.
- **Issues:**
  - Use only `## Context`, `## Deliverables` and `## Details`, and leave out empty sections.
  - Make them single issues, typed correctly as feature, improvement or bug.
  - Split multi-phase work into blocking issues.
  - Follow-ups after a merge get new issues.
- **Keep the PR and the issue in sync with what was actually done.** Edit the issue itself instead of commenting, and remove questions once they're answered.
- **Review bots:** decide which comments are worth addressing and draft replies. Post only when he says to.
- **Nothing external (chat messages, issue comments, PR replies, emails) goes out until he OKs it.** Offer options to choose from.

## Working with him

- **He dictates.** Read for intent, not literal wording. If an instruction is ambiguous and destructive ("no animations anywhere" could mean add some or remove all), confirm first.
- **Planning:** for big work, write a short feature doc first and ask questions as multiple choice, with your recommendation first and one plain sentence per option. While he's still exploring, give a researched recommendation and wait. After that, let the data decide.
- **Once a direction is set, keep going.** Build end to end and go with your own recommendations on open decisions. Do the hands-on steps yourself (env vars, deploys, dashboards, browser tasks). If another process is holding the browser automation, free it. Look values up in past sessions and sibling projects before asking. Never end a turn idle mid-task.
- **Show progress, don't polish in silence.** Give him something to look at soon. Post short updates on long waits so he never has to ask "stuck?". Keep test loops fast.
- **When he corrects a premise, take it as fact** and recheck anything that depended on it.
- **Raise compliance, legal or privacy concerns once, up front,** before doing setup work, not halfway through.
- **For visual decisions,** mock the options side by side next to the current state, with a recommendation.
- **Hand-offs are copy-pasteable:** SQL with the expected result, CSVs with only the needed columns, exact lists of what to change. For non-engineering readers, add context.
- **He values evidence-backed recommendations** and reviews that name a concrete risk ("this lookup is now copied in four places").

## Demos, videos and reels

- **Cut every dead moment.** Cut right at the action, with clips around 1–1.5s and the hook first. Make the point obvious. Being complete beats hitting a target length.
- **The overlay matches the footage frame for frame.** Never show or check off something that isn't happening on screen. Sound effects hit exactly on the action.
- **Sync to the song's real highlight and lyric,** not the intro.
- **No artificial slow-mo, timelapse or speed-ups,** and no footage swaps he didn't ask for.
- **Use real, recognisable sounds and graphics,** never generated stand-ins. Use the exact assets he names, untrimmed.
- **Flattering frames of the people on camera,** including the first and last frames. Review every clip in full, not from thumbnails, and add variety.
- **Previews always include the music.** "No audio" means no music; keep the voice.
- **Preview a small piece first** (the intro) before applying a change everywhere.
- **Thumbnails** keep text away from the bottom, where player controls cover it.

## Self-check before showing him anything

- Did I research references and follow existing patterns, or does this look generic?
- Could anything here be cut (words, controls, lines, badges) without losing meaning?
- Is this the smallest diff that fixes the root cause, reusing what already exists?
- Did I verify it in the real flow, with screenshots at desktop and mobile widths and real data?
- Does it look and read the same on every platform it ships to?
- Are names accurate, copy minimal, and comments few?
- Is anything out of scope that should be its own issue?
- Is my message short, with the answer first?
