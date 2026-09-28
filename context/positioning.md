# Positioning

## A thesis page, not a specification and not a tool

**Id:** 577decbf-5b79-4452-b51d-273a119ccb7d
**Type:** decision
**Status:** active
**Evidence:** confirmed
**Source:** maintainer decision, 2026-09-14, at the repository's creation
**Revisit when:** a second author wants to contribute more than wording, or the page starts prescribing a format of its own
**See:** https://github.com/oliver-zehentleitner/keep-the-why — 7feab02f-0de5-48f6-8dfa-20fa233cf0a1 — as of 2026-09-28

This repository is one `README.md`, rendered as a site, plus the reasoning behind it. It states what repo-native project memory is and why the classic repository layout already is most of it. It defines no format, ships no code, and links the parts that exist instead of absorbing them.

**Reason:** the argument is older than any tool: keep everything in one place, stay independent and simple, give whoever works on the project access to all of it. A page can make that argument for twenty years; a tool would tie it to a release cycle. The format for the missing layer already has a normative specification elsewhere (Keep the Why); repeating it here would create a second source of truth for the same thing.

**Rejected alternative:** an umbrella repository that vendors or mirrors the skill, the linter and the dashboard. Rejected — three release cycles in one repository, and the page would become a distribution channel instead of an argument.

**Rejected alternative:** a "standard" with its own name, badge and conformance rules. Rejected — the standard is the repository layout everyone already uses; naming it again would be the kind of extra layer the thesis argues against.

## The repository, not the tool, is the unit of the argument

**Id:** 2f1c1642-f8f0-4b5d-9bb7-afdff49924e5
**Type:** decision
**Status:** active
**Evidence:** confirmed
**Source:** maintainer decision, 2026-09-14
**Revisit when:** a repo-native layer appears that cannot be expressed as plain files in the repository

The page's first table lists what a repository already remembers, file by file, before it names anything new. The new layer, `context/`, is presented as one more row in that table, and the parts that maintain it are presented as optional except for the repository and the agent.

**Reason:** the claim is that project memory needs no platform because the repository is one. If the page led with a product, it would be making the opposite claim. Putting `context/` in the same table as `README.md` and `CHANGELOG.md` says what kind of thing it is: a file next to the others, not a system beside them.

**Consequence:** every part in the "five parts" table has a "required?" column, and only the repository and the agent say yes. The skill is what writes the why, but a project that stops using it keeps a readable directory.

## Keep the Why is named as one part, not as the whole

**Id:** 6288e2c2-5d05-405a-8355-3d1c2564adf0
**Type:** decision
**Status:** active
**Evidence:** confirmed
**Source:** maintainer decision, 2026-09-14
**Revisit when:** the thesis and the skill start to diverge in what they call the missing layer
**See:** https://github.com/oliver-zehentleitner/keep-the-why — 92734fc2-5bb5-47e4-ab6e-fad8ee26551f — as of 2026-09-28

The page says the repository is the project memory and that Keep the Why is the part that writes its missing layer. It does not say Keep the Why is the project memory.

**Reason:** the maintainer built Keep the Why first, as a decision-record tool for agents, and arrived at the broader view afterwards: the tool is one facet of something that mostly exists already. Stating the broader view honestly means giving the tool its place and no more. It also keeps the page useful to someone who wants the idea and a different implementation.

**Rejected alternative:** folding this page into keepthewhy.com as a "philosophy" section. Rejected — that site is the practice, with releases and measurements; the thesis should be readable without adopting any of it.

## The site is two hand-written files, not a documentation generator

**Id:** 9c7f3476-45ea-4a6e-9364-155663041ceb
**Type:** decision
**Status:** active
**Evidence:** confirmed
**Source:** maintainer decision, 2026-09-14, after seeing the first deploy
**Revisit when:** the page grows beyond one screen of sections, or a second page is needed
**See:** positioning.md#the-context-dashboard-is-exported-into-the-site-by-the-deploy-workflow-beside-the-two-hand-written-files — b864ddeb-81e7-4689-b367-45181e76928f — as of 2026-09-28

`docs/` holds `index.html` and `style.css`, written by hand, served by GitHub Pages without a build step. The first version used the same MkDocs Material setup as keepthewhy.com and looked identical to it.

**Reason:** this is a thesis page, not a documentation site: one argument, one screen of sections, meant to be read once. A docs generator gave it a docs site's furniture — navigation drawer, search, section index — and the same face as the practice it names, which blurred the one distinction the page exists to make. Two plain files also keep the page's own claim: no dependencies, no build, opens unchanged in twenty years. System fonts, no external requests, for the same reason.

