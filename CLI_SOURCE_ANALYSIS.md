# CLI Source Code Analysis

## Question
**Is all the source that creates the CLI experience in this repo?**

## Answer
**No, the actual CLI source code is NOT in this repository.**

## What IS in This Repository

This repository (`anthropics/claude-code`) contains:

1. **Plugin System Examples** - Official Claude Code plugins that extend functionality:
   - agent-sdk-dev
   - claude-opus-4-5-migration
   - code-review
   - commit-commands
   - explanatory-output-style
   - feature-dev
   - frontend-design
   - hookify
   - learning-output-style
   - plugin-dev
   - pr-review-toolkit
   - ralph-wiggum
   - security-guidance

2. **Documentation and Configuration**:
   - README.md with installation instructions
   - CHANGELOG.md with version history
   - Plugin documentation in `/plugins/README.md`
   - Example hooks in `/examples/hooks/`
   - DevContainer configuration in `.devcontainer/`

3. **Automation Scripts** (for repository management):
   - TypeScript scripts for issue deduplication (`scripts/auto-close-duplicates.ts`)
   - Bash scripts for issue commenting (`scripts/comment-on-duplicates.sh`)
   - GitHub Actions workflows in `.github/workflows/`

4. **Only 2 Source Files Total**:
   ```
   $ find . -name "*.ts" -o -name "*.tsx" -o -name "*.js" -o -name "*.jsx" | wc -l
   2
   ```
   Both are automation scripts, not CLI implementation.

## What is NOT in This Repository

The actual Claude Code CLI implementation is **closed source** and distributed as:

1. **NPM Package**: `@anthropic-ai/claude-code` (deprecated installation method)
2. **Native Installers**:
   - MacOS/Linux: `curl -fsSL https://claude.ai/install.sh | bash`
   - Homebrew: `brew install --cask claude-code`
   - Windows: `irm https://claude.ai/install.ps1 | iex`
   - WinGet: `winget install Anthropic.ClaudeCode`

## Evidence

1. **No Build Configuration**: No `package.json`, `tsconfig.json`, or build scripts for the CLI itself
2. **No Source Directories**: No `src/`, `lib/`, `dist/`, or `build/` directories
3. **Installation Methods**: All installation methods reference external sources:
   - NPM package hosted on npmjs.com
   - Install scripts from claude.ai
   - Native packages via Homebrew/WinGet
4. **DevContainer References NPM**: The Dockerfile installs from NPM:
   ```dockerfile
   RUN npm install -g @anthropic-ai/claude-code@${CLAUDE_CODE_VERSION}
   ```

## Conclusion

This repository is a **documentation and plugin repository** for Claude Code, not the source code repository for the CLI itself. The actual CLI implementation is:

- **Closed source** - Source code is not publicly available
- **Distributed via package managers** - NPM, Homebrew, WinGet, and install scripts
- **Maintained by Anthropic** - Based on references to `anthropics/claude-code` in issue templates and workflows

The repository serves as:
- Official plugin collection and examples
- Documentation hub
- Issue tracking location
- Community resources

If you're looking to extend Claude Code functionality, you should:
1. Use the **plugin system** documented in `/plugins/README.md`
2. Create custom **commands**, **agents**, **hooks**, or **MCP servers**
3. Reference the examples in this repository

## Repository Purpose

This is essentially the **public-facing extensions and documentation repository** for a closed-source CLI tool, similar to how VS Code has a public extensions marketplace but the core editor is in a separate repository.
