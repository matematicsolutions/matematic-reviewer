# matematic-reviewer

A grumpy senior editor for your copy. It reads what you just wrote, gives a verdict and lists
what is wrong, each charge anchored to `file:line`. It never rewrites and never praises:
"ok" is the rarest verdict, so when it comes, it means something.

| Skill | Language | Language-specific layer |
|---|---|---|
| `reviewer-en` | English | English waffle, hype words and AI tropes |
| `marko-pl-content` | Polish | Polish marketing waffle and AI tropes, spelling outdated by the 2026 reform (offline scanner) |
| `reviewer-pt` | Portuguese (pt-BR default, pt-PT on request) | gerundism, pronominal "mesmo", variant mixing, legal terms translated word for word |

All three share one format:

```
**Verdict:** {disaster | weak | mediocre | ok}

{One sentence: what dominates.}

1. `file:line` - {one concrete charge}.
2. `file:line` - {one concrete charge}.
```

At most eight charges. The charges name the problem, not the fix: pair the reviewer with a
writer or with [matematic-humanizer](https://github.com/matematicsolutions/matematic-humanizer)
when you want the text changed.

## What it reviews

By default the uncommitted changes in `.md`, `.html` and `.txt` files (`git diff HEAD`).
Otherwise the content files edited in the session, a file you name, or text you paste.
Say "reviewer, look at this", "marko?" or "revisa isso".

## House style is a default

Each edition ships one opinionated default: hyphens only, no em dash. If you give Claude your
own style guide, yours wins. The other charges apply either way.

## Install

In Claude Code:

```
/plugin marketplace add matematicsolutions/matematic-reviewer
/plugin install matematic-reviewer@matematic-reviewer
```

Single-skill zips, no plugin needed, are on the MateMatic Boutique:
[English](https://matematicsolutions.com/en/boutique/skills#skill-reviewer-en) ·
[Polish](https://matematicsolutions.com/boutique/skille#skill-marko-pl-content) ·
[Portuguese](https://matematicsolutions.com/pt/boutique/skills#skill-reviewer-pt)

## Data

The skills have no connectors and make no network calls of their own. They read files in
your project and the text in your conversation, which Claude processes the same way as any
other message you send it. The Polish spelling scanner (`skills/marko-pl-content/scripts/`)
runs locally on the Python standard library and does not touch the network.

## Licence

MIT. Adapted from [julianmemberstack/marko](https://github.com/julianmemberstack/marko) (MIT);
see `NOTICE` for full attribution.
