# Scope of commands in a workspace

These specs describe how pnpm commands behave inside workspaces (a.k.a. monorepos or multi-package repositories).

# TL;DR

1. Running `pnpm install` in the root will install dependencies of all workspace packages.
1. Running `pnpm install express` in the root will add `express` as a dependency to the root `package.json` only.
1. Running `pnpm install -r express` (or `pnpm install express -- .`) in the root will install express as dependency in all workspace packages.

***

If a command is executed without arguments (for instance, `pnpm install`) then the command affects every package in the workspace. It doesn't matter if the command is executed in the root of the workspace or in any subdirectory of the workspace.

If a command is executed with arguments (for instance, `pnpm install express`) then the command affects only the closest `package.json`. In order to run a command with arguments on many packages, filtering should be used. For instance, to perform installation in every package of the workspace, run `pnpm install express -- .` in the root of the workspace
(or `pnpm install -r express`).
