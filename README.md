<div align="center">

<img src="./assets/michael.png" width="320" height="320" alt="Michael Cummings" />

# michael-taste

**Teach Claude how I like things built, so the first draft is the one I ship.**

[![Claude Code skill](https://img.shields.io/badge/Claude%20Code-skill-D97757)](#install)
[![license: MIT](https://img.shields.io/badge/license-MIT-blue)](./LICENSE)

</div>

## No more

> "This looks super basic."
>
> "Too wordy."
>
> "We aren't reinventing the wheel here."
>
> "Did you check this on mobile?"
>
> "Did you hallucinate that?"
>
> "What are you stopping for? Finish this."

I got tired of saying the same things to Claude over and over, so I had it turn them into a skill. UI, copy, code, PRs, marketing assets, video.

## How it was made

Claude read ~5k of my messages, mostly the replies I sent right after it delivered something, and pulled out what I asked to change and why. A rule only made it in if I said it more than once or said it as a standing preference.

It ended up as 100+ rules across design, copy, code, PRs, marketing assets and video. The seven that cause the most rework go first, and there's a self-check at the end Claude runs before showing me anything.

## Install

```sh
git clone https://github.com/michaelcummingsofficial/michael-taste.git
cp -R michael-taste/skills/michael-taste ~/.claude/skills/
```

Claude loads it on its own when you ask it to build, design or write something.

## Make your own

Some of this will fit you, some won't. Imo the method is the better part. Paste this into Claude Code:

```text
Read my Claude Code transcripts in ~/.claude/projects. Use parallel subagents if there are a lot.
Focus on the messages I sent right after you delivered something, and pull out what I asked you to change and why.
Keep a rule only if I said it more than once or stated it as a standing preference. Skip anything specific to one project.
Write it up as a skill at ~/.claude/skills/my-taste/SKILL.md: a one-line description, the 7 rules that would save me the most rework first, then the rest grouped by area (design, copy, code, PRs, etc).
Keep it short. One line per rule, no background or quotes, only what changes how you work.
```

Or fork this repo and swap in your rules!!

## License

MIT
