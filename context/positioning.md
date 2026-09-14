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
