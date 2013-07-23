# ADD: Automation Driven Development
### Building apps with an emphasis on continuous delivery

The only thing worse than putting a bug into production is not being able to push out a fix the minute you know a bug exists.

### Why?

* The most important thing is shipping. Now.
* You can NEVER know everything that can go wrong until you are in production, in front of users
* You will NEVER know 100% of your acceptance/usage criteria until you are in production, in front of users
* You need to be able to respond to users immediately and automatically.
* Manual dependency management stinks.
* Manual deployment stinks.
* Manually managing a static set of template tools stinks.
* Where you deploy should be flexible and it should happen automatically.

### Assumptions

* You run OSX (or can manage installation yourself)
* You use [Homebrew](http://mxcl.github.io/homebrew/)
* You have [Node.js](http://nodejs.org/) (with NPM, included now with node)

### Creating this repo from scratch
    # make sure you are up-to-date
    brew update
    brew upgrade # at your own risk
    npm update -g
    # install npm goodness
    npm install -g yo grunt-cli bower yeoman-generator generator-webapp karma generator-mocha generator-karma generator-travis-ci
    # make sure we have phantomjs
    brew install phantomjs
    # and compass
    gem install compass
    # create the project
    mkdir ~/add && cd $_
    # install basic scaffolding
    yo webapp;
    # replace crappy oldIE support with new hotness
    sed -i 's/"jquery": "~1.9.1"/"jquery": "~2.0.2"/' bower.json
     # rebuild bower
    bower install
    # make sure we can run jshint without grunt just because we like to sometimes (IDE support)
    echo 'app/scripts/vendor
    app/bower_components' >> .jshintignore
    # setup gh-pages merge on build success
    yo travis-ci:gh-pages
    # test it
    gem install travis-lint
    travis-lint

## Build Status

[![Build Status](https://travis-ci.org/atomantic/add.png?branch=dev)](https://travis-ci.org/atomantic/add)
