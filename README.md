# README

Template for new Rails projects.

## Getting started

To get going clone this repository and perform the following steps:

1. Clone this repository
1. You can now run `bin/configure`, which will help you in configuring the template.
   Alternatively perform all of the following steps manually.
1. Change application name in `config/application.rb`.
1. Update `database.yml` to reflect the new application name.
1. Update `TODO` items in `config/environments/production.rb`.
1. If you plan on using Figaro, copy `config/application.yml.example` to `config/application.yml`.
1. ESLint is preconfigured for modern JS with React support (AirBnB styleguide). If you want to use
   it install packages with `npm install`, otherwise remove `.eslintrc` and `package.json`.
1. If you don't plan on tracking the template, you can remove the `.git` directory.
   Otherwise you can rename the remote:
   ```shell
   $ git remote rename origin rails_new
   ```
1. Add your new remote as appropriate.

## Note on Webpacker, the asset pipeline, and ES6

Note that ES6 will not work by default for files in `app/assets/javascript` because Uglifier will fail to process them.

If you want to use ES6 there, you can modify `config/production.rb`:

```diff
-  config.assets.js_compressor = :uglifier
+  config.assets.js_compressor = Uglifier.new(harmony: true)
```

Also note that for everything to work properly on Heroku, you need to set up your buildpacks like this:

```
heroku buildpacks:clear
heroku buildpacks:set heroku/nodejs
heroku buildpacks:add heroku/ruby
```

We did not enable this by default yet, since this feature still seems to be in flux and Uglifier may get replaced by alternative tools in the short to mid term.

## Optional configurations

* If you want to use [AirBrake](https://airbrake.io), make sure the following 2 environment variables are set:
    * `AIRBRAKE_PROJECT_ID`
    * `AIRBRAKE_API_KEY`
* [New Relic](https://newrelic.com) is pre configured in `config/newrelic.yml`,
  but you need to comment in the environment variables for it work on Heroku
  (lines 10 and 17).

## Environment variables

| Variable              | Comment                                                                 |
| --------------------- | ----------------------------------------------------------------------- |
| GOOGLE_ANALYTICS_ID   | Will be added to the main application layout if set                     |
| BLOCK_HTTP_TRACE      | Disable HTTP TRACE method if set to true/t/1                            |
| DATABASE_URL          | Used for `production` env, automatically set by Heroku                  |
| HTTP_METHOD_BLACKLIST | If you want to block more than just TRACE, e.g. `"TRACE,OPTIONS"`       |
| PORT                  | Port Puma will listen on, defaults to 3000                              |
| RAILS_LOG_TO_STDOUT   | Set by Heroku Ruby buildpack, set manually on other platforms if needed |
| RAILS_MAX_THREADS     | Number of Puma threads, defaults to 5                                   |

## Contents

All of the following have been installed and pre-configured.

### Base system

* Rails 5.1.0
* Ruby 2.4.1
* [pg](https://github.com/ged/ruby-pg) for `ActiveRecord`
* The app is preconfigured for Google Analytics, just add `GOOGLE_ANALYTICS_ID` to the environment.

### General

* [active_model_serializers](https://github.com/rails-api/active_model_serializers)
* [devise](https://github.com/plataformatec/devise)
* [draper](https://github.com/drapergem/draper)
* [figaro](https://github.com/laserlemon/figaro)
* [foreman](https://github.com/ddollar/foreman)
* [high_voltage](https://github.com/thoughtbot/high_voltage)
* [pundit](https://github.com/elabs/pundit)
* [sidekiq](https://github.com/mperham/sidekiq)

### Frontend

All of these are managed by `yarn`.

* [bootstrap4](https://www.npmjs.com/package/bootstrap-v4-dev)
* [jquery](https://www.npmjs.com/package/jquery)
* [jquery-ujs](https://www.npmjs.com/package/jquery-ujs/)
* [popper.js](https://www.npmjs.com/package/popper.js)

### Development

* [bullet](https://github.com/flyerhzm/bullet)
* [memory_profiler](https://github.com/SamSaffron/memory_profiler)
* [newrelic_rpm](https://github.com/newrelic/rpm)
* [nullalign](https://github.com/tcopeland/nullalign)
* [pry](https://github.com/rweng/pry-rails)
* [pry-byebug](https://github.com/deivid-rodriguez/pry-byebug)
* [pry-doc](https://github.com/pry/pry-doc)
* [rack-mini-profiler](https://github.com/MiniProfiler/rack-mini-profiler)
* [RuboCop](https://github.com/bbatsov/rubocop)

### Test

* Preconfigured for Rails 5.1+ system tests with Rspec. Install the necessary driver with `brew install chromedriver` and see `spec/system/landing_page_spec.rb` for an example.
* [bundler-audit](https://github.com/rubysec/bundler-audit)
* [capybara](https://github.com/teamcapybara/capybara)
* [factory_girl_rails](https://github.com/thoughtbot/factory_girl_rails)
* [shoulda-matchers](https://github.com/thoughtbot/shoulda-matchers)
* [spring-commands-rspec](https://github.com/jonleighton/spring-commands-rspec)
* [webmock](https://github.com/bblimke/webmock)

### Production

* [airbrake](https://github.com/airbrake/airbrake)
* [heroku-deflater](https://github.com/romanbsd/heroku-deflater)
* [lograge](https://github.com/roidrage/lograge)
* [rails_12factor](https://github.com/heroku/rails_12factor)
* [rake-timeout](https://github.com/heroku/rack-timeout)
* [secureheaders](https://github.com/twitter/secureheaders)

## Removed

The following default Rails gems have been removed:

* [coffee-rails](https://github.com/rails/coffee-rails)
* [jbuilder](https://github.com/rails/jbuilder)
