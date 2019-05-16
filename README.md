# simple_automation
A simplified automation project to exemplify automation


* `gem install bundler`
* `bundle install`
* `cucumber --init`

In the generated env.rb file, add the following:
```require 'capybara'
require 'capybara/cucumber'
require 'selenium-webdriver'

Capybara.default_driver = :selenium_chrome_headless
```
