# docsync

<p align="center">
  <img src="https://img.shields.io/badge/languages-40%2B-blueviolet" alt="40+ languages">
  <img src="https://img.shields.io/badge/license-MIT-green" alt="MIT License">
  <img src="https://img.shields.io/badge/install-clawhub-blue" alt="ClawHub">
  <img src="https://img.shields.io/badge/zero-telemetry-brightgreen" alt="Zero telemetry">
</p>

<h3 align="center">Auto-generate docs from code. Detect drift. Keep docs alive.</h3>

<p align="center">
  <a href="https://docsync.pages.dev">Website</a> &middot;
  <a href="#quick-start">Quick Start</a> &middot;
  <a href="#how-it-works">How It Works</a> &middot;
  <a href="https://docsync.pages.dev/#pricing">Pricing</a>
</p>

---

## The Problem

Documentation rots. You know it. Your team knows it. That function you documented last month? The signature changed twice since then. The README? Written when the project had 3 files.

**DocSync fixes this by making documentation a first-class citizen of your git workflow.**

## Quick Start

```bash
# Install via ClawHub (free)
clawhub install docsync

# Generate docs for your project
docsync generate .

# Check what's undocumented
docsync drift

# Auto-fix stale docs
docsync auto-fix

# Install git hooks to catch drift on every commit
docsync hooks install
```

## How It Works

```
You commit code
      │
      ▼
Pre-commit hook fires
      │
      ▼
DocSync parses staged files (tree-sitter)
      │
      ├─ Extracts: functions, classes, types, exports
      ├─ Compares against existing docs
      │
      ▼
 Drift detected?
   ├─ No  → commit proceeds ✓
   └─ Yes → blocks commit, suggests auto-fix
```

### Code Analysis

DocSync uses [tree-sitter](https://tree-sitter.github.io/) for accurate AST parsing across **40+ languages**. When tree-sitter isn't installed, it falls back to regex-based extraction.

### Drift Detection

Every commit is checked for:
- **Undocumented symbols** — new functions/classes with no docs (critical)
- **Stale signatures** — code changed but docs didn't (warning)
- **Dead references** — deleted code still mentioned in docs (warning)

### Git Hook Enforcement

Uses [lefthook](https://github.com/evilmartians/lefthook) for fast, parallel pre-commit hooks. Runs only on staged files — no full-repo scans.

## Supported Languages

TypeScript, JavaScript, Python, Rust, Go, Java, C, C++, Ruby, PHP, C#, Swift, Kotlin — and any language with a tree-sitter grammar.

## Free vs Pro

| Feature | Free | Pro ($29/user/mo) | Team ($49/user/mo) |
|---------|:----:|:------------------:|:-------------------:|
| Doc generation | ✓ | ✓ | ✓ |
| Drift detection | | ✓ | ✓ |
| Git hooks | | ✓ | ✓ |
| Auto-fix | | ✓ | ✓ |
| Onboarding guides | | | ✓ |
| Architecture docs | | | ✓ |
| Custom templates | | | ✓ |

**Free tier is fully functional** for one-shot doc generation. Pro adds the "living docs" workflow.

## Privacy

- **100% local processing** — your code never leaves your machine
- **Zero telemetry** — no analytics, no tracking, no phone-home
- **Offline license validation** — works in air-gapped environments

## FOSS Stack

Built entirely on open-source tools:

- [tree-sitter](https://tree-sitter.github.io/) — Multi-language AST parsing (MIT)
- [lefthook](https://github.com/evilmartians/lefthook) — Git hooks manager (MIT)
- [difftastic](https://difftastic.wilfred.me.uk/) — Structural diff tool (MIT)

## Contributing

PRs welcome! See [CONTRIBUTING.md](CONTRIBUTING.md).

## License

MIT — free to use, modify, and distribute.

The DocSync skill scripts are MIT licensed. Premium features (drift detection, hooks, auto-fix) require a [license key](https://docsync.pages.dev/#pricing).
