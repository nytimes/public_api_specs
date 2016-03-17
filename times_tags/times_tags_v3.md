The TimesTags API
=================

**Note:** This document describes version 1, which is the current version of the
TimesTags API.

With the TimesTags API, you can mine the riches of the New York Times tag set.
The TimesTags service matches your query to the controlled vocabularies that
fuel NYTimes.com metadata. You supply a string of characters, and the service
returns a ranked list of suggested terms.

**Note:** In this document, curly braces { } indicate required variables. Square
brackets [ ] indicate optional parameters or placeholders.

**The TimesTags API at a Glance**

**Base URI**

`http://api.nytimes.com/svc/suggest/v1/timestags`

**Scope**

New York Times tags used to build [Times
Topics](<http://topics.nytimes.com/top/reference/timestopics/index.html>) pages,
reflecting the expertise of Times indexers since 1851.
See [Tags](<http://developer.nytimes.com/docs/timestags_api/#h3-tags>) for more
information on the scope.

**HTTP method**

GET

**Response formats**

JSON (`.json`)

 

Why Use TimesTags?
------------------

The TimesTags service can help you build a tag set, standardize names of people
and organizations, or identify subjects that are currently making news.
Information architects and librarians may also wish to compare Times tags
to [Library of Congress subject headings](<http://authorities.loc.gov/>) and
other classification systems.

Additionally, the terms you retrieve with the TimesTags API can be used with the
Times Article Search API.

For general thoughts on the potential of metadata, see the post [Messing Around
With
Metadata](<http://open.nytimes.com/2007/10/23/messing-around-with-metadata/>) on
our Open blog. For background information on Times indexing practices, see the
article [Dusting Off the Search
Engine](<http://query.nytimes.com/gst/fullpage.html?res=990CE7DF123BF934A25752C1A9679C8B63>).
And for more on the power of auto-suggest methods, see [Enriching Search:
Auto-Suggest in
IE8](<http://open.blogs.nytimes.com/2008/10/06/enriching-search-auto-suggest-in-ie8/>).

Requests
--------

TimesTags requests use the following URI structure:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/suggest/v1/timestags?query={search-string}&[optional-param1=value1]&[...]&api-key={your-api-key}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 

### TAGS

The TimesTags API operates on a subset of Times tags: those tags used to
create [Times
Topics](<http://topics.nytimes.com/top/reference/timestopics/index.html>) pages.
The subset includes approximately 27,000 tags:

>   `(Des)`: 3,000 terms  
>   `(Geo)`: 1,500 terms  
>   `(Org)`: 7,500 terms  
>   `(Per)`: 15,000 terms

In responses, tags are ranked according to how frequently they are used (they
are listed in descending order). For example, if your query is *palin*, the most
commonly used matching tag is *Palin, Sarah (Per)*. The ranking reflects current
usage, so tags will move down the list as their “newsiness” declines. New tags
are added regularly.

Your query is matched to the beginning of each word in each tag. For
example, `query=son&filter=(Per)` returns all of the following tags:

>   `Sondheim, Stephen`  
>   `Sontag, Susan`  
>   `Bono, Sonny`

Each tag includes a dictionary abbreviation in parentheses. See the [description
of
the filter parameter](<http://developer.nytimes.com/docs/timestags_api/#h3-optional>) for
more information about Times dictionaries. The dictionary abbreviations are also
used in `<meta>` tags on NYTimes.com.

### FORMAT

The TimesTags service returns JSON, with a `content-type` of `text/plain`. The
JSON response format is ideal for browser auto-suggest applications.

### TIMES STYLE

The following notes may help you formulate your query:

-   Times tags do not use special characters (accents, diacritics, etc.).

-   Refer to [The New York Times Manual of Style and
    Usage](<http://www.nytstore.com/The-New-York-Times-Manual-of-Style-and-Usage_p_6879.html>) for
    preferred terms and general style tips.

**Personal Names**

Personal names are in the format *LastName, FirstName MiddleInitial.* Middle
initials and appellations (Jr/Sr) do not include periods.

>   Example: `Albee, Edward (Per)`

Exceptions to the standard order for personal names:

-   For names in which the family name precedes the given name (such as Chinese,
    Korean and Thai names), the order is reversed.

-   For royal names that do not include family names, only the given name is
    included in the standardized name.

**Organization Names**

Organization names that are derived from personal names are in the
format *LastName, FirstName*.

>   Example: `Gates, Bill and Melinda, Foundation (Org)`

Company names generally use abbreviations such as *Corp*, *Co* and *Inc*, but
may vary.

 

Examples
--------

These examples do not include the required `api-key` parameter. Be sure to
include your API key in your request.

### REQUESTS

Get tags based on a few characters, searching all dictionaries:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/suggest/v1/timestags?query=cel
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Get names of people and organizations:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/suggest/v1/timestags?query=edwards&filter=(Per),(Org)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Get tags corresponding to a country, as a geographical unit and as a subject:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/suggest/v1/timestags?query=french&filter=(Geo),(Des)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Get the top five descriptive terms containing the characters `econ`:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/suggest/v1/timestags?query=econ&filter=(Des)&max=5
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

### RESPONSES

Here is a sample response to the first example given above (`cel`):

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
{
   "cel",[
      "Cellular Telephones (Des)",
      "Boston Celtics (Org)",
      "Celebrities (Des)",
      "Stem Cells (Des)",
      "Celebrex (Drug) (Des)",
      "Sickle Cell Anemia (Des)",
      "Dion, Celine (Per)",
      "Cruz, Celia (Per)",
      "Basements and Cellars (Des)",
      "Cellucci, Paul (Per)" 
   ]
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Here is a sample response to the `french` example:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
{
   "french",[
      "France (Geo)",
      "French Open (Tennis) (Des)",
      "French Language (Des)",
      "French Guiana (Geo)",
      "St Barthelemy (French West Indies) (Geo)",
      "French Alps (Geo)",
      "French Fries (Des)",
      "French Polynesia (France) (Geo)",
      "French Southern Territories (Geo)" 
   ]
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Here is a sample response to the `econ` example:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
{
   "econ",[
      "Economic Conditions and Trends (Des)",
      "United States Economy (Des)",
      "Embargoes and Economic Sanctions (Des)",
      "Economics (Des)",
      "Economic Stimulus Act of 2008 (Des)" 
   ]
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 
-
