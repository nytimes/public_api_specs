The Movie Reviews API
=====================

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

 

Examples
--------

These examples use an `.json` extension for illustration purposes. Also, these
examples do not include the required `api-key` parameter. Be sure to include
your API key in your request.

### REQUESTS

**Search Reviews by Keyword**  
Search for the keyword *big*, with additional limiting parameters:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/movies/v2/reviews/search.json?query=big&thousand-best=Y&opening-date=1930-01-01;2000-01-01
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Reviews and NYT Critics' Picks**  
Most recent NYT Critics' Picks on DVD, results 41-60:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/movies/v2/reviews/dvd-picks.json?order=by-date&offset=40
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Reviews by Reviewer**  
Reviews by Manohla Dargis, ordered by title:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/movies/v2/reviews/reviewer/manohla-dargis/all.json?order=by-title
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Reviewer Details**  
Biographical information for A. O. Scott:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/movies/v2/critics/a-o-scott.json
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 

### RESPONSES

Here is a portion of a JSON response to the
first [example](<http://developer.nytimes.com/docs/movie_reviews_api/#h3-example-request>) (search
on keyword *big*):

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
{
  "status":"OK",
  "copyright":"Copyright (c) 2008 The New York Times Company.  All Rights Reserved.",
  "num_results":8,
  "results":[
     {
        "nyt_movie_id":135855,
        "display_title":"Big Night",
        "sort_name":"Big Night",
        "mpaa_rating":"R",
        "critics_pick":"Y",
        "thousand_best":"Y",
        "byline":"Janet Maslin",
        "headline":"",
        "capsule_review":"Restaurateur brothers stake all on one dinner. Succulent comedy.",
        "summary_short":"",
        "publication_date":"1996-03-29",
        "opening_date":"1996-09-20",
        "dvd_release_date":"1998-04-07",
        "date_updated":"2008-11-04 03:54:15",
        "seo-name":"Big-Night",
        "link":{
           "type":"article",
           "url":"http:\/\/movies.nytimes.com\/movie\/
                   review?res=9501E6DA1539F93AA15750C0A960958260",
           "suggested_link_text":"Read the New York Times Review of Big Night"
        },
        "related_urls":[
           {
              "type":"overview",
              "url":"http:\/\/movies.nytimes.com\/movie\/
                     135855\/Big-Night\/overview",
              "suggested_link_text":"Overview of Big Night"
           },
           {
              "type":"showtimes",
              "url":"http:\/\/movies.nytimes.com\/movie\/
                     135855\/Big-Night\/showtimes",
              "suggested_link_text":"Tickets & Showtimes for Big Night"
           },
           {
              "type":"awards",
              "url":"http:\/\/movies.nytimes.com\/movie\/
                     135855\/Big-Night\/details",
              "suggested_link_text":"Cast, Credits & Awards for Big Night"
           },
           {
              "type":"community",
              "url":"http:\/\/movies.nytimes.com\/movie\/
                     135855\/Big-Night\/rnr",
              "suggested_link_text":"Readers' Reviews of Big Night"
           },
           {
              "type":"trailers",
              "url":"http:\/\/movies.nytimes.com\/movie\/
                     135855\/Big-Night\/trailers",
              "suggested_link_text":"Trailers & Clips for Big Night"
           }
        ]
     },
     {
        "nyt_movie_id":5460,
        "display_title":"The Big Red One",
        "sort_name":"Big Red One, The",
        "mpaa_rating":"",
        "critics_pick":"N",
        "thousand_best":"Y",
        "byline":"Vincent Canby",
        "headline":"There's No Glory in War, Unless You Mean Survival",
        "capsule_review":"WWII infantry combat. Powerful, slashing drama.",
        "summary_short":"",
        "publication_date":"1980-07-18",
        "opening_date":null,
        "dvd_release_date":null,
        "date_updated":"2008-11-04 03:53:53",
        "seo-name":"The-Big-Red-One",
        "link":{
           "type":"article",
           "url":"http:\/\/movies.nytimes.com\/2004\/10\/02\/movies\/
                  02red.html",
           "suggested_link_text":"Read the New York Times Review of The Big Red One"
        },
        "related_urls":[
           {
              "type":"overview",
              "url":"http:\/\/movies.nytimes.com\/movie\/
                     5460\/The-Big-Red-One\/overview",
              "suggested_link_text":"Overview of The Big Red One"
           },
           {
              "type":"showtimes",
              "url":"http:\/\/movies.nytimes.com\/movie\/
                     5460\/The-Big-Red-One\/showtimes",
              "suggested_link_text":"Tickets & Showtimes for The Big Red One"
           },
           {
              "type":"awards",
              "url":"http:\/\/movies.nytimes.com\/movie\/
                     5460\/The-Big-Red-One\/details",
              "suggested_link_text":"Cast, Credits & Awards for The Big Red One"
           },
           {
              "type":"community",
              "url":"http:\/\/movies.nytimes.com\/movie\/
                     5460\/The-Big-Red-One\/rnr",
              "suggested_link_text":"Readers' Reviews of The Big Red One"
           },
           {
              "type":"trailers",
              "url":"http:\/\/movies.nytimes.com\/movie\/
                     5460\/The-Big-Red-One\/trailers",
              "suggested_link_text":"Trailers & Clips for The Big Red One"
           }
        ]
     },
   ...
  ]
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
