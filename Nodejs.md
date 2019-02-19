There are **no** conventions for the directory/file structure. However most (professional) express applications use a setup like:

    /
      /bin - scripts, helpers, binaries
      /lib - your application
      /config - your configuration
      /public - your public files
      /test - your tests

An example which uses this setup is [nodejs-starter](https://github.com/gravityonmars/nodejs-starter).


I personally changed this setup to:

    /
      /etc - contains configuration
      /app - front-end javascript files
        /config - loads config
        /models - loads models
      /bin - helper scripts
      /lib - back-end express files
        /config - loads config to app.settings
        /models - loads mongoose models
        /routes - sets up app.get('..')...
      /srv - contains public files
      /usr - contains templates
      /test - contains test files

In my opinion this matches better the unix-style directory structure (whereas the above mixes this up a bit).

I also like this pattern to separate files:

**lib/index.js**

    var http = require('http');
    var express = require('express');
    
    var app = express();
    
    app.server = http.createServer(app);
    
    require('./config')(app);
    
    require('./models')(app);
    
    require('./routes')(app);
    
    app.server.listen(app.settings.port);
    
    module.exports = app;

**lib/static/index.js**

    var express = require('express');
    
    module.exports = function(app) {
    
      app.use(express.static(app.settings.static.path));
    
    };

This allows decoupling neatly all source code with out having to bother dependencies. A real good solution for fighting nasty javascript. A real world example is [nearby](https://github.com/bodokaiser/nearby) which uses this setup.

**Update (filenames):**

Regarding filenames most common are *short*, *lower-case* filenames. If your file can only be described with two words most JavaScript projects use an underscore as delimiter.

**Update (variables):**

Regarding variables same "rules" apply as for filenames. Prototypes or classes however should use *camel-case*.

**Update (styleguides):**

- https://github.com/feross/standard
- https://github.com/airbnb/javascript
