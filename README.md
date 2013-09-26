# grunt-wp-assets v0.1.3 [![Build Status](https://travis-ci.org/hariadi/grunt-wp-assets.png?branch=master)](https://travis-ci.org/hariadi/grunt-wp-assets)

> WordPress assets revisioning.

## Overview

Grunt.js plugin that searches requested WordPress static asset, revisioning, and update static asset reference in given target (tested in `wp_enqueue_style` and `wp_register_script`).


### Getting Started
This plugin requires Grunt `~0.4.1`

Install this plugin with this command:

```shell
npm install grunt-wp-assets --save-dev
```

Once the plugin has been installed, it may be enabled inside your Gruntfile with this line of JavaScript:

```js
grunt.loadNpmTasks('grunt-wp-assets');
```


## Usage Examples

### defaut config


```javascript
wprev: {
  assets: {
    src: ['path/to/style.css',
          'path/to/scripts.js',],
    dest: 'path/to/target.php'
  }
},

```

This example task will copy `path/to/style.css` to `assets/css/{md5hash}.style.css` and `path/to/scripts.js` to `path/to/{md5hash}.scripts.js` and update assets referecnce in `path/to/target.php`.

### Custom config


```javascript
wprev: {
  assets: {
  options: {
      algorithm: 'sha1',
      length: 4,
      format: false,
      rename: true
  },
    src: ['assets/css/main.min.css',
          'assets/js/scripts.min.js',],
    dest: 'scripts.php'
  }
},

```

This example task will rename `assets/css/main.min.css` to `assets/css/main.min.{sha1hash}.css` and `assets/js/scripts.min.js` to `assets/js/scripts.min.{sha1hash}.js` and update assets referecnce in `scripts.php`.


## Options

### rename

Type: `Boolean`
Default: `false`

It will rename the `src` target instead of copy.

### format

Type: `Boolean`
Default: `true`

File name format.
```
true: {hash}.{filename}.{ext}
false: {filename}.{hash}.{ext}
```

### encoding

Type: `String`
Default: `'utf8'`

The file encoding.

### algorithm

Type: `String`
Default: `'md5'`

`algorithm` is dependent on the available algorithms supported by the version of OpenSSL on the platform. Examples are `'sha1'`, `'md5'`, `'sha256'`, `'sha512'`, etc. On recent releases, `openssl list-message-digest-algorithms` will display the available digest algorithms.

### length

Type: `Number`
Default: `4`

The number of characters of the file hash to prefix the file name with.





## Release History

 * 2013-09-07   v0.1.3   Rename source target, not destination. Change default characters length of hash file prefix to 4.
 * 2013-09-05   v0.1.2   Refactored docs
 * 2013-09-04   v0.1.0   Initial commit.
 

## Author

+ [Hariadi Hinta](https://github.com/hariadi)

## License
Copyright (c) 2013 Hariadi Hinta
Released under the MIT license


***

_This file was generated on Thu Sep 26 2013 18:43:22._
