# lerna-getting-started

[![lerna](https://img.shields.io/badge/maintained%20with-lerna-cc00ff.svg)](https://lerna.js.org/)

Lerna helps to solve this by allowing easy management of multiple JS applications/ repositories by:

- Allowing sharing of common packages across all applications

- Allowing sharing of commands across all applications

### Getting Started - Allowing sharing of common packages across all applications

Each package maintains its node_modules with all dependencies it needs. Hoisting dependencies to the root of the repository is possible. Let's try it...

```sh 
$ npm run bootstrap
```

which internally calls `` npx lerna clean -y && npx lerna bootstrap --hoist``

Now all packages are installed in the root of the repository, and node_modules local to packages contain only symlinks.

### Allowing sharing of commands across all applications
By using ``npm run lerna-test`` command, Lerna will look at each package's package.json file for an npm script that matches the script and runs it.
