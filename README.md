# michael-taste

A Claude Code skill that teaches Claude how I like things built: UI and visual design, copy, code changes, PRs, marketing assets and video. With it loaded, the first draft lands close to what I want, instead of after five rounds of "too wordy", "looks generic" or "did you check this on mobile?".

## How it was made

I mined about 4,100 of my own messages to Claude Code, from roughly 30 projects across two machines. Subagents read every message I sent right after Claude delivered something, and pulled out what I asked to change and why. A rule only made it in if I'd said it more than once or stated it as a standing preference. Project-specific rules were left out.

The skill opens with the seven rules that cause the most rework. A self-check list at the end is for Claude to run before showing me anything.

## Install

Copy the skill into your Claude Code skills folder:

```sh
git clone https://github.com/michaelcummingsofficial/michael-taste.git
cp -R michael-taste/skills/michael-taste ~/.claude/skills/
```

Claude loads it automatically when you ask it to build, design or write something.

## Make your own

These are my preferences, so some will fit you and some won't. The better use is the method: have Claude read your own session transcripts in `~/.claude/projects`, find what you correct repeatedly, and write it up as a skill. Then fork this one and replace the rules with yours.

## License

MIT
