Constructing a Search Query
---------------------------

You can get useful results from the Article Search API with a simple query. But
you can also use filters and facets to extend the functionality of the API.

### FILTERING YOUR SEARCH

Use filters to narrow the scope of your search. You can specify the fields and
the values that your query will be filtered on.

Filter query uses standard [Lucene
syntax](<http://www.lucenetutorial.com/lucene-query-syntax.html>); separate the
filter field name and value with a colon, and surround multiple values with
parentheses: `field-name:("value1" "value2" ... "value n")`. The default
connector for values in parentheses is OR. If you declare an explicit boolean
value, it must be capitalized.

You can filter on multiple values and fields: `field-nameA:("value1") AND
field-nameB:("value2" "value3"). `For a list of all fields you can filter on,
see the [Filter Query
Fields](<http://developer.nytimes.com/docs/read/article_search_api_v2#filters-fields>) table.


**Pagination**

The Article Search API returns a max of 10 results at a time.
The meta node in the response contains the total number of matches ("hits") and the current offset.
Use the page query parameter to paginate thru results (page=0 for results 1-10, page=1 for 11-20, ...).
You can paginate thru up to 100 pages (1,000 results).
If you get too many results try filtering by date range.


**Filter Query Examples**

Restrict your search to articles with The New York Times as the source:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
 &fq=source:("The New York Times")
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Restrict your search to articles from either the Sports or Foreign desk:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
 &fq=news_desk:("Sports" "Foreign")
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Restrict your search to articles that are about New York City and from the
Sports desk:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
&fq=news_desk:("Sports") AND glocations:("NEW YORK CITY")
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

If you do not specify a field, the scope of the filter query will look for
matches in the body, headline and byline. The example below will restrict your
search to articles with The New York Times in the body, headline or byline:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
 &fq=The New York Times
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Filter Query Fields**

| **Field**                   | **Behavior**                  |
|-----------------------------|-------------------------------|
| body                        | Multiple tokens               |
| body.search                 | Left-edge n-grams             |
| creative\_works             | Single token                  |
| creative\_works.contains    | Multiple tokens               |
| day\_of\_week               | Single token                  |
| document\_type              | Case-sensitive exact match    |
| glocations                  | Single token                  |
| glocations.contains         | Multiple tokens               |
| headline                    | Multiple tokens               |
| headline.search             | Left-edge n-grams             |
| kicker                      | Single token                  |
| kicker.contains             | Multiple tokens               |
| news\_desk                  | Single token                  |
| news\_desk.contains         | Multiple tokens               |
| organizations               | Single token                  |
| organizations.contains      | Multiple tokens               |
| persons                     | Single token                  |
| persons.contains            | Multiple tokens               |
| pub\_date                   | Timestamp (YYYY-MM-DD)        |
| pub\_year                   | Integer                       |
| secpg                       | Multiple tokens               |
| source                      | Single token                  |
| source.contains             | Multiple tokens               |
| subject                     | Single token                  |
| subject.contains            | Multiple tokens               |
| section\_name               | Single token                  |
| section\_name.contains      | Multiple tokens               |
| type\_of\_material          | Single token                  |
| type\_of\_material.contains | Multiple tokens               |
| web\_url                    | Single token (case-sensitive) |
| word\_count                 | Integer                       |

 

**News Desk Values**

-   Adventure Sports

-   Arts & Leisure

-   Arts

-   Automobiles

-   Blogs

-   Books

-   Booming

-   Business Day

-   Business

-   Cars

-   Circuits

-   Classifieds

-   Connecticut

-   Crosswords & Games

-   Culture

-   DealBook

-   Dining

-   Editorial

-   Education

-   Energy

-   Entrepreneurs

-   Environment

-   Escapes

-   Fashion & Style

-   Fashion

-   Favorites

-   Financial

-   Flight

-   Food

-   Foreign

-   Generations

-   Giving

-   Global Home

-   Health & Fitness

-   Health

-   Home & Garden

-   Home

-   Jobs

-   Key

-   Letters

-   Long Island

-   Magazine

-   Market Place

-   Media

-   Men's Health

-   Metro

-   Metropolitan

-   Movies

-   Museums

-   National

-   Nesting

-   Obits

-   Obituaries

-   Obituary

-   OpEd

-   Opinion

-   Outlook

-   Personal Investing

-   Personal Tech

-   Play

-   Politics

-   Regionals

-   Retail

-   Retirement

-   Science

-   Small Business

-   Society

-   Sports

-   Style

-   Sunday Business

-   Sunday Review

-   Sunday Styles

-   T Magazine

-   T Style

-   Technology

-   Teens

-   Television

-   The Arts

-   The Business of Green

-   The City Desk

-   The City

-   The Marathon

-   The Millennium

-   The Natural World

-   The Upshot

-   The Weekend

-   The Year in Pictures

-   Theater

-   Then & Now

-   Thursday Styles

-   Times Topics

-   Travel

-   U.S.

-   Universal

-   Upshot

-   UrbanEye

-   Vacation

-   Washington

-   Wealth

-   Weather

-   Week in Review

-   Week

-   Weekend

-   Westchester

-   Wireless Living

-   Women's Health

-   Working

-   Workplace

-   World

-   Your Money

**Section Name Values**

-   Arts

-   Automobiles

-   Autos

-   Blogs

-   Books

-   Booming

-   Business

-   Business Day

-   Corrections

-   Crosswords & Games

-   Crosswords/Games

-   Dining & Wine

-   Dining and Wine

-   Editors' Notes

-   Education

-   Fashion & Style

-   Food

-   Front Page

-   Giving

-   Global Home

-   Great Homes & Destinations

-   Great Homes and Destinations

-   Health

-   Home & Garden

-   Home and Garden

-   International Home

-   Job Market

-   Learning

-   Magazine

-   Movies

-   Multimedia

-   Multimedia/Photos

-   N.Y. / Region

-   N.Y./Region

-   NYRegion

-   NYT Now

-   National

-   New York

-   New York and Region

-   Obituaries

-   Olympics

-   Open

-   Opinion

-   Paid Death Notices

-   Public Editor

-   Real Estate

-   Science

-   Sports

-   Style

-   Sunday Magazine

-   Sunday Review

-   T Magazine

-   T:Style

-   Technology

-   The Public Editor

-   The Upshot

-   Theater

-   Times Topics

-   TimesMachine

-   Today's Headlines

-   Topics

-   Travel

-   U.S.

-   Universal

-   UrbanEye

-   Washington

-   Week in Review

-   World

-   Your Money

**Type of Material Values**

-   Addendum

-   An Analysis

-   An Appraisal

-   Article

-   Banner

-   Biography

-   Birth Notice

-   Blog

-   Brief

-   Caption

-   Chronology

-   Column

-   Correction

-   Economic Analysis

-   Editorial

-   Editorial Cartoon

-   Editors' Note

-   First Chapter

-   Front Page

-   Glossary

-   Interactive Feature

-   Interactive Graphic

-   Interview

-   Letter

-   List

-   Marriage Announcement

-   Military Analysis

-   News

-   News Analysis

-   Newsletter

-   Obituary

-   Obituary (Obit)

-   Op-Ed

-   Paid Death Notice

-   Postscript

-   Premium

-   Question

-   Quote

-   Recipe

-   Review

-   Schedule

-   SectionFront

-   Series

-   Slideshow

-   Special Report

-   Statistics

-   Summary

-   Text

-   Video

-   Web Log

### USING FACETS

Use facets to view the relative importance of certain fields to a search term,
and gain insight about how to best refine your queries and filter your search
results.

The following fields can be used as facet
fields: `source`, `section_name`, `document_type`, `type_of_material` and`day_of_week`.

Specify facets using the `facet_fields` parameter. The response will contain an
array with a count for the five terms that have the highest count for each
facet. For example, including the following in your request will add a facet
array with a count for the top five days of the week to the response:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
&facet_field=day_of_week
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

By default, facet counts ignore all filters and return the count for all results
of a query. For the following queries, the facet count in each response will be
identical, even though the results returned in one set is restricted to articles
published in 2012: 

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
q=obama&facet_field=source&begin_date=20120101&end_date=20121231
q=obama&facet_field=source
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

You can force facet counts to respect filters by setting `facet_filter=true`.
Facet counts will be restricted based on any filters you have specified (this
includes both explicit filter queries set using the `fq` parameter and implicit
filters like `begin_date`).

The facet array in the response to the
query`q=obama&facet_field=source&begin_date=20120101&end_date=20121231`:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
facets": {

    "source": {
        "_type": "terms",
        "missing": 524,
        "total": 83121,
        "other": 317,
        "terms": [
            {
                "term": "The New York Times",
                "count": 68530
            },
            {
                "term": "AP",
                "count": 7705
            },
            {
                "term": "Reuters",
                "count": 4969
            },
            {
                "term": "International Herald Tribune",
                "count": 1464
            },
            {
                "term": "",
                "count": 136
            }
        ]
    }

}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

If you set facet\_filter to true the facet array for the
query`q=obama&facet_field=source&begin_date=20120101&end_date=20121231&facet_filter=true` will
only count facet occurences in 2012:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
facets": {

    "source": {
        "_type": "terms",
        "missing": 192,
        "total": 22596,
        "other": 139,
        "terms": [
            {
                "term": "The New York Times",
                "count": 14812
            },
            {
                "term": "AP",
                "count": 4286
            },
            {
                "term": "Reuters",
                "count": 3025
            },
            {
                "term": "International Herald Tribune",
                "count": 226
            },
            {
                "term": "AP; The New York Times",
                "count": 108
            }
        ]
    }

}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Examples
--------

