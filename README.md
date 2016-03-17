# React Setup with NPM, Babel and Webpack

## NPM

- __application is usually made up of a bunch of different modules__ (a module being just some code that you've decided to group together).
- If wanted underscore, jQuery => their modules have to be installed.
- Modules are not only for library / framework. __Programs also__
- __NPM allows__ you to easily __manage different packages__ (modules) and keep track of which version you've installed

### Steps
- ```npm init```
- ```npm install jquery --save``` => to test with one module

  =>- ```node_modules``` folder which contains jquery and any of jquery's dependencies
    - inside of your package.json file you should see that jquery is saved under "dependencies".

__if you were collaborating with a teammate, instead of having to push your entire node_modules folder to github, your teammate can just clone your project and run npm install and all of your dependencies that are saved inside of your package.json file (in this case just jquery) will be downloaded to her node_modules folder.__

```--save``` saves jQuery to our package.json file as a dependency

### NPM scripts

Inside of your package.json file, under the "scripts" property, add
```  "scripts": {
    "test": "ava 'app/**/*.test.js' --verbose --require ./other/setup-ava-tests.js"
  }```
=> Now, whenever you run __npm run test__ in your command line, that ava command will get ran and your tests will run
