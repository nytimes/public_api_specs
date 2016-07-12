The Event Listings API
======================

With the Event Listings API, you can search the New York Times listing of noteworthy cultural events in New York City and beyond.

Note: In this document, curly braces { } indicate required items. Square brackets [ ] indicate optional items or placeholders.

  Base URI: http://api.nytimes.com/svc/events/{version}/listings
  Scope: A Times selection of NYC cultural events
  HTTP method: GET
  Response formats: JSON (.json)

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


Searching Event Listings
------------------------

In the Event Listings API, there are three main methods of searching for events:

Spatial Search: Set a geographic center and have all results within a set radius returned or receive all results within a box bounded by specified northeast and southwest points.

Faceted Search: Return a subset of results based on the facets you specify

Full Text Search: Search for results based on a keyword query

You can use a single search method or use multiple methods in conjuction with each other.

### SPATIAL SEARCH
Spatial searches can be accomplished in two ways: searching within a radius or setting a bounded box.

To search within a radius, you must specify the longitude and latitude of the center point:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
ll=40.756146,-73.99021
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


