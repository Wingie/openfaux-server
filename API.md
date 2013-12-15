API Documentation
=================

**Note:** _This is a work in progress and may (will) change without notice._

* * *

## Server-Client Interaction

The openfaux client should set certain extra headers on every request made to the server. These should ideally not be forwarded by the proxy request.

The server can process the header information before (or even after) retrieving the content. `process()` in `ProxyRequest` is overriden to parse the headers.

A convention can be adopted (for the sake of brevity), 

+ __ofx-request-x__  : _for options that need to be acted on before the request is made_
+ __ofx-response-x__  :  _for options for specically need to be acted on the response body_

## Authentication

It is useful to be able to notice if a request has been spoofed or tampered with. In the testclient.py the host+time of the request is hashed as a signature.
I guess since we are opensource, this might be redundant. but in any case, it can serve as an example of how to add and parse the headers.

One issue with this sort of authentication happens when the proxy needs to do a 302 response redirect; the signature will not match for the second request.

