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
Each agent generates a skill file in `.claude/skills/` directory:
- `security-best-practices.md` - Security guidelines specific to your stack
- `performance-optimization.md` - Performance patterns and optimizations
- `react-patterns.md` - React-specific patterns (if React detected)
- `backend-patterns.md` - Backend framework patterns (if backend detected)
- `frontend-patterns.md` - Frontend framework patterns (if frontend detected)
- `database-patterns.md` - Database and ORM patterns (if database detected)
- `testing-patterns.md` - Testing strategies and patterns
- `architecture-patterns.md` - Codebase structure and organization patterns
- `dependency-management.md` - Dependency management best practices
- `code-quality-standards.md` - Linting, formatting, and quality standards

## Execution Flow

1. **Initialize**: Create `.claude/skills/` directory if it doesn't exist
2. **Detect Stack**: Run tech-stack-detector agent and capture results
3. **Activate Agents**: Based on detection results, activate relevant agents:
   - Always: security, performance, architecture, dependency, code-quality
   - Conditionally: react (if React), backend (if backend), frontend (if frontend), database (if database), testing (if testing frameworks)
4. **Generate Skills**: Each agent generates its skill file with stack-specific guidance
5. **Summary**: Provide a summary of generated skills and how to use them

## Usage

Run `/analyze-and-generate-skills` in your workspace. The command will:
- Scan your codebase comprehensively
- Detect your complete tech stack
- Generate 5-10 specialized skills based on what's detected
- Save all skills to `.claude/skills/` for automatic future reference

## Output

The command will create skill files such as:
- `security-best-practices.md` - Always generated
- `performance-optimization.md` - Always generated
- `react-patterns.md` - Generated if React detected
- `backend-patterns.md` - Generated if backend framework detected
- `frontend-patterns.md` - Generated if frontend framework detected
- `database-patterns.md` - Generated if database detected
- `testing-patterns.md` - Generated if testing frameworks detected
- `architecture-patterns.md` - Always generated
- `dependency-management.md` - Always generated
- `code-quality-standards.md` - Always generated

These skills will be automatically referenced in future code generation prompts to ensure the highest quality output that matches your codebase's patterns, conventions, and best practices.

## Agent Coordination

The command coordinates all agents by:
1. Sharing tech stack detection results with all agents
2. Ensuring conditional agents only run when relevant technologies are detected
3. Collecting all generated skill content
4. Writing skills to appropriate files
5. Providing a comprehensive summary of what was generated
