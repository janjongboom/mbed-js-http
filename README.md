# mbed.js wrapper for mbed-http

JS on mbed driver for HTTP calls, based on [sandbox/mbed-http](http://developer.mbed.org/teams/sandbox/code/mbed-http/).

This wrapper was generated via [mbed-js-wrapper-generator](https://github.com/janjongboom/mbed-js-wrapper-generator).

## Usage

1. In your [Gulp-based mbed.js project](https://github.com/ARMmbed/mbed-js-example), run:

    ```
    $ npm install mbed-js-http
    ```

1. Clear your build directory:

    ```
    $ rm -r build/out
    ```

1. Use the library via:

    ```js
    var network = /* get a network connection from somewhere... See below. */

    var get = HttpRequest(network, http_method.HTTP_GET, 'http://httpbin.org/status/418');
	var gres = get.send();

    print("Status is " + gres.status_code());
    ```

## Getting a network connection

See [ARMmbed/mbed-js-easy-connect](https://github.com/armmbed/mbed-js-easy-connect).

## HTTPS

This library does not support HTTPS right now. The underlying library (mbed-http) however *does*. I've left it out right now because:

* HTTPS requires mbed TLS, which is relatively big, especially when combining it with JerryScript.
* It cannot be linked out when not using it (as in C++).

If you want HTTPS:

* Change `#include http_request.h` into `#include https_request.h`.
* Rename all `HttpRequest` instances to `HttpsRequest`.
* Note that the constructor for the JS object changes, so you'll need to do a little work there (one extra parameter).

## Todo

* `send()` is synchronous. Should not be synchronous.
* Header allocation should be on the heap. Now the lib often runs out of stack memory when reading the headers.