These examples do not include the required `api-key` parameter. Be sure to
include your API key in your request.

### REQUESTS

Searches for documents containing 'new york times' and returns results 20-29.
Results are sorted by oldest to newest:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/search/v2/articlesearch.json?q=new+york+times&page=2&sort=oldest&api-key=####
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Retrieves all documents, but only returns those published on 01/01/2012 and
containing 'romney.' Facet count will be returned for 'day\_of\_week' and will
be reflective of all documents (i.e., the date range filter and filter query do
not affect facet counts):

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/search/v2/articlesearch.json?fq=romney&facet_field=day_of_week&begin_date=20120101&end_date=20120101&api-key=####
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

### RESPONSES

Here is a portion of a sample JSON response to the second example:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
{

    "response": {
        "meta": {
            "hits": 25,
            "time": 332,
            "offset": 0
        },
        "docs": [
            {
                "web_url": "http://thecaucus.blogs.nytimes.com/2012/01/01/virginia-attorney-general-backs-off-ballot-proposal/",
                "snippet": "Virginia's attorney general on Sunday backed off of a proposal to loosen the state's ballot access rules to allow more Republican presidential candidates to qualify.",
                "lead_paragraph": "DES MOINES -- Virginia's attorney general on Sunday backed off of a proposal to loosen the state's ballot access rules to allow more Republican presidential candidates to qualify.",
                "abstract": "Virginia's attorney general on Sunday backed off of a proposal to loosen the state's ballot access rules to allow more Republican presidential candidates to qualify.",
                "print_page": null,
                "blog": [ ],
                "source": "The New York Times",
                "multimedia": [ ],
                "headline": {
                    "main": "Virginia Attorney General Backs Off Ballot Proposal",
                    "kicker": "The Caucus"
                },
                "keywords": [
                    {
                        "rank": "4",
                        "name": "persons",
                        "value": "Paul, Ron"
                    },
                    {
                        "rank": "3",
                        "name": "persons",
                        "value": "Gingrich, Newt"
                    },
                    {
                        "rank": "2",
                        "name": "persons",
                        "value": "Cuccinelli, Kenneth T II"
                    },
                    {
                        "rank": "5",
                        "name": "persons",
                        "value": "Perry, Rick"
                    },
                    {
                        "rank": "1",
                        "name": "type_of_material",
                        "value": "News"
                    },
                    {
                        "rank": "6",
                        "name": "persons",
                        "value": "Romney, Mitt"
                    },
                    {
                        "rank": "7",
                        "name": "subject",
                        "value": "Presidential Election of 2012"
                    },
                    {
                        "rank": "8",
                        "name": "organizations",
                        "value": "Republican Party"
                    },
                    {
                        "rank": "9",
                        "name": "glocations",
                        "value": "Virginia"
                    }
                ],
                "pub_date": "2012-01-01T18:46:02Z",
                "document_type": "blogpost",
                "news_desk": null,
                "section_name": "U.S.",
                "byline": {
                    "person": [
                        {
                            "organization": "",
                            "role": "reported",
                            "rank": 1
                        }
                    ],
                    "original": "By MICHAEL D. SHEAR"
                },
                "word_count": 185,
                "type_of_material": "Blog",
                "_id": "4fd3a2548eb7c8105d8ea27e"
            },
            ...
            {
                "web_url": "http://www.nytimes.com/2012/01/01/us/politics/republicans-wage-hidden-ground-war-in-iowa.html",
                "snippet": "Far from candidates’ spotlights, hundreds of aides and volunteers are waging an unglamorous ground war unfolding with hidden intensity.",
                "lead_paragraph": "DES MOINES -- A few days before the Iowa caucuses, Newt Gingrich's campaign headquarters just outside the city is a spectacle of pre-computer-age disorder, with volunteers rushing voter updates across the room on yellow Post-it notes. At the offices of Mitt Romney, who has built a ground organization aimed at matching the intensity of his television advertising barrage, aides are methodically analyzing data on each voter to create the perfect pitch: those worried about illegal immigration, for example, are invited to join a conference call with a border county sheriff in Arizona.",
                "abstract": "Hundreds of campaign staff members, aides and volunteers are waging an unglamorous ground war that will largely determine the outcome of the Republican presidential caucuses in Iowa; in the closing hours before the caucuses, the tedious and time-consuming work of identifying voters and persuading them to show up at the caucuses could make the difference among Republican who cannot seem to make up their minds. Photos (L)d",
                "print_page": "1",
                "blog": [ ],
                "source": "The New York Times",
                "multimedia": [
                    {
                        "url": "images/2012/01/01/us/01ground-span/01ground-span-thumbStandard.jpg",
                        "subtype": "thumbnail",
                        "legacy": {
                            "hasthumbnail": "Y",
                            "thumbnailheight": 75,
                            "thumbnail": "images/2012/01/01/us/01ground-span/01ground-span-thumbStandard.jpg"
                        },
                        "type": "image",
                        "height": 75
                    },
                    {
                        "width": 600,
                        "url": "images/2012/01/01/us/01ground-span/01ground-span-articleLarge.jpg",
                        "height": 370,
                        "subtype": "xlarge",
                        "legacy": {
                            "xlargewidth": 600,
                            "xlargeheight": 370,
                            "xlarge": "images/2012/01/01/us/01ground-span/01ground-span-articleLarge.jpg",
                            "hasxlarge": "Y"
                        },
                        "type": "image"
                    }
                ],
                "headline": {
                    "main": "Over Phones and Greasy Pizza, a Battle for Iowa"
                },
                "keywords": [
                    {
                        "name": "persons",
                        "value": "BACHMANN, MICHELE M"
                    },
                    {
                        "name": "persons",
                        "value": "SANTORUM, RICK"
                    },
                    {
                        "name": "persons",
                        "value": "PERRY, RICK"
                    },
                    {
                        "name": "persons",
                        "value": "PAUL, RON"
                    },
                    {
                        "name": "persons",
                        "value": "GINGRICH, NEWT"
                    },
                    {
                        "name": "persons",
                        "value": "ROMNEY, MITT"
                    },
                    {
                        "name": "persons",
                        "value": "SULZBERGER A G"
                    },
                    {
                        "name": "glocations",
                        "value": "IOWA"
                    },
                    {
                        "name": "organizations",
                        "value": "REPUBLICAN PARTY"
                    },
                    {
                        "name": "subject",
                        "value": "PRIMARIES AND CAUCUSES"
                    },
                    {
                        "name": "subject",
                        "value": "PRESIDENTIAL ELECTION OF 2012"
                    }
                ],
                "pub_date": "2012-01-01T00:00:00Z",
                "document_type": "article",
                "news_desk": "National Desk",
                "section_name": "Front Page; U.S.",
                "byline": {
                    "person": [
                        {
                            "firstname": "A.",
                            "middlename": "G.",
                            "lastname": "SULZBERGER",
                            "rank": 1,
                            "role": "reported",
                            "organization": ""
                        },
                        {
                            "organization": "",
                            "role": "reported",
                            "firstname": "Michael",
                            "rank": 2,
                            "lastname": "BARBARO"
                        }
                    ],
                    "original": "By A. G. SULZBERGER and MICHAEL BARBARO"
                },
                "word_count": 2365,
                "type_of_material": "News",
                "_id": "4fd2ba9a8eb7c8105d8b0a8b"
            }
        ],
        "facets": {
            "day_of_week": {
                "_type": "terms",
                "missing": 1871790,
                "total": 13098462,
                "other": 3005891,
                "terms": [
                    {
                        "term": "Sunday",
                        "count": 3122347
                    },
                    {
                        "term": "Thursday",
                        "count": 1775373
                    },
                    {
                        "term": "Friday",
                        "count": 1747040
                    },
                    {
                        "term": "Wednesday",
                        "count": 1734063
                    },
                    {
                        "term": "Tuesday",
                        "count": 1713748
                    }
                ]
            }
        }
    }

}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


**Limit Fields in Response**

You can limit the number fields returned in the response with the `fl` parameter.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
 &fl=web_url
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
