# combi-server-router
_A request router made for the combi-server framework_

## Usage

* Install with `npm install --save combi-server-router`
* Require with `var Route = require("combi-server-router")`
* Create a router `var router = new Route.Router();`
* Add some routes `router.get('/', functionToServeIndexPage);`
* Mount the middleware `server.use(Route.middleware(router));`
* ???
* Profit

## API

Requiring combi-server-router exposes two objects on the target variable,
`Router` and `middleware`.

### Router

`Router` is a constructor for a [router-core](https://github.com/BuyPro/Router-Core)
request router. Refer to the documentation of that for more details. To summarise:

* router.method(VERB): Enable a HTTP verb on this router. By default, GET and POST
    already exists, as does ALL (Catch all for all methods). VERB is case insensitive,
    will be uppercased, and routes can be added to it with the following method
* router.\[verb\](path, handler): Add a route for the specified (lower case) verb at the
    given path. Sections of the URL can be parametised by prefixing them with a colon.
    The path can also be a regular expression, although capture groups will not add
    parameters.
    
### middleware

`middleware` is simply the connecting glue from router-core to combi-server, it processes
the given request object and passes it to the router-core module. It's used as a combi-server
middleware in the following way: `server.use(Route.middleware(router));` where `server` is
the combi-server object, `Route` is the require'd combi-server-router and `router` is a
configured router-core router.
