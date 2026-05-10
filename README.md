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
[![License: FSL-1.1-MIT](https://img.shields.io/badge/License-FSL--1.1--MIT-blue.svg)](https://fsl.software/)

Multi-language coding tools for AI agents -- umbrella package with auto-detection.

## Overview

This is the **umbrella package** that provides a unified interface for all coding tools across multiple programming languages. It automatically detects the language from file extensions and routes to the appropriate parser.

## Package Structure

| Package | Description |
|---------|-------------|
| **@compilr-dev/agents-coding** | This umbrella (re-exports everything + auto-detection) |
| [@compilr-dev/agents-coding-core](https://www.npmjs.com/package/@compilr-dev/agents-coding-core) | Git tools, project detection, smart runners, code search (30 tools, 14 skills) |
| [@compilr-dev/agents-coding-ts](https://www.npmjs.com/package/@compilr-dev/agents-coding-ts) | TypeScript/JavaScript AST analysis (15 tools) |
| [@compilr-dev/agents-coding-python](https://www.npmjs.com/package/@compilr-dev/agents-coding-python) | Python AST analysis via Tree-sitter |
| [@compilr-dev/agents-coding-go](https://www.npmjs.com/package/@compilr-dev/agents-coding-go) | Go AST analysis via Tree-sitter |

## Installation

```bash
# Umbrella package (recommended - includes everything)
npm install @compilr-dev/agents-coding @compilr-dev/agents

# Or individual packages for lighter installs
npm install @compilr-dev/agents-coding-core @compilr-dev/agents
npm install @compilr-dev/agents-coding-ts    # TypeScript analysis only
```

This single install gives you:
- **Core Tools** - Git operations, project detection, smart runners, code search
- **TypeScript/JavaScript** - AST-based analysis via TypeScript compiler
- **Python** - AST-based analysis via Tree-sitter
- **Go** - AST-based analysis via Tree-sitter

## Quick Start

```typescript
import { Agent } from '@compilr-dev/agents';
import {
  // Core tools (language-agnostic)
  gitStatusTool,
  gitDiffTool,
  detectProjectTool,
  runTestsTool,

  // Unified tools with auto-detection
  getFileStructureTool,
} from '@compilr-dev/agents-coding';

const agent = new Agent({
  provider: yourProvider,
  tools: [gitStatusTool, detectProjectTool, getFileStructureTool],
});
```

## Language Auto-Detection

The umbrella provides unified tools that automatically detect the language:

```typescript
import { detectLanguage, getFileStructureTool } from '@compilr-dev/agents-coding';

// Detect language from file path
detectLanguage('src/app.ts');     // 'typescript'
detectLanguage('main.py');         // 'python'
detectLanguage('cmd/server.go');   // 'go'

// Unified tool routes to correct parser
const result = await getFileStructureTool.execute({ path: 'src/app.ts' });
// Uses TypeScript parser automatically
```

## Direct Language Access

Access language-specific tools directly when needed:

```typescript
import {
  ts,      // TypeScript tools
  python,  // Python tools
  go,      // Go tools
} from '@compilr-dev/agents-coding';

// Use language-specific tools directly
const tsResult = await ts.getFileStructureTool.execute({ path: 'app.ts' });
const pyResult = await python.getFileStructureTool.execute({ path: 'main.py' });
const goResult = await go.getFileStructureTool.execute({ path: 'main.go' });
```

## Core Tools

All language-agnostic tools from `@compilr-dev/agents-coding-core`:

### Git Tools
- `gitStatusTool` - Parsed git status
- `gitDiffTool` - Structured diffs
- `gitLogTool` - Commit history
- `gitCommitTool` - Safe commit workflow
- `gitBranchTool` - Branch management
- `gitStashTool` - Stash operations

### Project Detection
- `detectProjectTool` - Detect project type, framework, tooling
- `findProjectRootTool` - Find project root directory

### Smart Runners

| Tool | Supported |
|------|-----------|
| `runTestsTool` | vitest, jest, mocha, ava, pytest, cargo test, go test, npm test, ruff |
| `runLintTool` | eslint, biome, ruff, pylint, flake8, clippy, golangci-lint, npm |
| `runBuildTool` | vite, next, tsc, webpack, rollup, esbuild, turbo, cargo, go, python, maven, gradle |
| `runFormatTool` | prettier, biome, dprint, black, ruff, rustfmt, gofmt, npm |

All runners support `dryRun` mode to detect without executing.

### Code Search
- `findDefinitionTool` - Find symbol definitions
- `findReferencesTool` - Find symbol usages
- `findTodosTool` - Find TODO/FIXME comments

## Skills

```typescript
import { codingSkills } from '@compilr-dev/agents-coding';

// Available skills:
// - git-workflow
// - test-driven
// - code-navigation
// - pr-workflow
// - project-onboarding
// - code-optimization
```

## Requirements

- **Node.js** 18 or higher
- **@compilr-dev/agents** peer dependency

## Related Packages

- [@compilr-dev/agents](https://www.npmjs.com/package/@compilr-dev/agents) - Core agent library
- [@compilr-dev/cli](https://www.npmjs.com/package/@compilr-dev/cli) - AI-powered CLI assistant

## Links

- [Website](https://compilr.dev)
- [npm Package](https://www.npmjs.com/package/@compilr-dev/agents-coding)
- [Report Issues](https://github.com/compilr-dev/agents-coding/issues)

## License

[FSL-1.1-MIT](https://fsl.software/) - See [LICENSE](LICENSE) for details. Converts to MIT after 2 years per version.

---

<p align="center">
  <strong>Built with care by <a href="https://compilr.dev">compilr.dev</a></strong>
</p>
