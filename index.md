![original](./bower-logo.png)

---

## DISCLAIMER

<br/>

1. The problems I want to solve might not be the problems you want to solve.
1. I have tools at my disposal that you might not (e.g. Github Enterprise).
1. I haven't had a chance to look at [jspm](http://jspm.io/).

---

![inline](bower-is-a-cancer.png)

---

![fit](build-error.png)

---

## That's the point!

---

## Nested vs. Flat

![inline](./flat-vs-nested-deps.png)

<sub>Image by Max Ogden from [Nested Dependencies](http://maxogden.com/nested-dependencies.html)</sub>

---

## Lots of little modules

In the style of [substack: how I write modules](http://substack.net/how_I_write_modules), _but_ for the browser.

<br/>
<br/>

Who is doing this?

---

![fit](http://blog.cubettech.com/wp-content/uploads/2014/11/Capture.png)

---

![inline](./question.png)

---

![inline](./rob-dodson.png)

---

![inline](./addy-osmani.png)

---

## The Problem With npm

*According to npm.*

[npm and front-end packaging](http://blog.npmjs.org/post/101775448305/npm-and-front-end-packaging):

<br/>

1. `node_modules` isn’t arranged the way front-end packages need it to be
1. Front-end dependencies have different conflict-resolution needs

---

## The Other Problem With npm

<br/>

[https://github.com/npm/npm/issues/3328](https://github.com/npm/npm/issues/3328)

<br/>
<br/>

TL;DR: If you want to use version ranges for npm packages
you _need_ to put them in a registry.

---

## [`bower install`](http://bower.io/docs/api/#install)

* `jquery` (registered package)
* `git@github.com:user/package.git` (or https/svn)
* `git+ssh://git@github.com/user/package` (or https/svn)
* `user/package` (shorthand) *
* `http://example.com/script.js`
* `http://example.com/package.zip` (or `.tar` e.g. CI build)

<sub>\* via Github or as per [`shorhand-resolver`](http://bower.io/docs/config/#shorthand-resolver)</sub>

---

## [Configuration](http://bower.io/docs/config/)

`.bowerrc`

```json
{
  "directory": "components",
  "shorthand-resolver": "git://example.com/{{shorthand}}.git",
  "tmp": "/.bower/tmp",
  "storage": {
    "packages": "/.bower/packages"
  },
  "scripts": {
    "postinstall": "grunt bower_postinstall"
  }
}
```

<sub>BTW `scripts` are for [Bower Hooks](https://github.com/bower/bower/blob/master/HOOKS.md) - `preinstall`, `postinstall`, `uninstall`</sub>

---

## Workflows

* `bower update`
* [`bower link`](https://oncletom.io/2013/live-development-bower-component/)
* ["shrinkwrap"](https://github.com/bower/bower/pull/1748) (soon?)
* `bower info <package>`
* `bower list`
* dist vs. source

---

## Bower @ Xero

* Package manager for front-end modules
* Including sass partials (e.g. shared variables)
* Recommendation on when to use Bower and when to use npm
* *Lots* of little modules

<br/>

Bower is better for us ATM.

---

## Live Demos

<br/>
<br/>
<br/>

This might go awfully wrong

---

## Registries

* [bower/registry](https://github.com/bower/registry)
* [private-bower](https://www.npmjs.com/package/private-bower)
* and others on npm
* [Artifactory Pro](http://www.jfrog.com/artifactory/features/#addon-bower)

---

### Bower and CI

Make sure you do this:

<br/>

```bash
  env.CI=true
```

<br/>
<br/>
<br/>

<sub>Travis and some other CI systems do this by default</sub>

---

## The Future

`package.json`

```json
  ...
  "dependencies": {
    ...
  },
  "devDependencies": {
    ...
  },
  "browserDependencies": {
    ...
  },
  ...
```

<sub>[npm ⇔ Angular brainstorming session](https://github.com/npm/npm/wiki/npm%E2%87%94Angular-brainstorming-session) / [npm ⇔ Polymer brainstorming session](https://github.com/npm/npm/wiki/npm-%E2%87%94-Polymer-brainstorming-session)</sub>

---

![](https://www.youtube.com/watch?v=HO1dqfQsAuY)
