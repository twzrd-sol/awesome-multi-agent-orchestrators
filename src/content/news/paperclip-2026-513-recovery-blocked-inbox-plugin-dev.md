---
title: "Paperclip v2026.513.0 adds source-scoped recovery and a Blocked Inbox"
description: "Paperclip released v2026.513.0 with first-class recovery actions on source issues, a Blocked Inbox attention view, local plugin development scaffolding, ordered sub-issue navigation, and remote sandbox resume hardening."
date: 2026-05-13T22:24:48Z
playerSlug: "paperclip"
sourceName: "Paperclip v2026.513.0 GitHub release"
sourceUrl: "https://github.com/paperclipai/paperclip/releases/tag/v2026.513.0"
category: "Release"
tags:
  - orchestration
  - recovery
  - blockers
  - plugins
draft: false
---

![Paperclip recovery and Blocked Inbox diagram](/images/news/paperclip-2026-513-recovery-blocked-inbox.svg)

Paperclip released `v2026.513.0` on 2026-05-13, and the release keeps pushing the product toward a more operator-readable control plane for agent work.

The main shift is recovery. Instead of treating stalled or missing-disposition work as a side-channel cleanup problem, Paperclip now creates first-class recovery actions on the source issue itself. Those actions carry an owner, evidence, wake policy, and a resolution outcome: `restored`, `blocked`, `cancelled`, or `false_positive`.

Highlights:

- Source-scoped recovery actions make stalled-work recovery visible on the original issue, active run panels, blocker notices, and issue rows.
- Blocked resolutions now require a real first-class blocker rather than a comment-only explanation.
- The new Blocked Inbox tab gives operators a dedicated attention view for blocked work, with blocked-reason chips, filtering, search, deterministic urgency sorting, responsive layouts, and a backend blocker-attention contract.
- Local plugin development gets a CLI-first workflow: `paperclipai plugin init`, local-path installs, plugin key routing, dashboard capabilities, dev watcher startup and reload, SDK worker entrypoint validation, a new guide, and refreshed `paperclip-create-plugin` skill instructions.
- Ordered sub-issue navigation lets the issue detail footer move through siblings and into a parent's first ordered child while preserving hidden-issue filtering and dependency-aware ordering.
- Remote sandbox host workspace resumes are hardened: Paperclip persists the host workspace cwd, rejects unsafe saved directories, skips non-file entries during restore snapshots, and limits model-provider API keys passed to environment-driver plugins.
- A comment-listing regression tied to `Date` binding in postgres-js was fixed with ISO timestamp binding and explicit `::timestamptz` casts.

For Open Orchestrators readers, the important signal is that Paperclip is turning failure recovery into a product surface. Blocked work, stalled runs, recovery ownership, evidence, wake behavior, and plugin authoring are becoming explicit pieces of the operator loop instead of hidden background behavior.

That matters because multi-agent systems do not only need more workers. They need a clean way to see why work stopped, who owns the next move, whether the right blocker exists, and how to extend the system safely with plugins.

Operators should read the full release notes before upgrading. The release includes one additive database migration, `0084_issue_recovery_actions`, which adds the `issue_recovery_actions` table and supporting indexes. No application configuration changes are required.

Source confidence: High. The article is based on the official Paperclip GitHub release.

Evidence:

- [Paperclip v2026.513.0 GitHub release](https://github.com/paperclipai/paperclip/releases/tag/v2026.513.0)
- [Paperclip GitHub repository](https://github.com/paperclipai/paperclip)
- [Open Orchestrators Paperclip player note](https://openorchestrators.org/players/paperclip/)

Explicit non-claims:

- This update does not claim source-scoped recovery eliminates every stalled-work case.
- This update does not benchmark the new Blocked Inbox against other project-management or incident-triage systems.
- This update does not claim every local plugin development path is stable for every third-party package layout.
