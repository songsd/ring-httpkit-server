# Ring-Httpkit-Server

A library forked from Ring-Server for starting a web server to serve a [Ring][1] handler with
sensible default options and environment variable overrides

Using http-kit as web server,supporting websocket.

[1]: https://github.com/ring-clojure/ring

## Features

When starting in development mode (i.e. `LEIN_NO_DEV` is not set):

* The server finds a free port to start on
* It automatically reloads changed files
* It renders exceptions and their stacktraces in HTML
* A web browser is automatically opened to the started server

In production:

* You can specify the port via the `PORT` environment variable
* You can add hooks to run on startup and shutdown.


## Usage 

Simple usage:

```clojure
(use 'ring.server.standalone)
(serve your-handler)
```

You can also specify a map of options:

```clojure
(serve your-handler {:port 4040})
```

The following options are supported:

* `:port`    - The port to start the server on, overrides `$PORT`

* `:init`    - A function executed when the server starts

* `:destroy` - A function executed when the server stops

* `:open-browser?` -
  True if you want a browser to be opened to the server. Defaults to
  true in development mode, false in production mode.

* `:browser-uri` -
  A path to append to the target URL if opening a browser (default 
  none). The full URI will be constructed like:
  `http://{host}:{port}{browser-uri}`

* `:stacktraces?` -
  True if you want a stacktrace to be displayed in the browser when
  an exception is raised. Default to true in development, false in
  production.

* `:stacktrace-middleware` -
  Override the default Ring stacktrace middleware with a custom
  middleware function.

* `:auto-reload?` -
  True if you want your source files to be automatically reloaded
  when they are modified. Defaults to true in development, false in
  production.
  
* `:reload-paths` -
  A seq of source paths to reload. Defaults to [\"src\"]. 
  Only relevant if :auto-reload? is true.

* `:auto-refresh?` -
  True if you want your browser to automatically refresh when source
  files are changed. Defaults to false.

## License

Copyright © 2015 James Reeves

Distributed under the Eclipse Public License, the same as Clojure.
