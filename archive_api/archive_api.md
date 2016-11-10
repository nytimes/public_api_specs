The Archive API
===============

The **Archive API** provides JSON lists of NYT articles by month.

**Note:** In this document, curly braces { } indicate required items. Square
brackets [ ] indicate optional items or placeholders.

To use the Archive API, you must [sign up for an API key](<http://developer.nytimes.com/apps/register>).
Usage is limited to 2,000 requests per day (rate limits are subject to change).
Please read and agree to the [API Terms of Use](<http://developer.nytimes.com/tou>) and
the [Attribution Guidelines](<http://developer.nytimes.com/attribution>) before you proceed.

Requests
--------

The Archive API uses a [RESTful](<http://en.wikipedia.org/wiki/Representational_State_Transfer>) style.
For general tips on creating a request URI, see [Constructing a Request](<http://developer.nytimes.com/docs/reference/requests>).

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/archive/v1/{year}/{month}.json?api-key={your-api-key}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

###

Examples
--------

Here is a portion of a sample JSON response:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
{
    "response": {
        "meta": {
            "hits": 612,
            "time": 319,
            "offset": 0
        },
        "docs": [
            {
                "web_url": "http://fifthdown.blogs.nytimes.com/2012/01/02/super-bowl-advertising-sells-out/",
                "snippet": "For the Feb. 5 game in Indianapolis, NBC said it sold all of its 30-second ads, at an average of $3.5 million, by Thanksgiving.",
                "lead_paragraph": null,
                "abstract": "For the Feb. 5 game in Indianapolis, NBC said it sold all of its 30-second ads, at an average of $3.5 million, by Thanksgiving.",
                "print_page": null,
                "blog": [],
                "source": "The New York Times",
                "multimedia": [],
                "headline": {
                    "main": "Super Bowl Advertising Sells Out",
                    "kicker": "The Fifth Down"
                },
                "keywords": [],
                "pub_date": "2012-01-02T23:46:50Z",
                "document_type": "blogpost",
                "news_desk": null,
                "section_name": "Sports",
                "subsection_name": "Pro Football",
                "byline": {
                    "person": [
                        {
                            "organization": "",
                            "role": "reported",
                            "firstname": "Richard",
                            "rank": 1,
                            "lastname": "SANDOMIR"
                        }
                    ],
                    "original": "By RICHARD SANDOMIR"
                },
                "type_of_material": "Blog",
                "_id": "54f325df38f0d8529ba360a3",
                "word_count": "345",
                "slideshow_credits": null
            },
            ...
        ]
    },
    "status": "OK",
    "copyright": "Copyright (c) 2013 The New York Times Company.  All Rights Reserved."
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Supported Multimedia Options
----------------------------

Each result, if available, includes a multimedia payload.
We include up to 5 image sizes, whichever are available for that article.

Those image sizes are as follows, with the width and height if those are constant.
Some vary depending on whether the image is landscape or portrait.

| Image Name          | Width | Height |
|---------------------|-------|--------|
| Standard Thumbnail  | 75    | 75     |
| thumbLarge          | 150   | 150    |
| Normal              | 190   |        |
| mediumThreeByTwo210 |       | 210    |
| superJumbo          |       |        |

