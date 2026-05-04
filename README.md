# AI Engineering Skills

This repository contains a collection of reusable, LLM-agnostic structured workflows ("Skills") designed to standardize complex software engineering tasks for AI coding assistants.<br/>**本仓库包含了一系列可复用的、与具体大语言模型（LLM）无关的结构化工作流（"Skills"），旨在为 AI 编程助手标准化复杂的软件工程任务。**

## What is a "Skill"?

A Skill is essentially a highly structured prompt asset. Rather than relying on conversational back-and-forth, these `.skill.md` files explicitly define out a task's:<br/>**Skill 本质上是一个高度结构化的提示词（Prompt）资产。这些 `.skill.md` 文件不是依赖于对话式的来回沟通，而是明确定义了一个任务的：**
- Core Goals<br/>**核心目标**
- Constraints & Guardrails<br/>**约束与护栏**
- Step-by-Step Execution Phases<br/>**分步执行阶段**

Even though they use the `.skill.md` extension (native to tools like GitHub Copilot), they are platform agnostic.<br/>**尽管它们使用了 `.skill.md` 扩展名（这在 GitHub Copilot 等工具中是原生的），但它们是平台无关的。**

They can be seamlessly read and executed by any context-aware coding agent (Cursor, Windsurf, Roo Code/Cline, Aider, etc.).<br/>**它们可以被任何具备上下文感知能力的编程智能体（如 Cursor、Windsurf、Roo Code/Cline、Aider 等）无缝读取和执行。**

## Available Skills

Currently included in the `/skills` directory:<br/>**目前 `/skills` 目录中包含以下内容：**

- `agent-env-installer`: Standardizes the injection and setup of project-specific AI configurations, custom agents, and context environments.<br/>**`agent-env-installer`: 标准化特定项目 AI 配置、自定义 Agent 和上下文环境的注入与设置。**
- `canvas-app-refactor`: Provides a safe, strict pipeline for refactoring monolithic single-file AI-generated prototypes into modular (MVC) architectures without compromising UI/UX fidelity.<br/>**`canvas-app-refactor`: 提供一个安全、严格的流水线，用于将单文件 AI 生成的原型重构为模块化（MVC）架构，且不破坏 UI/UX 的一致性。**
- `gh-pages-action-deployer`: Establishes a modern, branchless CI/CD deployment pipeline for static web applications via GitHub Actions Artifacts.<br/>**`gh-pages-action-deployer`: 通过 GitHub Actions Artifacts 为静态 Web 应用程序建立现代的、无分支的 CI/CD 部署流水线。**

## How to use

Simply provide your AI assistant with the relevant Markdown file.<br/>**只需为您的 AI 助手提供相关的 Markdown 文件即可。**
- You can `@` mention it in IDEs like Cursor.<br/>**您可以在 Cursor 等 IDE 中使用 `@` 提及它。**
- Feed it into the system prompt of custom modes/agents.<br/>**将其喂给自定义模式/智能体的系统提示词中。**
- Or simply tell your agent: *"Read the instructions in `skills/[name].skill.md` and execute the refactor on my current project."*<br/>**或者直接告诉您的智能体：*“阅读 `skills/[name].skill.md` 中的说明，并在我当前的项目中执行重构。”***