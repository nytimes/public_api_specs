The Times Newswire API
======================

With the Times Newswire API, you can get links and metadata for Times articles
and blog posts as soon as they are published on NYTimes.com. The Times Newswire
API provides an up-to-the-minute stream of published items.

For information about changes in the current version, see [Introducing Version 3
of the Times Newswire
API](<http://open.blogs.nytimes.com/2010/05/04/introducing-version-3-of-the-times-newswire-api>) and
the [summary of changes on this
page](<http://developer.nytimes.com/docs/times_newswire_api/#changes>).

**Note:** In this document, curly braces { } indicate required items. Square
brackets [ ] indicate optional items or placeholders.

**The Times Newswire API at a Glance**

**Base URI**

`http://api.nytimes.com/svc/news/{version}/content`

**Scope**

Newly published articles, blog posts and related assets originating at The Times
and The International Herald Tribune. Stories from wire services such as the AP
are not included.  


**HTTP method**

GET

**Response formats**

JSON (`.json`, default)

 

### RECENT NEWS

To get recent news items, use the following URI structure:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/news/{version}/content/{source}/{section}[/time-period][.response-format]?api-key={your-API-key}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 

### SPECIFIC NEWS ITEMS

With this request type, you can "query" the Newswire API for a specific news
item. The response will be a standard Newswire response, but for that item only.

Note: The Newswire cache is cleared regularly, so only recent news items can be
retrieved with this request type. Use the [Article Search
API](<http://developer.nytimes.com/docs/article_search_api>) to get older items.

To get a specific recent news item, use the following URI structure:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/news/{version}/content[.response-format]?url={item-url}&api-key={your-API-key}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 

Examples
--------

These examples use an `.json` extension for illustration purposes. Also, these
examples do not include the required `api-key`parameter. Be sure to include your
API key in your request.

### REQUESTS

**Recent Items**

All available items in all sections:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/news/v3/content/all/all.json
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

All available items in all sections, 15 results starting at item 50:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/news/v3/content/all/all.json?limit=15&offset=50
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

10 items published in the Arts section of the NYT or the IHT in the last 24
hours:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/news/v3/content/all/arts/24.json?limit=10
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Items published in the NYT Business section in the last 72 hours:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/news/v3/content/nyt/business/72.json
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Items published in the Business or World section of the IHT in the last week
(168 hours):

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/news/v3/content/iht/business;world/168.json
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Specific News Item**

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/news/v3/content.json?url=http:\/\/www.nytimes.com\/2010\/04\/27\/books\/27carey.html
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/news/v3/content.json?url=http:%2F%2Fwww.nytimes.com%2F2010%2F04%2F27%2Fbooks%2F27carey.html
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

### RESPONSES

These sample responses are provided for illustration purposes only.

Here is a portion of a JSON response:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
{
   "status":"OK",
   "copyright":"Copyright (c) 2010 The New York Times Company.  All Rights Reserved.",
   "num_results":20,
   "results":[
      {
         "section":"U.S.",
         "title":"Weather Aids Crews in Oil Spill Cleanup Efforts ",
         "abstract":"Calm in the Gulf of Mexico let crews step up multiple 
           efforts to contain the crude oil leaking uncontrollably and spreading 
           toward the coasts of four states.",
         "url":"http:\/\/www.nytimes.com\/2010\/05\/05\/us\/05spill.html",
         "byline":"By IAN URBINA, JUSTIN GILLIS and LIZ ROBBINS",
         "item_type":"Article",
         "source":"The New York Times",
         "updated_date":"2010-05-04T14:28:20-04:00",
         "created_date":"2010-05-04T14:15:44-04:00",
         "published_date":"2010-05-05T00:00:00-04:00",
         "material_type_facet":"News",
         "kicker":"",
         "subheadline":"",
         "des_facet":[
            "Accidents and Safety",
            "Oil (Petroleum) and Gasoline",
            "Explosions",
            "Wells"
         ],
         "org_facet":"",
         "per_facet":"",
         "geo_facet":[
            "Gulf of Mexico",
            "Louisiana"
         ],
         "related_urls":[
            {
               "suggested_link_text":"Gulf Oil Spill Is Bad, but How Bad?",
               "url":"http:\/\/www.nytimes.com\/\/2010\/05\/04\/science\/
                 earth\/04enviro.html"
            }
         ],
         "multimedia":[
            {
               "url":"http:\/\/graphics8.nytimes.com\/images\/2010\/05\/05\/
                 us\/05spillspan-cnd\/05spillspan-cnd-thumbStandard.jpg",
               "format":"Standard Thumbnail",
               "height":75,
               "width":75,
               "type":"image",
               "subtype":"photo",
               "caption":"Local fishermen hired by British Petroleum left the 
                  Mississippi River's main shipping channel on Tuesday to lay out 
                  floating booms in coastal waters to protect sections of vulnerable 
                  shoreline.",
               "copyright":"Nicole Bengiveno\/The New York Times"
            }
         ]
      },
      ...
   ]
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
