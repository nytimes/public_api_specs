The Most Popular API
====================

With the Most Popular API, you can get links and metadata for the blog posts and
articles that are most frequently e-mailed, shared and viewed by NYTimes.com
readers.

**Note:** In this document, curly braces { } indicate required items. Square
brackets [ ] indicate optional items or placeholders.

**The Most Popular API at a Glance**

**Base URI**

`http://api.nytimes.com/svc/mostpopular/{version}/`  
`{mostemailed | mostshared | mostviewed}`

**Scope**

The past 30 days of articles and blog posts originating at The Times and The
International New York Times. Stories from wire services such as the AP are not
included.

**HTTP method**

GET

**Response formats**

JSON (`.json`, default)

 

Examples
--------

These examples use an `.json` extension for illustration purposes. Also, these
examples do not include the required `api-key `parameter. Be sure to include
your API key in your request.

Each example is linked to the Times API Console, which allows you to generate
requests and responses without coding.

### REQUESTS

**Most E-Mailed**

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/mostpopular/v2/mostemailed/all-sections/1.json
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Most Shared**

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/mostpopular/v2/mostshared/business/facebook;twitter/7.json
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Most Viewed**

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/mostpopular/v2/mostviewed/arts/30.json?offset=40
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

### RESPONSES

These responses are provided for illustration purposes only.

Here is a portion of a sample JSON response to the most e-mailed example:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
{
   "status":"OK",
   "copyright":"Copyright (c) 2010 The New York Times Company.  All Rights Reserved.",
   "num_results":1863,
   "results":[
      {
         "url":"http:\/\/www.nytimes.com\/2010\/08\/31\/science\/31bedbug.html",
         "column":"",
         "section":"Science",
         "byline":"By DONALD G. McNEIL Jr.",
         "title":"They Crawl, They Bite, They Baffle Scientists",
         "abstract":"Ask experts why bedbugs disappeared for 40 years, why they came
        back, why they don't spread disease, and you hear one answer:
        "Good question.""",
         "published_date":"2010-08-31",
         "source":"The New York Times",
         "des_facet":[
            "PESTICIDES",
            "SCIENCE AND TECHNOLOGY",
            "BEDBUGS"
         ],
         "org_facet":"",
         "per_facet":"",
         "geo_facet":[
            "CENTERS FOR DISEASE CONTROL AND PREVENTION"
         ],
         "media":[
            {
               "type":"image",
               "subtype":"photo",
               "caption":"THE ICK FACTOR  The lab of Stephen A. Kells, 
        a University of Minnesota entomologist. Bedbugs are not known to
        transmit disease.",
               "copyright":"Allen Brisson-Smith for The New York Times",
               "media-metadata":[
                  {
                     "url":"http:\/\/graphics8.nytimes.com\/images\/2010\/08\/31\/
            science\/31bedbug\/31bedbugspan-thumbStandard.jpg",
                     "format":"Standard Thumbnail",
                     "height":75,
                     "width":75
                  }
               ]
            },
            {
               "type":"image",
               "subtype":"photo",
               "caption":"LITTLE RESEARCH  Stephen A. Kells is one of the few
             specializing in bedbugs.",
               "copyright":"Allen Brisson-Smith for The New York Times",
               "media-metadata":[
                  {
                     "url":"http:\/\/graphics8.nytimes.com\/images\/
               2010\/08\/31\/science\/31bedbug2\/31bedbug2-thumbStandard.jpg",
                     "format":"Standard Thumbnail",
                     "height":75,
                     "width":75
                  }
               ]
            }
         ]
      },
    ...
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Here is a portion of a sample JSON response to the most shared example:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
{
   "status":"OK",
   "copyright":"Copyright (c) 2010 The New York Times Company.  All Rights Reserved.",
   "num_results":94,
   "results":[
      {
         "url":"http:\/\/www.nytimes.com\/2010\/08\/25\/business\/25econ.html",
         "column":"",
         "section":"Business Day",
         "byline":"By DAVID STREITFELD",
         "title":"U.S. Home Sales at Lowest Level in More Than a Decade",
         "abstract":"Sales of previously occupied homes plunged in July despite low 
        mortgage rates, in part because of an expired tax break, an industry
        group reported.",
         "published_date":"2010-08-25",
         "source":"The New York Times",
         "des_facet":[
            "Housing and Real Estate",
            "United States Economy",
            "Sales"
         ],
         "org_facet":"",
         "per_facet":"",
         "geo_facet":"",
         "media":[
            {
               "type":"image",
               "subtype":"photo",
               "caption":"A home for sale in Los Angeles. July home sales in the United
           States were down 27.2 percent from June.",
               "copyright":"Kevork Djansezian\/Getty Images",
               "media-metadata":[
                  {
                     "url":"http:\/\/graphics8.nytimes.com\/images\/2010\/08\/25\
              /business\/5markets1\/25markets1-thumbStandard.jpg",
                     "format":"Standard Thumbnail",
                     "height":75,
                     "width":75
                  }
               ]
            }
         ]
      },
    ...
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 

Here is a portion of a sample JSON response to the most viewed example:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
{
   "status":"OK",
   "copyright":"Copyright (c) 2010 The New York Times Company.  All Rights Reserved.",
   "num_results":57,
   "results":[
      {
         "url":"http:\/\/www.nytimes.com\/2010\/07\/30\/arts\/design\/
       30eakins.html",
         "column":"Art Review",
         "section":"Arts",
         "byline":"By KAREN ROSENBERG",
         "title":"Deft Surgery for a Painting Under the Scalpel",
         "abstract":"An exhibition at the Philadelphia Museum of Art shows Thomas
       Eakins's "Gross Clinic," an 1875 masterpiece that has recently
       been restored.",
         "published_date":"2010-07-30",
         "source":"The New York Times",
         "des_facet":[
            "Art"
         ],
         "org_facet":[
            "Philadelphia Museum of Art"
         ],
         "per_facet":[
            "Eakins, Thomas"
         ],
         "geo_facet":"",
         "media":[
            {
               "type":"image",
               "subtype":"photo",
               "caption":"\u201cThe Gross Clinic\u201d as it appeared before it was restored.",
               "copyright":"Philadelphia Museum of Art",
               "media-metadata":[
                  {
                     "url":"http:\/\/graphics8.nytimes.com\/images\/2010\/07\/30\/arts\/
                       30EAKINS\/EAKINS-thumbStandard.jpg",
                     "format":"Standard Thumbnail",
                     "height":75,
                     "width":75
                  },
                  {
                     "url":"http:\/\/graphics8.nytimes.com\/images\/
                       2010\/07\/30\/arts\/30EAKINS\/EAKINS-thumbStandard.jpg",
                     "format":"Standard Thumbnail",
                     "height":75,
                     "width":75
                  }
               ]
            }
         ]
      },
     ...
   ]
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
