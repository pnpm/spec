# Specifications of pnpm's shrinkwrap file

The purpose of pnpm's shrinkwrap file is to freeze the state of `node_modules`. It has the same purpose as npm's `package-lock.json` and Yarn's `yarn.lock`.

## Relation of pnpm version to shrinkwrap file version

| shrinkwrap file version | used by pnpm versions |
| --   | --             |
| 5.0  | >=3.0.0       |
| 3.9 and 4.0  | >=2.17.0       |
| 3.9  | >=2.13.3       |
| 3.8  | >=2.8.0       |
| 3.7  | >=2.0.0       |
| 3.6  | >=1.43.0       |
| 3.5  | >=1.40.0       |
| 3.4  | >=1.23.0       |
| 3.3  | >=1.22.0       |
| 3.2  | >=1.18.1       |
| 3.1  | >=1.17 <1.18.1 |
| 3    | >=1 <1.17      |
| 2    | >=0.62 <1      |
