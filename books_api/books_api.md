Books API: Best Sellers
=======================

With the Best Sellers request type, you can get data from all New York Times
best-seller lists, including rank history for specific best sellers. To learn
more about the Book Reviews request type,
go [here](<http://developer.nytimes.com/docs/books_api/Books_API_Book_Reviews>).

**Note:** In this document, curly braces { } indicate required items. Square
brackets [ ] indicate optional items or placeholders.

**The Best Sellers Request Type at a Glance**

**Base URI**

`http://api.nytimes.com/svc/books/{version}/lists`

**Scope**

New York Times best-seller lists from June 2008 to present (one-week delay)  


**HTTP method**

GET

**Response formats**

JSON (`.json`, default), JSONP (`.jsonp`)

 

To retrieve best-seller lists, you must [sign up for an API key](</signup>) for
the Books API. Usage is limited to 5,000 requests per day (rate limits are
subject to change). Please read and agree to the [API Terms of Use](</tau>) and
the [Attribution Guidelines](</attribution>) before you proceed.

Requests
--------

The Best Sellers service uses
a [RESTful](<http://en.wikipedia.org/wiki/Representational_State_Transfer>) style.
Five request types are available: [get a best-seller
list](<http://developer.nytimes.com/docs/books_api/Books_API_Best_Sellers#h3-list>), [search
best-seller
lists](<http://developer.nytimes.com/docs/books_api/Books_API_Best_Sellers#h3-list-search>), [get
the history of a best
seller](<http://developer.nytimes.com/docs/books_api/Books_API_Best_Sellers#h3-history>), [get
an overview of all of the best-seller lists for a given
week](<http://developer.nytimes.com/docs/books_api/Books_API_Best_Sellers#h3-overview>) and [get
the names of Times best-seller
lists.](<http://developer.nytimes.com/docs/books_api/Books_API_Best_Sellers#h3-list-names>)

For general tips on creating a request URI, see [Constructing a
Request](<http://developer.nytimes.com/docs/reference/requests>).

 

### BEST-SELLER LISTS

To get a Times best-seller list, use the following URI structure:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/books/{version}/lists/[date/]{list-name}[.response_format]?[optional-param1=value1]&[...]&api-key={your-API-key}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 

### SEARCH BEST-SELLER LISTS

To search best-seller list data, use the following URI structure:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/books/{version}/lists[.response_format]?{search-param1=value1}&[...]&[optional-param1=value1]&[...]&api-key={your-API-key}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 

Responses
---------

An HTTP response code of 200 (OK) is returned for all requests that are
successfully understood and processed. See
the [Errors](<http://developer.nytimes.com/docs/books_api/Books_API_Best_Sellers#h2-errors>)section
for additional response codes.

### RESULT SETS

-   For best-seller history requests that search by `ISBN`, the
    default `sort-by` value is `ISBN`. For all other best-seller history
    requests, the default `sort-by` value is `title`. For list searches, the
    default `sort-by` value is `rank`.

-   The service returns 20 results at a time. Use the `offset` parameter to page
    through the results. (For best-seller history requests, the maximum number
    of results is 20; the `offset` parameter is not available.)

 

Examples
--------

### REQUESTS

These examples use an `.json` extension for illustration purposes. Also, these
examples do not include the required `api-key` parameter. Be sure to include
your API key in your request.

Get a Trade Fiction Paperback best-seller list by date:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/books/v2/lists/2010-10-01/trade-fiction-paperback.json
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Search the current Hardcover Fiction list for best sellers that have been on the
list for 2 weeks:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/books/v2/lists.json?list=hardcover-fiction&weeks-on-list=2
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Get the history of a best seller:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/books/v2/lists/best-sellers/history.json?title=pioneer
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

### RESPONSES

Here is a portion of a JSON response to the [Trade Fiction Paperback list
example](<http://developer.nytimes.com/docs/books_api/Books_API_Best_Sellers#example1>):

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
{
   "status":"OK",
   "copyright":"Copyright (c) 2011 The New York Times Company.  All Rights Reserved.",
   "num_results":35,
   "last_modified":"2011-02-10T16:43:13-05:00",
   "results":[
      {
         "list_name":"Trade Fiction Paperback",
         "display_name":"Paperback Trade Fiction",
         "bestsellers_date":"2010-09-19",
         "published_date":"2010-10-03",
         "rank":1,
         "rank_last_week":1,
         "weeks_on_list":65,
         "asterisk":0,
         "dagger":0,
         "isbns":[
            {
               "isbn10":"0307454541",
               "isbn13":"9780307454546",
            },
            {
               "isbn10":"0307473473",
               "isbn13":"9780307473479",
            },
            {
               "isbn10":"0307272117",
               "isbn13":"9780307272119",
            },
            {
               "isbn10":"0739384155",
               "isbn13":"9780739384152",
            }
         ],
         "book_details":[
            {
               "title":"THE GIRL WITH THE DRAGON TATTOO",
               "description":"A hacker and a journalist investigate the disappearance 
                   of a Swedish heiress.",
               "contributor":"by Stieg Larsson",
               "author":"Stieg Larsson",
               "contributor_note":"",
               "price":14.95,
               "age_group":"",
               "publisher":"Vintage Crime\/Black Lizard",
               "primary_isbn13":"9780307454546",
               "primary_isbn10":"0307454541",
            }
         ],
         "reviews":[
            {
               "book_review_link":"http:\/\/www.nytimes.com\/2008\/09\/30\
                   /books\/30kaku.html",
               "first_chapter_link":"",
               "sunday_review_link":"http:\/\/www.nytimes.com\/2008\/09\/14\
                   /books\/review\/Berenson-t.html",
               "article_chapter_link":""
            }
         ]
      },
      {
         "list_name":"Trade Fiction Paperback",
         "display_name":"Paperback Trade Fiction",
         "bestsellers_date":"2010-09-19",
         "published_date":"2010-10-03",
         "rank":20,
         "rank_last_week":18,
         "weeks_on_list":3,
         "asterisk":0,
         "dagger":0,
         "isbns":[
            {
               "isbn10":"0312429983",
               "isbn13":"9780312429980",
            },
            {
               "isbn10":"0805080686",
               "isbn13":"9780805080681",
            }
         ],
         ..
         "book_details":[
            {
               "title":"WOLF HALL",
               "description":"Thomas More and Thomas Cromwell clash in the court 
                  of Henry VIII; winner of the 2009 Man Booker Prize.",
               "contributor":"by Hilary Mantel",
               "author":"Hilary Mantel",
               "contributor_note":"",
               "price":16,
               "age_group":"",
               "publisher":"Picador",
               "primary_isbn13":"9780312429980",
               "primary_isbn10":"0312429983",
            }
         ],
         "reviews":[
            {
               "book_review_link":"http:\/\/www.nytimes.com\/2009\/10\/05\
                    /books\/05maslin.html",
               "first_chapter_link":"",
               "sunday_review_link":"http:\/\/www.nytimes.com\/2009\/11\/01\
                    /books\/review\/Benfey-t.html",
               "article_chapter_link":"http:\/\/www.nytimes.com\/2009\/10\/07\
                   /books\/07booker.html"
            }
         ]
      }
   ]
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Errors
------

The Best Sellers API returns the [standard
errors](<http://developer.nytimes.com/docs/reference/errors>). In addition, an
error message will be returned if no results are found for your search request.
Formatting errors (such as improper date formats) may also be returned.

 

Books API: Book Reviews
=======================

With the Book Reviews request type, you can retrieve New York Times book
reviews. To learn more about the Best Sellers request type,
go [here](<http://developer.nytimes.com/docs/books_api/Books_API_Best_Sellers>).

**Note:** In this document, curly braces { } indicate required items. Square
brackets [ ] indicate optional items or placeholders.

**The Book Reviews Request Type at a Glance**

**Base URI**

`http://api.nytimes.com/svc/books/{version}/reviews`

**Scope**

New York Times book reviews  


**HTTP method**

GET

**Response formats**

JSON (`.json`, default),  JSONP (`.jsonp`)

 

You can search for book reviews in three ways:

-   [ISBN](<http://developer.nytimes.com/docs/books_api/Books_API_Book_Reviews#h3-isbn>)

-   [Title](<http://developer.nytimes.com/docs/books_api/Books_API_Book_Reviews#h3-title>)

-   [Author](<http://developer.nytimes.com/docs/books_api/Books_API_Book_Reviews#h3-author>)

 

### ISBN

Searching by ISBN is the recommended method. You can enter 10- or 13-digit
ISBNs. To search by ISBN, use the following URI structure:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/books/v3/reviews[.response-format]?isbn={ISBN}&api-key={your-API-key}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 

### TITLE

You’ll need to enter the full title of the book. Spaces in the title will be
converted into the characters %20. To search by title, use the following URI
structure:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/books/v3/reviews[.response-format]?title={TITLE}&api-key={your-API-key}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 

### AUTHOR

You’ll need to enter the author’s first and last name, separated by a space.
This space will be converted into the characters %20. To search by author, use
the following URI structure:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/books/v3/reviews[.response-format]?author={AUTHOR}&api-key={your-API-key}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 

Examples
--------

### REQUESTS

These examples use a `.json` extension for illustration purposes. Also, these
examples do not include the required `api-key`parameter. Be sure to include your
API key in your request.

Get reviews for a given book by ISBN:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/books/v3/reviews.json?isbn=9781446484197
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Get reviews for a given book by title:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/books/v3/reviews.json?title=1Q84
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Get reviews for books by a given author:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/books/v3/reviews.json?author=Haruki%20Murakami
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

### RESPONSES

Here is a JSON response to the ISBN example:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
{
    status: "OK",
    copyright: "Copyright (c) 2014 The New York Times Company. All Rights Reserved.",
    num_results: 2,
    results: 
    [
        {
            url: "http://www.nytimes.com/2011/11/10/books/1q84-by-haruki-murakami-review.html",
            publication_dt: "2011-11-10 00:00:00",
            byline: "JANET MASLIN",
            book_title: "1Q84",
            book_author: "Haruki Murakami",
            summary: "In “1Q84,” the Japanese novelist Haruki Murakami writes about characters in a Tokyo with two moons.",
            isbn13: 
            [
                "9781446484203",
                "9780307476463",
                "9780307593313",
                "9780307957023",
                "9780345802934",
                "9781446484197",
                "9781455830497",
                "9781469258843",
                "9788483832967"
            ]
        },
        {
            url: "http://www.nytimes.com/2011/11/06/books/review/1q84-by-haruki-murakami-translated-by-jay-rubin-and-philip-gabriel-book-review.html",
            publication_dt: "2011-11-06 00:00:00",
            byline: "KATHRYN SCHULZ",
            book_title: "1Q84",
            book_author: "Haruki Murakami",
            summary: "Haruki Murakami has translated Raymond Chandler into Japanese, and there’s a lot of Marlowe to his madness.",
            isbn13: 
            [
                "9780307476463",
                "9780307593313",
                "9780307957023",
                "9780345802934",
                "9781446484197",
                "9781446484203",
                "9781455830497",
                "9781469258843",
                "9788483832967"
            ]
        }
    ]
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Here is a JSON response to the title example:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
{
    status: "OK",
    copyright: "Copyright (c) 2014 The New York Times Company. All Rights Reserved.",
    num_results: 2,
    results: 
    [
        {
            url: "http://www.nytimes.com/2011/11/10/books/1q84-by-haruki-murakami-review.html",
            publication_dt: "2011-11-10 00:00:00",
            review_type: "regular",
            byline: "JANET MASLIN",
            book_title: "1Q84",
            book_author: "Haruki Murakami",
            summary: "In “1Q84,” the Japanese novelist Haruki Murakami writes about characters in a Tokyo with two moons.",
            isbn13: 
            [
                "9781446484203",
                "9780307476463",
                "9780307593313",
                "9780307957023",
                "9780345802934",
                "9781446484197",
                "9781455830497",
                "9781469258843",
                "9788483832967"
            ]
        },
        {
            url: "http://www.nytimes.com/2011/11/06/books/review/1q84-by-haruki-murakami-translated-by-jay-rubin-and-philip-gabriel-book-review.html",
            publication_dt: "2011-11-06 00:00:00",
            review_type: "sunday",
            byline: "KATHRYN SCHULZ",
            book_title: "1Q84",
            book_author: "Haruki Murakami",
            summary: "Haruki Murakami has translated Raymond Chandler into Japanese, and there’s a lot of Marlowe to his madness.",
            isbn13: 
            [
                "9780307476463",
                "9780307593313",
                "9780307957023",
                "9780345802934",
                "9781446484197",
                "9781446484203",
                "9781455830497",
                "9781469258843",
                "9788483832967"
            ]
        }
    ]
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Here is a portion of a JSON response to the author example:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
{
    status: "OK",
    copyright: "Copyright (c) 2014 The New York Times Company. All Rights Reserved.",
    num_results: 6,
    results: 
    [
        {
            url: "http://www.nytimes.com/2011/11/10/books/1q84-by-haruki-murakami-review.html",
            publication_dt: "2011-11-10 00:00:00",
            review_type: "regular",
            byline: "JANET MASLIN",
            book_title: "1Q84",
            book_author: "Haruki Murakami",
            summary: "In “1Q84,” the Japanese novelist Haruki Murakami writes about characters in a Tokyo with two moons.",
            isbn13: 
            [
                "9781446484203",
                "9780307476463",
                "9780307593313",
                "9780307957023",
                "9780345802934",
                "9781446484197",
                "9781455830497",
                "9781469258843",
                "9788483832967"
            ]
        },
        {
            url: "http://www.nytimes.com/1999/02/17/books/books-of-the-times-an-obsessive-attraction-that-cripples-two-lives.html",
            publication_dt: "1999-02-17 00:00:00",
            review_type: "regular",
            byline: "RICHARD BERNSTEIN",
            book_title: "South of the Border, West of the Sun",
            book_author: "Haruki Murakami",
            summary: "",
            isbn13: 
            [
                "9780375402517"
            ]
        },
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Errors
------

The Book Reviews request type returns the [standard
errors](<http://developer.nytimes.com/docs/reference/errors>). In addition, an
error message will be returned if no results are found for your search request.
Formatting errors (such as improper date formats) may also be returned.
