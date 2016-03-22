# grunt-stamplay

> Deploy your project as a grunt module

## Getting Started
This plugin requires Grunt `~0.4.5`

If you haven't used [Grunt](http://gruntjs.com/) before, be sure to check out the [Getting Started](http://gruntjs.com/getting-started) guide, as it explains how to create a [Gruntfile](http://gruntjs.com/sample-gruntfile) as well as install and use Grunt plugins. Once you're familiar with that process, you may install this plugin with this command:

```shell
npm install grunt-stamplay --save-dev
```

Once the plugin has been installed, it may be enabled inside your Gruntfile with this line of JavaScript:

```js
grunt.loadNpmTasks('grunt-stamplay');
```

## The "stamplay" task

### Overview
In your project's Gruntfile, add a section named `stamplay` to the data object passed into `grunt.initConfig()`.

```js
grunt.initConfig({
  stamplay: {
    options: {
      appId: 'YOUR-APPID',
      apiKey: 'YOUR-APIKEY',
      public: './'
    },
    deploy: {
      message: 'deploy message',    // message to describe the deploy
      ignore: [                     // files that mustn't be uploaded with the deploy
        '**/.*',
        '**/node_modules/**'
      ]
    }
  },
});
```

### Options

#### options.appId
Type: `String`

The appId of the project on Stamplay

#### options.apiKey
Type: `String`

The apiKey of the project on Stamplay

#### options.public
Type: `String`

The public property tells the task which directory to upload to Stamplay. This directory must be inside the project directory and must exist. The default value is the root directory or your project.

#### Custom Options
In this example, headers property is used to specify to the Stamplay platform that all files with `.html` extetions can be cached from the client. You can find more informations about options [here](https://stamplay.com/docs/hosting/command-line)

```js
grunt.initConfig({
  stamplay: {
    options: {
      appId: 'YOUR-APPID',
      apiKey: 'YOUR-APIKEY',
      public: './'
    },
    deploy: {
      message: 'deploy message',
      ignore: [
        '**/.*',
        '**/node_modules/**'
      ],
      headers: [{
        source: '**/*.@(html)',
        headers: [{
          key: 'Cache-Control',
          value: 'max-age=7200'
        }]
      }]
    }
  },
});
```

## Release History
#### v1.0.0 - (21-03-2016)
    - Stamplay deploy task

