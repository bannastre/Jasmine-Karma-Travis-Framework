# jasmine-karma-travis-test
A sample repo to set up a JS project with automated testing

Created using the walkthrough by Bryan Braun, here:  
https://www.bryanbraun.com/2015/05/17/setting-up-automated-testing-for-a-small-client-side-javascript-project/


## Steps to follow:

#### 1. Package.json

    ```
    {
    "name": "project-name",
      "description": "My Project&#39;s Description",
      "version": "0.0.1",
      "devDependencies": {
        "jasmine-core": "*"
      }
    }```  

#### 2. npm install  

    ```$ npm install```


#### 3. Add Jasmine stand-alone file  
- Get the latest file [here]()
- run ```$unzip unzip jasmine-standalone-{version}.zip```


#### 4. PhantomJS  

    ```$ brew install phantomjs```

#### 5. Karma

    ```$ npm install --save-dev karma karma-cli karma-jasmine karma-phantomjs-launcher```  

    ```$ karma init```

#### 6. Travis
    Add the following to ```.travis.yml``` file:

    ```
    language: node_js
    node_js:
        - "6"
    before_script:
        - "npm install -g jasmine"
        - "npm install"
    ```
