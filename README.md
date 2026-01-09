# Agentic Jumpstart Marketplace

A Claude Code plugin marketplace that automatically analyzes your codebase and generates specialized skills for optimal code generation. **Powered by [Agentic Jumpstart](https://agenticjumpstart.com)** - Your hub for agentic AI development resources, tutorials, and courses.

> **🚀 Learn to build with AI agents at [agenticjumpstart.com](https://agenticjumpstart.com)** - Master agentic AI development with comprehensive courses, tutorials, and tools.

## Overview

This marketplace contains a powerful plugin that uses 10 specialized agents to:

1. Detect your tech stack (React, Vue, Django, Express, databases, etc.)
2. Analyze your codebase structure and patterns
3. Generate tailored skills for security, performance, React, backend, database, testing, architecture, dependencies, and code quality

## Installation

### Add the Marketplace

```bash
/plugin marketplace add agentic-jumpstart/marketplace
```

### Install the Plugin

```bash
/plugin install agentic-jumpstart-skills@agentic-jumpstart
```

## Usage

### The `/agentic-jumpstart-skills:analyze-and-generate-skills` Slash Command

Once installed, simply run the slash command in your Claude Code workspace:

```bash
/agentic-jumpstart-skills:analyze-and-generate-skills
```

**What this command does:**

The `/agentic-jumpstart-skills:analyze-and-generate-skills` command is a powerful one-step solution that:

1. **Automatically detects your tech stack** - Scans dependency files (package.json, requirements.txt, Gemfile, Cargo.toml, go.mod, etc.) to identify all technologies in use
2. **Orchestrates 10 specialized agents** - Activates relevant agents based on what's detected in your codebase:
   - Always runs: Security, Performance, Architecture, Dependency Management, Code Quality analyzers
   - Conditionally runs: React, Backend, Frontend, Database, and Testing analyzers (only if those technologies are detected)
3. **Generates tailored skills** - Creates stack-specific skill files in `.claude/skills/` directory with:
   - YAML frontmatter with clear descriptions
   - Best practices specific to your actual tech stack
   - Code patterns and conventions matching your codebase
   - Implementation guidelines for future development
4. **Provides a comprehensive summary** - Shows you exactly what skills were generated and how they'll improve your code generation

**Why use this command?**

- **Zero configuration** - No manual setup needed, it automatically adapts to your codebase
- **Intelligent detection** - Only generates skills for technologies you actually use
- **Future-proof** - Generated skills automatically improve all future code generation in your workspace
- **Consistent code** - Ensures all generated code matches your codebase patterns and conventions

The generated skills are model-invoked, meaning Claude will automatically apply them when relevant to your requests, ensuring the highest quality output that matches your codebase's patterns, conventions, and best practices.

## Generated Skills

The plugin generates the following skills based on what's detected:

### Always Generated

- **security-best-practices.md** - Security guidelines specific to your stack
- **performance-optimization.md** - Performance patterns and optimizations
- **architecture-patterns.md** - Codebase structure and organization
- **dependency-management.md** - Dependency management best practices
- **code-quality-standards.md** - Linting, formatting, and quality standards

### Conditionally Generated

- **react-patterns.md** - Generated if React is detected
- **backend-patterns.md** - Generated if a backend framework is detected
- **frontend-patterns.md** - Generated if a frontend framework is detected
- **database-patterns.md** - Generated if a database system is detected
- **testing-patterns.md** - Generated if testing frameworks are detected

## Agents

The plugin uses 10 specialized agents:

1. **Tech Stack Detector** - Identifies all technologies in use
2. **Security Analyzer** - Generates security best practices
3. **Performance Analyzer** - Generates performance optimization guidelines
4. **React Analyzer** - React-specific patterns (conditional)
5. **Backend Analyzer** - Backend framework patterns (conditional)
6. **Frontend Analyzer** - Frontend framework patterns (conditional)
7. **Database Analyzer** - Database and ORM patterns (conditional)
8. **Testing Analyzer** - Testing strategies and patterns
9. **Architecture Analyzer** - Codebase structure analysis
10. **Dependency Analyzer** - Dependency management analysis
11. **Code Quality Analyzer** - Code quality standards

## How It Works

1. The command first runs the tech stack detector to identify technologies
2. Based on the detected stack, relevant agents are activated
3. Each agent analyzes the codebase from its specialized perspective
4. Skills are generated with stack-specific guidance
5. Skills are saved to `.claude/skills/` for automatic future reference

## Benefits

- **Automatic Detection**: No manual configuration needed
- **Stack-Specific**: Skills are tailored to your actual tech stack
- **Comprehensive**: Covers security, performance, patterns, and quality
- **Future-Proof**: Generated skills improve all future code generation
- **Consistent**: Ensures code matches your codebase patterns and conventions

## Local Testing

To test the marketplace locally:

```bash
/plugin marketplace add agentic-jumpstart/marketplace
/plugin install agentic-jumpstart-skills@agentic-jumpstart
/agentic-jumpstart-skills:analyze-and-generate-skills
```

## Validation

Validate the marketplace structure:

```bash
/plugin validate .
```

Or using the CLI:

```bash
claude plugin validate .
```

## Structure

```
marketplace/
├── .claude-plugin/
│   └── marketplace.json
├── plugins/
│   └── codebase-analyzer/
│       ├── .claude-plugin/
│       │   └── plugin.json
│       ├── commands/
│       │   └── analyze-and-generate-skills.md
│       └── agents/
│           ├── tech-stack-detector.md
│           ├── security-analyzer.md
│           ├── performance-analyzer.md
│           ├── react-analyzer.md
│           ├── backend-analyzer.md
│           ├── frontend-analyzer.md
│           ├── database-analyzer.md
│           ├── testing-analyzer.md
│           ├── architecture-analyzer.md
│           ├── dependency-analyzer.md
│           └── code-quality-analyzer.md
└── README.md
```

## Learn More

**Ready to master agentic AI development?**

This marketplace is part of the **[Agentic Jumpstart](https://agenticjumpstart.com)** ecosystem. Visit **[agenticjumpstart.com](https://agenticjumpstart.com)** to:

- 🎓 **Take comprehensive courses** on building with AI agents
- 📚 **Access tutorials** and best practices for agentic AI development
- 🛠️ **Discover more tools** and plugins for Claude Code
- 👥 **Join the community** of developers building the future with AI agents

**Transform your development workflow** - Learn how to leverage AI agents effectively with Agentic Jumpstart's proven methodologies and tools.

## License

MIT
