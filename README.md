# azure-graphapi

Node.js package for making Azure Active Directory Graph API calls

## Installation

```
npm install azure-graphapi --save
```

## Usage

```javascript
var GraphAPI = require('azure-graphapi');

var graph = new GraphAPI(tenant, clientId, clientSecret);

graph.get('users/a8272675-dc21-4ff4-bc8d-8647830fa7db', function(err, user) {
    if (!err) {
        console.dir(user);
    }
}
```

## Details

This package provides an HTTPS interface to the [Azure Active Directory Graph API](https://msdn.microsoft.com/en-us/library/azure/hh974476.aspx). You will need the tenant (i.e., domain) of your Azure AD instance as well as an application within that AD instance that has permissions to access you directory. This application is identified by a `clientId` and authenticated using a `clientSecret`. The `clientSecret` is also called an application key.

## Interface

```javascript
GraphAPI(tenant, clientId, clientSecret, [apiVersion])
```

[Constructor] Creates a new `GraphAPI` instance. If the `apiVersion` is not specified, it defaults to version 1.5.

```javascript
get(uri, callback)
```

[Method] Performs an HTTPS GET request. The `uri` must *not* begin with a slash. The callback signature is `callback(err, response)`.

```javascript
post(uri, data, callback)
```

[Method] Performs an HTTPS POST request. The `uri` must *not* begin with a slash. The `data` is the request object. The callback signature is `callback(err, response)`.


```javascript
put(uri, data, callback)
```

[Method] Performs an HTTPS PUT request. The `uri` must *not* begin with a slash. The `data` is the request object. The callback signature is `callback(err, response)`.

```javascript
patch(uri, data, callback)
```

[Method] Performs an HTTPS PATCH request. The `uri` must *not* begin with a slash. The `data` is the request object. The callback signature is `callback(err, response)`.

```javascript
delete(uri, callback)
```

[Method] Performs an HTTPS DELETE request. The `uri` must *not* begin with a slash. The callback signature is `callback(err)`.

```javascript
request(method, uri, data, callback)
```

[Method] Performs the HTTPS request specified by the `method`. The `uri` must *not* begin with a slash. The `data` is the request object and can be `null`. The callback signature is `callback(err)` for 204 (No Content) responses and `callback(err, response)` for all other success status codes.

```javascript
getObjects(uri, objectType, callback)
```

[Method] Performs an HTTPS GET request and accumulates all objects having the specified `objectType` (e.g., "User"). The `uri` must *not* begin with a slash. The callback signature is `callback(err, response)`. This method follows the `odata.nextLink` property in the response continues until no more batches of objects are available.

## License

(The MIT License)

Copyright (c) 2015 Frank Hellwig

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.


