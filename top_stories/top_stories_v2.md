The Top Stories API
===================

The Top Stories API provides JSON and JSONP lists of articles and associated
images by section.

**Note:** In this document, curly braces { } indicate required items. Square
brackets [ ] indicate optional items or placeholders.

To use the Top Stories API, you must [sign up for an API
key](<http://developer.nytimes.com/apps/register>). Usage is limited to 5,000
requests per day (rate limits are subject to change). Please read and agree to
the [API Terms of Use](<http://developer.nytimes.com/tou>) and
the [Attribution Guidelines](<http://developer.nytimes.com/attribution>) before
you proceed.

Requests
--------

The Top Stories API uses
a [RESTful](<http://en.wikipedia.org/wiki/Representational_State_Transfer>) style.
For general tips on creating a request URI, see [Constructing a
Request](<http://developer.nytimes.com/docs/reference/requests>).


Usage
-----

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/topstories/v1/{section}.{response-format}?api-key={your-api-key}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

*section* - The section name. The possible values are: home, arts, automobiles, books, business, fashion, food, health,
  insider, magazine, movies, national, nyregion, obituaries, opinion, politics, realestate,
  science, sports, sundayreview, technology, theater, tmagazine, travel, upshot, and world.
 
*response-format* - The response format, either json or jsonp.
  With jsonp the callback is set to the section name and 'TopStoriesCallback' (e.g. 'homeTopStoriesCallback').

*api-key* - Your API key.


Examples
--------

Here is a portion of a sample JSON response:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
{
    status: "OK",
    copyright: "Copyright (c) 2014 The New York Times Company. All Rights Reserved.",
    section: "home",
    last_updated: "2014-12-03T12:25:02-05:00",
    num_results: 22,
    results: [
        {
            section: "Business Day",
            subsection: "Economy",
            title: "New Round of Fiscal Battles in Congress Clouds the Economy",
            abstract: "As another round of fiscal brinkmanship looms with Republican control of Congress, the impact on tax policy, government programs and the overall economy could be severe.",
            url: "http://www.nytimes.com/2014/12/03/business/economy/uncertainty-in-washington-poses-long-list-of-economic-perils.html",
            byline: "By JONATHAN WEISMAN",
            item_type: "Article",
            updated_date: "2014-12-02T20:44:18-5:00",
            created_date: "2014-12-02T20:44:20-5:00",
            published_date: "2014-12-03T00:00:00-5:00",
            material_type_facet: "News",
            kicker: "",
            des_facet: [
                "United States Politics and Government",
                "United States Economy",
                "Law and Legislation",
                "Shutdowns (Institutional)"
            ],
            org_facet: [
                "Democratic Party",
                "Republican Party"
            ],
            "per_facet":[  
                "Scott, Keith Lamont (1973-2016)",
                "McCrory, Pat"
            ],
            "geo_facet":[  
                "North Carolina",
                "Charlotte (NC)"
            ],
            multimedia:
            [
                {
                    url: "http://static01.nyt.com/images/2014/12/03/business/Economy/Economy-thumbStandard.jpg",
                    format: "Standard Thumbnail",
                    height: 75,
                    width: 75,
                    type: "image",
                    subtype: "photo",
                    caption: "Jeb Hensarling, chairman of the House Financial Services Committee, has opposed a long-term terrorism insurance bill.",
                    copyright: "Chip Somodevilla/Getty Images"
                },
                ...
            ]
        },
        ...
    ]
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Supported Multimedia Options
----------------------------

Each result, if available, includes a multimedia payload. We include up to 5
image sizes, whichever are available for that article. For almost all of
results, they will all be there. 

Those image sizes are as follows, with the width and height if those are
constant. Some vary depending on whether the image is landscape or portrait. 

| Image Name          | Width | Height |
|---------------------|-------|--------|
| Standard Thumbnail  | 75    | 75     |
| thumbLarge          | 150   | 150    |
| Normal              | 190   |        |
| mediumThreeByTwo210 |       | 210    |
| superJumbo          |       |        |

