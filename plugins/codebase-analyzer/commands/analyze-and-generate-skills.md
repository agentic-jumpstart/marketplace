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

- Each skill is created in its own subdirectory
- Inside each subdirectory, there is a `skill.md` file that describes how to apply the skill

Generated skills follow this directory structure (all prefixed with "agentic-jumpstart-"):

- `.claude/skills/agentic-jumpstart-security/` → `skill.md` - Security guidelines specific to your stack
- `.claude/skills/agentic-jumpstart-performance/` → `skill.md` - Performance patterns and optimizations
- `.claude/skills/agentic-jumpstart-react/` → `skill.md` - React-specific patterns (if React detected)
- `.claude/skills/agentic-jumpstart-backend/` → `skill.md` - Backend framework patterns (if backend detected)
- `.claude/skills/agentic-jumpstart-frontend/` → `skill.md` - Frontend framework patterns (if frontend detected)
- `.claude/skills/agentic-jumpstart-database/` → `skill.md` - Database and ORM patterns (if database detected)
- `.claude/skills/agentic-jumpstart-testing/` → `skill.md` - Testing strategies and patterns
- `.claude/skills/agentic-jumpstart-architecture/` → `skill.md` - Codebase structure and organization patterns
- `.claude/skills/agentic-jumpstart-dependency-management/` → `skill.md` - Dependency management best practices
- `.claude/skills/agentic-jumpstart-code-quality/` → `skill.md` - Linting, formatting, and quality standards

## Execution Flow

1. **Initialize**: Create `.claude/skills/` directory if it doesn't exist
2. **Detect Stack**: Run tech-stack-detector agent and capture results
3. **Activate Agents**: Based on detection results, activate relevant agents:
   - Always: security, performance, architecture, dependency, code-quality
   - Conditionally: react (if React), backend (if backend), frontend (if frontend), database (if database), testing (if testing frameworks)
4. **Generate Skills**: Each agent creates a subdirectory in `.claude/skills/` prefixed with "agentic-jumpstart-" and generates a `skill.md` file inside it with stack-specific guidance on how to apply the skill
5. **Summary**: Provide a summary of generated skills and how to use them

## Usage

Run `/analyze-and-generate-skills` in your workspace. The command will:

- Scan your codebase comprehensively
- Detect your complete tech stack
- Generate 5-10 specialized skills based on what's detected
- Create subdirectories in `.claude/skills/` prefixed with "agentic-jumpstart-" for each skill
- Generate a `skill.md` file in each subdirectory describing how to apply that skill
- Save all skills for automatic future reference

## Output

The command will create skill directories and files following this structure:

**Skill Directory Structure:**

```
.claude/skills/
├── agentic-jumpstart-security/
│   └── skill.md          # Always generated
├── agentic-jumpstart-performance/
│   └── skill.md          # Always generated
├── agentic-jumpstart-react/
│   └── skill.md          # Generated if React detected
├── agentic-jumpstart-backend/
│   └── skill.md          # Generated if backend framework detected
├── agentic-jumpstart-frontend/
│   └── skill.md          # Generated if frontend framework detected
├── agentic-jumpstart-database/
│   └── skill.md          # Generated if database detected
├── agentic-jumpstart-testing/
│   └── skill.md          # Generated if testing frameworks detected
├── agentic-jumpstart-architecture/
│   └── skill.md          # Always generated
├── agentic-jumpstart-dependency-management/
│   └── skill.md          # Always generated
└── agentic-jumpstart-code-quality/
    └── skill.md          # Always generated
```

Each `skill.md` file contains detailed instructions on how to apply that specific skill, including:

- Best practices specific to your tech stack
- Code patterns and conventions
- Implementation guidelines
- Examples relevant to your codebase

These skills will be automatically referenced in future code generation prompts to ensure the highest quality output that matches your codebase's patterns, conventions, and best practices.

## Agent Coordination

The command coordinates all agents by:

1. Sharing tech stack detection results with all agents
2. Ensuring conditional agents only run when relevant technologies are detected
3. Collecting all generated skill content
4. Creating subdirectories in `.claude/skills/` prefixed with "agentic-jumpstart-" for each skill
5. Writing `skill.md` files in each subdirectory with instructions on how to apply the skill
6. Providing a comprehensive summary of what was generated
