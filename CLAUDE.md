# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This repository contains a collection of 83 specialized AI subagents for Claude Code, organized as Markdown files with frontmatter metadata. Each subagent provides domain-specific expertise across software development, infrastructure, and business operations.

## Repository Structure

- **Root directory**: Contains 83 individual `.md` files, each defining a specific subagent
- **examples/**: Contains usage examples and documentation (currently `tdd-usage.md`)
- **Subagent categories**: Architecture & System Design, Programming Languages, Infrastructure & Operations, Quality Assurance & Security, Data & AI, Documentation, Business & Operations, and Specialized Domains

## Subagent Architecture

Each subagent file follows a consistent structure:

```markdown
---
name: subagent-name
description: Activation criteria for this subagent
model: haiku|sonnet|opus  # Optional: Model selection based on task complexity
tools: tool1, tool2       # Optional: Tool restrictions
---

System prompt defining the subagent's expertise and behavior
```

### Model Distribution
- **Haiku (11 agents)**: Quick, focused tasks with minimal computational overhead
- **Sonnet (46 agents)**: Standard development and specialized engineering tasks
- **Opus (22 agents)**: Complex reasoning, architecture, and critical analysis

## Key Subagent Categories

### Architecture & System Design
- `backend-architect`, `cloud-architect`, `graphql-architect` - System design and infrastructure
- `frontend-developer`, `ui-ux-designer` - User interface and experience
- `mobile-developer`, `ios-developer`, `flutter-expert` - Mobile applications

### Programming Languages
- Systems: `c-pro`, `cpp-pro`, `rust-pro`, `golang-pro`
- Web: `javascript-pro`, `typescript-pro`, `python-pro`, `ruby-pro`, `php-pro`
- Enterprise: `java-pro`, `csharp-pro`, `scala-pro`

### Quality & Security
- `code-reviewer`, `security-auditor`, `test-automator`, `tdd-orchestrator`
- `performance-engineer`, `debugger`, `error-detective`

### Infrastructure & Operations
- `devops-troubleshooter`, `deployment-engineer`, `terraform-specialist`
- `database-optimizer`, `network-engineer`, `incident-responder`

### Data & AI
- `data-scientist`, `ml-engineer`, `ai-engineer`, `prompt-engineer`
- `mlops-engineer`, `data-engineer`

## Development Workflow

Since this is a documentation-based repository with no build system:

### Adding New Subagents
1. Create a new `.md` file with lowercase, hyphen-separated naming
2. Include proper frontmatter with `name`, `description`, and optional `model`/`tools`
3. Define comprehensive system prompt with expertise areas
4. Update README.md to include the new agent in appropriate category

### Modifying Existing Subagents
1. Edit the specific `.md` file
2. Maintain consistent frontmatter format
3. Ensure system prompt clarity and specificity

### Quality Assurance
- Activation criteria should be clear and specific in the `description` field
- System prompts should define 8-12 capability areas per agent
- Model selection should match task complexity (haiku < sonnet < opus)

## Usage Examples

The `examples/tdd-usage.md` file demonstrates how to invoke subagents through the Task tool:

```bash
# Basic agent invocation
Use Task tool with subagent_type="backend-architect"
Prompt: "Design authentication API with JWT tokens"

# Orchestrated workflows
Use Task tool with subagent_type="tdd-orchestrator"
Prompt: "Implement user authentication with TDD approach"
```

## Agent Coordination Patterns

### Sequential Processing
```
backend-architect → frontend-developer → test-automator → security-auditor
```

### Parallel Execution
```
performance-engineer + database-optimizer → Merged analysis
```

### Validation Pipeline
```
payment-integration → security-auditor → Validated implementation
```

## Installation Context

This repository is designed to be cloned into `~/.claude/agents/` directory where Claude Code automatically detects and loads the subagents for use.