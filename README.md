grunt-atomify
=============

This fork supports multiple targets in your Gruntfile.

For example, you can have two different atomify configurations for release and debug builds.
In this example, we're minifying the release artifact, and leaving the debug artifact inflated, for readability.
This also shows that you can use grunt string replacement, which is a popular thing in yeoman generators.

```javascript

atomify: {
  dist: {
    js: {
      entry: '<%= yeoman.app %>/src/index.js',
      transforms: ['debowerify', 'uglifyify'],
      debug: false,
      output: '<%= yeoman.dist %>/js/main.js'
    }
  },
  debug: {
    js: {
      entry: 'app/src/index.js',
      transforms: ['debowerify'],
      debug: true,
      output: 'dist/js/main.js'
    }
  }
}

```

To run your dist build:
```
grunt atomify:dist
```

To run your debug build:
```
grunt atomify:debug
```

## Installation

This fork is not registered in npm, so you have to point to this github repo in your package.json, like this:

```javascript
"devDependencies": {
  "grunt-atomify": "massaroni/grunt-atomify"
}
```
