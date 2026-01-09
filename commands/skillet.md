---
name: skillet
description: Deep-dive tech stack analyzer that spawns multiple sub-agents to comprehensively analyze your project and generate 10+ security-focused, professionally-written skills tailored to your specific tech stack
---

# Skillet: Comprehensive Tech Stack Analyzer & Security Skill Generator

You are a senior software architect and security expert. When this command is invoked, you MUST perform a comprehensive multi-agent deep-dive analysis of the project's tech stack and generate at least 10 tailored skills focused on security, maintainability, and professional code quality.

## Phase 1: Multi-Agent Tech Stack Analysis

Launch the following sub-agents IN PARALLEL to perform comprehensive analysis:

### Sub-Agent 1: Frontend Framework Analysis
Analyze for:
- React (hooks, state management, effects, context, suspense, server components)
- Next.js (App Router, Pages Router, API routes, middleware, ISR, SSR, SSG)
- Vue.js, Angular, Svelte, or other frameworks
- State management (Redux, Zustand, Jotai, Recoil, MobX)
- Styling solutions (Tailwind, CSS Modules, Styled Components, Emotion)
- UI component libraries (shadcn/ui, Radix, MUI, Chakra)

### Sub-Agent 2: Backend & API Analysis
Analyze for:
- Express.js, Fastify, Hono, Koa
- Next.js API routes and server actions
- GraphQL (Apollo, TRPC, Relay)
- REST API patterns
- WebSocket implementations
- Microservices architecture

### Sub-Agent 3: Database & ORM Analysis
Analyze for:
- PostgreSQL, MySQL, MongoDB, Redis
- ORMs (Prisma, Drizzle, TypeORM, Mongoose, Kysely)
- Database migrations and seeding
- Connection pooling
- Query optimization patterns

### Sub-Agent 4: Authentication & Authorization Analysis
Analyze for:
- Auth providers (NextAuth/Auth.js, Clerk, Supabase Auth, Firebase Auth)
- JWT handling and refresh token patterns
- OAuth implementations
- RBAC/ABAC patterns
- Session management

### Sub-Agent 5: Infrastructure & DevOps Analysis
Analyze for:
- Docker and containerization
- CI/CD pipelines
- Cloud providers (AWS, Vercel, Cloudflare)
- Environment configuration
- Logging and monitoring
- Error tracking (Sentry, LogRocket)

## Phase 2: Generate Project-Specific Skills

Based on the analysis, generate EXACTLY these skill files in `.claude/skills/` directory:

### Required Skills to Generate (Minimum 10):

1. **[framework]-security.md** - Based on detected frontend framework
2. **[backend]-security.md** - Based on detected backend framework
3. **api-security.md** - REST/GraphQL security patterns
4. **auth-security.md** - Authentication best practices
5. **database-security.md** - Database security patterns
6. **input-validation.md** - Input sanitization and validation
7. **dependency-security.md** - Supply chain security
8. **code-quality.md** - DRY, maintainable, professional patterns
9. **testing-practices.md** - Security-focused testing
10. **error-handling.md** - Secure error handling
11. **[additional-tech].md** - Any other relevant tech detected

## Phase 3: Skill Generation Template

Each generated skill MUST follow this structure:

```markdown
---
name: [skill-name]
description: [Comprehensive description for when to use this skill]
globs: [Relevant file patterns]
---

# [Skill Name]: Security & Best Practices Guide

## Overview
[Brief explanation of this technology and why security matters]

## Security Principles
[Core security concepts specific to this technology]

## OWASP Top 10 Considerations
[How this technology relates to OWASP vulnerabilities]

## Secure Code Patterns

### Pattern 1: [Name]
[Code examples with security annotations]

### Pattern 2: [Name]
[Code examples with security annotations]

## Anti-Patterns to Avoid
[Common security mistakes with examples]

## Best Practices Checklist
- [ ] [Security check 1]
- [ ] [Security check 2]
...

## Code Quality Standards
[DRY, maintainable, professional code guidelines]
```

## Execution Instructions

When `/skillet` is invoked:

1. **Create Todo List** - Track all analysis and generation tasks
2. **Launch Sub-Agents** - Use Task tool to spawn 5 parallel analysis agents
3. **Aggregate Results** - Compile all tech stack findings
4. **Generate Skills** - Create `.claude/skills/` directory if not exists
5. **Write Each Skill** - Generate all 10+ skill files
6. **Summary Report** - Provide completion summary with all generated skills

## Output Format

After completion, display:

```
╔══════════════════════════════════════════════════════════════════╗
║                    SKILLET ANALYSIS COMPLETE                       ║
╠══════════════════════════════════════════════════════════════════╣
║ Tech Stack Detected:                                               ║
║   Frontend: [technologies]                                         ║
║   Backend: [technologies]                                          ║
║   Database: [technologies]                                         ║
║   Auth: [technologies]                                             ║
║   Infrastructure: [technologies]                                   ║
╠══════════════════════════════════════════════════════════════════╣
║ Skills Generated:                                                  ║
║   1. .claude/skills/[skill-name]/SKILL.md                         ║
║   2. .claude/skills/[skill-name]/SKILL.md                         ║
║   [... list all generated skills]                                  ║
╠══════════════════════════════════════════════════════════════════╣
║ Security Coverage:                                                 ║
║   - OWASP Top 10 mitigations                                      ║
║   - Input validation patterns                                      ║
║   - Authentication hardening                                       ║
║   - SQL injection prevention                                       ║
║   - XSS prevention                                                 ║
║   - CSRF protection                                                ║
║   - Secure session management                                      ║
║   - Dependency vulnerability scanning                              ║
╚══════════════════════════════════════════════════════════════════╝
```

## Key Terminology to Include in Generated Skills

All generated skills MUST emphasize:

**Security Terms:**
- Defense in depth
- Principle of least privilege
- Zero trust architecture
- Input sanitization
- Output encoding
- Parameterized queries
- Cryptographic best practices
- Secure by default
- Fail securely
- Attack surface reduction

**Code Quality Terms:**
- DRY (Don't Repeat Yourself)
- SOLID principles
- Single responsibility
- Separation of concerns
- Immutability
- Pure functions
- Defensive programming
- Type safety
- Null safety
- Error boundaries

**Professional Standards:**
- Clean code architecture
- Maintainable code patterns
- Self-documenting code
- Consistent naming conventions
- Modular design
- Testable code structure
- Performance optimization
- Memory management
- Resource cleanup
- Graceful degradation

$ARGUMENTS
