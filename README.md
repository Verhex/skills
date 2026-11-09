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
| [design-system](design-system/SKILL.md) | You define or change shared components, variants or design tokens. |
| [visual-language](visual-language/SKILL.md) | You set or revise the visual direction: type, colour roles, density, motion. |
| [design-critic](design-critic/SKILL.md) | A design needs a review with evidence and a PASS / REVISE / NO-GO verdict. |

The skills are independent of each other. Take one or all.

## Install

A skill is a folder with a `SKILL.md`. Copy the folders you want into the place your agent reads skills from.

For Claude Code, that is `~/.claude/skills/` for every project or `.claude/skills/` inside one project:

```sh
git clone https://github.com/Verhex/skills.git
cp -r skills/beuser ~/.claude/skills/
```

Each folder also carries `agents/openai.yaml` with display metadata for agents that read that format.

## License

[MIT](LICENSE)
