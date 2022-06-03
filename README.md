# simple_automation
A simplified automation project to speed up getting started

# Setup
* `gem install bundler`
* `bundle install`
* `cucumber --init`

Automation drivers for your browser and os are also required. On Mac they can be installed with homebrew:

`brew install chromedriver geckodriver`

In the generated env.rb file, add the following:
```
require 'capybara'
require 'capybara/cucumber'
require 'selenium-webdriver'

Capybara.default_driver = :selenium_chrome_headless
```

Note: available drivers with the selenium-webdriver gem and can be used in place of the above driver config
* selenium (Firefox with a window)
* selenium_headless (Firefox without a window)
* selenium_chrome (Chrome with a window)
* selenium_chrome_headless (Chrome without a window)

Create a new file named Rakefile, and add the following:
```
require 'rubygems'
require 'cucumber'
require 'cucumber/rake/task'

# available formats: message, progress, pretty, html, json, rerun, junit, testng
# info about other formats at https://cucumber.io/docs/cucumber/reporting/
Cucumber::Rake::Task.new(:features) do |t|
  t.cucumber_opts =["--format pretty", "--publish-quiet"] # Any valid command line option can go here.
end
```

# Writing Test Cases
Create a new file in _features_ directory with the file extension `.feature` and add the following template:
```
Feature: Your feature
Scenario: Your scenario
Given starting conditions
When test actions
Then test outcome
```

Notes:
* Only one Feature is allowed per file. To organize tests into more features, add one file for each additional feature.
* Each Scenario describes a single test case. Begin new test cases by defining a new Scenario.
* Use only one `Given`, `When`, and `Then` definition per test case. For multiple lines for each keyword, use the keyword `And`. Each `And` is an extension of the `Given`, `When`, or `Then` most recently defined within the same test case.
* All uses of `And` must follow either a defined `Given`, `When`, or `Then`.

# Automating Test Cases
Create a new file in _features/step_definitions_ directory with the file extension `.rb`. Running tests without defined step code will provide a template for each method you need to define.
https://rubydoc.info/github/jnicklas/capybara is a good reference for how to define steps.

# Running Test Cases
To run tests use terminal to run the command:

`rake features`
