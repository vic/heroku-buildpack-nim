Heroku buildpack: Nim
=====================

This is a [Heroku buildpack](http://devcenter.heroku.com/articles/buildpacks) for [Nim](http://nim-lang.org) apps. It uses [Nimble](https://github.com/nim-lang/nimble) for dependency management.

Usage
-----

The buildpack expects you to include a `.nimble` file in order to download dependencies and build your app.


Be sure to set the [bin](https://github.com/nim-lang/nimble/blob/master/developers.markdown#binary-packages) value on your nimble file to the executable name for your app.

And create a `Procfile` with a process to run for your executable:

```yaml
web: ./main
```

Create an app using this buildpack

```shell
heroku create --stack cedar --buildpack https://github.com/vic/heroku-buildpack-nim.git
```

Options
-------

You may want to set the following variables using `heroku config:set`

```shell
NIM_BRANCH=master # set to devel if your app needs latest Nim version


NIM_REPO=git://github.com/Araq/Nim.git # change only if using your own nim fork


NIMBLE_DEP=nimble # an specific nimble dependency if needed, like nimble@#master

```

If you want to use an specific Nim version use the `NIM_BRANCH` environment variable.

```shell
heroku config:set NIM_BRANCH=devel
```


Example
-------

An [example nimble app](https://github.com/vic/nim-heroku-example) lives [here](http://nim-heroku-example.herokuapp.com)
