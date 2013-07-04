##Welcome to Wakanda Server Side Templating module##

The server side templating module is based on the [underscore](http://www.underscorejs.org) module.

###Example: Quickly start the templating
```js
var ssjs = require('wakemplate');
ssjs.start();
```

This will render any .ssjs file that exist in the active webFolder.

The start function takes two optional parameters:

- **`regex`**

  A string that represent the template files. ('/.*\.ssjs$' by default)

- **`baseFolder`**

  The folder path where the server must look for the templates. (The active webFolder by default)
  
A templae file must be a valid [underscore template](http://underscorejs.org/#template). For example:

###Example:
```js
<% ds.Comment.forEach(function(entity){%>
  <h4><%= entity.user %></h4>
  <p><%= entity.comment %></p>
<%});%>
```

Notice that, if you are not familiar with the underscore templates syntax, you can modify the templateSettings variable (Refer to the [underscore](http://www.underscorejs.org) website for more information)

And finally, in the template context, you have the access to the http [request](http://doc.wakanda.org/HTTP-Request-Handlers/HTTPRequest.201-803366.en.html) and the http [response](http://doc.wakanda.org/HTTP-Request-Handlers/HTTPResponse.201-805902.en.html) objects.
  
###Example:
```js
<% response.headers['Content-Type'] = 'text/javascript'; %>
var array = <%= JSON.stringify(ds.Comment.toArray('user')) %>;
```
