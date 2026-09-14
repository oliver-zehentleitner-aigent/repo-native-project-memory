# Repo-native project memory

**Your repository already is your project's memory. One directory was missing.**

> Project memory is not another database for your coding agent. Your repository already is the project memory. AI just exposed the one thing it was systematically missing: why.

A repository is the one place a software project keeps everything that describes it: what it is, how to use it, how to build and test it, what changed, who may contribute how, under which terms. That layout has worked for decades, for people, without a platform. It works for AI coding agents too, for the same reason: everything is plain files, next to the code, versioned by Git, readable by anything that can read a directory.

This page states a thesis, not a product: the repository is the project memory. It needs no extra service, no account, no subscription. It already holds most of the durable knowledge needed to understand and change a codebase, for people and for agents alike. What it lacked is the layer that holds the reasoning worked out in AI sessions, the why, and that layer can be repo-native too.

## Three things that have held for twenty years

1. **Keep everything in one place.** README, docs, tests, build scripts, changelog, license: one clone carries the whole project. Anyone who has it has all of it.
2. **Stay independent, open and simple.** Plain text, an open version control system, no vendor between you and your files. That is why a repository from 2006 still opens today, and why one from today will open in 2046.
3. **Whoever works on the project needs access to all of its knowledge.** That used to mean people. Now it means the coding agents too, and the classic layout already covers almost everything they need.

## What a repository already remembers

| Element | The question it answers | Who reads it | Who maintains it today |
|---|---|---|---|
| `README.md` | What is this, should I care, how do I start | evaluators, new developers, agents on first contact | humans and agents |
| `docs/` | How do I configure, operate, troubleshoot | users, agents doing the work | humans and agents |
| `CHANGELOG.md` | What changed, in which version | upgraders, reviewers, agents reconstructing the past | increasingly agents, more detailed than any human kept it |
| `CONTRIBUTING.md` | How does a change get in, which conventions apply | contributors, agents about to change code | humans |
| `LICENSE`, `SECURITY.md`, `CODE_OF_CONDUCT.md` | Under which terms, how to report, how to behave | everyone | humans |
| `tests/` | What the code is supposed to do, executably | developers, CI, agents checking their own work | humans and agents |
| `pyproject.toml`, `package.json`, `Cargo.toml`, `composer.json`, … | What this depends on, how it is built and published | build tools, agents setting up | humans and agents |
| `AGENTS.md`, `CLAUDE.md` | Where an agent should look first, which conventions to follow | agents | humans, since 2025 |
| Git history | Who changed what, when, in which commit | everyone, if they dig | everyone, as a byproduct |

That is project memory. It always was. Every row is a plain file or a Git object; every row comes with the clone; every row answers *what* and *how*. Issues and pull request discussions sit next to it as hosted collaboration memory — valuable, searchable, and not in the clone; whatever from there should outlive the platform has to be written into one of the rows above.

## Why the question comes up now

Because coding agents have a memory problem, and it is not the one people usually name. An agent remembers what is in its context window. A new session starts from nothing: the explanation you gave yesterday is gone, the question you settled gets asked again, the turn you ruled out gets proposed again. That is session memory, and many of the products now sold as "project memory" are a response to it.

Take the memory an agent needs apart and it falls into three zones:

- **Personal knowledge** — who you are, how you like to work, what you never want to see again. This belongs to you, not to a project: a global note, an Obsidian vault, a Markdown file every agent on your machine can read.
- **General knowledge** — what the world knows. An agent does not have to hold it; like you, it can look it up.
- **Project knowledge** — what this project is, how it works, what changed, and why it is the way it is. This belongs in the project, and travels with it.

The third zone is the table above, and the table is nearly complete. Agents already maintain the README, the docs and the changelog, and they use them without being told to — the layout is so established that every agent knows what a `README.md` or a `CHANGELOG.md` is for. They know *what* the project does and *what* changed. What they cannot find anywhere is *why*: which alternatives were considered, which were rejected and for what reason, which workaround exists because of which incident, which constraint the code does not show. That reasoning is produced in every working session, in the conversation, and a new session throws it away.

## The missing layer, and where it goes

