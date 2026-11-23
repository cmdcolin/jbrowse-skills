# JBrowse 2 agent skills

Skills for working with [JBrowse 2](https://jbrowse.org/jb2/) from an AI coding
agent: authoring a config, using the hosted genomes, screenshotting the result,
and driving a running JBrowse.

## Install

They are plain Markdown files, so "installing" them is copying a directory into
your agent's skills folder: `~/.agents/skills/` for Codex, Gemini CLI, Cursor
and others that read `SKILL.md` folders, `~/.claude/skills/` for Claude
Code. The commands below use the first; swap the folder for Claude Code.

**curl + tar**, no Node, nothing left behind:

```bash
mkdir -p ~/.agents/skills
curl -sL https://github.com/cmdcolin/jbrowse-skills/archive/refs/heads/main.tar.gz |
  tar -xz --strip-components=2 -C ~/.agents/skills jbrowse-skills-main/skills
```

**git**, if you want to pull updates later:

```bash
git clone --depth 1 https://github.com/cmdcolin/jbrowse-skills /tmp/jbrowse-skills
cp -r /tmp/jbrowse-skills/skills/. ~/.agents/skills/
```

**degit**, the shortest if you have Node:

```bash
npx --yes degit --force cmdcolin/jbrowse-skills/skills ~/.agents/skills
```

Any of them takes a single skill instead of all four — append its directory
name to the source path (`.../skills/jbrowse-capture`) and to the destination.

To pull updates, re-run the same command: the files are generated, so there is
nothing local to merge.

## What is here

| Skill | Use it when |
| --- | --- |
| `jbrowse-authoring` | writing a `config.json`, session or track from scratch, including preparing the data files |
| `jbrowse-hosted-data` | the genome is one of the tens of thousands already published at [genomes.jbrowse.org](https://genomes.jbrowse.org) |
| `jbrowse-capture` | you need to see a view rather than just build one |
| `jbrowse-mcp` | driving a running JBrowse: Desktop over its MCP server, or a JBrowse Web page through `window.jb` |

Each is a directory with a `SKILL.md` and, where it needs one, a
`references/` folder, in the [Agent Skills](https://agentskills.io) format.
Nothing in the content is specific to one agent: the files are plain Markdown and
work as context for any assistant.

## Source

**Generated. Do not edit here.** These are mirrored from
[GMOD/jbrowse-components](https://github.com/GMOD/jbrowse-components) under
`.claude/skills/`, by `scripts/sync-skills-repo.ts` in that repo. Edits made
here are overwritten on the next sync, and the authoring skill's
`references/config-types.md` is generated from the live config schemas, so it
would be reverted even sooner.

Open issues and pull requests against jbrowse-components.

## See also

- [Using JBrowse with AI agents](https://jbrowse.org/jb2/docs/agents/)
- [`@jbrowse/capture`](https://www.npmjs.com/package/@jbrowse/capture) — the
  Puppeteer helper the capture skill drives
- [`@jbrowse/img`](https://www.npmjs.com/package/@jbrowse/img) — static export
  with no browser
