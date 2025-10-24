# Multi-Agent Coding

**A systematic methodology for building complex software with coordinated AI agents.**

This repository demonstrates PRD-first development using Claude Code's multi-agent orchestration to build applications faster through parallel execution and contract-driven development.

## What This Is

This project teaches a reusable process for AI-assisted development:

1. **Start with a comprehensive PRD** - Clear requirements enable everything else
2. **Configure CLAUDE.md** - Point to your PRD and planning agent
3. **Define specialized agents** - Each owns a specific domain with clear boundaries
4. **Execute in parallel** - Multiple agents work simultaneously
5. **Integrate smoothly** - Contracts ensure clean composition

## Repository Structure

```
multi-agent-coding/
├── agent-templates/           # Reusable templates for your projects
│   ├── CLAUDE.md.example     # Configuration template
│   └── subagent-template.md  # Domain agent template
│
└── blackjack-app/            # Complete working example
    ├── blackjack-prd.md      # Starting point: comprehensive PRD
    ├── CLAUDE.md             # Agent orchestration config
    └── .claude/agents/       # Agent definitions
        ├── 01-foundation.md
        ├── 02-logic.md
        ├── 03-frontend.md
        └── 04-integration.md
```

## Quick Start

### Prerequisites

- [Claude Code](https://docs.claude.com/en/docs/claude-code/overview) installed
- Claude Pro subscription

### Try the Demo

**Build the blackjack app with Claude:**

```bash
# Clone the repository
git clone https://github.com/bufothefrog/multi-agent-coding.git
cd multi-agent-coding/blackjack-app

# Open in Claude Code and start working on the PRD
# Tell Claude: "Please implement the blackjack-prd.md"
```

Claude will read the PRD, discover the agent definitions in `.claude/agents/`, and orchestrate the build using specialized agents working in parallel.

**Explore the methodology:**
```bash
# 1. Read the PRD (the starting point)
cat blackjack-app/blackjack-prd.md

# 2. Review the configuration
cat blackjack-app/CLAUDE.md

# 3. Examine agent definitions
cat blackjack-app/.claude/agents/01-foundation.md
```

**Adapt to your project:**
```bash
cp agent-templates/CLAUDE.md.example your-project/CLAUDE.md
cp agent-templates/planning-agent.md your-project/.claude/agents/planning-agent.md
# Customize using subagent-template.md
```

## Core Principles

1. **PRD First** - Comprehensive requirements enable parallel development
2. **Contracts Enable Parallelism** - Define interfaces before implementation
3. **Clear Boundaries** - Each agent owns a specific domain
4. **Context Management** - Chunk work to respect token limits
5. **Easy Integration** - Smooth composition validates the approach

## Why This Works

**Traditional Sequential:**
- Build backend → Build frontend → Add features → Debug integration
- 3-4 weeks, tight coupling, painful integration

**Multi-Agent Parallel:**
- Define contracts → [Backend + Frontend + Features simultaneously] → Integration
- 1-2 weeks, loose coupling, smooth integration

## Resources

- [Advanced Context Engineering for Coding Agents](https://github.com/humanlayer/advanced-context-engineering-for-coding-agents/blob/main/ace-fca.md) - Comprehensive guide to context engineering techniques for AI coding agents