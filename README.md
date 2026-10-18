# Publish Skill

An agent skill to extract, package, and publish agent skills to GitHub for the open skills ecosystem ([skills.sh](https://skills.sh)).

## Installation

Install via the Skills CLI:

```bash
npx skills add NoJuanNobody/publish-skill -g
```

## Features

- **Extract**: Pull skill text and metadata from images, screenshots, prompts, or notes.
- **Package**: Create standards-compliant `SKILL.md` files with YAML frontmatter.
- **Publish**: Scaffolds git repositories and automatically publishes them to GitHub via `gh`.
- **Verify**: Tests discovery with `npx skills add <repo> --list`.