**Rejected alternative:** MkDocs Material with a custom theme. Rejected — the theme would have to be maintained against a generator that has announced a breaking rewrite, for a page that needs neither search nor navigation.

**Consequence:** the thesis exists twice, in `README.md` (canonical, what GitHub shows) and in `docs/index.html` (the same sentences, laid out). A change to the argument is made in both; the page is small enough that this costs less than a build pipeline would.

**Consequence (2026-09-28):** the deploy workflow adds a generated dashboard of this repository's `context/` under `/dashboard/live/`. It is a view of the reasoning, not a second page of the thesis: `index.html` and `style.css` stay hand-written and build-free, and the footer's "two plain files" still describes the page that makes the argument.

## Claims are written to be hard to attack, not to be loud

**Id:** 8dd3f6b9-3539-4fd2-bac3-a0ec1880f71b
**Type:** decision
**Status:** active
**Evidence:** confirmed
**Source:** maintainer review of the first published version, 2026-09-14
**Revisit when:** a sentence on the page is challenged on facts, or a claim is added that the page cannot back

The page avoids absolutes where they are technically assailable: not "one clone carries the whole project" but the repository-native knowledge; not "every agent knows what a README is" but coding agents understand it; not "every product sold as project memory" but many; not "it was complete for humans" but it holds most of the durable knowledge. Issues and pull-request discussions are named as hosted collaboration memory, outside the clone, with the rule that what matters long-term has to be written back into the repository. Keep the Why is introduced as one convention and implementation for the why layer, never as the project memory itself.

**Reason:** the thesis competes with products that make loud claims; its advantage is that it can be checked. A single sentence that a reader can refute — "GitHub issues are not Git objects" — costs more credibility than a stronger claim would have won. The strongest version of the argument is the precise one: the repository already is the memory, and AI exposed the one layer it was missing.

**Rejected alternative:** keeping the sharper wording for effect and correcting on challenge. Rejected — a thesis page has no second chance with a reader who found the first error.

**Consequence (2026-09-22):** the term itself is defined in one sentence directly under the lede, in the page's meta description and in the README's opening — "repo-native project memory is the durable knowledge about a software project kept as plain files in its repository … readable by people and coding agents alike". Added because AI-search answers, asked what the term means, defined it from other projects' pages and cited this page only for where Keep the Why fits: the page carried the thesis in its first lines but never an "X is Y" sentence, which is what outside systems quote. The sentence names, it claims nothing, so it sits inside this entry's rule rather than against it.

## The context dashboard is exported into the site by the deploy workflow, beside the two hand-written files

**Id:** b864ddeb-81e7-4689-b367-45181e76928f
**Type:** decision
**Status:** active
**Evidence:** confirmed
**Source:** maintainer request, 2026-09-28
**Revisit when:** the export needs anything from this repository beyond a `pip install` and one command, or cross-repository links stop needing a published export
**See:** positioning.md#the-site-is-two-hand-written-files-not-a-documentation-generator — 9c7f3476-45ea-4a6e-9364-155663041ceb — as of 2026-09-28
**See:** positioning.md#keep-the-why-is-named-as-one-part-not-as-the-whole — 6288e2c2-5d05-405a-8355-3d1c2564adf0 — as of 2026-09-28
**See:** https://github.com/oliver-zehentleitner/keep-the-why — ffdb33a5-3d9c-43b8-951b-a95a90ac2a74 — as of 2026-09-28

`docs.yml` installs `keep-the-why-dashboard` on the runner and exports this repository's `context/` into the uploaded site at `/dashboard/live/` (`index.html`, `state.json`, `badge.svg`), with the full Git history for the dates and authors, not anonymized. `.keep-the-why` names the published `state.json` as `dashboard-state`. The page links it from the paragraph that says this repository keeps its own `context/`.

**Reason:** the entries here and in Keep the Why's `context/` reference each other with `See` lines across the two repositories. A dashboard follows such a reference through the target's published export, found by the `dashboard-state` line; without an export of its own, every reference into this repository would end at the canonical and the Id. The same export lets a reader browse the page's reasoning without cloning it, which the page argues any repository's `context/` should allow.

**Rejected alternative:** a family, with Keep the Why as parent or child. Rejected — a family routes entries between its members, and this page is deliberately not part of the practice it names (the entry on naming Keep the Why as one part); two unrelated projects that cite each other need references, not routing.

**Rejected alternative:** committing the export to `docs/`. Rejected — generated files in a directory whose rule is two hand-written files, and a stale dashboard the day someone forgets to regenerate it.
