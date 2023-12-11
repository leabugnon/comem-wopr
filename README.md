# WOPR

Play tic-tac-toe against the WOPR.

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Installation](#installation)
  - [Requirements](#requirements)
  - [Initial setup](#initial-setup)
- [Usage](#usage)
  - [Run in development mode](#run-in-development-mode)
  - [Run in production mode](#run-in-production-mode)
- [Updating](#updating)
- [Configuration](#configuration)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->



## Installation

### Requirements

* [Ruby](https://www.ruby-lang.org) 2.7.x or 3.x
* [Node.js](https://nodejs.org) 20.x
* [Redis](https://redis.io) 4+

### Initial setup

```bash
# Clone the repository
git clone https://github.com/leabugnon/comem-wopr.git
cd comem-wopr

# Configure Bundler.
bundle config set path 'vendor/bundle'

# Install dependencies (Ruby gems & npm packages).
bundle install
npm ci

# Build the web assets.
npm run build
```



## Usage

### Run in development mode

```
cd /path/to/application
bundle exec ruby app.rb
```

### Run in production mode

Set the `$WOPR_ENV` environment variable to run the application in production
mode:

```
cd /path/to/application
WOPR_ENV=production bundle exec ruby app.rb
```

You should point your Apache or nginx web server to the application's `public`
directory, which contains its static files.



## Updating

Your deployment workflow should install new dependencies and re-build the web
assets every time the frontend's source code is updated:

```bash
cd /path/to/application
bundle install
npm install
npm run build
```



## Configuration

The following environment variables can be set to customize the application's behavior:

Variable                        | Default value              | Description
:------------------------------ | :------------------------- | :-------------------------------------------
`WOPR_ENV`                      | `development`              | Set to `production` for deployment.
`WOPR_PORT` or `PORT`           | 4567                       | Port on which to listen to.
`WOPR_REDIS_PREFIX`             | `wopr:`                    | Prefix prepended to all Redis database keys.
`WOPR_REDIS_URL` or `REDIS_URL` | `redis://localhost:6379/0` | Redis connection URL.
