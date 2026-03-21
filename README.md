# asm-tricks

Assembly tricks: both construction and detection.

A Cargo workspace for Rust crates targeting multi-architecture assembly manipulation — covering both the generation ("construction") and analysis/identification ("detection") of assembly patterns.

**Current status: pre-implementation skeleton.** The workspace exists with its dependency graph declared but no crates have been written yet. The `crates/` directory is empty.

## Repository

- GitHub: <https://github.com/portal-co/asm-tricks>
- License: MPL-2.0
- Workspace resolver: edition 3 (`resolver = "3"`)

## Workspace layout

```
asm-tricks/
├── Cargo.toml        # virtual workspace root (members = [])
└── crates/           # empty — no crates exist yet
```

The root `Cargo.toml` is a **virtual manifest** (`members = []`). There are no library or binary crates. Attempting to build currently produces:

```
error: manifest path contains no package: The manifest is virtual, and the workspace has no members.
```

## Declared workspace dependencies

The following crates are pinned as `[workspace.dependencies]` for use by future member crates. All are sourced from Git repositories under the `portal-co` GitHub organization.

| Dependency | Version req | Source |
|---|---|---|
| `portal-pc-asm-common` | `0.1.1` | <https://github.com/portal-co/asm-common.git> |
| `rv-asm` | `*` | <https://github.com/portal-co/rv-utils.git> |
| `portal-solutions-asm-x86-64` | `0.1.0` | <https://github.com/portal-co/asm-arch.git> |
| `portal-solutions-asm-aarch64` | `0.1.0` | <https://github.com/portal-co/asm-arch.git> |
| `portal-solutions-asm-riscv64` | `0.1.0` | <https://github.com/portal-co/asm-arch.git> |

The declared targets (x86-64, AArch64, RISC-V 64) indicate the planned scope of architecture support.

## Commit history

| Commit | Message |
|---|---|
| `27af287` | add arch deps |
| `3c1780f` | add deps |
| `156c29a` | init |

## What to expect

Based on the description and dependencies, the intended scope is:

- **Construction**: programmatic assembly of instruction sequences for supported ISAs using the `portal-solutions-asm-*` crates and `rv-asm`.
- **Detection**: pattern matching or identification of known instruction sequences/tricks in existing code.
- **Common infrastructure**: shared types and utilities via `portal-pc-asm-common`.

No API, no examples, and no documentation exist yet beyond this file.
