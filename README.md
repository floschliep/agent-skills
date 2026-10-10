# Agent skills

My personal agent skills: workflows I use and refine, with their history in Git.

## Skills

| Skill | Purpose |
| --- | --- |
| [agent-post-mortem](skills/agent-post-mortem/SKILL.md) | Analyze failed agent tasks and choose a better path forward. |
| [check-trajectory](skills/check-trajectory/SKILL.md) | Check an active task for drift in goals, strategy, or scope. |
| [define-outcome](skills/define-outcome/SKILL.md) | Establish the desired outcome and success criteria before planning. |
| [fixing-bugs](skills/fixing-bugs/SKILL.md) | Choose complete fixes and verify the resulting behavior. |
| [review-agent-guidance](skills/review-agent-guidance/SKILL.md) | Capture durable lessons in agent guidance after a task. |
| [shape-change](skills/shape-change/SKILL.md) | Establish observable behavior and data semantics before implementation. |

## Local setup

Keep this checkout as the source of truth and symlink individual skill folders into
`~/.agents/skills`. For example, when that destination does not already exist:

```sh
mkdir -p ~/.agents/skills
ln -s "$PWD/skills/check-trajectory" ~/.agents/skills/check-trajectory
```

Run the link command from the repository root. Repeat for the skills you want.
Edit the files in this checkout, then commit and push changes normally. Keep the
checkout at the same path so the links continue to work.

Each skill includes a `SKILL.md` and any supporting files it needs. These are
personal workflows; some assume Codex tools and are not tested across harnesses.
`fixing-bugs` refers to `diagnosing-bugs`, which I install separately from
[Matt Pocock's skills](https://github.com/mattpocock/skills).

## License

No license has been selected yet.
