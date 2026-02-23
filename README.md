# @compilr-dev/agents-coding

```
      \|/
    ╭══════════╮     ___  ___  _ __ ___  _ __ (_) |_ __
    ║'  ▐▌  ▐▌ │    / __|/ _ \| '_ ` _ \| '_ \| | | '__|
    ║          │   | (__| (_) | | | | | | |_) | | | |
    ╰─═──────═─╯    \___|\___/|_| |_| |_| .__/|_|_|_|
      \________\                        | | .dev
                                        |_| coding
```

> Coding-specific tools and language analysis for AI assistants

[![npm version](https://img.shields.io/npm/v/@compilr-dev/agents-coding.svg)](https://www.npmjs.com/package/@compilr-dev/agents-coding)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

> [!WARNING]
> This package is in beta. APIs may change between minor versions.

Extension package for [@compilr-dev/agents](https://www.npmjs.com/package/@compilr-dev/agents) that provides coding-specific tools for git operations, project detection, smart runners, code search, and language-specific AST analysis.

## Overview

This is the **umbrella package** that bundles the entire coding tools ecosystem:

| Package | Description |
|---------|-------------|
| **@compilr-dev/agents-coding** | This package -- batteries-included with auto-detection |
| [@compilr-dev/agents-coding-core](https://www.npmjs.com/package/@compilr-dev/agents-coding-core) | Git tools, project detection, smart runners, code search |
| [@compilr-dev/agents-coding-ts](https://www.npmjs.com/package/@compilr-dev/agents-coding-ts) | TypeScript/JavaScript AST analysis |
| [@compilr-dev/agents-coding-python](https://www.npmjs.com/package/@compilr-dev/agents-coding-python) | Python AST analysis (Tree-sitter) |
| [@compilr-dev/agents-coding-go](https://www.npmjs.com/package/@compilr-dev/agents-coding-go) | Go AST analysis (Tree-sitter) |

Install just this package for everything, or install individual packages for a lighter footprint.

## Installation

```bash
# Umbrella package (recommended - includes everything)
npm install @compilr-dev/agents-coding @compilr-dev/agents

# Or individual packages for lighter installs
npm install @compilr-dev/agents-coding-core @compilr-dev/agents
npm install @compilr-dev/agents-coding-ts    # TypeScript analysis
```

## Features

- **Git Tools** - Status, diff, log, commit, branch, stash operations
- **Project Detection** - Detect project type, find root, analyze structure
- **Smart Runners** - Run tests, lint, build, format with auto-detection
- **Code Search** - Find definitions, references, and TODOs
- **Language Analysis** - AST-based analysis for TypeScript, Python, Go
- **14 Skills** - Reusable prompts for coding workflows
- **Auto-detection** - Automatically selects the right language analyzer

## Language Auto-Detection

The umbrella package includes a dispatcher that automatically selects the right analyzer:

```typescript
import { createLanguageTools } from '@compilr-dev/agents-coding';

// Auto-detects project language and returns appropriate tools
const tools = await createLanguageTools('/path/to/project');
```

## Git Tools

```typescript
import {
  gitStatusTool,
  gitDiffTool,
  gitLogTool,
  gitCommitTool,
  gitBranchTool,
  gitStashTool
} from '@compilr-dev/agents-coding';
```

| Tool | Description |
|------|-------------|
| `gitStatusTool` | Get parsed git status |
| `gitDiffTool` | View diffs with file filtering |
| `gitLogTool` | Parsed commit history |
| `gitCommitTool` | Safe commit workflow |
| `gitBranchTool` | Create, switch, list, delete branches |
| `gitStashTool` | Push, pop, list, apply, drop stashes |

## Project Detection

```typescript
import {
  detectProjectTool,
  findProjectRootTool
} from '@compilr-dev/agents-coding';
```

| Tool | Description |
|------|-------------|
| `detectProjectTool` | Full project analysis (type, framework, structure) |
| `findProjectRootTool` | Walk up directories to find project root |

## Smart Runners

Auto-detect and run the appropriate tool for your project:

```typescript
import {
  runTestsTool,
  runLintTool,
  runBuildTool,
  runFormatTool
} from '@compilr-dev/agents-coding';
```

| Tool | Supported |
|------|-----------|
| `runTestsTool` | vitest, jest, mocha, ava, pytest, cargo test, go test, npm test, ruff |
| `runLintTool` | eslint, biome, ruff, pylint, flake8, clippy, golangci-lint, npm |
| `runBuildTool` | vite, next, tsc, webpack, rollup, esbuild, turbo, cargo, go, python, maven, gradle |
| `runFormatTool` | prettier, biome, dprint, black, ruff, rustfmt, gofmt, npm |

All runners support `dryRun` mode to detect without executing.

## Code Search

```typescript
import {
  findDefinitionTool,
  findReferencesTool,
  findTodosTool
} from '@compilr-dev/agents-coding';
```

| Tool | Description |
|------|-------------|
| `findDefinitionTool` | Find symbol definitions (multi-language) |
| `findReferencesTool` | Find symbol usage across codebase |
| `findTodosTool` | Extract TODO/FIXME comments |

## Skills

Reusable prompts for coding workflows:

```typescript
import {
  gitWorkflowSkill,
  projectSetupSkill,
  testDrivenSkill,
  codeReviewSkill,
  debuggingSkill,
  refactoringSkill
} from '@compilr-dev/agents-coding';
```

## Usage with Agent

```typescript
import { Agent, ClaudeProvider } from '@compilr-dev/agents';
import {
  gitStatusTool,
  gitDiffTool,
  detectProjectTool,
  runTestsTool
} from '@compilr-dev/agents-coding';

const agent = new Agent({
  provider: new ClaudeProvider({ apiKey: process.env.ANTHROPIC_API_KEY }),
  tools: [gitStatusTool, gitDiffTool, detectProjectTool, runTestsTool],
  systemPrompt: 'You are a coding assistant.',
});
```

## Requirements

- **Node.js** 20 or higher
- **@compilr-dev/agents** peer dependency

## Related Packages

- [@compilr-dev/agents](https://www.npmjs.com/package/@compilr-dev/agents) - Core agent library
- [@compilr-dev/cli](https://www.npmjs.com/package/@compilr-dev/cli) - AI-powered CLI assistant

## Links

- [Website](https://compilr.dev)
- [npm Package](https://www.npmjs.com/package/@compilr-dev/agents-coding)
- [Report Issues](https://github.com/compilr-dev/agents-coding/issues)

## License

MIT - See [LICENSE](LICENSE) for details.

---

<p align="center">
  <strong>Built with care by <a href="https://compilr.dev">compilr.dev</a></strong>
</p>