People had a mechanism for the why, for the few large decisions a year: Architecture Decision Records, written by hand, and most projects still have none. What nobody had was an affordable mechanism for the hundred small reasons that actually make a codebase what it is — the retry loop that looks over-engineered, the flag a customer's proxy made necessary, the ordering constraint that looks safe to parallelize. Those lived in one person's head and left with that person, because writing each one down cost more than it seemed worth. Agents change that cost: the reasoning is spoken out loud anyway, and an agent that is in the conversation can write it down as a byproduct, synthesized, short, in a fixed form, committed together with the code it explains. Sometimes there is only a reason and no code, when a change was started and abandoned once the reason not to became clear. That is the case that matters most, because nothing else, no diff, no commit, no PR, would ever record it.

So the missing layer is one more directory:

| Element | The question it answers | Who reads it | Who maintains it |
|---|---|---|---|
| `context/` | Why is it built this way, what was tried and rejected | anyone about to change something, human or agent | agents in the session where the reason surfaces, confirmed by people |

It closes a natural gap instead of opening a new system. One honest difference to the other rows: `README.md` needs no instruction, every agent already knows what it is for; `context/` is not an established structure yet, so for now an agent needs to be told what goes there, in which form, and when to ask first. That is what the skill below is — the convention and its implementation, until the convention is as ordinary as a changelog. It lives where the rest already lives, is versioned by the same Git, travels with every clone and fork, shows up in the pull request beside the code diff where the reviewer needs it, and merges under the same review as the code. No extra layer to buy, no service to keep running, no account whose expiry takes the memory with it.

## The system, in five parts

Repo-native project memory is not one tool. Read as an architecture: the README, docs, tests, configuration and history hold the *what* and *how*; `context/` holds the *why*; Git stores, versions, distributes and reviews all of it; the agent is the interface that captures and retrieves; Keep the Why is the convention and the implementation for the why layer. In parts:

| Part | Role | What it is | Required? |
|---|---|---|---|
| **The repository** | stores, versions, distributes, reviews | Git, and the layout above | yes, and you already have it |
| **The agent** | the interface: captures, retrieves, asks | whichever coding agent you work with | yes, any that reads a `SKILL.md` or an `AGENTS.md` |
| **[Keep the Why](https://keepthewhy.com)**, the skill | integrates into the working session, synthesizes what is worth keeping into `context/` under clear rules, asks before it writes when unsure | instructions, in the open cross-agent skill format | it is the part that writes the why; without it the layer stays empty |
| **`keep-the-why-lint`** | checks and verifies the structure: fields, values, index, nothing hidden | a small Python package, in CI or run by the agent after it writes | no; nice to have the moment more than one person or agent writes |
| **`keep-the-why-dashboard`** | shows it: the graph, an entry with its Git history, what still needs a person | a read-only page over the files and Git, local or exported | no; everything runs through the agent anyway |

That is it. Task fulfilled, no further complexity. Anything beyond it, project management, dashboards for teams, workflows, can be built on top, and for a company that may be the right call. Open source should not have to depend on it. A project that stops using every part except the repository loses nothing: the directory is still Markdown, still in Git, still readable.

## What repo-native means, as a checklist

- Plain files in the repository; nothing lives only in a service.
- Versioned and distributed by Git; no second synchronization problem.
- Readable by humans and by agents with no tool in between.
- Reviewed like code: in the pull request, next to the change it explains.
- No account, no subscription, no telemetry, no daemon, no database.
- Works without every optional part; degrades to Markdown, never to nothing.

## What this is not

- Not a product. There is nothing here to install; the parts that exist are linked above and each stands on its own.
- Not a replacement for issue trackers, project management or team workflows. Those manage work. This remembers why the code is what it is.
- Not a claim that agents replace the discipline of thinking, pruning and questioning that keeps any documentation honest. They lower the cost of writing it down; people still decide what is true.

## Who

Oliver Zehentleitner — [GitHub](https://github.com/oliver-zehentleitner) · [blog](https://blog.technopathy.club). This page is the thesis; the practice is [Keep the Why](https://keepthewhy.com), and this repository keeps its own `context/` in the same format, because the argument should hold for the page that makes it.

## License

[MIT](LICENSE)
