# simple_automation
A simplified automation project to exemplify automation


* `gem install bundler`
* `bundle install`
* `cucumber --init`

In the generated env.rb file, add the following:
```
require 'capybara'
require 'capybara/cucumber'
require 'selenium-webdriver'

Capybara.default_driver = :selenium_chrome_headless
```

Create a new file named Rakefile, and add the following:
```
require 'rubygems'
require 'cucumber'
require 'cucumber/rake/task'

Cucumber::Rake::Task.new(:features) do |t|
  t.cucumber_opts = "--format pretty" # Any valid command line option can go here.
end
```

to run tests use the command


* `rake features`
