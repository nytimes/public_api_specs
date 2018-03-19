# The Movie Reviews API

With the Movie Reviews API, you can search New York Times movie reviews by
keyword and get lists of NYT Critics' Picks.

**Note:** In this document, curly braces { } indicate required items. Square
brackets [ ] indicate optional items or placeholders.

**The Movie Reviews API at a Glance**

**Base URI**

`http://api.nytimes.com/svc/movies/{version}/{reviews | critics}`

**Scope**

Movie reviews by New York Times critics

**HTTP method**

GET

**Response formats**

JSON (`.json`, default)



## Examples

These examples use an `.json` extension for illustration purposes. Also, these
examples do not include the required `api-key` parameter. Be sure to include
your API key in your request.

### REQUESTS

**Search Reviews by Keyword**
Search for the keyword *big*, with additional limiting parameters:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/movies/v2/reviews/search.json?query=big&opening-date=1930-01-01;2000-01-01
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Reviews and NYT Critics' Picks**
Most recent NYT Critics' Picks, results 41-60:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/movies/v2/reviews/search.json?critics-pick=Y&order=by-date&offset=40
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


**Reviewer Details**
Biographical information for A. O. Scott:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/movies/v2/critics/A.%20O.%20Scott.json
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~



### RESPONSES

Here is a portion of a JSON response to the
first [example](<http://developer.nytimes.com/docs/movie_reviews_api/#h3-example-request>) (search
on keyword *big*):

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
{
  "status":"OK",
  "copyright":"Copyright (c) 2008 The New York Times Company.  All Rights Reserved.",
  "has_more":false
  "num_results":8,
  "results":[
     {
        "display_title":"Big Night",
        "sort_name":"Big Night",
        "mpaa_rating":"R",
        "critics_pick":"Y",
        "byline":"Janet Maslin",
        "headline":"",
        "capsule_review":"Restaurateur brothers stake all on one dinner. Succulent comedy.",
        "summary_short":"",
        "publication_date":"1996-03-29",
        "opening_date":"1996-09-20",
        "date_updated":"2008-11-04 03:54:15",
        "link":{
           "type":"article",
           "url":"http:\/\/movies.nytimes.com\/movie\/
                   review?res=9501E6DA1539F93AA15750C0A960958260",
           "suggested_link_text":"Read the New York Times Review of Big Night"
        }
     }
   ...
  ]
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


### Pagination

Use *offset* to paginate thru results, 20 at a time (offset=0, offset=20, ...).  The *has_more* field indicates if there are more results to get.
