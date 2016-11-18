The Archive API
===============

The **Archive API** provides lists of NYT articles by month going back to 1851.

**Note:** In this document, curly braces { } indicate required items. Square
brackets [ ] indicate optional items or placeholders.

To use the Archive API, you must [sign up for an API key](<http://developer.nytimes.com/apps/register>).
Usage is limited to 2,000 requests per day (rate limits are subject to change).
Please read and agree to the [API Terms of Use](<http://developer.nytimes.com/tou>) and
the [Attribution Guidelines](<http://developer.nytimes.com/attribution>) before you proceed.

The API uses a [RESTful](<http://en.wikipedia.org/wiki/Representational_State_Transfer>) style.


**Base URI**

The API is simple, just pass in the year and month and your API key.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/archive/v1/{year}/{month}.json?api-key={your-api-key}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**HTTP method**

GET

**Response format**

JSON


### REQUESTS

NYT articles for November, 2016.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/archive/v1/2016/11.json?api-key={your-api-key}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

NYT articles for September, 1851.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/archive/v1/1851/9.json?api-key={your-api-key}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


### RESPONSES

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
                "web_url": "http://opinionator.blogs.nytimes.com/2012/01/02/it-costs-more-but-is-it-worth-more/",
                "snippet": "Before paying for an expensive cancer treatment, Medicare should demand evidence that it’s more effective than cheaper options.",
                "lead_paragraph": null,
                "abstract": "Before paying for an expensive cancer treatment, Medicare should demand evidence that it’s more effective than cheaper options.",
                "print_page": null,
                "blog": [],
                "source": "The New York Times",
                "multimedia": [
                    {
                        "width": 190,
                        "url": "images/2012/01/02/opinion/02ZEKE-img/02ZEKE-img-thumbWide.jpg",
                        "height": 126,
                        "subtype": "wide",
                        "legacy": {
                            "wide": "images/2012/01/02/opinion/02ZEKE-img/02ZEKE-img-thumbWide.jpg",
                            "wideheight": "126",
                            "widewidth": "190"
                        },
                        "type": "image"
                    },
                    {
                        "width": 600,
                        "url": "images/2012/01/02/opinion/02ZEKE-img/02ZEKE-img-articleLarge-v2.jpg",
                        "height": 400,
                        "subtype": "xlarge",
                        "legacy": {
                            "xlargewidth": "600",
                            "xlarge": "images/2012/01/02/opinion/02ZEKE-img/02ZEKE-img-articleLarge-v2.jpg",
                            "xlargeheight": "400"
                        },
                        "type": "image"
                    },
                    {
                        "width": 75,
                        "url": "images/2012/01/02/opinion/02ZEKE-img/02ZEKE-img-thumbStandard.jpg",
                        "height": 75,
                        "subtype": "thumbnail",
                        "legacy": {
                            "thumbnailheight": "75",
                            "thumbnail": "images/2012/01/02/opinion/02ZEKE-img/02ZEKE-img-thumbStandard.jpg",
                            "thumbnailwidth": "75"
                        },
                        "type": "image"
                    }
                ],
                "headline": {
                    "main": "It Costs More, but Is It Worth More?",
                    "kicker": "Opinionator"
                },
                "keywords": [],
                "pub_date": "2012-01-02T22:18:41Z",
                "document_type": "blogpost",
                "news_desk": null,
                "section_name": "Opinion",
                "subsection_name": null,
                "byline": {
                    "person": [
                        {
                            "firstname": "Ezekiel",
                            "middlename": "J.",
                            "lastname": "EMANUEL",
                            "rank": 1,
                            "role": "reported",
                            "organization": ""
                        },
                        {
                            "organization": "",
                            "role": "reported",
                            "firstname": "Steven",
                            "rank": 2
                        }
                    ],
                    "original": "By EZEKIEL J. EMANUEL and STEVEN D. PEARSON"
                },
                "type_of_material": "Blog",
                "_id": "54f325e938f0d8529ba360a5",
                "word_count": "904",
                "slideshow_credits": null
            },
            ...
        ]
    },
    "status": "OK",
    "copyright": "Copyright (c) 2016 The New York Times Company.  All Rights Reserved."
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

