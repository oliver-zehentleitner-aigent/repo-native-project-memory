# Positioning

## A thesis page, not a specification and not a tool

**Type:** decision
**Status:** active
**Evidence:** confirmed
**Source:** maintainer decision, 2026-09-14, at the repository's creation
**Revisit when:** a second author wants to contribute more than wording, or the page starts prescribing a format of its own

This repository is one `README.md`, rendered as a site, plus the reasoning behind it. It states what repo-native project memory is and why the classic repository layout already is most of it. It defines no format, ships no code, and links the parts that exist instead of absorbing them.

**Reason:** the argument is older than any tool: keep everything in one place, stay independent and simple, give whoever works on the project access to all of it. A page can make that argument for twenty years; a tool would tie it to a release cycle. The format for the missing layer already has a normative specification elsewhere (Keep the Why); repeating it here would create a second source of truth for the same thing.

**Rejected alternative:** an umbrella repository that vendors or mirrors the skill, the linter and the dashboard. Rejected — three release cycles in one repository, and the page would become a distribution channel instead of an argument.

**Rejected alternative:** a "standard" with its own name, badge and conformance rules. Rejected — the standard is the repository layout everyone already uses; naming it again would be the kind of extra layer the thesis argues against.

## The repository, not the tool, is the unit of the argument

**Type:** decision
**Status:** active
**Evidence:** confirmed
**Source:** maintainer decision, 2026-09-14
**Revisit when:** a repo-native layer appears that cannot be expressed as plain files in the repository

The page's first table lists what a repository already remembers, file by file, before it names anything new. The new layer, `context/`, is presented as one more row in that table, and the parts that maintain it are presented as optional except for the repository and the agent.

**Reason:** the claim is that project memory needs no platform because the repository is one. If the page led with a product, it would be making the opposite claim. Putting `context/` in the same table as `README.md` and `CHANGELOG.md` says what kind of thing it is: a file next to the others, not a system beside them.

**Consequence:** every part in the "five parts" table has a "required?" column, and only the repository and the agent say yes. The skill is what writes the why, but a project that stops using it keeps a readable directory.

## Keep the Why is named as one part, not as the whole

**Type:** decision
**Status:** active
**Evidence:** confirmed
**Source:** maintainer decision, 2026-09-14
**Revisit when:** the thesis and the skill start to diverge in what they call the missing layer

The page says the repository is the project memory and that Keep the Why is the part that writes its missing layer. It does not say Keep the Why is the project memory.

**Reason:** the maintainer built Keep the Why first, as a decision-record tool for agents, and arrived at the broader view afterwards: the tool is one facet of something that mostly exists already. Stating the broader view honestly means giving the tool its place and no more. It also keeps the page useful to someone who wants the idea and a different implementation.

**Rejected alternative:** folding this page into keepthewhy.com as a "philosophy" section. Rejected — that site is the practice, with releases and measurements; the thesis should be readable without adopting any of it.

## The site is two hand-written files, not a documentation generator

**Type:** decision
**Status:** active
**Evidence:** confirmed
**Source:** maintainer decision, 2026-09-14, after seeing the first deploy
**Revisit when:** the page grows beyond one screen of sections, or a second page is needed

`docs/` holds `index.html` and `style.css`, written by hand, served by GitHub Pages without a build step. The first version used the same MkDocs Material setup as keepthewhy.com and looked identical to it.

**Reason:** this is a thesis page, not a documentation site: one argument, one screen of sections, meant to be read once. A docs generator gave it a docs site's furniture — navigation drawer, search, section index — and the same face as the practice it names, which blurred the one distinction the page exists to make. Two plain files also keep the page's own claim: no dependencies, no build, opens unchanged in twenty years. System fonts, no external requests, for the same reason.

**Rejected alternative:** MkDocs Material with a custom theme. Rejected — the theme would have to be maintained against a generator that has announced a breaking rewrite, for a page that needs neither search nor navigation.

**Consequence:** the thesis exists twice, in `README.md` (canonical, what GitHub shows) and in `docs/index.html` (the same sentences, laid out). A change to the argument is made in both; the page is small enough that this costs less than a build pipeline would.

## Claims are written to be hard to attack, not to be loud

**Type:** decision
**Status:** active
**Evidence:** confirmed
**Source:** maintainer review of the first published version, 2026-09-14
**Revisit when:** a sentence on the page is challenged on facts, or a claim is added that the page cannot back

The page avoids absolutes where they are technically assailable: not "one clone carries the whole project" but the repository-native knowledge; not "every agent knows what a README is" but coding agents understand it; not "every product sold as project memory" but many; not "it was complete for humans" but it holds most of the durable knowledge. Issues and pull-request discussions are named as hosted collaboration memory, outside the clone, with the rule that what matters long-term has to be written back into the repository. Keep the Why is introduced as one convention and implementation for the why layer, never as the project memory itself.

**Reason:** the thesis competes with products that make loud claims; its advantage is that it can be checked. A single sentence that a reader can refute — "GitHub issues are not Git objects" — costs more credibility than a stronger claim would have won. The strongest version of the argument is the precise one: the repository already is the memory, and AI exposed the one layer it was missing.

**Rejected alternative:** keeping the sharper wording for effect and correcting on challenge. Rejected — a thesis page has no second chance with a reader who found the first error.
