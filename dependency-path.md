# Dependency path

A path to a dependency with a specific set of resolved subdependencies.
It is always a valid filesystem path.
It mostly equals the [package ID](package-id.md) of the dependency but may differ when:

1. The package has peer dependencies which are resolved neither by its own dependencies nor with top dependencies.
2. The package has dependencies with peer dependencies that are resolved from higher in the dependency tree.

In those cases the package path has the next format: `<package ID>/<peer specs...>`

E.g., if `foo@1.0.0` dependends on peers `bar@2.0.0` and `@scope/qar@3.0.0` then its path is: `/registry.npmjs.org/foo/1.0.0/bar@2.0.0+@scope!qar@3.0.0`.

Peer specs are joined with `+` and if a peer is scoped then the `/` symbol is escaped with `!`.

## Relative path

