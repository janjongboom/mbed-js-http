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

## Todo

* `send()` is synchronous. Should not be synchronous.
* Header allocation should be on the heap. Now the lib often runs out of stack memory when reading the headers.
