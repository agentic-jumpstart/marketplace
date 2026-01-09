# /analyze-and-generate-skills

Analyze the codebase to detect the tech stack and generate specialized skills for optimal code generation.

## Process Overview

This command orchestrates 10 specialized agents to comprehensively analyze your codebase and generate tailored skills.

### Step 1: Tech Stack Detection

First, activate the **tech-stack-detector** agent to identify all technologies in use:

- Scan dependency files (package.json, requirements.txt, Gemfile, Cargo.toml, go.mod, etc.)
- Identify frontend frameworks, backend frameworks, databases, testing tools, and build systems
- Create a comprehensive tech stack inventory

### Step 2: Parallel Agent Analysis

Based on the detected tech stack, activate the following agents in parallel:

1. **security-analyzer** - Always runs to generate security best practices
2. **performance-analyzer** - Always runs to generate performance optimization guidelines
3. **react-analyzer** - Only if React is detected
4. **backend-analyzer** - Only if a backend framework is detected
5. **frontend-analyzer** - Runs if any frontend framework is detected
6. **database-analyzer** - Only if a database system is detected
7. **testing-analyzer** - Runs if testing frameworks are detected
8. **architecture-analyzer** - Always runs to analyze code structure
9. **dependency-analyzer** - Always runs to analyze dependencies
10. **code-quality-analyzer** - Always runs to establish quality standards

### Step 3: Skill Generation

Each agent generates a skill in the `.claude/skills/` directory following this structure:

- Each skill is created in its own subdirectory (prefixed with "agentic-jumpstart-")
- Inside each subdirectory, there is a `SKILL.md` file (case-sensitive, uppercase) that describes how to apply the skill
- The `SKILL.md` file must follow the official Skill format with YAML frontmatter and Markdown instructions

**SKILL.md File Format:**

Each `SKILL.md` file must have:

1. **YAML frontmatter** (between `---` markers) starting on line 1 with no blank lines before it
2. **Required fields** in the frontmatter:
   - `name`: The skill name (e.g., "agentic-jumpstart-security")
   - `description`: A clear description that Claude uses to decide when to apply the skill. This is critical - include specific capabilities and trigger terms users would mention.
3. **Markdown instructions** after the frontmatter that describe how to apply the skill

**Example SKILL.md structure:**

```markdown
---
name: agentic-jumpstart-security
description: Security best practices and guidelines specific to your tech stack. Use when writing secure code, reviewing security concerns, or when the user mentions security, vulnerabilities, or authentication.
---

# Security Best Practices

[Markdown instructions on how to apply security practices...]
```

Generated skills follow this directory structure (all prefixed with "agentic-jumpstart-"):

- `.claude/skills/agentic-jumpstart-security/` → `SKILL.md` - Security guidelines specific to your stack
- `.claude/skills/agentic-jumpstart-performance/` → `SKILL.md` - Performance patterns and optimizations
- `.claude/skills/agentic-jumpstart-react/` → `SKILL.md` - React-specific patterns (if React detected)
- `.claude/skills/agentic-jumpstart-backend/` → `SKILL.md` - Backend framework patterns (if backend detected)
- `.claude/skills/agentic-jumpstart-frontend/` → `SKILL.md` - Frontend framework patterns (if frontend detected)
- `.claude/skills/agentic-jumpstart-database/` → `SKILL.md` - Database and ORM patterns (if database detected)
- `.claude/skills/agentic-jumpstart-testing/` → `SKILL.md` - Testing strategies and patterns
- `.claude/skills/agentic-jumpstart-architecture/` → `SKILL.md` - Codebase structure and organization patterns
- `.claude/skills/agentic-jumpstart-dependency-management/` → `SKILL.md` - Dependency management best practices
- `.claude/skills/agentic-jumpstart-code-quality/` → `SKILL.md` - Linting, formatting, and quality standards

## Execution Flow

1. **Initialize**: Create `.claude/skills/` directory if it doesn't exist
2. **Detect Stack**: Run tech-stack-detector agent and capture results
3. **Activate Agents**: Based on detection results, activate relevant agents:
   - Always: security, performance, architecture, dependency, code-quality
   - Conditionally: react (if React), backend (if backend), frontend (if frontend), database (if database), testing (if testing frameworks)
