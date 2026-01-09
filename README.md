# Codebase Skills Marketplace

A Claude Code plugin marketplace that automatically analyzes your codebase and generates specialized skills for optimal code generation.

## Overview

This marketplace contains a powerful plugin that uses 10 specialized agents to:
1. Detect your tech stack (React, Vue, Django, Express, databases, etc.)
2. Analyze your codebase structure and patterns
3. Generate tailored skills for security, performance, React, backend, database, testing, architecture, dependencies, and code quality

## Installation

### Add the Marketplace

```bash
/plugin marketplace add ./marketplace
```

Or if hosting on GitHub:

```bash
/plugin marketplace add owner/repo
```

### Install the Plugin

```bash
/plugin install codebase-analyzer@codebase-skills-marketplace
```

## Usage

Once installed, run the analysis command:

```bash
/analyze-and-generate-skills
```

This will:
1. Scan your codebase for tech stack information
2. Activate 10 specialized agents to analyze different aspects
3. Generate skill files in `.claude/skills/` directory
4. Provide a summary of generated skills

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
/plugin marketplace add ./marketplace
/plugin install codebase-analyzer@codebase-skills-marketplace
/analyze-and-generate-skills
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

## License

MIT
