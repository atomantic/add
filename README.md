# ADD: Automation Driven Development
### Building apps with an emphasis on continuous delivery

Why?

* The most important thing is shipping. Now.
* Manual dependency management stinks.
* Manual deployment stinks.
* Manually managing a static set of template tools stinks.
* Where you deploy should be flexible and it should happen automatically.

### Creating this repo from scratch
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
    # test it
    gem install travis-lint
    travis-lint;
    # make sure we can run jshint without grunt just because we like to sometimes (IDE support)
    echo 'app/scripts/vendor
    app/bower_components' >> .jshintignore
    # setup gh-pages merge on build success
    yo travis-ci:gh-pages


[![Build Status](https://travis-ci.org/atomantic/add.png?branch=master)](https://travis-ci.org/atomantic/add)
