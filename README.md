spm-agent-nodejs
================
[![bitHound Score](https://www.bithound.io/github/sematext/spm-agent-nodejs/badges/score.svg)](https://www.bithound.io/github/sematext/spm-agent-nodejs/)
![build status](https://api.travis-ci.org/sematext/spm-agent-nodejs.svg)

![npm-stats](https://nodei.co/npm/spm-agent-nodejs.png?downloads=true&downloadRank=true)

[SPM performance monitoring by Sematext](http://sematext.com/spm/integrations/nodejs-spm-integration.html) - this is the Node.js monitoring agent for SPM.

Following information is collected and transmitted to SPM (Cloud or On-Premises version):

- OS Metrics (CPU / Mem)
- Process Memory
- EventLoop stats
- Garbage Collector stats
- Web server stats (requests, error rate, response times etc.)
  Working for all web servers frameworks that use Node.js http/https module including 
  - "connect" based frameworks
  - Express.js, 
  - Sails.js
  - Hapi.js
  - Restify
  - and others ...

The module is able to run in cluster mode (master/worker). 

# Status

Supported Node-Versions: Node >= 0.10, io.js >= 1.2

Please check our [blog](http://blog.sematext.com/2015/03/30/nodejs-iojs-monitoring/) for more information or
contact us [npmjs@sematext.com](mailto:npmjs@sematext.com).

# Installation

```

    npm install spm-agent-nodejs

```

Get a free account and create a Node.js API token at [www.sematext.com](https://apps.sematext.com/users-web/register.do)

# Configuration

We use https://www.npmjs.com/package/rc for configuration. This means config parameters can be passed via several config
locations commandline args or ENV variables. We recommend to use a file in current directory in INI or JSON format called ".spmagentrc".
This file can be generated by providing setting and environment variable and calling a helper script:

        export SPM_TOKEN=YOUR-SPM-TOKEN
        node ./node_modules/spm-agent-nodejs/bin/spmconfig.js

The command above generates following default configuration file:

        # Directory for buffered metrics
        dbDir = ./spmdb

        # Application Token for SPM
        [tokens]
          spm = YOUR-SPM-TOKEN

        [logger]
          # log file directory default is ./spmlogs
          dir = ./spmlogs
          # silent = true means no creation of log files
          silent = false
          # log level for output - debug, info, error, defaults to error to be quiet
          level = error


The only required setting is the SPM Application Token, this could be set via config file ".spmagentrc" or environment variable:

    export spmagent_tokens__spm=YOUR-SPM-APP-TOKEN

Please note the use of double "_" for nested properties


# Usage

Add this line at the begin of your source code / main script / app.js

```js
    var spmAgent = require ('spm-agent-nodejs')
```

There is an alternative using io.js (>1.6.4). It supports a command line option "-r" to preload node modules before the actual application is started. In this case the original source code needs no change:

```sh
  iojs -r './spm-agent-nodejs' yourApp.js
```

# Results

Screenshot taken from [announcement blog post](http://blog.sematext.com/2015/03/30/nodejs-iojs-monitoring/)

![SPM for Node.js screenshot](https://sematext.files.wordpress.com/2015/03/nodejs-overview-2.png?w=936)

# Troubleshooting

Please visit our [WIKI](https://sematext.atlassian.net/wiki/display/PUBSPM/SPM+for+Node.js) for more information

# Other SPM related packages

Please check out [spm-metrics-js](https://www.npmjs.com/package/spm-metrics-js) to monitor any custom metric in your application.

# LICENCE

      Copyright (c) Sematext Group, Inc.
      All Rights Reserved

      SPM for NodeJS is free-to-use, proprietary software.
      THIS IS PROPRIETARY SOURCE CODE OF Sematext Group, Inc. (Sematext)
      This source code may not be copied, reverse engineered, or altered for any purpose.
      This source code is to be used exclusively by users and customers of Sematext.
      Please see the full license (found in LICENSE in this distribution) for details on its license and the licenses of its dependencies.

