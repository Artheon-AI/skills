# Artheon skills

Artheon's plugin marketplace, named `artheon`. It ships the Agent Skills behind Artheon's offer to Claude and other agents. Each plugin is a folder of plain Agent Skills.

| Plugin | Skills | For |
|---|---|---|
| `knowledge-base` | `notion-nightly-maintenance`, `notion-weekly-maintenance` | Everyone using a Notion knowledge base built from Artheon's template |

## Add the marketplace

Add it once, then install the plugins you need.

**Claude app:** Customize > Plugins > Add > Add marketplace, enter `Artheon-AI/skills`, then install `knowledge-base`. Plugins update on their own.

**Claude Code:**

```sh
claude plugin marketplace add Artheon-AI/skills
claude plugin install knowledge-base@artheon
```

Inside a session, `/plugin marketplace add Artheon-AI/skills` and `/plugin install knowledge-base@artheon` do the same. Run `claude plugin marketplace update artheon` to pick up a new release.

## Template versions

The Notion template's changelog is [`plugins/knowledge-base/skills/kb-setup/references/template-changelog.md`](plugins/knowledge-base/skills/kb-setup/references/template-changelog.md).

## Licence

[MIT](LICENSE).
