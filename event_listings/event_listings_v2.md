The Event Listings API
======================

With the Event Listings API, you can search the New York Times listing of noteworthy cultural events in New York City and beyond.

Note: In this document, curly braces { } indicate required items. Square brackets [ ] indicate optional items or placeholders.

| Base URI | http://api.nytimes.com/svc/events/{version}/listings |
| Scope | A Times selection of NYC cultural events |
| HTTP method | GET |
| Response formats | JSON (.json) |

To use the Events API, you must sign up for an API key.  Usage is limited to 1,000 requests per day (rate limits are subject to change). Please read and agree to the API Terms of Use and Attribution Guidelines before you proceed.

Requests
--------

The Events service uses a [RESTful](<http://en.wikipedia.org/wiki/Representational_State_Transfer>) style.

### URI Structure

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/events/{version}/listings[.response-format]?[optional-param1=value1]&[...]&api-key={your-API-key}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

### Parameters

With the exceptions of version (specified in the URI path) and response-format (added to the path as an extension), these parameters are specified as name-value pairs in a query string.
