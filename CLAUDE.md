# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project status

This repository is a fresh scaffold: the only tracked file is a placeholder `README.md` (`# weebs`). There is no source code, build system, test setup, or tooling yet, so there are no build, lint, or test commands to document.

Update this file once the stack and project structure are chosen, adding:
- Build, lint, and test commands, including how to run a single test
- A high-level overview of the architecture

## Agent skills

### Issue tracker

Issues are tracked in GitHub Issues on `Penomatikus/weebs` (via the `gh` CLI). See `docs/agents/issue-tracker.md`.

### Triage labels

Default label names: `needs-triage`, `needs-info`, `ready-for-agent`, `ready-for-human`, `wontfix`. See `docs/agents/triage-labels.md`.

### Domain docs

Single-context: one `GLOSSARY.md` and `docs/adr/` at the repo root. See `docs/agents/domain.md`.

### Product spec

How weebs behaves (search, Catalogue rules, Refresh, notifications, UI decisions) is in `docs/spec.md`, written in glossary terms. Read it before working on a feature and update it when behaviour changes.
