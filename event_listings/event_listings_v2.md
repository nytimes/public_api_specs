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

## Parameters

With the exceptions of version (specified in the URI path) and response-format (added to the path as an extension), these parameters are specified as name-value pairs in a query string.

### version (Required)	
v2
The current version is v2. (Version 1 is for internal use only.)

### api-key (Required)	
Alphanumeric
For more information, see Requesting a Key.

### response-format
Sets the representation data format	.json (extension)

### ll
Limits the results to events within radius distance of the specified latitude and longitude coordinates.	Two float values, separated by a comma

latitude,longitude

For example, the following parameter would use The New York Times Building as the center of the search, ll=40.756146,-73.99021

By default, the search radius is 1,000 meters. You can set a search radius with the radius parameter.

### radius
Sets the radius of a spatial search (in meters)
(ll must be specified)	Positive integer

Integer value. The default value is 1,000. 

Note: The ll parameter is required to use radius.

### ne
Along with sw, forms a bounded box using the longitude and latitude coordinates specified as the northeast corner. The search results are limited to the resulting box.	Two float values, separated by a comma

latitude,longitude 

Note: The sw parameter is required to use this parameter.

### sw
Along with ne, forms a bounded box using the longitude and latitude coordinates specified as the southwest corner. The search results are limited to the resulting box.	Two float values, separated by a comma

latitude,longitude 

Note: The ne parameter is required to use this parameter.
query	Search keywords to perform a text search on the fields: web_description, event_name and venue_name. 'AND' searches can be performed by wrapping query terms in quotes. If you do not specify a query, all results will be returned.

### filters
Filters search results based on the facets provided	Drill down on search results by filtering on facets. For more information on the values you can filter on, see Facets.

### date_range
Limits the results to events occuring within the specified date range	Start date to end date in the following format: YYYY-MM-DD:YYYY-MM-DD

### facets
Displays a count of all facets in the response	
0 | 1

When facets is set to 1, a count of all facets will be included in the response.

Default value: 0.

### sort
Sorts your results on the fields specified	
sort_value1+[asc | desc],sort_value2+[asc|desc],[...]

Appending +asc to a facet or response will sort results on that value in ascending order. Appending +desc to a facet or response  will sort results in descending order. You can sort on multiple fields. You can sort on any facet. For the list of responses you can sort on, see the Sortable Field column in the Response table.

If you are doing a spatial search with the ll parameter, you can also sort by the distance from the center of the search: dist+[asc | desc]

Note: either +asc or +desc is required when using the sort parameter.

### limit
Limits the number of results returned	Integer

The default value is 20.

### offset
Sets the starting point of the result set	Positive integer 

The first 20 results are shown by default. To page through the results, set offset to the appropriate value (e.g., offset=20 displays results 21–40).



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

By default, the radius is 1,000 meters, you can set a custom search radius:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
ll=40.756146,-73.99021&radius=2500
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Note: setting a radius without a center point will return an error.

When searching within a radius, you can sort search results based on their proximity to the center point:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
ll=40.756146,-73.99021&radius=2500&sort=dist+asc
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

When searching within a bounded box, you must specify both a southwest and northeast corner:

sw=40.756146,-73.99021&ne=40.778267,-73.96988
For a full example search query, see Examples.

### FACETED SEARCH
Using facets to limit the categories in your search can result in more exact results. For example, you can search for Jazz events in Manhattan by filtering your results using facets:

filters=category:Jazz,borough:Manhattan
You can also specify multiple values for a single facet:

filters=category:(Jazz Dance),borough:Manhattan
See Facets, for more information. For a full example search query, see Examples.

### FULL TEXT SEARCH
Using the query parameter will perform a full text search on the web_description, event_name and vanue_name fields. For example, to search for any events that contains the word Avenue or Street:

query=Avenue+Street
To perform an AND search, and only return results that contain the complete phrase "Avenue Q", wrap the search term in quotes:

query="Avenue Q"
For a full example search query, see Examples.

### FACETS
Below is a list of the facets you can filter your search on using the filters parameter. For an overview of faceted search, see the Faceted Search section. The Examples section has examples of different searches, some of which filter by facets.

Each facet can be filtered by the values that facet can accept. For a full list of all acceptable facet:value pairs look at the facet section of any Event Listings query that has the facets parameter set to 1.


### Examples

category: Theater

subcategory: Off Broadway

borough: Queens

neighborhood: Greenwich Village

times_pick: true

free: true

kid_friendly: true

last_chance: true

festival: true

long_running_show: true

previews_and_openings: true

Below is a simple example of filtering a search by a single facet:

### filters=category:forChildren
If the facet value contains spaces, you must enclose it in double quotes:

### filters=borough:"Staten Island"
You can exclude facets from your filtered search:

### filters=category:(-Jazz)
You can filter on multiple facets:

### filters=category:Jazz,borough:Manhattan
You can also filter a search on more than one value for a single facet. The values should be inside parentheses:

### filters=neighborhood:(SoHo Harlem "Midtown South")

## Responses

An HTTP response code of 200 (OK) is returned for all requests that are successfully understood and processed. See the Errors section for additional response codes.

### DATA FIELDS
Setting the facets parameter to true will display a set of facet values , drawn from all search results. These sets are collected in a facets array at the beginning of the response. 

Note: the sets of facet values (collected in the facets array) are returned in addition to the search results. Each search result record can also include facet values for that specific result, if facets are specified with the fields parameter.

The API returns 10 records at a time. However, the facets array at the beginning of the response is drawn from all results, not just the current set of 10.

Most of the data returned by the Event Listings API is self-explanatory. This section provides additional information about some of the response fields.

Note: Sortable fields are fields that you can sort results on using the sort parameter.

In this table, fields are listed in alphabetical order.


