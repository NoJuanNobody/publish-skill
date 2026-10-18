---
name: publish-skill
description: Extract, package, and publish agent skills to GitHub for the open skills ecosystem (npx skills / skills.sh). Use when the user wants to turn an idea, prompt, or screenshot into an installable skill, create a public GitHub skill repo, or share skills via the Skills CLI.
---

# Publish Skill

Automates the process of extracting, creating, packaging, and publishing an agent skill to GitHub so it is immediately installable via the open Skills CLI (`npx skills add <owner>/<repo>`).

## When to Use

- User asks to turn a screenshot, image, or text prompt into a distributable agent skill.
- User wants to create or publish a skill for `npx skills` / `skills.sh`.
- User asks: "publish this skill", "create a repo for this skill", "share this skill on skills.sh", or "make an installable skill from X".

## Workflow

### 1. Extract & Draft the `SKILL.md`

Every skill package requires a valid `SKILL.md` file with YAML frontmatter:

```markdown
---
name: <kebab-case-skill-name>
description: <Concise, trigger-rich description of what the skill does and when to invoke it>
---

# <Skill Title>

<Detailed instructions, core principles, protocols, and workflows>
```

- If source is an image/screenshot: Inspect the image using visual tools or OCR, clean up formatting, ensure valid YAML frontmatter.
- Keep the `description` clear with explicit trigger words so agents recognize when to use it.

### 2. Scaffold Repository Structure

Create a dedicated local folder for the skill:

```bash
mkdir -p <target-path>/<skill-name>
```

Inside that directory, create:
1. `SKILL.md`: The core skill instructions and frontmatter.
2. `README.md`: Explaining the skill with quick installation instructions:
   ```markdown
   # <Skill Title>

   <Brief summary>

   ## Installation

   Install with [`npx skills`](https://skills.sh):

   ```bash
   npx skills add <owner>/<repo-name> -g
   ```
   ```

### 3. Initialize Git & Publish to GitHub

1. Initialize git and commit:
   ```bash
   git init
   git add .
   git commit -m "Initial commit: <Skill Title> skill"
   ```

2. Create a public GitHub repository and push using GitHub CLI (`gh`):
   ```bash
   gh repo create <owner>/<repo-name> --public --source=. --remote=origin --push
   ```

### 4. Verify Installation via `npx skills`

Confirm that the ecosystem can clone and detect the skill without errors:

```bash
npx skills add <owner>/<repo-name> --list
```

### 5. Provide Ready-to-Share Links

Present the user with:
- GitHub repository URL.
- One-line install command for friends and peers:
  ```bash
  npx skills add <owner>/<repo-name> -g
  ```
