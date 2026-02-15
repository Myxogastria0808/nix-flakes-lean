# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A Lean 4 sample project using Nix flakes for development environment management. The project is configured as an executable (not a library).

## Development Environment

The dev environment is managed via Nix flakes with direnv integration (`.envrc` → `use flake`). The flake provides `lean4` and `elan` (Lean version manager). The Lean toolchain version is pinned to `leanprover/lean4:4.27.0` in `lean-toolchain`.

## Build & Run Commands

```sh
lake build                    # Build the project
lake exe nix-flakes-lean      # Run the compiled executable
./run.sh                      # Build and run in one step
```

## Project Structure

- `Main.lean` — Executable entry point (defines `main : IO Unit`)
- `nix-flakes-lean.lean` — Library root module, imports submodules
- `nix-flakes-lean/Basic.lean` — Library submodule
- `lakefile.toml` — Lake build configuration (package name: `nix-flakes-lean`, default target: executable)
- `flake.nix` — Nix flake defining the dev shell

## CI

GitHub Actions workflow (`.github/workflows/lean_action_ci.yml`) runs on push, PR, and manual dispatch using `leanprover/lean-action@v1`.
