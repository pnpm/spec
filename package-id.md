# Package ID

An identifier that can be used to detect the source of the package.
Is always a valid filesystem path.

## Packages from npm-compatible registries

`<registry URL>/<package name>/<package version>`

E.g.:

```
registry.npmjs.org/gulp/2.1.0
registry.npmjs.org/@cycle/dom/14.1.0
registry.node-modules.io/@wmhilton/log/1.1.0
```

If the registry origin has a protocol then the `:` is substituted with a `+`.

```
localhost+4873/foo/1.0.0
```

## Packages from Git

`<Git URL domain>/<Git path>/<commit hash>`

E.g.: `github.com/alexGugel/ied/b246270b53e43f1dc469df0c9b9ce19bb881e932`
