# Angular.js EE Snippets for Sublime Text 2/3

<!-- toc -->

* [Overview](#overview)
* [How to install](#how-to-install)
* [Snippets](#snippets)
  * [Require.js](#requirejs)
    * [Require.js: [config]](#requirejs-config)
    * [Require.js: [require]](#requirejs-require)
    * [Require.js: [define]](#requirejs-define)
    * [Require.js: [load]](#requirejs-load)
  * [Angular.js EE (Enterprise Edition)](#angularjs-ee-enterprise-edition)
    * [Angular.js EE: [bootstrap]](#angularjs-ee-bootstrap)
    * [Angular.js EE: [package]](#angularjs-ee-package)
    * [Angular.js EE: [module]](#angularjs-ee-module)
    * [Angular.js EE: [module-use]](#angularjs-ee-module-use)
    * [Angular.js EE: [mock-package]](#angularjs-ee-mock-package)
    * [Angular.js EE: [mock-pass-urls]](#angularjs-ee-mock-pass-urls)
    * [Angular.js EE: [mock-pass-backend]](#angularjs-ee-mock-pass-backend)
    * [Angular.js EE: [mock-data]](#angularjs-ee-mock-data)
    * [Angular.js EE: [mock-backend]](#angularjs-ee-mock-backend)
    * [Angular.js EE: [mock-urls]](#angularjs-ee-mock-urls)
  * [Angular.js](#angularjs)
    * [Angular.js: [angular]](#angularjs-angular)
    * [Angular.js: [config]](#angularjs-config)
    * [Angular.js: [constant]](#angularjs-constant)
    * [Angular.js: [controller]](#angularjs-controller)
    * [Angular.js: [decorator]](#angularjs-decorator)
    * [Angular.js: [directive]](#angularjs-directive)
    * [Angular.js: [directiveLong]](#angularjs-directivelong)
    * [Angular.js: [factory]](#angularjs-factory)
    * [Angular.js: [filter]](#angularjs-filter)
    * [Angular.js: [module]](#angularjs-module)
    * [Angular.js: [provider]](#angularjs-provider)
    * [Angular.js: [resource-id]](#angularjs-resource-id)
    * [Angular.js: [resource]](#angularjs-resource)
    * [Angular.js: [routeProvider]](#angularjs-routeprovider)
    * [Angular.js: [when]](#angularjs-when)
    * [Angular.js: [otherwise]](#angularjs-otherwise)
    * [Angular.js: [run]](#angularjs-run)
    * [Angular.js: [service]](#angularjs-service)
    * [Angular.js: [value]](#angularjs-value)
    * [Globals](#globals)
    * [jQuery lite](#jquery-lite)
    * [Scope functions](#scope-functions)
    * [Log functions](#log-functions)
    * [Variables](#variables)
    * [Directives (on HTML)](#directives-on-html)
* [Contributing](#contributing)
* [LICENSE](#license)

<!-- toc stop -->


## Overview

* Sublime Text 2 / 3 Snippets and Completions for [Angular.js](http://angularjs.org/), [[GitHub] erkobridee / angularjs-ee-boilerplate](https://github.com/erkobridee/angularjs-ee-boilerplate) v [0.6.0](https://github.com/erkobridee/angularjs-ee-boilerplate/tree/0.6.0) and [Require.js](http://requirejs.org/)

* Based on: [[GitHub] maxhoffmann / angular-snippets](https://github.com/maxhoffmann/angular-snippets)

--

* This snippet library provides completions for Angular.js and Require.js (focused to the **angularjs-ee-boilerplate** code).

* Sublime Text uses fuzzy searching for snippets and completions therefore you don’t have to write triggers completely.

* All snippets add Angular’s inline notation for dependencies automatically, so you don’t have to type them twice.



## How to install

Manually:

1 - Clone or [download](https://github.com/the-front/sublime-angularjs-ee-snippets/archive/master.zip) git repo into your packages folder (in ST, find Browse Packages... menu item to open this folder)

```sh
$ git clone https://github.com/the-front/sublime-angularjs-ee-snippets.git
```

2 - Restart ST editor (if required)


## Snippets

Below is a list of all triggers and respectives snippets currently supported on this package.

> **trigger:** [*triggerName*] `TAB` key.


### Require.js

#### Require.js: [config]

**Description:** 

<pre>config                  Require.js</pre>

**Content:**

```javascript
require({

  // libraries dependencies (fallback support)
  paths: {

    ${1:lib}: [
      '${2:lib-path}'
    ]$0

  },

  // define js scripts dependencies
  shim: {

    '${1}': {
      ${3:deps: [],}
      ${4:exports: ''}
    }

  },

  priority: [
    '$5'
  ],

  deps: ['./$6']

});
```

#### Require.js: [require]

**Description:** 

<pre>require                  Require.js</pre>

**Content:**

```javascript
require('${1:path/file_js}');$0
```

#### Require.js: [define]

**Description:** 

<pre>define                  Require.js</pre>

**Content:**

```javascript
define(function(require) {
  'use strict';

  $1

  ${2:return ${0:object_or_function};}

});
```

#### Require.js: [load]

**Description:** 

<pre>load                  Require.js</pre>

**Content:**

```javascript
define(function(require) {
  'use strict';

  $0

});
```


### Angular.js EE (Enterprise Edition)

#### Angular.js EE: [bootstrap]

**Description:** 

<pre>bootstrap                  Angular.js EE</pre>

**Content:**

```javascript
define(function(require) {
  'use strict';

  var angular = require('angular');

  angular.element(document).ready(startAngularApp);

  //---

  function startAngularApp() {
${1:
    console.log('start angular application');
}
    // define angular module to bootstrap application
    var module = angular.module(
      // module name
      '${4:run}',

      // module dependencies
      [
${2:        // enable mock and intercep $HTTP requests
        require('./require.mock.load').name,

}${3:        require('app/main/package').name}
      ]
    );

    // start angular app
    angular.bootstrap(document, [module.name]);

  }$0

});
```

#### Angular.js EE: [package]

**Description:** 

<pre>package                  Angular.js EE</pre>

**Content:**

```javascript
define(function(require) {
  'use strict';

  var module = require('./module');
${1:  require('./resource');}
  require('./controller');
  require('./routes');$2

  return module;$0

});
```

#### Angular.js EE: [module]

**Description:** 

<pre>module                  Angular.js EE</pre>

**Content:**

```javascript
define(function(require) {
  'use strict';

  var angular = require('angular');
${2:  require('angularResource');
}
${4:  require('uiRouter');}
${6:  require('uiBootstrap');}

  // angular module definition
  return angular.module(
    // module name
    '${1:moduleName}',
  
    // module dependencies
    [
${3:      'ngResource',
}
${5:      'ui.router',}
${7:      'ui.bootstrap',
}
${8:      require('shared/fend/input-utils/package').name,
      require('shared/fend/pagination/package').name}
    ]
  );

});
```

#### Angular.js EE: [module-use]

**Description:** 

<pre>module-use                  Angular.js EE</pre>

**Content:**

```javascript
define(function(require) {
  'use strict';

  var module = require('$1./module');

  $0

});
```

#### Angular.js EE: [mock-package]

**Description:** 

<pre>mock-package                  Angular.js EE</pre>

**Content:**

```javascript
define(function(require) {
  'use strict';

  // allow request pass through angular.js mock url interceptor
  //$1 require('./allow-pass');

  /**/$2
  require('./data'); // local mock data
  require('./url-interceptors'); // intercepts and responds
  /*$3*/

});
```

#### Angular.js EE: [mock-pass-urls]

**Description:** 

<pre>mock-pass-urls                  Angular.js EE</pre>

**Content:**

```javascript
define(function(require) {
  'use strict';

  var backend = require('shared/mock/backend');

  backend.addResource(AllowPass);

  //---

  // mock resource dependencies injection
  AllowPass.\$inject = [${1/(?:.+)/'/g}${1/,[ ]*/', '/g}${1/(?:.+)/', /g}$5];

  // mock resource definition
  function AllowPass(${1:\$httpBackend, regexpUrl}) {

${2:    // Allow GET users from GitHub API}
    ${4:\$httpBackend
      .when('GET', regexpUrl(/${3:api\.github\.com\/users}(\/)?([A-z0-9]+)?\$/))
      .passThrough();}$0

  }

});
```

#### Angular.js EE: [mock-pass-backend]

**Description:** 

<pre>mock-pass-backend                  Angular.js EE</pre>

**Content:**

```javascript
define(function(require) {
  'use strict';

  var backend = require('shared/mock/backend');

  backend.addResource(AllowPass);

  //---

  AllowPass.\$inject = [${1/(?:.+)/'/g}${1/,[ ]*/', '/g}${1/(?:.+)/', /g}$6];

  function AllowPass(${1:\$httpBackend, regexpUrl}) {

    //--- @begin: Allow pass to server

    // get all
    \$httpBackend
      .when('GET', regexpUrl(/${2:rest}\/${3:resource}(\?|\$)/))
      .passThrough();

    // get one
    \$httpBackend
      .when('GET', regexpUrl(/$2\/$3(\/)?([A-z0-9]+)?\$/))
      .passThrough();

    // create
    \$httpBackend
      .when('POST', regexpUrl(/$2\/$3\$/))
      .passThrough();

    // update
    \$httpBackend
      .when('PUT', regexpUrl(/$2\/$3(\/)?([A-z0-9]+)?\$/))
      .passThrough();

    // delete
    \$httpBackend
      .when('DELETE', regexpUrl(/$2\/$3(\/)?([A-z0-9]+)?\$/))
      .passThrough();

${5:    // search
    \$httpBackend
      .when('GET', regexpUrl(/$2\/$3\/${4:search}\/([A-z0-9]+)(\?|\$)/))
      .passThrough();}

    //--- @end: Allow pass to server

  }

});
```

#### Angular.js EE: [mock-data]

> Use [LokiJS](http://lokijs.org/) to manage object collection

**Description:** 

<pre>mock-data                  Angular.js EE</pre>

**Content:**

```javascript
define(function(require) {
  'use strict';

  var module = require('shared/mock/module');

  module.factory('${1:Name}Collection', $1CollectionFactory);

  //---

  $1CollectionFactory.\$inject = ['DataStore', 'Helpers', '\$log'];

  function $1CollectionFactory(DataStore, helpers, console) {

    console.debug('$1Collection');

    /*
      options = {
        name: '',
        objType: '',
        hasOwnId: false, // save and use this 'id 'as '_id' inside collection?
        indicesArray: ['id'],
        fn: {
          searchValue: function(data, find) {},
          init: function( collection ) {}
        }
      }
    */
    var collection = DataStore.create({
      name: '${1/([A-Za-z0-9]+)?/(?2::\l$1)/g}',
      objType: '${3:$1$2}',
      //hasOwnId: true,
      indicesArray: ['id', 'name'$4],
      fn: {
        searchValue: function(data, find) {

          if(!find) return [];

          var r = [], obj,
              regexp = new RegExp(find, 'i'),
              len = data.length;

          for (var i = 0; i < len; i++) {
            obj = data[i];

            if(obj.name.match(regexp) || obj.description.match(regexp))
              r.push(obj);
          }

          return r;

        },

        init: function( collection ) {

          console.debug( 'init $1Collection' );

          var seq = 0;

${5:          // manual fake data definition}
          ${6:collection.insert({
            id          : seq,
            name        : 'manual fake $3 name ' + (seq+1),
            description : 'manual some fake $3 descrition ' + (seq+1)
          \});
          seq++;
          }$0

          for (var i = 42; i > 0; i--) {
            collection.insert({
              id          : seq,
              name        : 'fake $3 name ' + (seq+1),
              description : 'some fake $3 descrition ' + (seq+1)
            });
            seq++;
          }


        }
      }
    });


    function $1Collection() {}
    var ClassDef = helpers.extendsFn( $1Collection, collection );

    ClassDef.prototype.sayMyName = function() {
      return 'Angular.js : $1Collection Mock';
    };

    var instance = new $1Collection();

    console.debug( instance.sayMyName() );
    console.debug( instance );
    console.debug( instance.list() );

    return instance;

  }

});
```

#### Angular.js EE: [mock-backend]

> Complete CRUD + Search

**Description:** 

<pre>mock-backend                  Angular.js EE</pre>

**Content:**

```javascript
define(function(require) {
  'use strict';

  var angular = require('angular');
  var backend = require('shared/mock/backend');
  require('./data$1');

  backend.addResource(UrlInterceptors);

  //---

  UrlInterceptors.$inject = [
    '${2:Name}Collection', 'Helpers',
    '\$httpBackend', 'regexpUrl', 'getParams',
    '\$log',$3
  ];

  function UrlInterceptors(
    collection, helpers, \$httpBackend,
    regexpUrl, getParams, console$4
  ) {

    //--- @begin: URL interceptor$0

    // get all
    \$httpBackend.when('GET', regexpUrl(/${5:rest}\/${6:resource}(\?|\$)/))
      .respond(function(method, url, data) {

        console.debug('GET ' + url);

        var result,
            params = getParams(url),
            options = {page: 1, size: 10};

        if(params) {
          console.debug(params);
          options.page = params.page;
          options.size = params.size;
        }

        result = collection.list(options);

        return [200, angular.copy(result)];
      });

    // get one
    \$httpBackend.when('GET', regexpUrl(/$5\/$6(\/)?([A-z0-9]+)?\$/))
      .respond(function(method, url, data) {
        console.debug('GET ' + url);

        var result,
            regexp = /$5\//,
            id = helpers.getIdFromURL(url, regexp),
            object = collection.getById(id);

        if(object) {
          result = [200, angular.copy(object)];
        } else {
          result = [404, helpers.notFound(id)];
        }

        return result;
      });

    // create
    \$httpBackend.when('POST', regexpUrl(/$5\/$6\$/))
      .respond(function(method, url, data) {
        console.debug('POST ' + url);

        data = angular.fromJson(data);
        data = collection.insert(data);

        console.debug(data);

        return [201, angular.copy(data)];
      });

    // update
    \$httpBackend.when('PUT', regexpUrl(/$5\/$6(\/)?([A-z0-9]+)?\$/))
      .respond(function(method, url, data) {
        console.log('PUT ' + url);

        data = angular.fromJson(data);

        collection.update(data);

        console.debug(data);

        return [202, angular.copy(data)];
      });

    // delete
    \$httpBackend.when('DELETE', regexpUrl(/$5\/$6(\/)?([A-z0-9]+)?\$/))
      .respond(function(method, url, data) {
        console.debug('DELETE ' + url);

        var result,
            bookmark,
            regexp = /$5\//,
            id = helpers.getIdFromURL(url, regexp),
            object = collection.getById(id);

        if(object) {
          collection.remove(object);
          result = [202, helpers.createResultMessage(202, '$2 id: ' + id + ' removed')];
        } else {
          result = [404, helpers.notFound(id)];
        }

        return result;

      });

${8:    // search
    \$httpBackend.when('GET', regexpUrl(/$5\/$6\/${7:search}\/([A-z0-9]+)(\?|\$)/))
      .respond(function(method, url, data) {
        console.debug('GET ' + url);

        var result,
            regexp = /$6\/$7\//,
            find = helpers.getValueFromURL(url, regexp),
            params = getParams(url),
            options = {page: 1, size: 10\};

        if(params) {
          console.debug(params);
          options.page = params.page;
          options.size = params.size;
        \}

        console.debug(find);

        result = collection.search(find, options);

        return [200, angular.copy(result)];
      \});
}
    //--- @end: URL interceptor

${9:    console.debug('$2 Mock URL Interceptors');
    console.debug(collection.getById(1));
    console.debug(collection.list());
}
  }

});
```

#### Angular.js EE: [mock-urls]

**Description:** 

<pre>mock-urls                  Angular.js EE</pre>

**Content:**

```javascript
define(function(require) {
  'use strict';

  var angular = require('angular');
  var backend = require('shared/mock/backend');${2:
  require('./data$1');}

  backend.addResource(UrlInterceptors);

  //---

  UrlInterceptors.$inject = [
    'Helpers', '\$httpBackend', 'regexpUrl', 
    'getParams', '\$log',$3
  ];

  function UrlInterceptors(
    helpers, \$httpBackend, regexpUrl, 
    getParams, console$4
  ) {

    //--- @begin: URL interceptor

    $0

    //--- @end: URL interceptor

  }

});
```

##### Angular.js EE: [mock-w-all]

> HTTP GET - all

**Description:** 

<pre>mock-w-all                  Angular.js EE</pre>

**Content:**

```javascript
// get all
${1:\$httpBackend}.when('GET', regexpUrl(/${2:rest}\/${3:resource}(\?|\$)/))
  .respond(function(method, url, data) {

    console.debug('GET ' + url);

    var result,
        params = getParams(url)${4:,
        options = {page: 1, size: 10\};

    if(params) {
      console.debug(params);
      options.page = params.page;
      options.size = params.size;
    \}}$0

    result = ${5:collection.list(options);}

    return [200, angular.copy(result)];
  });
```

##### Angular.js EE: [mock-w-one]

> HTTP GET - one (by id)

**Description:** 

<pre>mock-w-one                  Angular.js EE</pre>

**Content:**

```javascript
// get one
${1:\$httpBackend}.when('GET', regexpUrl(/${2:rest}\/${3:resource}(\/)?([A-z0-9]+)?\$/))
  .respond(function(method, url, data) {
    console.debug('GET ' + url);

    var result,
        regexp = /$2\//,
        id = helpers.getIdFromURL(url, regexp),
        object = ${4:collection.getById(id);}$0

    if(object) {
      result = [200, angular.copy(object)];
    } else {
      result = [404, helpers.notFound(id)];
    }

    return result;
  });
```

##### Angular.js EE: [mock-w-post]

> HTTP POST - create

**Description:** 

<pre>mock-w-post                  Angular.js EE</pre>

**Content:**

```javascript
// create
${1:\$httpBackend}.when('POST', regexpUrl(/${2:rest}\/${3:resource}\$/))
  .respond(function(method, url, data) {
    console.debug('POST ' + url);

    data = angular.fromJson(data);
    data = ${4:collection.insert(data);}$0

    console.debug(data);

    return [201, angular.copy(data)];
  });
```

##### Angular.js EE: [mock-w-put]

> HTTP PUT - update

**Description:** 

<pre>mock-w-put                  Angular.js EE</pre>

**Content:**

```javascript
// update
${1:\$httpBackend}.when('PUT', regexpUrl(/${2:rest}\/${3:resource}(\/)?([A-z0-9]+)?\$/))
  .respond(function(method, url, data) {
    console.log('PUT ' + url);

    data = angular.fromJson(data);

    ${4:collection.update(data);}$0

    console.debug(data);

    return [202, angular.copy(data)];
  });
```

##### Angular.js EE: [mock-w-delete]

> HTTP DELETE

**Description:** 

<pre>mock-w-delete                  Angular.js EE</pre>

**Content:**

```javascript
// delete
${1:\$httpBackend}.when('DELETE', regexpUrl(/${2:rest}\/${3:resource}(\/)?([A-z0-9]+)?\$/))
  .respond(function(method, url, data) {
    console.debug('DELETE ' + url);

    var result,
        regexp = /$2\//,
        id = helpers.getIdFromURL(url, regexp),
        object = ${5:collection.getById(id);}$0

    if(object) {
      ${6:collection.remove(object);}
      result = [202, helpers.createResultMessage(202, '$3$4 id: ' + id + ' removed')];
    } else {
      result = [404, helpers.notFound(id)];
    }

    return result;

  });
```

##### Angular.js EE: [mock-w-search]

> HTTP GET - search collection by value

**Description:** 

<pre>mock-w-search                  Angular.js EE</pre>

**Content:**

```javascript
// search
${1:\$httpBackend}.when('GET', regexpUrl(/${2:rest}\/${3:resource}\/${4:search}\/([A-z0-9]+)(\?|\$)/))
  .respond(function(method, url, data) {
    console.debug('GET ' + url);

    var result,
        regexp = /$3\/$4\//,
        find = helpers.getValueFromURL(url, regexp),
        params = getParams(url)${6:,
        options = {page: 1, size: 10\};

    if(params) {
      console.debug(params);
      options.page = params.page;
      options.size = params.size;
    \}}$0

    console.debug(find);

    result = ${5:collection.search(find, options);}

    return [200, angular.copy(result)];
  \});
```


### Angular.js

#### Angular.js: [angular]

**Description:** 

<pre>angular                  Angular.js</pre>

**Content:**

```javascript
angular
```

#### Angular.js: [config]

**Description:** 

<pre>config                  Angular.js</pre>

**Content:**

```javascript
config(${3:configure});

//---

$3.\$inject = [${1/(?:.+)/'/g}${1/,[ ]*/', '/g}${1/(?:.+)/',/g} ${2}];

function $3($1) {

  ${0:// TODO: define code}

}
```

#### Angular.js: [constant]

**Description:** 

<pre>constant                  Angular.js</pre>

**Content:**

```javascript
constant('${1:name}', ${2:value});
```

#### Angular.js: [controller]

**Description:** 

<pre>controller                  Angular.js</pre>

**Content:**

```javascript
controller(
  // controller name
  '${1:Name}Ctrl',

  // dependencies injection
  [
    ${2/(?:.+)/'/g}${2/,[ ]*/', '/g}${2/(?:.+)/', /g}

// controller definition
function (${2:\$scope}) {

  $0

}]);
```

#### Angular.js: [decorator]

**Description:** 

<pre>decorator                  Angular.js</pre>

**Content:**

```javascript
decorator('${1:name}', [${2/(?:.+)/'/g}${2/,[ ]*/', '/g}${2/(?:.+)/', /g}function (${2:\$provide}) {
  \$provide.decorator('${3:name}', [${4/(?:.+)/'/g}${4/,[ ]*/', '/g}${4/(?:.+)/', /g}function(${4:\$delegate}) {
    return ${5:\$delegate}$0;
  }]);
}]);
```

#### Angular.js: [directive]

**Description:** 

<pre>directive                  Angular.js</pre>

**Content:**

```javascript
directive(
  // component name
  '${1:name}',

  // dependencies injection
  [
    ${2/(?:.+)/'/g}${2/,[ ]*/', '/g}${2/(?:.+)/', /g}

// component definition
function ($2) {
  return {
    restrict: '${3:A}',
    link: function (scope, iElement, iAttrs) {

      $0

    }
  };
}]);
```

#### Angular.js: [directiveLong]

**Description:** 

<pre>directiveLong                  Angular.js</pre>

**Content:**

```javascript
directive(
  // component name
  '${1:name}',

  // dependencies injection
  [
    ${2/(?:.+)/'/g}${2/,[ ]*/', '/g}${2/(?:.+)/', /g}

// component definition
function ($2) {
  return {$0
${3:    priority: 0,}
${4:    template: '<div></div>',}
${6:    templateUrl: '${5:directive}.html',}
${7:    replace: true,}
${8:    transclude: true,}
${10:    restrict: 'A$9',}
${12:    scope: \{$11\},}
${14:    controller: [
      // dependencies injection
      ${13/(?:.+)/'/g}${13/,[ ]*/', '/g}${13/(?:.+)/', /g}

    // controller definition
    function(${13:\$scope, \$element, \$attrs, \$transclude}) \{

    \}],}
${15:    compile: function compile(tElement, tAttrs, transclude) \{
      return function postLink(scope, iElement, iAttrs, controller) \{

      \}
    \},}
${16:    link: function postLink(scope, iElement, iAttrs) \{

    \}}
  };
}]);
```

#### Angular.js: [factory]

**Description:** 

<pre>factory                  Angular.js</pre>

**Content:**

```javascript
factory(
  // factory name
  '${1:name}',

  // dependencies injection
  [
    ${2/(?:.+)/'/g}${2/,[ ]*/', '/g}${2/(?:.+)/', /g}

// factory definition
function ($2) {

  $0

  return {
    $3
  };
}]);
```

#### Angular.js: [filter]

**Description:** 

<pre>filter                  Angular.js</pre>

**Content:**

```javascript
filter(
  // filter name
  '${1:name}',

// filter definition
function() {

  return function(input, ${2:configValue}) {
    input = input || '';
    var out = '';

    ${0://TODO: define filter process code}

    return out;
  };

});
```

#### Angular.js: [module]

**Description:** 

<pre>module                  Angular.js</pre>

**Content:**

```javascript
module(
  // module name
  '${1:moduleName}',

  // module dependencies
  [
    // 'dependencyModuleName',
    $2
  ]
);
```

#### Angular.js: [provider]

**Description:** 

<pre>provider                  Angular.js</pre>

**Content:**

```javascript
provider(
  // provider name
  '${1:name}',

  // dependencies injection
  [
    ${2/(?:.+)/'/g}${2/,[ ]*/', '/g}${2/(?:.+)/', /g}

// provider definition
function ($2) {
  $0

  this.\$get = [${3/(?:.+)/'/g}${3/,[ ]*/', '/g}${3/(?:.+)/', /g}function($3) {
    return {

    };
  }];
}]);
```

#### Angular.js: [resource-id]

**Description:** 

<pre>resource-id                  Angular.js</pre>

**Content:**

```javascript
factory(
  // resource name
  '${1:Name}Resource',

  // dependencies injection
  [
    ${2/(?:.+)/'/g}${2/,[ ]*/', '/g}${2/(?:.+)/', /g}

// resource definition
function (${2:\$resource}) {

  return \$resource(
    '${3:url}/:id',
    {
      'id': ''$0
    },
    {
      'update': { 'method': 'PUT' }
    }
  );

}]);
```

#### Angular.js: [resource]

**Description:** 

<pre>resource                  Angular.js</pre>

**Content:**

```javascript
factory(
  // resource name
  '${1:Name}Resource',

  // dependencies injection
  [
    ${2/(?:.+)/'/g}${2/,[ ]*/', '/g}${2/(?:.+)/', /g}

// resource definition
function (${2:\$resource}) {

  return \$resource(
    '${3:url}'
  );

}]);
```

#### Angular.js: [routeProvider]

**Description:** 

<pre>routeProvider                  Angular.js</pre>

**Content:**

```javascript
config(

  // dependencies injection
  ['\$routeProvider',

// routes definition
function (\$routeProvider) {

  \$routeProvider
    .when(
      '/${1:route}',
      {
        controller: '${2:ControllerName}Ctrl',
        templateUrl: '${3:app}/${4:module}/${5:template}.html'
      }
    )$0;

}]);
```

#### Angular.js: [when]

**Description:** 

<pre>when                  Angular.js</pre>

**Content:**

```javascript
when(
  '/${1:route}',
  {
    controller: '${2:ControllerName}Ctrl',
    templateUrl: '${3:app}/${4:module}/${5:template}.html'
  }
)$0
```

#### Angular.js: [otherwise]

**Description:** 

<pre>otherwise                  Angular.js</pre>

**Content:**

```javascript
otherwise(${1:{ redirectTo: '/${2:route}' \}})
```

#### Angular.js: [run]

**Description:** 

<pre>run                  Angular.js</pre>

**Content:**

```javascript
run([${1/(?:.+)/'/g}${1/,[ ]*/', '/g}${1/(?:.+)/', /g}function ($1) {

  $0

}]);
```

#### Angular.js: [service]

**Description:** 

<pre>service                  Angular.js</pre>

**Content:**

```javascript
service(
  // service name
  '${1:name}',

  // dependencies injection
  [
    ${2/(?:.+)/'/g}${2/,[ ]*/', '/g}${2/(?:.+)/', /g}

// service definition
function ($2) {

  $0

}]);
```

#### Angular.js: [value]

**Description:** 

<pre>value                  Angular.js</pre>

**Content:**

```javascript
value('${1:name}', ${2:value});
```


#### Globals

<table>
  <tr><th>trigger</th><th>completion</th></tr>
  <tr><th>angular.bind</th><td><pre>angular.bind({self}, {function})</pre></td></tr>
  <tr><th>angular.bootstrap</th><td><pre>angular.bootstrap({element}{, [{modules}]})</pre></td></tr>
  <tr><th>angular.copy</th><td><pre>angular.copy({source}{, {destination}})</pre></td></tr>
  <tr><th>angular.element</th><td><pre>angular.element({element})</pre></td></tr>
  <tr><th>angular.equals</th><td><pre>angular.equals({obj1}, {obj2})</pre></td></tr>
  <tr><th>angular.extend</th><td><pre>angular.extend({destination}, {source})</pre></td></tr>
  <tr><th>angular.forEach</th><td><pre>angular.forEach({obj}, {iterator})</pre></td></tr>
  <tr><th>angular.fromJson</th><td><pre>angular.fromJson({jsonString})</pre></td></tr>
  <tr><th>angular.identity</th><td><pre>angular.identity()</pre></td></tr>
  <tr><th>angular.injector</th><td><pre>angular.injector([{modules}])</pre></td></tr>
  <tr><th>angular.isArray</th><td><pre>angular.isArray({value})</pre></td></tr>
  <tr><th>angular.isDate</th><td><pre>angular.isDate({value})</pre></td></tr>
  <tr><th>angular.isDefined</th><td><pre>angular.isDefined({value})</pre></td></tr>
  <tr><th>angular.isElement</th><td><pre>angular.isElement({value})</pre></td></tr>
  <tr><th>angular.isFunction</th><td><pre>angular.isFunction({value})</pre></td></tr>
  <tr><th>angular.isNumber</th><td><pre>angular.isNumber({value})</pre></td></tr>
  <tr><th>angular.isObject</th><td><pre>angular.isObject({value})</pre></td></tr>
  <tr><th>angular.isString</th><td><pre>angular.isString({value})</pre></td></tr>
  <tr><th>angular.isUndefined</th><td><pre>angular.isUndefined({value})</pre></td></tr>
  <tr><th>angular.lowercase</th><td><pre>angular.lowercase({string})</pre></td></tr>
  <tr><th>angular.module</th><td><pre>angular.module('{moduleName}', [])</pre></td></tr>
  <tr><th>angular.noop</th><td><pre>angular.noop</pre></td></tr>
  <tr><th>angular.toJson</th><td><pre>angular.toJson({string})</pre></td></tr>
  <tr><th>angular.uppercase</th><td><pre>angular.uppercase({string})</pre></td></tr>
  <tr><th>angular.version</th><td><pre>angular.version</pre></td></tr>
</table>

#### jQuery lite

<table>
  <tr><th>trigger</th><th>completion</th></tr>
  <tr><th>angular: addClass</th><td><pre>addClass({className})</pre></td></tr>
  <tr><th>angular: after</th><td><pre>after({el})</pre></td></tr>
  <tr><th>angular: append</th><td><pre>append({el})</pre></td></tr>
  <tr><th>angular: attr</th><td><pre>attr({el})</pre></td></tr>
  <tr><th>angular: bind</th><td><pre>bind({eventType}{, eventData}{, eventHandler})</pre></td></tr>
  <tr><th>angular: children</th><td><pre>children()</pre></td></tr>
  <tr><th>angular: clone</th><td><pre>clone({withDataAndEvents})</pre></td></tr>
  <tr><th>angular: contents</th><td><pre>contents({withDataAndEvents})</pre></td></tr>
  <tr><th>angular: css</th><td><pre>css({propertyName(s)})</pre></td></tr>
  <tr><th>angular: data</th><td><pre>data({key, value | obj})</pre></td></tr>
  <tr><th>angular: eq</th><td><pre>eq({index})</pre></td></tr>
  <tr><th>angular: find</th><td><pre>find({tag})</pre></td></tr>
  <tr><th>angular: hasClass</th><td><pre>hasClass({className})</pre></td></tr>
  <tr><th>angular: html</th><td><pre>html()</pre></td></tr>
  <tr><th>angular: next</th><td><pre>next()</pre></td></tr>
  <tr><th>angular: parent</th><td><pre>parent()</pre></td></tr>
  <tr><th>angular: prepend</th><td><pre>prepend({content})</pre></td></tr>
  <tr><th>angular: prop</th><td><pre>prop({propertyName})</pre></td></tr>
  <tr><th>angular: ready</th><td><pre>ready({handler})</pre></td></tr>
  <tr><th>angular: remove</th><td><pre>remove({selector})</pre></td></tr>
  <tr><th>angular: removeAttr</th><td><pre>removeAttr({attributeName})</pre></td></tr>
  <tr><th>angular: removeClass</th><td><pre>removeClass({className})</pre></td></tr>
  <tr><th>angular: removeData</th><td><pre>removeData({name})</pre></td></tr>
  <tr><th>angular: replaceWith</th><td><pre>replaceWith({newContent})</pre></td></tr>
  <tr><th>angular: text</th><td><pre>text()</pre></td></tr>
  <tr><th>angular: toggleClass</th><td><pre>toggleClass({className})</pre></td></tr>
  <tr><th>angular: triggerHandler</th><td><pre>triggerHandler({eventType})</pre></td></tr>
  <tr><th>angular: unbind</th><td><pre>unbind({eventType{, handler})</pre></td></tr>
  <tr><th>angular: val</th><td><pre>val({eventType{, handler})</pre></td></tr>
  <tr><th>angular: wrap</th><td><pre>wrap({wrappingElement})</pre></td></tr>

  <tr><th>angular: controller</th><td><pre>controller({name})</pre></td></tr>
  <tr><th>angular: injector</th><td><pre>injector()</pre></td></tr>
  <tr><th>angular: scope</th><td><pre>scope()</pre></td></tr>
  <tr><th>angular: inheritedData</th><td><pre>inheritedData()</pre></td></tr>
</table>

#### Scope functions

<table>
  <tr><th>trigger</th><th>completion</th></tr>
  <tr><th>angular: $apply</th><td><pre>apply({exp})</pre></td></tr>
  <tr><th>angular: $broadcast</th><td><pre>broadcast({name}{, args})</pre></td></tr>
  <tr><th>angular: $destroy</th><td><pre>destroy()</pre></td></tr>
  <tr><th>angular: $digest</th><td><pre>digest()</pre></td></tr>
  <tr><th>angular: $emit</th><td><pre>emit({name}{, args})</pre></td></tr>
  <tr><th>angular: $eval</th><td><pre>eval({expression})</pre></td></tr>
  <tr><th>angular: $evalAsync</th><td><pre>evalAsync({expression})</pre></td></tr>
  <tr><th>angular: $new</th><td><pre>new({isolate})</pre></td></tr>
  <tr><th>angular: $on</th><td><pre>on({name}, {listener})</pre></td></tr>
  <tr><th>angular: $watch</th><td><pre>watch({watchExpression}{, listener}{, objectEquality})</pre></td></tr>
  <tr><th>angular: $watchCollection</th><td><pre>watchCollection({obj}, {listener})</pre></td></tr>
  <tr><th>angular: $id</th><td><pre>id</pre></td></tr>
</table>

#### Log functions

<table>
  <tr><th>trigger</th><th>completion</th></tr>
  <tr><th>angular: $log.debug</th><td><pre>log.debug('{debug}')</pre></td></tr>
  <tr><th>angular: $log.error</th><td><pre>log.error('{error}')</pre></td></tr>
  <tr><th>angular: $log.info</th><td><pre>log.info('{info}')</pre></td></tr>
  <tr><th>angular: $log.log</th><td><pre>log.log('{log}')</pre></td></tr>
  <tr><th>angular: $log.warn</th><td><pre>log.warn('{warning}')</pre></td></tr>
  <tr><th>angular: $log.assertEmpty</th><td><pre>log.assertEmpty()</pre></td></tr>
  <tr><th>angular: $log.reset</th><td><pre>log.reset()</pre></td></tr>
</table>

#### Variables

<table>
  <tr><th>trigger</th><th>completion</th></tr>
  <tr><th>angular: $angular</th><td><pre>angular</pre></td></tr>
  <tr><th>angular: $anchorScroll</th><td><pre>anchorScroll</pre></td></tr>
  <tr><th>angular: $animation</th><td><pre>animation</pre></td></tr>
  <tr><th>angular: $animator</th><td><pre>animator</pre></td></tr>
  <tr><th>angular: $cacheFactory</th><td><pre>cacheFactory</pre></td></tr>
  <tr><th>angular: $compile</th><td><pre>compile</pre></td></tr>
  <tr><th>angular: $controller</th><td><pre>controller</pre></td></tr>
  <tr><th>angular: $exceptionHandler</th><td><pre>exceptionHandler</pre></td></tr>
  <tr><th>angular: $location</th><td><pre>location</pre></td></tr>
  <tr><th>angular: $locationProvider</th><td><pre>locationProvider</pre></td></tr>
  <tr><th>angular: $log</th><td><pre>log</pre></td></tr>
  <tr><th>angular: $parse</th><td><pre>parse</pre></td></tr>
  <tr><th>angular: $resource</th><td><pre>resource</pre></td></tr>
  <tr><th>angular: $rootElement</th><td><pre>rootElement</pre></td></tr>
  <tr><th>angular: $rootScope</th><td><pre>rootScope</pre></td></tr>
  <tr><th>angular: $route</th><td><pre>route</pre></td></tr>
  <tr><th>angular: $routeParams</th><td><pre>routeParams</pre></td></tr>
  <tr><th>angular: $routeProvider</th><td><pre>routeProvider</pre></td></tr>
  <tr><th>angular: $templateCache</th><td><pre>templateCache</pre></td></tr>
  <tr><th>angular: $timeout</th><td><pre>timeout</pre></td></tr>
  <tr><th>angular: $scope</th><td><pre>scope</pre></td></tr>
</table>

#### Directives (on HTML)

**IMPORTANT**

Completions won’t show in HTML unless you have added this line to your `User.sublime-preferences`:

```json
"auto_complete_triggers": [ 
  {"selector": "text.html", "characters": "<"}, 
  {"selector": "text.html meta.tag", "characters": " " } 
]
```

--

<table>
  <tr><th>trigger</th><th>completion</th></tr>
  <tr><th>ng-animate</th><td>ng-animate="{enter: '{example}-enter', leave: '{example}-leave'}"</td></tr>
  <tr><th>ng-animates</th><td>ng-animate="'{class-prefix}'"</td></tr>
  <tr><th>ng-app</th><td>ng-app=""</td></tr>
  <tr><th>ng-bind</th><td>ng-bind=""</td></tr>
  <tr><th>ng-bind-html-unsafe</th><td>ng-bind-html-unsafe=""</td></tr>
  <tr><th>ng-bind-template</th><td>ng-bind-template=""</td></tr>
  <tr><th>ng-change</th><td>ng-change=""</td></tr>
  <tr><th>ng-checked</th><td>ng-checked=""</td></tr>
  <tr><th>ng-class</th><td>ng-class=""</td></tr>
  <tr><th>ng-class-even</th><td>ng-class-even=""</td></tr>
  <tr><th>ng-class-odd</th><td>ng-class-odd=""</td></tr>
  <tr><th>ng-click</th><td>ng-click=""</td></tr>
  <tr><th>ng-cloak</th><td>ng-cloak</td></tr>
  <tr><th>ng-controller</th><td>ng-controller="{Name}Ctrl"</td></tr>
  <tr><th>ng-dblclick</th><td>ng-dblclick=""</td></tr>
  <tr><th>ng-disabled</th><td>ng-disabled=""</td></tr>
  <tr><th>ng-form</th><td>ng-form=""</td></tr>
  <tr><th>ng-hide</th><td>ng-hide=""</td></tr>
  <tr><th>ng-href</th><td>ng-href=""</td></tr>
  <tr><th>ng-if</th><td>ng-if=""</td></tr>
  <tr><th>ng-include</th><td>ng-include="{template}" {onload="" autoscroll=""}</td></tr>
  <tr><th>ng-init</th><td>ng-init=""</td></tr>
  <tr><th>ng-keydown</th><td>ng-keydown=""</td></tr>
  <tr><th>ng-keypress</th><td>ng-keypress=""</td></tr>
  <tr><th>ng-keyup</th><td>ng-keyup=""</td></tr>
  <tr><th>ng-list</th><td>ng-list=""</td></tr>
  <tr><th>ng-model</th><td>ng-model=""</td></tr>
  <tr><th>ng-mousedown</th><td>ng-mousedown=""</td></tr>
  <tr><th>ng-mouseenter</th><td>ng-mouseenter=""</td></tr>
  <tr><th>ng-mouseleave</th><td>ng-mouseleave=""</td></tr>
  <tr><th>ng-mousemove</th><td>ng-mousemove=""</td></tr>
  <tr><th>ng-mouseover</th><td>ng-mouseover=""</td></tr>
  <tr><th>ng-mouseup</th><td>ng-mouseup=""</td></tr>
  <tr><th>ng-multiple</th><td>ng-multiple=""</td></tr>
  <tr><th>ng-nbind</th><td>ng-non-bindable=""</td></tr>
  <tr><th>ng-open</th><td>ng-open=""</td></tr>
  <tr><th>ng-pluralize</th><td>ng-pluralize count="" when="'': '{}'"</td></tr>
  <tr><th>ng-readonly</th><td>ng-readonly=""</td></tr>
  <tr><th>ng-repeat</th><td>ng-repeat="{item} in {array}"</td></tr>
  <tr><th>ng-selected</th><td>ng-selected=""</td></tr>
  <tr><th>ng-show</th><td>ng-show=""</td></tr>
  <tr><th>ng-src</th><td>ng-src=""</td></tr>
  <tr><th>ng-style</th><td>ng-style=""</td></tr>
  <tr><th>ng-submit</th><td>ng-submit=""</td></tr>
  <tr><th>ng-swipe-left</th><td>ng-swipe-left=""</td></tr>
  <tr><th>ng-swipe-right</th><td>ng-swipe-right=""</td></tr>
  <tr><th>ng-switch</th><td>ng-switch on=""</td></tr>
  <tr><th>ng-switch-default</th><td>ng-switch-default=""</td></tr>
  <tr><th>ng-switch-when</th><td>ng-switch-when=""</td></tr>
  <tr><th>ng-transclude</th><td>ng-transclude</td></tr>
  <tr><th>ng-view</th><td>ng-view</td></tr>
</table>


## Contributing

  1. Fork it!
  2. Create your feature branch: `git checkout -b my-new-feature`
  3. Commit your changes: `git commit -m 'Add some feature'`
  4. Push to the branch: `git push origin my-new-feature`
  5. Submit a pull request :D

<!--
## History

Check [Release](https://github.com/erkobridee/sublime-angularjs-ee-snippets/releases) list.

## TODO:

Publish to Sublime Package Control

https://sublime.wbond.net/docs/submitting_a_package

-->

## LICENSE

MIT : [erkobridee.mit-license.org](http://erkobridee.mit-license.org) 
