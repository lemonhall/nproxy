# nproxy

A cli proxy tool specialized in file replacing

## Installation

    npm install -g nproxy (node >= v0.8.x is required)

## Usage
    
    nproxy -l replace_rule.js 

### More Options:

    Usage: nproxy [options]

    Options:

      -h, --help         output usage information
      -V, --version      output the version number
      -l, --list [list]  Specify the replace rule file
      -p, --port [port]  Specify the port nproxy will listen on(8989 by default)

## Template of Replace Rule file(should be a .js file)

    module.exports = [

      // 1. replace single file
      {
        pattern: /homepage\.js/,      // Match url you wanna replace
        responder:  "file path"
      },

      // 2. replace combo file with src with absolute file path
      {
        pattern: /group\/homepageTileFramework.*\.js/,
        responder: [
          '/home/goddyzhao/workspace/webapp/ui/homepage/js/a.js',
          '/home/goddyzhao/workspace/webapp/ui/homepage/js/b.js',
          '/home/goddyzhao/workspace/webapp/ui/homepage/js/c.js'
        ] 
      },

      // 3. replace combo file with src with relative file path and specified dir
      {
        pattern: /group\/homepageTileFramework.*\.js/,
        responder: {
          dir: '/home/goddyzhao/workspace/webapp/ui/homepage/js',
          src: [
            'a.js',
            'b.js',
            'c.js'
          ]
        }
      }
    ];

