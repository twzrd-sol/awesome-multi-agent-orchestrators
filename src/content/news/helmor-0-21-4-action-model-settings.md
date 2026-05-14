---
title: "Helmor v0.21.4 tightens action-model settings for PR and commit helpers"
description: "Helmor's May 14 stable release keeps Opus 4.7 action-model choices after restart, renames the PR/MR model setting to Action model, and routes create, reopen, commit, and push helpers through that setting."
date: 2026-05-14T12:27:55Z
playerSlug: "helmor"
sourceName: "Helmor GitHub release"
sourceUrl: "https://github.com/dohooo/helmor/releases/tag/v0.21.4"
category: "Release"
tags:
  - orchestration
  - coding-agents
  - action-models
  - pull-requests
  - worktrees
draft: false
---

Helmor's `v0.21.4` release is small, but it is a clean operator-surface signal. The release fixes model settings for Helmor's action helpers: Opus 4.7 selections for Review and Action models now survive restart, and the old PR/MR model setting is renamed to `Action model` because the same setting now drives create PR/MR, reopen PR/MR, and commit-and-push helpers.

That matters for Open Orchestrators readers because Helmor is not only adding another UI preference. It is separating review intent from action intent inside a local coding-agent workbench. When an orchestrator has distinct model choices for reviewing code and taking repository actions, the operator gets a clearer control surface for how agents move from analysis to shipping.

The surrounding release window supports that reading. `v0.21.3` fixed Codex `/goal` continuations so they inherit the current workspace permission mode instead of stale context permissions, while `v0.21.2` improved Codex slash-command discovery from linked directories and the repository root, upgraded bundled Claude Code and Codex CLIs, and added Claude's `/goal` command to the composer.

Taken together, the useful signal is that Helmor is polishing the path from agent plan to repository action: command discovery, goal continuation, permission-mode inheritance, review/action model persistence, and commit/PR helpers. None of those are flashy alone. Combined, they make the local orchestrator feel more like a controlled operator station for Claude Code, Codex, and repo automation.

Source confidence: High for the release details and timestamps from GitHub releases. Medium for downstream workflow implications because the release notes describe control surfaces, not measured improvement in PR quality or shipping speed.

Evidence:

- [Helmor v0.21.4 GitHub release](https://github.com/dohooo/helmor/releases/tag/v0.21.4)
- [Helmor v0.21.3 GitHub release](https://github.com/dohooo/helmor/releases/tag/v0.21.3)
- [Helmor v0.21.2 GitHub release](https://github.com/dohooo/helmor/releases/tag/v0.21.2)
- [Helmor GitHub repository](https://github.com/dohooo/helmor)

Explicit non-claims:

- This update does not claim Helmor's action-model split automatically improves code quality.
- This update does not benchmark Helmor against other local agent IDEs or workbenches.
- This update does not claim every named helper is available in every provider, permission mode, or repository setup.
