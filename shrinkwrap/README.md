# Specifications of pnpm's shrinkwrap file

The purpose of pnpm's shrinkwrap file is to freeze the state of `node_modules`. It has the same purpose as npm's `package-lock.json` and Yarn's `yarn.lock`.

## Relation of pnpm version to shrinkwrap file version

| shrinkwrap file version | used by pnpm versions |
| -- | -- |
| 3  | 1  |
| 2  | 0.62>=, <1 |
