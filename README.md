# lerna-getting-started

[![lerna](https://img.shields.io/badge/maintained%20with-lerna-cc00ff.svg)](https://lerna.js.org/)


### About

Splitting up large codebases into separate independently versioned packages is extremely useful for code sharing. However, making changes across many repositories is messy and difficult to track, and testing across repositories gets complicated really fast.

To solve these (and many other) problems, some projects will organize their codebases into multi-package repositories (sometimes called monorepos). Projects like [Babel](https://github.com/babel/babel/tree/master/packages), [React](https://github.com/facebook/react/tree/master/packages), [Angular](https://github.com/angular/angular/tree/master/modules),
[Ember](https://github.com/emberjs/ember.js/tree/master/packages), [Meteor](https://github.com/meteor/meteor/tree/devel/packages), [Jest](https://github.com/facebook/jest/tree/master/packages), and many others develop all of their packages within a single repository.

Lerna is a tool that optimizes the workflow around managing multi-package repositories with git and npm.

Lerna can also reduce the time and space requirements for numerous copies of packages in development and build environments - normally a downside of dividing a project into many separate NPM packages. See the [hoist documentation](https://github.com/lerna/lerna/blob/master/doc/hoist.md) for details.

### What does a Lerna repo look like?
There's actually very little to it. You have a file structure that looks like this:

```sh
my-lerna-repo/
  package.json
  packages/
    package-1/
      package.json
    package-2/
      package.json
```

### What can Lerna do?
The two primary commands in Lerna are ``lerna bootstrap`` and ``lerna publish``.

bootstrap will link dependencies in the repo together. publish will help publish any updated packages.

### What can't Lerna do?
Lerna is not a deployment tool for serverless monorepos. Hoisting might be incompatible with traditional serverless monorepo deployment techniques.



### --hoist

Install external dependencies at the repo root so they're available to all packages. Any binaries from these dependencies will be linked into dependent package node_modules/.bin/ directories so they're available for npm scripts. If the option is present but no glob is given the default is ** (hoist everything). This option only affects the bootstrap command.

```sh
$ lerna bootstrap --hoist
```

For background on --hoist, see the [hoist documentation](https://github.com/lerna/lerna/blob/master/doc/hoist.md).

Note: If packages depend on different versions of an external dependency, the most commonly used version will be hoisted, and a warning will be emitted.
