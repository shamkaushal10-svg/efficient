# Efficient

A Codex skill that reduces token usage while preserving correctness, requested behavior,
artifacts, formatting, and verification.

It makes Codex more selective about file reads, command output, progress updates, repeated
context, and final prose. "Same output" means the same substantive result; wording may be
shorter unless exact text is required.

## Requirements

- Codex with skill support
- Git

## Install

### Linux and macOS

```bash
mkdir -p "${CODEX_HOME:-$HOME/.codex}/skills"
git clone https://github.com/shamkaushal10-svg/efficient.git \
  "${CODEX_HOME:-$HOME/.codex}/skills/efficient"
```

### Windows PowerShell

```powershell
$skills = if ($env:CODEX_HOME) {
  Join-Path $env:CODEX_HOME "skills"
} else {
  Join-Path $HOME ".codex\skills"
}

New-Item -ItemType Directory -Force -Path $skills | Out-Null
git clone https://github.com/shamkaushal10-svg/efficient.git `
  (Join-Path $skills "efficient")
```

Restart Codex after installation so it discovers the skill.

## Use

Invoke the skill explicitly in any prompt:

```text
$efficient fix the failing tests in this repository.
```

```text
$efficient review this pull request and report only actionable findings.
```

```text
Use $efficient to implement this feature with minimal token usage.
```

The skill can be used for coding, debugging, reviews, research, and command-line tasks.

## Verify Installation

The following file should exist:

```text
~/.codex/skills/efficient/SKILL.md
```

If `CODEX_HOME` is set, look under `$CODEX_HOME/skills/efficient/SKILL.md` instead.

## Update

Linux and macOS:

```bash
git -C "${CODEX_HOME:-$HOME/.codex}/skills/efficient" pull --ff-only
```

Windows PowerShell:

```powershell
$root = if ($env:CODEX_HOME) { $env:CODEX_HOME } else { Join-Path $HOME ".codex" }
git -C (Join-Path $root "skills\efficient") pull --ff-only
```

Restart Codex after updating.

## Uninstall

Linux and macOS:

```bash
rm -rf "${CODEX_HOME:-$HOME/.codex}/skills/efficient"
```

Windows PowerShell:

```powershell
$root = if ($env:CODEX_HOME) { $env:CODEX_HOME } else { Join-Path $HOME ".codex" }
Remove-Item -Recurse -Force (Join-Path $root "skills\efficient")
```
