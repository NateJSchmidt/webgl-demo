# webgl-demo
Thie repository follows the basic [threejs demo from their website](https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene), which makes a rotating cube appear in your browser.  The motivation for creating this repository is to layout and explain how this demo is done with a realistic workflow.  Sure it'll all work if you download threejs, open vi (or your favorite editor), and start banging out the code, but unless you plan to write everything in plain text files without any other dependencies, this is unrealistic.

This repository demonstrates one possible way to create the [demo](/src/demo.ts), but with an IDE and a development environment capable of pulling in depencies and delivering a product.  Note that I didn't orchestrate the deployment (although this could be done easily enough with running nginx in Docker) - perhaps I'll get to this in a future update.

## Laying out the main components
* **Node.js and yarn** - While this code doesn't run on a Node.js server, it still utilizes the Node.js repository for dependencies.  It does this using _yarn_.  So you will want to make sure that you have installed _nodejs_ and _yarn_
* **Project structure** - All dependencies for this project are defined in [package.json](/package.json).  I built this using yarn.  I first ran `yarn init` and then did `yarn add -D <package_name>` for each dependency I had.
* **Webpack** - Webpack is where most of the magic happens.  See [webpack.js.org](https://webpack.js.org/) for the details, but in short webpack is what builds and bundles my product.  It produces the following files in a _build_ directory based on the configured specified in [webpack.config.js](/webpack.config.js):
  * index.html
  * bundle.js
* **Typescript** - Believe it or not, this project is not coded in javascript.  It is actually written in [typescript](https://www.typescriptlang.org/).  Webpack uses a typescript loader, `ts-loader`, to do the compilation.  The real source code is located in [demo.ts](/src/demo.ts).

## Steps to get setup and going
1. Clone this repository and go to it's root
2. Download all of the dependencies by running:  `yarn install`
3. Compile with `./node_modules/.bin/webpack-cli`
4. Run the demo by double clicking the `./build/index.html` file that gets created (note that the `./build/bundle.js` file is pulled in as a script)
5. Done

## Development environment
You can build and run this wherever you do your web development, but I figure I'll list my setup because it may help someone...  I developed this on Windows 10 running Ubuntu 18.04 LTS in WSL 1.0.  The IDE I used is Visual Studo Code with the Remote - WSL plugin to run it through WSL.

There are a couple of annoying "gotchas" with WSL 1.0.  See my other repository [here](https://github.com/NateJSchmidt/wsl1.0-workarounds) for some scripting to help you get around some of them.