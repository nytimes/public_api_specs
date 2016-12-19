# Books API
The Books API has services for getting information about *The New York Times* **Best Sellers Lists** and **Book Reviews**.

The services are [RESTful](<https://en.wikipedia.org/wiki/Representational_state_transfer>).

**Note:** In this document, curly braces { } indicate required items.
Square brackets [ ] indicate optional items or placeholders.

To use the Books API, you must [sign up for an API key](<http://developer.nytimes.com/apps/register>).
Usage is limited to 1,000 requests per day (*rate limits are subject to change*).
Please read and agree to the [API Terms of Use](<http://developer.nytimes.com/tou>)
and the [Attribution Guidelines](<http://developer.nytimes.com/attribution>) before you proceed.


# Books API: Best Sellers
The Best Sellers services return information about NYT Best Sellers lists going back to June 2008.

## The Best Sellers Requests at a Glance

### Base URI

  `http://api.nytimes.com/svc/books/{version}/lists`

### Scope

New York Times Best Sellers lists from June 2008 to present.

### HTTP method

GET

### Response formats

JSON (`.json`, default), JSONP (`.jsonp`)

## Requests

There are four main requests types:

 * Get Best Sellers List Details 
 * Get Overview of Best Sellers Lists
 * Get Best Sellers List Names
 * Get Book's Best Sellers List History


### Get Best Sellers List Details

The details service lets you get a specific Best Sellers list's details.

`/svc/books/v3/lists/current/{date}/{list-name}.{format}`

You need to specify the list's name and either the published date or "current" as the date.
The list names need to be encoded (lower case with apostrophes removed and spaces replaced with hyphens).

`/svc/books/v3/lists/current/hardcover-fiction.json`

`/svc/books/v3/lists/2016-12-11/mass-market-paperback.json`

Optional query parameters include sort-by, sort-order and offset (which needs to be multiple of 20).

When using JSONP, you'll need to provide a callback function name.

`/svc/books/v3/lists/current/hardcover-nonfiction.jsonp?callback=nyt_hnf_func`


### Get Overview of Best Sellers Lists
The overview service returns the top 5 books for all the Best Sellers lists.

`/svc/books/v3/lists/overview.{format}`

You can optionally request an overview for a specific published date using the *published_date* query parameter.

`/svc/books/v3/lists/overview.json?published_date=2016-12-11`

If no date is set, an overview of the latest lists is returned.

`/svc/books/v3/lists/overview.json`

When using JSONP, you'll need to provide a callback function name.

`/svc/books/v3/lists/overview.jsonp?callback=nyt_overview_func`


### Get Best Sellers List Names
The names service returns a list of Best Sellers list names.
It includes in the response the type of list (weekly or monthly) and when it was first published and last published.
Lists have been added and removed over time.
For example the Food and Diet list was added in 2013 and the Children’s Chapter Books list was removed in 2012.
The response also includes the *list_name_encoded* which you use when calling the details service.

`/svc/books/v3/lists/names.json`


### Get Book's Best Sellers List History
The Best Sellers history service returns books and their history on the NYT Best Sellers lists. 

`/svc/books/v3/lists/best-sellers/history.json`

You can search for books by author, ISBN or title using the aptly named query parameters author, isbn, and title.

`/svc/books/v3/lists/best-sellers/history.json?isbn=9780143034759`

Use the sort-by query parameter to choose the field to sort by.
The options are: bestsellers-date, date, isbn, list, list-name, published-date, rank, rank-last-week, title, and weeks-on-list.
Use the sort-order query parameter to choose the sort direction. Either asc or desc for ascending or descending.
When searching by ISBN, the default sort-by value is isbn.

`/svc/books/v3/lists/best-sellers/history.json?author=John%20Grisham&sort-by=title&sort-order=desc`

The API returns 20 results at a time.
The total number of results is returned in the *num_results* field.
Use the offset query parameter to paginate thru results.
It must be a multiple of 20.
An offset of 0 gets the first 20 results.
An offset of 20 gets the next 20 results.

`/svc/books/v3/lists/best-sellers/history.json?author=John%20Grisham?offset=20`


### Get Age Groups
The age groups service returns a list of age groups.

`/svc/books/v3/lists/age-groups.json`


## Responses

An HTTP response code of 200 (OK) is returned for all requests that are successfully understood and processed.


## Examples

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



---


Books API: Book Reviews
=======================

With the Book Reviews request type, you can retrieve New York Times book
reviews.

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

The Book Reviews request type returns the [standard HTTP error codes](<https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html>).
In addition, an error message will be returned if no results are found for your search request.
Formatting errors (such as improper date formats) may also be returned.
