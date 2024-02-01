# heroku-buildpack-npmrc-yarn
A Heroku buildpack for overriding the .npmrc file in the build directory with the contents of a config var. Useful for authorizing with npm when installing private packages.

## Configure Multiple Buildpacks
### _Option 1:_ Heroku CLI or Dashboard
Add the buildpack to your Heroku app either using the CLI or the Heroku dashboard. The `heroku-buildpack-npmrc-yarn` needs to run before any buildpack using npm. In the following example, it runs before the `heroku/nodejs` buildpack.
```bash
$ heroku buildpacks:set --index 1 https://github.com/debitoor/heroku-buildpack-npmrc-yarn.git
$ heroku buildpacks:add heroku/nodejs
```


The same example given for the CLI use would have the following `.buildpacks` file.

``` bash
$ cat .buildpacks
https://github.com/debitoor/heroku-buildpack-npmrc-yarn.git
https://github.com/heroku/heroku-buildpack-nodejs.git
```

## Configure Config Var
Add the NPMRC config var in Heroku with the contents of your .npmrc file.

``` bash
 $ heroku config:set GITHUB_TOKEN=<token>
 $ heroku config:set REPO_USER=<token>
```
