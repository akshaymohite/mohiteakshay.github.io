---
layout: post
title:  "Rspec how to precompile assets for tests on Circle CI"
date:   2017-02-22 21:00:00 +0530
categories: rails
---

The other day, I was working on rspec and feature specs with Rails application.
The codebase had large number of javascript assets.
We had rspec and capybara with selenium webdriveer as the tools for running specs.
The first feature specs was getting timed out as assets were not getting compiled
in the capybara timeout specified in configuration. We precompiled assets for
circle CI where tests are run.


### Problem

The capybara timeout is specified as,

{% highlight ruby %}
  client = Selenium::WebDriver::Remote::Http::Default.new
  client.timeout = 60
{% endhighlight %}

Whenever first feature spec is run, the assets are compiled on the first request.
The feature spec is timed out if the server does not respond in the timeout which
is specified in for the selenium webdrive client.

As the assets were taking longer than the time required in which server is supposed to respond,
the first feature specs was failing. Thus, build was getting failed.

### Solution

We precompiled assets when tests are run.
This made sure that compiled assets are served directly when request is made for
the feature specs.

### Code

Added following block in `before(:suite)` to make sure that assets are
precompiled when specs are run.

{% highlight ruby %}
  config.before(:suite) do
    if ENV['CIRCLECI']
      Rails.application.load_tasks
      Rake::Task['assets:precompile'].invoke
    end
  end
{% endhighlight %}

- This makes sure that assets are precompiled only if the environment running
the specs is `CIRCLECI`. This flag is automatically avaiable if you're running
specs on CircleCI.

- It loads the `Rails.application.load_tasks` task and then invokes the
asset precompilation task defined in rails.

### Advantages

- This helped us in making sure that specs are not getting failed, as there was
no reason for build to get failed.
- This also makes sure that your assets don't have any issue and your app can
be deployed to production. (It won't have any issue related to assets.)