4. **Generate Skills**: Each agent creates a subdirectory in `.claude/skills/` prefixed with "agentic-jumpstart-" and generates a `SKILL.md` file (case-sensitive, uppercase) inside it. The `SKILL.md` file must include:
   - YAML frontmatter (between `---` markers) starting on line 1 with no blank lines before it
   - Required `name` field matching the subdirectory name
   - Required `description` field with specific capabilities and trigger terms that users would naturally say
   - Markdown instructions after the frontmatter with stack-specific guidance on how to apply the skill
5. **Summary**: Provide a summary of generated skills and how to use them

## Usage

Run `/analyze-and-generate-skills` in your workspace. The command will:

- Scan your codebase comprehensively
- Detect your complete tech stack
- Generate 5-10 specialized skills based on what's detected
- Create subdirectories in `.claude/skills/` prefixed with "agentic-jumpstart-" for each skill
- Generate a `SKILL.md` file (case-sensitive, uppercase) in each subdirectory with:
  - YAML frontmatter containing `name` and `description` fields
  - A clear `description` that includes specific capabilities and trigger terms
  - Markdown instructions describing how to apply that skill
- Save all skills for automatic future reference

## Output

The command will create skill directories and files following this structure:

**Skill Directory Structure:**

```
.claude/skills/
├── agentic-jumpstart-security/
│   └── SKILL.md          # Always generated
├── agentic-jumpstart-performance/
│   └── SKILL.md          # Always generated
├── agentic-jumpstart-react/
│   └── SKILL.md          # Generated if React detected
├── agentic-jumpstart-backend/
│   └── SKILL.md          # Generated if backend framework detected
├── agentic-jumpstart-frontend/
│   └── SKILL.md          # Generated if frontend framework detected
├── agentic-jumpstart-database/
│   └── SKILL.md          # Generated if database detected
├── agentic-jumpstart-testing/
│   └── SKILL.md          # Generated if testing frameworks detected
├── agentic-jumpstart-architecture/
│   └── SKILL.md          # Always generated
├── agentic-jumpstart-dependency-management/
│   └── SKILL.md          # Always generated
└── agentic-jumpstart-code-quality/
    └── SKILL.md          # Always generated
```

Each `SKILL.md` file follows the official Skill format:

**Required Structure:**

1. **YAML Frontmatter** (between `---` markers):

   - Must start on line 1 with no blank lines before it
   - Must include `name` field (matching the subdirectory name)
   - Must include `description` field (critical - Claude uses this to decide when to apply the skill)
   - The `description` should answer: "What does this Skill do?" and "When should Claude use it?" with specific trigger terms

2. **Markdown Instructions** (after the frontmatter):
   - Best practices specific to your tech stack
   - Code patterns and conventions
   - Implementation guidelines
   - Examples relevant to your codebase

**Important Notes:**

- The filename must be exactly `SKILL.md` (uppercase, case-sensitive)
- The `description` field is crucial - Claude reads descriptions to find relevant Skills, so include keywords users would naturally say
- Skills are model-invoked: Claude automatically applies relevant Skills when your request matches their description
- These skills will be automatically referenced in future code generation prompts to ensure the highest quality output that matches your codebase's patterns, conventions, and best practices

## Agent Coordination

The command coordinates all agents by:

1. Sharing tech stack detection results with all agents
2. Ensuring conditional agents only run when relevant technologies are detected
3. Collecting all generated skill content
4. Creating subdirectories in `.claude/skills/` prefixed with "agentic-jumpstart-" for each skill
5. Writing `SKILL.md` files (case-sensitive, uppercase) in each subdirectory with:
   - YAML frontmatter (between `---` markers) starting on line 1
   - Required `name` and `description` fields in the frontmatter
   - A clear `description` with specific capabilities and trigger terms
   - Markdown instructions after the frontmatter on how to apply the skill
6. Providing a comprehensive summary of what was generated
