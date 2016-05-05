<div align="center">
<img src="https://cloud.githubusercontent.com/assets/1616682/11403449/409e561e-9373-11e5-9aeb-7dbea090a0bd.gif" width="400px" />

Create node modules writing ES6 today compiled with `Babel`, test with `ava` and lint with `standard` on top of npm scripts

<p>
<a href="https://npmjs.org/package/generator-mnm">
  <img src="https://img.shields.io/npm/v/generator-mnm.svg?style=flat">
</a>
<a href="https://travis-ci.org/maurizzzio/generator-mnm">
  <img src="https://img.shields.io/travis/maurizzzio/generator-mnm.svg?style=flat">
</a>
<a href="https://npmjs.org/package/generator-mnm">
  <img src="http://img.shields.io/npm/dm/generator-mnm.svg?style=flat">
</a>
</p>

</div>
    
## Install

```sh
$ npm install -g yo generator-mnm
```

## Usage

```sh
$ yo mnm
```

<div align="center">
<img src="https://cloud.githubusercontent.com/assets/1616682/11389890/2d80b6a6-931b-11e5-910c-f2594f485098.gif">
</div>

## Features

- Made out of many other generators, the main generator only creates a `package.json` file
- Composable, since the logic to create the README, cli and other files is in its own subgenerator you just have to plug as many subgenerators as you need to your own generator
- [Babel](https://babeljs.io) for the code/tests
- [standard](http://standardjs.com/) to lint the code
- [ava](https://github.com/sindresorhus/ava) for testing
- [yargs](https://github.com/bcoe/yargs) to parse cli arguments (optional)
- [jsnext:main](https://github.com/rollup/rollup/wiki/jsnext:main) field included if you want to bundle your library using a ES6 module bundler like [Rollup](https://github.com/rollup/rollup)
- npm scripts as the build system

## Example

Check [https://github.com/maurizzzio/generator-mnm-example](https://github.com/maurizzzio/generator-mnm-example)

## List of npm scripts included

Common tasks

| task       | description  |
| -----      | ---          |
| `npm test` | `ava` |
| `npm run lint` | Lints the code with [standard](http://standardjs.com) |
| `npm run build` | Transforms the ES6 code located at `lib/` with [Babel](https://babeljs.io) (output goes `dist/`)| 
| `npm run clean` | Removes all the files inside the `dist/` directory using [rimraf](https://github.com/isaacs/rimraf)|

Watching files

| task | description |
| --- | --- |
| `npm run test:watch` | `ava --watch` |
| `npm run build:watch` | `babel ... --watch` |

### Useful npm commands that you should know

- `npm version major|minor|patch` bumps the package version
- `npm run` lists all available scripts

## Why?

This project is heavily inspired by [this article by Keith Cirkel][stop-using-grunt-gulp] where he describes that the existing build system tools attempt to solve the problems that exist among them "covering up the inadequacies of the other tools while also surfacing their own".

[James Halliday](https://www.npmjs.com/~substack) who is the creator of many awesome packages like `browserify` and `tape` also wrote an article where he points out that the command `npm run` is "perfectly adequate for everything while maintaining a very tiny configuration footprint."

### Articles to read:

- [Why we should stop using grunt][stop]
- [How to use npm as a build tool][how-to]
- [Task automation with run][task-automation]
- [Choose grunt, gulp or npm][choose]

### Inspiration projects

- https://github.com/yeoman/generator-node
- https://github.com/vinniegarcia/ES6-module-starter
- https://github.com/sindresorhus/generator-nm
- https://github.com/bucaran/generator-rise
- https://github.com/keithamus/npm-scripts-example 's awesome `package.json` file

## Composability

Just plug in any of the subgenerators or the generator itself on your generator

<div align="center">
<img src="https://camo.githubusercontent.com/f8dc3e07d956f1f8dbdea5f895800fe53772a50d/687474703a2f2f692e696d6775722e636f6d2f326771696966742e6a7067">
</div>

Generators used in this project

- [generator-babel](https://github.com/iamstarkov/generator-babel)
- [generator-travis](https://github.com/iamstarkov/generator-travis)
- [generator-git-init](https://github.com/iamstarkov/generator-git-init)
- [generator-license](https://github.com/jozefizso/generator-license)
- [generator-mnm/generators/src](./generators/src)
- [generator-mnm/generators/test](./generators/test)
- [generator-mnm/generators/cli](./generators/cli)
- [generator-mnm/generators/git](./generators/git)
- [generator-mnm/generators/readme](./generators/readme)

Refer to their README files on how to include it your generators

## Workflow

Typically 

```sh
# also check https://www.npmjs.com/package/initialize
npm init -y && git init

# generates src/index.js
# installs standard, babel-cli
# setup package.json standard ignore and .babelrc with babel-preset-2015
yo mnm:src

# generates test/index.js and links it with src/index.js
# installs ava
yo mnm:test
# alternative with code coverage enabled
yo mnm:test --coverage

# .gitignore
curl https://www.gitignore.io/api/node,vim >> .gitignore

# see https://www.npmjs.com/package/ghrepo
ghrepo -m "._."
# see https://www.npmjs.com/package/travisjs
travisjs hook
```

## Development

- `npm test`, `npm test:ci` run the tests

## License

2015-2016 MIT © [Mauricio Poppe](http://maurizzzio.com)

[stop-using-grunt-gulp]: http://blog.keithcirkel.co.uk/why-we-should-stop-using-grunt/
[stop]: http://blog.keithcirkel.co.uk/why-we-should-stop-using-grunt/
[how-to]: http://blog.keithcirkel.co.uk/how-to-use-npm-as-a-build-tool/
[task-automation]: http://substack.net/task_automation_with_npm_run
[choose]: http://ponyfoo.com/articles/choose-grunt-gulp-or-npm

