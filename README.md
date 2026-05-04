# AI Engineering Skills

This repository contains a collection of reusable, LLM-agnostic structured workflows ("Skills") designed to standardize complex software engineering tasks for AI coding assistants.

## What is a "Skill"?

A Skill is essentially a highly structured prompt asset. Rather than relying on conversational back-and-forth, these `.skill.md` files explicitly define out a task's:
- **Core Goals**
- **Constraints & Guardrails** 
- **Step-by-Step Execution Phases**

Even though they use the `.skill.md` extension (native to tools like GitHub Copilot), they are **platform agnostic**. They can be seamlessly read and executed by any context-aware coding agent (Cursor, Windsurf, Roo Code/Cline, Aider, etc.).

## Available Skills

Currently included in the `/skills` directory:

- **`agent-env-installer`**: Standardizes the injection and setup of project-specific AI configurations, custom agents, and context environments.
- **`canvas-app-refactor`**: Provides a safe, strict pipeline for refactoring monolithic single-file AI-generated prototypes into modular (MVC) architectures without compromising UI/UX fidelity.
- **`gh-pages-action-deployer`**: Establishes a modern, branchless CI/CD deployment pipeline for static web applications via GitHub Actions Artifacts.

## How to use

Simply provide your AI assistant with the relevant Markdown file. 
- You can `@` mention it in IDEs like Cursor.
- Feed it into the system prompt of custom modes/agents.
- Or simply tell your agent: *"Read the instructions in `skills/[name].skill.md` and execute the refactor on my current project."*