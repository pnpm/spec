# Workspace filtering

When running commands on a workspace, it is possible to limit them to a subset of packages.
pnpm supports package selectors that can be used together with its `recursive` commands:

```sh
pnpm recursive <cmd> [arg..] -- [selector...]
# or
pnpm recursive <cmd> [arg..] --filter <selector-1> --filter <selector-2>...
```

When packages in the workspace are filtered, every package is taken that matches at least one of
the selectors.

## Selecting by path

Selectors that start with `./` are selectors by filesystem path. Selectors by path don't support globs.

### Examples

Select all packages in the `packages` folder:

```sh
pnpm recursive install -- ./packages
```

## Selecting by package name

Selectors that don't start with `./` are selectors by package name.

### Selecting only the specified packages

To select an exact package, just specify its name. For insance,
the following command will be applied on `foo`, `bar` and `@pnpm/config`:

```
pnpm recursive install -- foo bar @pnpm/config
```

### Selecting a package with dependencies

To select a package and its dependencies, prefix the package name with two dots: `..<pkg name>`.
For instance, the next command will run installation in all dependencies of `foo` and in `foo`:

```
pnpm recursive install -- ..foo
```

### Selecting a package with dependents

To select a package and its dependent packages, suffix the package name with two dots: `<pkg name>..`.
For instance, the next command will run installation in all dependents of `foo` and in `foo`:

```
pnpm recursive install -- foo..
```

### Selecting transitive packages

To select all packages that are between two packages in the dependency graph, the two package names
should be concatenated with `..`: `<pkg1>..<pkg2>`.
The following command is performed on all transitive deps of `foo` and `bar` (including `foo` and `bar`):

```
pnpm recursive install -- foo..bar
```

### Combining selectors

Selecting all dependents and dependencies: `<cmd> -- ..<pkg>..`

Selecting dependencies of `pkg1` and transitive dependencies between `pkg1` ang `pkg2`: `<cmd> -- ..pkg1..pkg2`
