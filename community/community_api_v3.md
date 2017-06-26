The Community API v3
====================

With the Community API, you can get user-generated NYTimes.com content. The
current release includes article comments and readers' reviews of movies. (Other
types of user-generated content will be available in a later version.)

**The Community API at a Glance**

**Base URI**

`http://api.nytimes.com/svc/community/{version}/user-content/{resource-type}`

**Scope**

NYTimes.com user-generated content, currently comments on
articles.<http://dotearth.blogs.nytimes.com/> For movies, "comments" are
readers' reviews.

**HTTP method**

GET

**Response formats**

JSON

To use the Community API, you must [sign up for an API key](</signup>). Usage is
limited to 5000 requests per day (rate limits are subject to change). Please
read and agree to the [API Terms of Use](</tau>) and the [Attribution
Guidelines](</attribution>) before you proceed.

 

Requests
--------

The Community service uses
a [RESTful](<http://en.wikipedia.org/wiki/Representational_State_Transfer>) style.
Four request types are available: [Get recent
comments](<http://developer.nytimes.com/docs/community_api/The_Community_API_v3/#commentsRecent>), [get
comments by
date](<http://developer.nytimes.com/docs/community_api/The_Community_API_v3/#commentsDate>), [get
comments by user
ID](<http://developer.nytimes.com/docs/community_api/The_Community_API_v3/#commentsUser>) and [get
comments by
URL](<http://developer.nytimes.com/docs/community_api/The_Community_API_v3/#commentsURL>).

For general tips on creating a request URI, see [Constructing a
Request](<http://developer.nytimes.com/docs/reference/requests>).

### RECENT COMMENTS

To retrieve the most recent user comments, use the following URI structure:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/community/{version}/user-content/recent.json?api-key={your-API-key}[&optional-param1=value1][...]
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 

### COMMENTS BY DATE

To retrieve comments posted on a specific date, use the following URI structure:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/community/{version}/user-content/by-date.json?api-key={your-API-key}&date={YYYY-MM-DD}[&offset=int]
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 

### COMMENTS BY USER ID

To retrieve comments by a specific NYTimes.com user, use the following URI
structure:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/community/{version}/user-content/user.json?api-key={your-API-key}&userID={<int>}[&offset=<int>][&url={url-to-match}]
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 

### COMMENTS BY URL

To retrieve editor selected comments associated with a specific NYTimes.com URL, use the
following URI structure:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/community/{version}/user-content/url.json?api-key={your-API-key}&url={url}[&offset=int]
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


### Pagination

Use the offset query parameter to paginate thru the results, 25 comments at a time.  Use offset=0 to get the first 25 comments, offset=25 to get the next 25 comments, ...

 

Responses
---------

An HTTP response code of 200 (OK) is returned for all requests that are
successfully understood and processed. See
the [Errors](<http://developer.nytimes.com/docs/community_api/The_Community_API_v3/#h2-errors>)section
for additional response codes.

### FORMATS

The response format is [JSON](<http://json.org/>).

### DATA RETURNED

-   All comment records include the URL to the Times article on which the
    comments were made.

-   For movie overview URLs, the "comments" returned are readers' reviews of the
    movie.

-   Date fields are in [Unix/UTC
    format](<http://en.wikipedia.org/wiki/Unix_time>).

 

 

### URL MATCHING

When you [get comments by
URL](<http://developer.nytimes.com/docs/community_api/The_Community_API_v3/#commentsURL>),
you can specify whether to retrieve exact matches or closest stem matches. URL
matching is attempted at each segment of the path, as illustrated by the
following example:

>   First match attempt: `http://www.nytimes.com/2008/10/23/section/article*`  
>   Second match attempt: `http://www.nytimes.com/2008/10/23/section/*`  
>   Third match attempt: `http://www.nytimes.com/2008/10/23/*`

In result sets, matching URLs are sorted alphabetically.

(Note: not all NYTimes.com URLs follow the date-section-article structure. )

 

Examples
--------

These examples are for illustration purposes. Also, these examples do not
include the required `api-key` parameter. Be sure to include your API key in
your request.

### REQUESTS

**Get Recent Comments**

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/community/v3/user-content/recent.json
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Get Comments by Date**

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/community/v3/user-content/by-date.json?date=2008-01-02
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Get Comments by User ID**

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/community/v3/user-content/user.json?userID=2364811
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Get Comments by URL**

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/community/v3/user-content/url.json?url=http%3A%2F%2Fwww.nytimes.com%2F2008%2F01%2F02%2Fopinion%2F02diamond.html
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

### RESPONSES

Here is a portion of the JSON response to the Get Comments by URL example:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
{ 
    "status":"OK", 
    "copyright":"Copyright (c) 2015 The New York Times Company.  All Rights Reserved.", 
    "results": 
        { 
            "comments": 
            [ 
                { 
                    "commentID":20831, 
                    "status":"approved",
                    "commentSequence":138, 
                    "userID":44150303, 
                    "userDisplayName":"byakushi", 
                    "userLocation":"US", 
                    "userTitle":null, 
                    "userURL":null, 
                    "commentTitle":"", 
                    "commentBody":"I have always wondered how much energy US would save if it shut down Vegas? Can you imagine the amount of electricity consumed on the strip, the ice melted for its water supply - all in the name of gambling? That's the kind of consumerism I would like to see halted. Same goes for all the downtown skylines which cause so much light pollution. Even a simple thing like having an \"off\" switch in the homes rather than just power outlets would save a lot of energy and hopefully make a huge difference in the \"consumption footprint.\" Can American live with that?<br\/><br\/>As for the growing economies of China & India: the increased industrialization has also increased environmental pollution in those countries. West has conveniently handed down it's dirty work to them. And at the same time we have Americans screaming about lost jobs. When will they realize that they can't have it both ways?<br\/><br\/>All in all they are acting like spoilt brats who have realized that they are no longer the teacher's favorite. Is it surprising that other folks hate you for your spoilt ways, at the same time envying how you have it so easy?<br\/><br\/>", 
                    "createDate":"1199309173", 
                    "updateDate":"1199322293", 
                    "approveDate":"1199322293", 
                    "recommendations":5, 
                    "replyCount":0, 
                    "replies":[], 
                    "editorsSelection":false, 
                    "parentID":null, 
                    "parentUserDisplayName":null, 
                    "depth":1, 
                    "commentType":"comment", 
                    "trusted":0, 
                    "recommendedFlag":0, 
                    "reportAbuseFlag":0, 
                    "permID":"138", 
                    "picURL":"http:\/\/graphics8.nytimes.com\/images\/apps\/timespeople\/none.png", 
                    "timespeople":1, 
                    "sharing":0 
                    }, 
                { 
                    "commentID":20837, 
                    "status":"approved", 
                    "commentSequence":137, 
                    "userID":5173787, 
                    "userDisplayName":"Tom", 
                    "userLocation":"California", 
                    "userTitle":null, 
                    "userURL":null, 
                    "commentTitle":"", 
                    "commentBody":"\"Much American consumption is wasteful and contributes little or nothing to quality of life.\"<br\/><br\/>Purely the author's opinion... who decides what is considered wasteful and what contributes to quality of life?<br\/><br\/>\"For example, per capita oil consumption in Western Europe is about half of ours, yet Western Europe\u2019s standard of living is higher by any reasonable criterion, including life expectancy, health, infant mortality, access to medical care, financial security after retirement, vacation time, quality of public schools and support for the arts.\"<br\/><br\/>While most would agree that some of the above criteria are important measures of quality of life, they are not the only measures of quality of life.  For example, as #23 points out, life is much more convenient here than in Europe.  We also don't live with our parents until we are 40 years old, as is common in Europe.", 
                    "createDate":"1199309605", 
                    "updateDate":"1199315485", 
                    "approveDate":"1199315485", 
                    "recommendations":2, 
                    "replyCount":0, 
                    "replies":[], 
                    "editorsSelection":false,
                    "parentID":null,
                    "parentUserDisplayName":null,
                    "depth":1, 
                    "commentType":"comment",
                    "trusted":0, 
                    "recommendedFlag":0,
                    "reportAbuseFlag":0, 
                    "permID":"137", 
                    "picURL":"http:\/\/graphics8.nytimes.com\/images\/apps\/timespeople\/none.png", 
                    "timespeople":0, 
                    "sharing":0 
                    },
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
