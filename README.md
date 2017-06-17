# jasmine-karma-travis-test
A sample repo to set up a JS project with automated testing

Created using the walkthrough by Bryan Braun, here:  
https://www.bryanbraun.com/2015/05/17/setting-up-automated-testing-for-a-small-client-side-javascript-project/


### Getting started:   

Here's a [Gist](https://gist.github.com/bannastre/f470ad091849239dd7e38680197c465c) here with a sample of the files I put together using the walkthrough 

#### 1. Create a 'package.json' file that contains the following:

    {
    "name": "project-name",
      "description": "My Project&#39;s Description",
      "version": "0.0.1",
      "devDependencies": {
        "jasmine-core": "*"
      }
    }

#### 2. initialise the package modules using npm

    $ npm install
    
#### 3. Download and add a Jasmine stand-alone file to the project folder   

    $ unzip jasmine-standalone-{version}.zip

##### or install globally and initialize the project you are working on:
    
    $ npm install -g jasmine
    $ jasmine init 
    
 - Get the latest [version](https://jasmine.github.io/pages/getting_started.html)  


#### 4. Install PhantomJS browser webkit to test against   

    $ brew install phantomjs

#### 5. Install Karma test runner

    $ npm install --save-dev karma karma-jasmine karma-jasmine-jquery karma-phantomjs-launcher karma-coverage karma-cli
    $ karma init

  ##### Karma config (karma.conf.js):  
  
  Have a look at the [Gist](https://gist.github.com/bannastre/f470ad091849239dd7e38680197c465c) for a complete config file: 

        frameworks: [
          'jasmine'
        ],
        files: [
          'src/*.js',
          'spec/*.js'
        ],
        exclude: [
          'src/interface.js'
        ],
        preprocessors: {
          'src/*.js': 'coverage'
        },
        plugins: [
          'karma-jasmine',
          'karma-phantomjs-launcher',
          'karma-coverage'
        ],
        reporters: [
          'progress',
          'coverage'
        ],
        coverageReporter: {
          type: 'text',
          dir: 'coverage/'
        },
        browsers: ['PhantomJS'],

- Karma [docs](http://karma-runner.github.io/1.0/index.html)

#### 6. Add the test scripts to package.json

      "scripts": {
        "test": "karma start karma.conf.js --single-run"
      },
      
  devDependencies should now look like this:
  
        "devDependencies": {
          "jasmine-core": "*",
          "karma": "^1.7.0",
          "karma-cli": "^1.0.1",
          "karma-coverage": "^1.1.1",
          "karma-jasmine": "^1.1.0",
          "karma-jasmine-jquery": "^0.1.1",
          "karma-phantomjs-launcher": "^1.0.4"
        }
         
#### 7. Re-initialise the package modules using npm

    $ npm install

#### 8. Travis

- Add the following to .travis.yml file:

    ```
    language: node_js
    node_js:
        - "6"
    before_script:
        - "npm install -g jasmine"
        - "npm install"
    ```
