# Scope of commands in a workspace

These specs describe how pnpm commands behave inside workspaces (a.k.a. monorepos or multi-package repositories).

By default, every pnpm command only affects the `package.json` and `node_modules` in the *current working directory*.
So running `pnpm install foo` in the root of the workspace will only add `foo` to the `package.json` in the root of the monorepo.
Likewise, running `pnpm install foo` in any package in any subfolder, will only add `foo` to the single package.

In order to run a command on many packages of the workspace, filtering should be used.
For instance, to perform installation in every package of the workspace, run `pnpm install -- .` in the root of the workspace
(or `pnpm install -r`).

Let's see how it will work on the next workspace:

```
.
├─ pnpm-workspace.yaml
├─ libs
|  ├─ lib-a
|  └─ lib-b
└─ packages
   ├─ pkg-a
   └─ pkg-b
package.json
```

1. Running `pnpm install` in the root will only create `node_modules` for the root `package.json`.
1. Running `pnpm install -r` (or `pnpm install -- .`) in the root will install dependencies of all workspace packages.
1. Running `pnpm install -r` (or `pnpm install -- .`) in `libs/` directory will only install dependencies of `lib-a` and `lib-b`.
