# ADD: Automation Driven Development
### Building apps with an emphasis on continuous delivery

Why?

* The most important thing is shipping. Now.
* Manual dependency management stinks.
* Manual deployment stinks.
* Manually managing a static set of template tools stinks.
* Where you deploy should be flexible and it should happen automatically.

### Creating this repo from scratch
`
npm install -g yo grunt-cli bower generator-webapp generator-mocha
mkdir ~/add;
cd ~/add;
yo webapp;
bower install;
echo 'language: node_js
node_js:
    - "0.10"
    - "0.8"
    - "0.6"' >> .travis.yml
gem install travis-lint;
`