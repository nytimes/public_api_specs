The Geographic API
==================

The Geographic API extends the Semantic API, using a linked data approach to
enhance location concepts used in The New York Times' controlled vocabulary and
data resources which combine them with
the [GeoNames](<http://geonames.org/>) database, an authoritative and free to
use database of global geographical places, names and features.

**Note:** In URI examples and field names, *italics* indicate placeholders for
variables or values. Parentheses ( ) indicate optional items. Square brackets [
] are not a convention — when URIs include brackets, interpret them literally.

**The Geographic API at a Glance**

**Base URI**

`http://api.nytimes.com/svc/semantic/v2/geocodes`

**Scope**

The New York Times controlled vocabulary (over 2000 places used to classify New
York Times articles metadata) and New York Times articles from 1981 to today
(excludes wire services such as the Associated Press)

**HTTP method**

GET

**Response formats**

JSON

 

Getting Started
---------------

### KEY CONCEPTS

There are five types of queries with the Geographic API:

1.  **Latitude and Longitude values **

2.  **Query Terms:** String values that provide specific place information (like
    city names, country names or postal codes) and correspond to a wide range of
    GeoNames parameters.

3.  **Ranges**: Some GeoNames parameters (like population or elevation) are
    searchable across a range of values (greater than a lower boundary value and
    less than an upper boundaru value).<http://data.nytimes.com/>

4.  **Bounding Box**: The range of latitude and longitude values corresponding
    to the rectangular box formed by two lat-lon values.

5.  **Nearby**: Provides a list of places nearest to a lat-lon or place query
    string, listed in order of proximity

You can get good results with a simple query. But to make the most of all the
options and features of the API, be sure to read this entire page. Here's a
recommended approach:

1.  Read about the various request options and types under the different 

2.  Review the complete table of [Data
    Fields](<http://developer.nytimes.com/docs/geographic_api#h3-data>).

3.  Return to the Requests section to start building your request URI. While
    you're constructing your query, refer to
    the [examples](<http://developer.nytimes.com/docs/geographic_api#h2-examples>)and
    use the [API
    console](<http://prototype.nytimes.com/gst/apitool/index.html>) to test
    requests without coding.

 

Constructing a Search Query
---------------------------

The query syntax can use any combination of optional parameters listed above.

Queries using String values are matched exactly.

Queries using numerical values (Integer or Double) can be tested for equality,
greater than, less than, or in the case of value ranges, both greater than and
less than.

The general form for a Geographic API request by concept type and specific
concept:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/semantic/v2/geocodes/query.json?(query parameters)&api-key=your-API-key
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

### EXAMPLE QUERIES

Examples of Geographic API requests by concept type and specific concept:

-   Query to return 20 geocodes in the United States

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/semantic/v2/geocodes/query.json?country_code=US&api-key=your-API-key
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

-   Query to return up to 20 populated places with an elevation of exactly 2000
    meters.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/semantic/v2/geocodes/query.json?elevation=2000&feature_class=P&api-key=your-API-key
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

-   Query to return up to 20 populated places with an elevation greater than
    2000 meters.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/semantic/v2/geocodes/query.json?elevation=2000_&feature_class=P&api-key=your-API-key (notice the underscore after "2000")
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

-   Query to return up to 20 populated places with an elevation less than 3000
    meters.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/semantic/v2/geocodes/query.json?elevation=_3000&feature_class=P&api-key=your-API-key (notice the underscore before "3000")
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

-   Query to return up to 20 populated places with an elevation between 2000 and
    3000 meters.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/semantic/v2/geocodes/query.json?elevation=2000_3000&feature_class=P&api-key=your-API-key
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

-   Query to return up to 20 geocodes of feature\_class P (populated) in the
    United States with population greater than 50,000 people.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/semantic/v2/geocodes/query.json?feature_class=P&country_code=US&population=50000_&api-key=your-API-key
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

-   Query to return the 20 nearest geocodes to lat/lon 38.920833, -94.622222
    with population greater than 100,000 and feature\_class P (populated)

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/semantic/v2/geocodes/query.json?nearby=38.920833,-94.622222&population=100000_&feature_class=P&api-key=your-API-key (no space after comma between lat/lon)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
