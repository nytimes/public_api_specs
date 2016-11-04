The Archive API
===============

The **Archive API** provides JSON lists of NYT articles by month.

**Note:** In this document, curly braces { } indicate required items. Square
brackets [ ] indicate optional items or placeholders.

To use the Archive API, you must [sign up for an API key](<http://developer.nytimes.com/apps/register>).
Usage is limited to 5,000 requests per day (rate limits are subject to change).
Please read and agree to the [API Terms of Use](<http://developer.nytimes.com/Api_terms_of_use>) and
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

