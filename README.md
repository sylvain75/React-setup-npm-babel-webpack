# React Setup with NPM, Babel and Webpack

## NPM

- __application is usually made up of a bunch of different modules__ (a module being just some code that you've decided to group together).
- If wanted underscore, jQuery => their modules have to be installed.
- Modules are not only for library / framework. __Programs also__
- __NPM allows__ you to easily __manage different packages__ (modules) and keep track of which version you've installed

### Steps
- ```npm init```
- ```npm install jquery --save``` => to test with one module

=>  ```node_modules``` folder which contains jquery and any of jquery's     dependencies
    - inside of your package.json file you should see that jquery is saved under "dependencies".

__if you were collaborating with a teammate, instead of having to push your entire node_modules folder to github, your teammate can just clone your project and run npm install and all of your dependencies that are saved inside of your package.json file (in this case just jquery) will be downloaded to her node_modules folder.__

```--save``` saves jQuery to our package.json file as a dependency

### NPM scripts

Inside of your package.json file, under the "scripts" property, add
```  "scripts": {
    "test": "ava 'app/**/*.test.js' --verbose --require ./other/setup-ava-tests.js"
  }```
=> Now, whenever you run __npm run test__ in your command line, that ava command will get ran and your tests will run

## WEBPACK

- Webpack needs to know the starting point of your application, or your root JavaScript file.
```// In webpack.config.js
module.exports = {
  entry: [
    './app/index.js'
  ]
}```

- Webpack needs to know which transformations to make on your code. __Loaders__
for instance if coffee script loader needed run ```npm install --save-dev coffee-loader```
```// In webpack.config.js
module.exports = {
  entry: [
    './app/index.js'
  ],
  module: {
    loaders: []
  }
}```
For each Loader:
  - which file type to run the specific transformation on
  - which directories should be included or excluded from being transformed
  - which specific loader we want to run
  ```// In webpack.config.js
  module.exports = {
  entry: [
    './app/index.js'
  ],
  module: {
    loaders: [
      {test: /\.coffee$/, exclude: /node_modules/, loader: "coffee-loader"}
    ]
  },
  }```

- Webpack needs to know to which location it should save the new transformed code.
```// In webpack.config.js
module.exports = {
  entry: [
    './app/index.js'
  ],
  module: {
    loaders: [
      {test: /\.coffee$/, exclude: /node_modules/, loader: "coffee-loader"}
    ]
  },
  output: {
    filename: "index_bundle.js",
    path: __dirname + '/dist'
  },
}```

webpack.config.js file => Webpack configurations => in the root directory

__Usual folder structure:__
```/app
  - components
  - containers
  - config
  - utils
  __index.js__
  __index.html__
/dist
  __index.html__
  __index_bundle.js__
package.json
webpack.config.js
.gitignore```

## Babel
Babel.js is a wonderful tool for compiling your JavaScript. With Webpack you tell it which transformations to make on your code, while Babel is the specific transformation itself. In terms of React, Babel is going to allow us to transform our JSX and ES2016 into actual JavaScript.

run ```run npm install --save-dev babel-core babel-loader babel-preset-react```

__React then isolates the changes between the old and new virtual DOM and then only updates the real DOM with the necessary changes.__
