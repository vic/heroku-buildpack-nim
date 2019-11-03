Heroku Buildpack for Nim
========================

This is a [Heroku-compatible buildpack](http://devcenter.heroku.com/articles/buildpacks) for [Nim](http://nim-lang.org) apps. It uses [Nimble](https://github.com/nim-lang/nimble) for dependency management.

Currently supports Nim version 1.0 and upwards.

Example
-------

```shell
$ tree
.
├── Procfile
├── app.nimble
└── src
    └── app.nim

$ heroku create --buildpack https://github.com/vic/heroku-buildpack-nim.git
Creating your-app-1234
...

$ git push heroku master
...
```

Minimum `.nimble` file:

```ini
# Package

version       = "0.1.0"
author        = "John Doe"
description   = "my next great API"
license       = "MIT"
srcDir        = "src"
bin           = @["app"]

# Dependencies

requires "nim >= 1.0.2", "jester >= 0.4.3"
```

Usage
-----

The buildpack expects you to include a `.nimble` file in order to download dependencies and build your app.

Be sure to set the [bin](https://github.com/nim-lang/nimble#binary-packages) value on your nimble file to the executable name for your app.

And create a `Procfile` with a process to run for your executable. Should be the same binary that you defined in the `bin` setting of your `.nimble` file:

```yaml
web: ./app
```

Create an app using this buildpack

```shell
heroku create --buildpack https://github.com/vic/heroku-buildpack-nim.git
```

Nim version
-----------

Since Nim's master branch is deprecated, you have to define the branch of the Nim version that should be installed by this buildpack.

This buildpack was tested with Nim version 1.0:

```shell
heroku config:set NIM_BRANCH=version-1-0
```

You can use the most recent development version this way:
```shell
heroku config:set NIM_BRANCH=devel
```


Example
-------

An [example nimble app](https://github.com/vic/nim-heroku-example) lives [here](http://nim-heroku-example.herokuapp.com)
