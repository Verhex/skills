# Skills

Agent skills for product, design and engineering work. Each one is a short method an AI coding agent loads
when the moment comes: what to establish first, what to produce, and when it is done.

They prescribe no framework, platform or style. A skill reads the project it is used in and works with what is
there, whether that is a mobile app, a website, a desktop tool, a command line or a service.

## The skills

| Skill | Use it when |
|---|---|
| [beuser](beuser/SKILL.md) | You are about to build something a person uses, or need to accept it: write the journey, then have AI agents walk it as the persona on the real product. |
| [readonly-audit](readonly-audit/SKILL.md) | You need an answer about a codebase, system or incident without changing anything, with each claim graded by its evidence. |
| [authority-bootstrap](authority-bootstrap/SKILL.md) | A session starts or resumes: establish what was asked, what is permitted and the state of the workspace before acting. |
| [parallel-execution](parallel-execution/SKILL.md) | Work is split across several agents: cut lanes, brief them, supervise and merge the results. |
| [product-design](product-design/SKILL.md) | The product's model needs shaping before its screens: users, objects, main workflow, information architecture. |
| [agentic-ux](agentic-ux/SKILL.md) | The interface shows or controls AI agent work: state, approvals, intervention, failure and recovery. |
| [enterprise-ux](enterprise-ux/SKILL.md) | You design governance surfaces: scope, roles, permissions, policy, audit, secrets, cost. |
| [workspace-design](workspace-design/SKILL.md) | You design the app's shell and navigation for any form factor. |
| [component-system](component-system/SKILL.md) | You define or change shared components, variants or design tokens. |
| [visual-language](visual-language/SKILL.md) | You set or revise the visual direction: type, colour roles, density, motion. |
| [interface-review](interface-review/SKILL.md) | A design needs a review with evidence and a PASS / REVISE / NO-GO verdict. |

Each skill works alone. None requires another, and none starts another by itself; a skill may name a
neighbour for a different moment, and that pointer only matters if you installed it.

## Which one for which request

Several design skills can match one request. Pick by the question actually being asked, and take the smallest
set.

| The question is | Skill |
|---|---|
| What is this product, who is it for, what are its objects and flows? | product-design |
| How do people move between places and get back? | workspace-design |
| Which components and tokens do we share, and what must each specify? | component-system |
| What should it look like: type, colour, density, motion? | visual-language |
| Who may do what, and how is that shown and audited? | enterprise-ux |
| How do we show and control what an AI agent is doing? | agentic-ux |
| Is this design good enough to accept? | interface-review |
| Does the finished thing work for a real person, end to end? | beuser |
| Is this actually wired up? What happened here? | readonly-audit |
| How do we split this across agents and merge it? | parallel-execution |
| Where do I stand before I act? | authority-bootstrap |

A small visual change needs `visual-language` only. A new admin console may take `product-design`, then
`enterprise-ux` and `workspace-design`, then `interface-review`. Loading all of them for every request costs
context and adds nothing.

## Install

A skill is a folder with a `SKILL.md`. Copy the folders you want into the place your agent reads skills from.

For Claude Code, that is `~/.claude/skills/` for every project or `.claude/skills/` inside one project:

```sh
git clone https://github.com/Verhex/skills.git
cp -r skills/beuser ~/.claude/skills/
```

Each folder also carries `agents/openai.yaml` with display metadata for agents that read that format.

Three skills ship a filled example beside their `SKILL.md`:
[journey spec and verdict table](beuser/journey-spec.md), [lane brief](parallel-execution/lane-brief.md) and
[audit report](readonly-audit/report-template.md).

## Running authority-bootstrap at session start

Agents choose skills by matching the request, and a session start is not a request. To have
`authority-bootstrap` run when a session starts or resumes after compaction, attach it to a session-start
hook. This recipe is for Claude Code only; add it to `.claude/settings.json`:

```json
{
  "hooks": {
    "SessionStart": [
      {
        "hooks": [
          {
            "type": "command",
            "command": "echo '{\"hookSpecificOutput\":{\"hookEventName\":\"SessionStart\",\"additionalContext\":\"Before acting, load the authority-bootstrap skill and take its snapshot.\"}}'"
          }
        ]
      }
    ]
  }
}
```

The hook only adds one line to the agent's context; the skill does the work. Other agents need their own
equivalent, or the skill stays something you ask for by name.

## License

[MIT](LICENSE)
