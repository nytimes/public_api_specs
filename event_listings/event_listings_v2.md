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

| Name | Data Type | Sortable Field | Description |
| critic_name | Strings | Yes | The name of the NYTimes critic who reviewed the event |
| category | String | Yes | The category of the event |
| event_date_list | Array (of Dates) | No | The date(s) the event will be taking place |
| event_detail_url | String | No | The URL of the event detail page on NYTimes.com |
| event_id	Integer	Yes	An identifier assigned to the event
| event_name | String | Yes | The name of the event |
| event_schedule_id | Integer | Yes | An identifier assigned to the schedule for the event festival	Boolean	Yes	Indicates if the event is a festival |
| film_rating | Boolean | Yes | Indicates if the event has a film rating | 
| free | Boolean | Yes | Indicates if the event is free-of-charge |
| kid_friendly | Boolean | Yes | Indicates if the event is considered suitable for young audiences |
| last_chance | Boolean | Yes | Indicates whether the event has an approaching end date |
| last_modified | Date | Yes | The last time information for the event was changed |
| long_running_show | Boolean | Yes | Indicates whether the event has been in recurring for a long period of time |
| previews_and_openings | Boolean | Yes | Indicates whether the event is a preview or opening event |
| recurring_end_date | Date | No | The date the event will end it's recurring schedule (see recur_days for the days of the week the event takes place) |
| recurring_start_date | Date | No | The date the event began it's recurring schedule (see recur_days for the days of the week the event takes place) |
| recur_days | Array (Strings) | No | The days of the week the event takes place |
| times_pick | Boolean | Yes | Indicates whether the event is an NYTimes Critics' Pick |
| web_description | String | No | A description of the event |

## Examples
These examples do not include the required api-key parameter. Be sure to include your API key in your request.

Each example is linked to the Times API Console, which allows you to generate requests and responses without coding.

### SPATIAL SEARCH REQUESTS
Search for all events within 1,000 meters of The New York Times Building

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/events/v2/listings.json?&ll=40.756146,-73.99021&api-key=####
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Search for all events within 2,500 meters of The New York Times Building

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/events/v2/listings.json?ll=40.756146,-73.99021&radius=2500&api-key=####
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Search for all events within a bounded box with The New York Times as the southeast corner and Central Park as the northwest corner

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/events/v2/listings.json?sw=40.756146,-73.99021&ne=40.778267,-73.96988&api-key=####
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

##3 FACET SEARCH REQUESTS
Search for all Dance events in Manhattan

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/events/v2/listings.json?&filters=category:Dance,borough:Manhattan&api-key=####
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Search for all events in Manhattan that aren't Dance

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/events/v2/listings.json?&filters=category:(-Dance),borough:Manhattan&api-key=####
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Search for all events that are classified as either Theater or Dance

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/events/v2/listings.json?&filters=category:(Theater+Dance)&api-key=####
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

### FULL TEXT SEARCH REQUESTS
Search for any events containing "classical" or "play" in the event name, venue name or web description

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/events/v2/listings.json?&query=classical+play&api-key=####
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Search for any events containing the full phrase "hip hop" in the event name, venue name or web description

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/events/v2/listings.json?&query=%22hip+hop%22&api-key=####
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

### COMBINING ALL SEARCH REQUESTS TYPES
Search for any events containing "Book of Mormon" in the event name, venue name or web description that is within 3,000 meters of The New York Times Building and sorting the results by proximity to The New York Times Building

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/events/v2/listings.json?&query=%22Book+of+Mormon%22&ll=40.756146%2C-73.99021&radius=3000&sort=dist+asc&api-key=####
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Search for the first 10 Off Broadway events starting with the 6th event

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/events/v2/listings.json?&filters=subcategory:"Off+Broadway"&limit=10&offset=5&api-key=####
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

## Errors
The Event Listings API returns the standard errors.

### 400 Bad Request
A required parameter was not specified or your request was otherwise improperly formed. See the body of the error response for more details.

### 404 Not Found
The resource you requested does not exist.

### 500 Server Error
The request was successfully understood, but it could not be processed due to a server error. Please try your request again later, and contact us if the problem continues.

