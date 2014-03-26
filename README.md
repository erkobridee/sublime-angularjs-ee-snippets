# Angular.js EE Snippets for Sublime Text 2/3

<!-- toc -->
* [Overview](#overview)
* [Installation Options](#installation-options)
* [Snippets](#snippets)
  * [Require.js](#requirejs)
    * [[config]](#config)
    * [[define]    Require.js](#define-requirejs)
    * [[load]    Require.js](#load-requirejs)
  * [Angular.js EE (Enterprise Edition)](#angularjs-ee-enterprise-edition)
    * [[bootstrap]    Angular.js EE](#bootstrap-angularjs-ee)
    * [[load]    Angular.js EE](#load-angularjs-ee)
    * [[module]    Angular.js EE](#module-angularjs-ee)
    * [[module-use]    Angular.js EE](#module-use-angularjs-ee)
    * [[mock-load]    Angular.js EE](#mock-load-angularjs-ee)
    * [[mock-pass-urls]    Angular.js EE](#mock-pass-urls-angularjs-ee)
    * [[mock-pass-backend]    Angular.js EE](#mock-pass-backend-angularjs-ee)
    * [[mock-data]    Angular.js EE](#mock-data-angularjs-ee)
    * [[mock-backend]    Angular.js EE](#mock-backend-angularjs-ee)
    * [[mock-urls]    Angular.js EE](#mock-urls-angularjs-ee)
      * [[mock-w-all]    Angular.js EE](#mock-w-all-angularjs-ee)
      * [[mock-w-one]    Angular.js EE](#mock-w-one-angularjs-ee)
      * [[mock-w-post]    Angular.js EE](#mock-w-post-angularjs-ee)
      * [[mock-w-put]    Angular.js EE](#mock-w-put-angularjs-ee)
      * [[mock-w-delete]    Angular.js EE](#mock-w-delete-angularjs-ee)
      * [[mock-w-search]    Angular.js EE](#mock-w-search-angularjs-ee)
  * [Angular.js](#angularjs)
    * [Services](#services)
      * [[angular]    Angular.js](#angular-angularjs)
      * [[config]    Angular.js](#config-angularjs)
      * [[constant]    Angular.js](#constant-angularjs)
      * [[controller]    Angular.js](#controller-angularjs)
      * [[decorator]    Angular.js](#decorator-angularjs)
      * [[directive]    Angular.js](#directive-angularjs)
      * [[directiveLong]    Angular.js](#directivelong-angularjs)
      * [[factory]    Angular.js](#factory-angularjs)
      * [[filter]    Angular.js](#filter-angularjs)
      * [[module]    Angular.js](#module-angularjs)
      * [[provider]    Angular.js](#provider-angularjs)
      * [[resource-id]    Angular.js](#resource-id-angularjs)
      * [[resource]    Angular.js](#resource-angularjs)
      * [[routeProvider]    Angular.js](#routeprovider-angularjs)
      * [[when]    Angular.js](#when-angularjs)
      * [[otherwise]    Angular.js](#otherwise-angularjs)
      * [[run]    Angular.js](#run-angularjs)
      * [[service]    Angular.js](#service-angularjs)
      * [[value]    Angular.js](#value-angularjs)
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

* Sublime Text 2 / 3 Snippets and Completions for [Angular.js](http://angularjs.org/), [[GitHub] erkobridee / angularjs-ee-boilerplate](https://github.com/erkobridee/angularjs-ee-boilerplate) and [Require.js](http://requirejs.org/)

* Based on: [[GitHub] maxhoffmann / angular-snippets](https://github.com/maxhoffmann/angular-snippets)

--

* This snippet library provides completions for Angular.js and Require.js (focused to the **angularjs-ee-boilerplate** code).

* Sublime Text uses fuzzy searching for snippets and completions therefore you don’t have to write triggers completely.

* All snippets add Angular’s inline notation for dependencies automatically, so you don’t have to type them twice.



## Installation Options

<!-- * Package Control: search for "AngularJS EE Snippets" -->

* Manual: 

  * Download the package and put it manually inside your `Packages` directory. (`Menu >  Preferences > Browser Packages...`)

  * Clone repository inside your `Packages` directory.

```sh
$ cd ~/Library/Application\ Support/Sublime\ Text\ 2/Packages
$ git clone https://github.com/erkobridee/sublime-angularjs-ee-snippets.git
```


## Snippets

Below is a list of all triggers and respectives snippets currently supported on this package.

> **trigger:** [*triggerName*] `TAB` key.


### Require.js

#### [config]

**Description:** <pre>config		Require.js</pre>

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

#### [define]    Require.js

```javascript
define(
// require.js dependency injection
[
  $1
],

// require.js module scope
function($2) {
  'use strict';

  ${3: return ${0:object_or_function};}

});
```

#### [load]    Require.js

```javascript
define(
// require.js dependency injection
[
  $0
],

// require.js module scope
function() {});
```


### Angular.js EE (Enterprise Edition)

#### [bootstrap]    Angular.js EE

```javascript
define(
// require.js dependency injection
[
  'angular',

  $1'./require.mock.load',

  '$3app/main/require.load'
],

// require.js module scope
function(ng) {
  'use strict';

  ng.element(document).ready(function() {

    // define run module to bootstrap application
    ng.module(
      // module name
      '${0:run}',

      // module dependencies
      [
        $2'ngMockBackend',

        '${4:main}'
      ]
    );

    // start angular app
    ng.bootstrap(document, ['$0']);

  });

});
```

#### [load]    Angular.js EE

```javascript
define(
// require.js dependency injection
[
  './module',
${1:  './resource',}
  './controller',
  './routes'$0
],

// require.js module scope
function() {});
```

#### [module]    Angular.js EE

```javascript
define(
// require.js dependency injection
[
  'angular',
  'angularRoute'${1:,
  'angularResource'}
],

// require.js module scope
function(${2:ng}) {
  'use strict';

  // module definition
  return $2.module(
    // module name
    '${3:moduleName}',

    // module dependencies
    [
      'ngRoute'${4:,
      'ngResource'}$0
    ]
  );

});
```

#### [module-use]    Angular.js EE

```javascript
define(
// require.js dependency injection
[
  '$1./module'$2
],

// require.js module scope
function(${3:module}) {
  'use strict';

  $3$0

});
```

#### [mock-load]    Angular.js EE

```javascript
define(
// require.js dependency injection
[
  //$1'./allow-pass'

  /**/$2
  './data',
  './url-interceptors'
  /*$3*/
],

// require.js module scope
function() {});
```

#### [mock-pass-urls]    Angular.js EE

```javascript
define(
// require.js dependency injection
[
  'shared/mock/backend'
],

// require.js module scope
function(backend) {
  'use strict';


  backend.addResource(

    // mock resource dependencies injection
    [
      ${1/(?:.+)/'/g}${1/,[ ]*/', '/g}${1/(?:.+)/', /g}

  // mock resource definition
  function(${1:\$httpBackend, regexpUrl}) {

${2:    // Allow GET users from GitHub API}
    ${4:\$httpBackend
      .when('GET', regexpUrl(/${3:api\.github\.com\/users}(\/)?([A-z0-9]+)?\$/))
      .passThrough();}$0

  }]);


});
```

#### [mock-pass-backend]    Angular.js EE

```javascript
define(
// require.js dependency injection
[
  'shared/mock/backend'
],

// require.js module scope
function(backend) {
  'use strict';


  backend.addResource(

    // mock resource dependencies injection
    [
      ${1/(?:.+)/'/g}${1/,[ ]*/', '/g}${1/(?:.+)/', /g}

  // mock resource definition
  function(${1:\$httpBackend, regexpUrl}) {

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

${4:    // search
    \$httpBackend
      .when('GET', regexpUrl(/$2\/$3\/search\/([A-z0-9]+)(\?|\$)/))
      .passThrough();}

    //--- @end: Allow pass to server

  }]);


});
```

#### [mock-data]    Angular.js EE

> Use [LokiJS](http://lokijs.org/) to manage object collection

```javascript
define(
// require.js dependency injection
[
  'shared/mock/module'
],

// require.js module scope
function(module) {
  'use strict';


  module.factory(

    // factory name
    '${1:Name}Collection',

    // factory dependencies injection
    ['DataStore', 'Helpers', '\$log',

  // factory definition
  function(DataStore, helpers, console) {

    console.debug('$1Collection');

    var Collection = (function() {

      //--- private att

      var seq = 0;
      var collection = DataStore.addCollection(
        // collection name
        '${1/([A-Za-z0-9]+)?/(?2::\l$1)/g}',

        // Object Type
        '$1$2',

        // indices array
        [
          'id',
          'name'$3
        ]
      );

      //--- @begin: private functions

      function searchValue(find) {
        if(!find) return [];

        var r = [], obj,
            regexp = new RegExp(find, 'i'),
            data = collection.find(),
            len = data.length;

        for (var i = 0; i < len; i++) {
          obj = data[i];

          if(obj.name.match(regexp) || obj.description.match(regexp))
            r.push(obj);
        }

        return r;
      }

      //--- @end: private functions


      // class constructor
      var $1Collection = function() {};
      var ClassDef = $1Collection;
      //---

      //--- @begin: public functions

      ClassDef.prototype.getById = function(id) {
        var r = collection.find({'id': id});
        if(r.length > 0) return r[0];
        return null;
      };

      ClassDef.prototype.insert = function(object) {
        if(helpers.isObject(object)) {
          object.id = seq++;
          return collection.insert(object);
        }
        return null;
      };

      ClassDef.prototype.update = function(object) {
        if(helpers.isObject(object))
          collection.update(object);
      };

      ClassDef.prototype.remove = function(object) {
        if(helpers.isObject(object))
          collection.remove(object);
      };

      ClassDef.prototype.list = function(options) {
        options = options || {page: 1, size: 10};
        return helpers.paginate(collection.find(), options);
      };

      ClassDef.prototype.search = function(find, options) {
        options = options || {page: 1, size: 10};
        return helpers.paginate(searchValue(find), options);
      };

      //--- @end: public functions

      //--- @begin: init collection
      (function() {

        function createObject(_id, _name, _description$4) {
          return {
            id: _id,
            name: _name,
            description: _description$5
          };
        }

${9:        // manual fake data definition}
${0:        collection.insert(
          createObject(
            seq++,
            'Manual Person ' + (seq+1),
            'Manual Person ' + (seq+1) + 'Description'$6
          )
        );}

        for (var i = ${8:59}; i >= 0; i--) {
          collection.insert(
            createObject(
              seq++,
              'fake person ' + (seq+1),
              'some description to fake person ' + (seq+1)$7
            )
          );
        }

      })();
      //--- @end: init collection

      // return class definition
      return ClassDef;
    })();

    //---

    return new Collection();

  }]);


});
```

#### [mock-backend]    Angular.js EE

> Complete CRUD + Search

```javascript
define(
// require.js dependency injection
[
  'angular',
  'shared/mock/backend',

  './data$1'
],

// require.js module scope
function(ng, backend) {
  'use strict';


  backend.addResource(

    // mock resource dependencies injection
    [
      '${2:Name}Collection', 'Helpers',
      '\$httpBackend', 'regexpUrl', 'getParams',
      '\$log',$3

  // mock resource definition
  function(collection, helpers, \$httpBackend, regexpUrl, getParams, console$4) {

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

${9:    console.debug(collection.getById(1));
    console.debug(collection.list());
}
  }]);

});
```

#### [mock-urls]    Angular.js EE

```javascript
define(
// require.js dependency injection
[
  'angular',
  'shared/mock/backend'${2:,

  './data$1'}
],

// require.js module scope
function(ng, backend) {
  'use strict';


  backend.addResource(

    // mock resource dependencies injection
    [
      'Helpers',
      '\$httpBackend', 'regexpUrl', 'getParams',
      '\$log',$3

  // mock resource definition
  function(helpers, \$httpBackend, regexpUrl, getParams, console$4) {

    //--- @begin: URL interceptor

    $0

    //--- @end: URL interceptor

  }]);

});
```

##### [mock-w-all]    Angular.js EE

> HTTP GET - all

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

##### [mock-w-one]    Angular.js EE

> HTTP GET - one (by id)

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

##### [mock-w-post]    Angular.js EE

> HTTP POST - create

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

##### [mock-w-put]    Angular.js EE

> HTTP PUT - update

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

##### [mock-w-delete]    Angular.js EE

> HTTP DELETE

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

##### [mock-w-search]    Angular.js EE

> HTTP GET - search collection by value

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

#### Services

##### [angular]    Angular.js

```javascript
angular
```

##### [config]    Angular.js

```javascript
config([${1/(?:.+)/'/g}${1/,[ ]*/', '/g}${1/(?:.+)/', /g}function ($1) {
  $0
}]);
```

##### [constant]    Angular.js

```javascript
constant('${1:name}', ${2:value});
```

##### [controller]    Angular.js

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

##### [decorator]    Angular.js

```javascript
decorator('${1:name}', [${2/(?:.+)/'/g}${2/,[ ]*/', '/g}${2/(?:.+)/', /g}function (${2:\$provide}) {
  \$provide.decorator('${3:name}', [${4/(?:.+)/'/g}${4/,[ ]*/', '/g}${4/(?:.+)/', /g}function(${4:\$delegate}) {
    return ${5:\$delegate}$0;
  }]);
}]);
```

##### [directive]    Angular.js

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

##### [directiveLong]    Angular.js

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
${5:    templateUrl: 'directive.html',}
${6:    replace: true,}
${7:    transclude: true,}
${8:    restrict: 'A',}
${9:    scope: \{$10\},}
${11:    controller: [
      // dependencies injection
      ${12/(?:.+)/'/g}${12/,[ ]*/', '/g}${12/(?:.+)/', /g}

    // controller definition
    function(${12:\$scope, \$element, \$attrs, \$transclude}) \{

    \}],}
${13:    compile: function compile(tElement, tAttrs, transclude) \{
      return function postLink(scope, iElement, iAttrs, controller) \{

      \}
    \},}
${14:    link: function postLink(scope, iElement, iAttrs) \{

    \}}
  };
}]);
```

##### [factory]    Angular.js

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

##### [filter]    Angular.js

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

##### [module]    Angular.js

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

##### [provider]    Angular.js

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

##### [resource-id]    Angular.js

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

##### [resource]    Angular.js

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

##### [routeProvider]    Angular.js

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

##### [when]    Angular.js

```javascript
when(
  '/${1:route}',
  {
    controller: '${2:ControllerName}Ctrl',
    templateUrl: '${3:app}/${4:module}/${5:template}.html'
  }
)$0
```

##### [otherwise]    Angular.js

```javascript
otherwise(${1:{ redirectTo: '/${2:route}' \}})
```

##### [run]    Angular.js

```javascript
run([${1/(?:.+)/'/g}${1/,[ ]*/', '/g}${1/(?:.+)/', /g}function ($1) {
  $0
}]);
```

##### [service]    Angular.js

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

##### [value]    Angular.js

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
