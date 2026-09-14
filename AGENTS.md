# AGENTS.md

This repository is a thesis page, not a codebase: `README.md` is the canonical text, `docs/index.html` + `docs/style.css` are the hand-built site (no build step, no dependencies — GitHub Pages serves `docs/` as-is), `context/` keeps the reasoning behind the page itself.

- The content: `README.md`; the site in `docs/` says the same in its own layout — a change to the thesis is made in both
- Why things are the way they are: `context/index.md`
- If `AGENTS.local.md` exists in this checkout, read that too — personal/local notes, not committed.

Read `context/index.md` before changing the page's structure or claims; the choices behind them are recorded there.

## Keep the Why

This project records the reasoning behind its content with the Keep the Why
skill (https://keepthewhy.com) — the `.keep-the-why` file at the project
root is its config. Before doing anything else in a session, whatever the
first request is about, load the skill: in Claude Code, invoke the
`keep-the-why` skill (Skill tool); in any other agent, load the installed
`keep-the-why` skill (or read its `SKILL.md`) and follow it, including the
`references/*.md` files it points to for the situation at hand.
