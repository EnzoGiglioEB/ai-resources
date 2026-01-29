---
name: skill-creator
description: Guide for creating effective skills. This skill should be used when users want to create a new skill (or update an existing skill) that extends Claude's capabilities with specialized knowledge, workflows, or tool integrations.
license: Complete terms in LICENSE.txt
---

# Skill Creator

This skill provides guidance for creating effective skills.

## About Skills

Skills are modular, self-contained packages that extend Claude's capabilities by providing specialized knowledge, workflows, and tools. Think of them as "onboarding guides" for specific domains or tasks.

### What Skills Provide

1. Specialized workflows - Multi-step procedures for specific domains
2. Tool integrations - Instructions for working with specific file formats or APIs
3. Domain expertise - Company-specific knowledge, schemas, business logic
4. Bundled resources - Scripts, references, and assets for complex and repetitive tasks

### Anatomy of a Skill

```
skill-name/
├── SKILL.md (required)
│   ├── YAML frontmatter metadata
│   │   ├── name: (required)
│   │   └── description: (required)
│   └── Markdown instructions
└── Bundled Resources (optional)
    ├── scripts/          - Executable code
    ├── references/       - Documentation for context
    └── assets/           - Files for output
```

## Skill Creation Process

### Step 1: Understanding the Skill with Concrete Examples

Understand concrete examples of how the skill will be used. Ask:
- What functionality should the skill support?
- What would a user say that should trigger this skill?

### Step 2: Planning Reusable Contents

Analyze each example to identify helpful resources:
- Scripts for repeated code
- References for schemas and documentation
- Assets for templates and boilerplate

### Step 3: Initialize the Skill

Run `scripts/init_skill.py <skill-name> --path <output-directory>`

### Step 4: Edit the Skill

Write in imperative form. Answer:
1. What is the purpose?
2. When should it be used?
3. How should Claude use the bundled resources?

### Step 5: Package the Skill

Run `scripts/package_skill.py <path/to/skill-folder>`

Validates and creates distributable zip file.

### Step 6: Iterate

Test, identify improvements, update, and test again.

## Best Practices

- Keep SKILL.md lean, move details to references
- Use scripts for deterministic tasks
- Include grep patterns for large reference files
- Write for AI consumption (imperative, objective)
- Progressive disclosure: metadata → SKILL.md → resources
