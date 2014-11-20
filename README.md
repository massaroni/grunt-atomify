grunt-atomify
=============

This fork supports multiple targets in your Gruntfile.

For example, you can have two different atomify configurations for release and debug builds.
In this example, we're minifying the release artifact, and leaving the debug artifact inflated, and we're starting a
livereload server in debug mode, for interactive development.
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
    },
    server: {
      port: 9000,
      hostname: 'localhost',
      url: 'http://localhost:9000/yeoman/app/src/index.html',
      open: true,
      lr: {
        sync: true,
        port: 35729,
        verbose: true,
        // can't use grunt string replacement in these patterns
        patterns: [ 'yeoman/app/src/**/*.js' ]
      }
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
