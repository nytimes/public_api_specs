The Semantic API
================

The Semantic API complements the Articles API. With the Semantic API, you get
access to the long list of people, places, organizations and other locations,
entities and descriptors that make up the controlled vocabulary used as metadata
by The New York Times (sometimes referred to as Times Tags and used for Times
Topics pages.

**Note:** In URI examples and field names, *italics* indicate placeholders for
variables or values. Parentheses ( ) indicate optional items. Square brackets [
] are not a convention — when URIs include brackets, interpret them literally.

**The Semantic API at a Glance**

**Base URI**

`http://api.nytimes.com/svc/semantic/v2/concept`

**Scope**

The New York Times controlled vocabulary (over 100,000 people, places,
organizations and descriptors used to classify New York Times articles metadata)
and New York Times articles from 1981 to today (excludes wire services such as
the Associated Press)

**HTTP method**

GET

**Response formats**

JSON
 

Getting Started
---------------

### KEY CONCEPTS


The first and simplest way to access the API is to refer to a concept is by type. There are four
concept types: people, places, organizations and descriptors. The concept\_type
is a mandatory parameter for accessing the Semantic API with a concept type
request.

Examples of specific concepts, and their associated concept\_type:  


| **Concept Type** | **concept\_type** | **specific\_concept\_name ** |
|------------------|-------------------|------------------------------|
| Location         | nytd\_geo         | Acapulco (Mexico)            |
| Person           | nytd\_per         | Abbas, Mahmoud               |
| Organization     | nytd\_org         | 3M Company                   |
| Descriptor       | nytd\_des         | Absenteeism                  |

 

If you wish to determine which articles are associated with a particular
concept, you can use the article search API and specify the concept in the fq parameter.

| **Concept Type** | **specific\_concept\_name ** | **Search API Query**            |
|------------------|------------------------------|---------------------------------|
| Location         | Acapulco (Mexico)            | glocations: "Acapulco (Mexico)" |
| Person           | Abbas, Mahmoud               | persons: "Abbas, Mahmoud"       |
| Organization     | 3M Company                   | organizations: "3M Company"     |
| Descriptor       | Absenteeism                  | subject:absenteeism             |

If you are not sure the name and type of the concept that you are looking for, you can
use the search endpoint of the semantic API to find concepts by substring.

In addition to the mandatory parameters corresponding to the three ways of
accessing the Semantic API, optional parameters can also be applied. The
"fields" parameter can be given the value "all" to provide a global request that
includes all optional parameters.

Requests
--------

This section summarizes Semantic Search request URIs and parameters. For best
results, first review Key Concepts, then come back here to start building your
request URI.

### URI STRUCTURE

Semantic concept requests use the following URI structure:

-   **Name**: For concept type and specific concept requests:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/semantic/v2/concept/name/<concept_type>/<specific_concept>.json(?optional_parameters)&api-key=your-API-key
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


-   **Search**: For searching the complete list of concepts:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/semantic/v2/concept/search.json(?optional_parameters)&api-key=your-API-key
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 

###  

Constructing a Semantic API Request by Concept Type and Specific Concept
------------------------------------------------------------------------

concept\_type is one of four types:

1.  *nytd\_geo* for a location

2.  *nytd\_per* for a person

3.  *nytd\_org* for an organization

4.  *nytd\_des* for a descriptor

specific\_concept\_name is a term in The New York Times controlled
vocabulary.

The general form for a Semantic API request by concept type and specific
concept:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/semantic/v2/concept/name/<concept_type>/<specific_concept_name>.json(?optional_parameters)&api-key=your-API-key
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Examples of Semantic API requests by concept type and specific concept:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/semantic/v2/concept/name/nytd_des/Baseball.json?fields=all&api-key=your-API-key

http://api.nytimes.com/svc/semantic/v2/concept/name/nytd_per/Obama, Barack.json?fields=pages,links,scope_notes&api-key=your-API-key (you need the space after the comma separating last name and first name)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
 
 
Constructing a Semantic API Search Query
---------------------------

The general form for Search Query consists of a query string
(*query=*query\_term) and optional parameters.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/semantic/v2/concept/search.json?query=<query_term>(&optional_parameters)&api-key=your-api-key
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The optional parameters for a Search Query are *concept\_type*,
*concept\_uri*, *article\_uri*. These optional parameters are derived from
the other types of Semantic API requests and are explained in the instructions
for constructing those requests (above).

An example of a Search Query, it asks for all of the concepts of type
'nytd\_per' that contain the substring "Evan" and return the result formatted in
JSON.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/semantic/v2/concept/search.json?query=evan&concept_type=nytd_per&api-key=your-api-key
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 
-

Examples
--------

These examples do not include the required `api-key` parameter. Be sure to
include your API key in your request.

### REQUESTS & RESPONSES

**Request**

-   **Name**: Requests all fields for the concept with concept\_type
    ='nytd\_geo' and concept\_name='Kansas'.  

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/semantic/v2/concept/name/nytd_geo/Kansas?fields=all&api-key=your-API-key
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Response**

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
{
    status: "OK",
    copyright: "Copyright (c) 2011 The New York Times Company.  All Rights Reserved.",
    num_results: 1,
    source_database: "slave",
    fields: ["links", "taxonomy", "combinations", "scope_notes", "ticker_symbol", "geocodes", "search_api_query", "pages", "article_list"],
    results: [{
        concept_name: "Kansas",
        is_times_tag: 1,
        concept_status: "Active",
        concept_type: "nytd_geo",
        first_use: "2004-10-30",
        last_use: "2011-11-23",
        use_count: 167,
        links: [{
            relation: "sameAs",
            link: "http://rdf.freebase.com/ns/en.kansas",
            link_type: "freebase_uri",
            link_mapping_type: "manual"
        }, {
            relation: "sameAs",
            link: "http://dbpedia.org/resource/Kansas",
            link_type: "dbpedia_uri",
            link_mapping_type: "manual"
        }, {
            relation: "sameAs",
            link: "http://en.wikipedia.org/wiki/Kansas",
            link_type: "wikipedia_uri",
            link_mapping_type: "manual"
        }],
        taxonomy: [],
        combinations: [],
        scope_notes: [],
        ticker_symbol: [],
        geocodes: [{
            concept_name: "Kansas",
            is_times_tag: 1,
            concept_status: "Active",
            geoname_id: 4273857,
            name: "Kansas",
            latitude: 38.5002888,
            longitude: -98.5006275,
            elevation: 545,
            population: 2740759,
            country_code: "US",
            country_name: "United States",
            admin_code1: "KS",
            admin_code2: null,
            admin_code3: null,
            admin_code4: null,
            admin_name1: "Kansas",
            admin_name2: null,
            admin_name3: null,
            admin_name4: null,
            feature_class: "A",
            feature_class_name: "country, state, region,...",
            feature_code: "ADM1",
            feature_code_name: "first-order administrative division",
            time_zone_id: "America/North_Dakota/New_Salem",
            dst_offset: -5,
            gmt_offset: -6
        }],
        search_api_query: "http://api.nytimes.com/svc/search/v1/article?format=json&fields=body,date,title,url,byline,small_image_url,small_image_height,small_image_width&query=nytd_geo_facet%3A%5BKansas%5D&api-key=",
        pages: ["http://travel.nytimes.com/travel/guides/north-america/united-states/kansas/overview.html"],
        article_list: {
            offset: "0",
            results: [{
                body: "OVERLAND PARK, Kan. -- The prosecution of a Planned Parenthood affiliate here, the first such criminal case in the nation, has been treated locally as something of a proxy in the battle over abortion rights. Derided by supporters of the organization as politically motivated, the prosecution was celebrated by opponents as the capstone of",
                byline: "By A. G. SULZBERGER",
                date: "20111123",
                small_image_height: "75",
                small_image_url: "http://graphics8.nytimes.com/images/2011/11/23/us/23abortion_span/23abortion_span-thumbStandard.jpg",
                title: "Abortion Case Loses Ground, But Issue Stays Hot in Kansas",
                url: "http://www.nytimes.com/2011/11/23/us/kansas-abortion-prosecution-loses-some-steam-but-fire-is-still-hot.html"
            }, {
                body: "CIMARRON, Kan. -- The ubiquitous swerving and darting forms making their hopscotch journey across the landscape here in recent days are part of one of the most storied -- and least celebrated -- natural migrations on the Great Plains. Yes, the tumbleweeds are on the move again. Over the coming weeks, more and more of these vagabond bundles of",
                byline: "By A. G. SULZBERGER",
                date: "20111028",
                small_image_height: "75",
                small_image_url: "http://graphics8.nytimes.com/images/2011/10/28/us/TUMBLEWEEDS/TUMBLEWEEDS-thumbStandard.jpg",
                title: "Drifting Along, Tumbleweeds Are Piling Up Across Plains",
                url: "http://www.nytimes.com/2011/10/28/us/tumbleweeds-are-piling-up-across-the-plains.html"
            }, {
                body: "Adding fuel to the debate over his proposal for higher taxes on the rich, Warren E. Buffett said in a letter to a Kansas congressman that he paid $6.9 million in federal income taxes in 2010. The figure represent 17.4 percent of his $39.8 million in taxable income, a percentage he has repeatedly said is too low compared to what his own staff",
                byline: "By REUTERS",
                date: "20111013",
                title: "In Response To Lawmaker, Buffett Claims 17.4% Tax Rate",
                url: "http://www.nytimes.com/2011/10/13/business/in-letter-to-congressman-buffett-claims-17-4-tax-rate.html"
            }, {
                body: "TOPEKA, Kan. -- The startling vote came up at a City Council meeting here on Tuesday, provoked by a run-of-the-mill budget dispute over services that had spun out of control: decriminalize domestic violence. Three arms of government, all ostensibly representing the same people, have been at an impasse over who should be responsible for -- and pay",
                byline: "By A. G. SULZBERGER",
                date: "20111012",
                title: "Facing Cuts, a City Repeals Its Domestic Violence Law",
                url: "http://www.nytimes.com/2011/10/12/us/topeka-moves-to-decriminalize-domestic-violence.html"
            }, {
                body: "A federal judge on Thursday declined to halt a Kansas law that limits the availability of insurance coverage for abortions. The American Civil Liberties Union had requested a temporary injunction against the law, which was approved by the Legislature this year, while the group fights the law in court. Judge Wesley Brown of Federal District Court",
                byline: "By TIMOTHY WILLIAMS",
                date: "20110930",
                title: "NATIONAL BRIEFING | PLAINS; Kansas: Judge Refuses to Block Abortion Law",
                url: "http://www.nytimes.com/2011/09/30/us/kansas-judge-refuses-to-block-abortion-law.html"
            }, {
                body: "A lawsuit filed in Kansas this month has opened a new front in the legal war over women's reproductive rights. Since last year, 13 states, including Kansas, have enacted laws banning insurance coverage of abortion in the health insurance exchanges created by the federal health care reform law. Some states have gone even further, aggressively",
                date: "20110830",
                title: "EDITORIAL; Targeting Women: State efforts to end insurance coverage for abortions endanger women's health and rights",
                url: "http://www.nytimes.com/2011/08/30/opinion/targeting-women.html"
            }, {
                body: "In a foolhardy indulgence of partisan ideology, Gov. Sam Brownback of Kansas is returning a $31.5 million federal grant that would have made his state a leader in technology development for the new federal health care law. The Republican governor's unilateral rejection was presented as a matter of his grave concern over federal deficit problems.",
                date: "20110815",
                title: "EDITORIAL; Gov. Brownback's Selective Budget Worries",
                url: "http://www.nytimes.com/2011/08/15/opinion/gov-brownbacks-selective-budget-worries.html"
            }, {
                body: "A federal judge ruled Monday that Planned Parenthood would most likely succeed in overturning a new Kansas law that denies the group access to federal family planning money, saying he believes that the law is unconstitutional and was intended to punish the group for advocating for abortion rights. The judge, J. Thomas Marten, granted Planned",
                byline: "By THE ASSOCIATED PRESS",
                date: "20110802",
                title: "NATIONAL BRIEFING | PLAINS; Kansas: Ruling for Planned Parenthood",
                url: "http://www.nytimes.com/2011/08/02/us/02brfs-JUDGERULESFO_BRF.html"
            }, {
                body: "SALINA, Kan. -- This state, so sparsely populated in parts that five counties have no doctors at all, has struggled for years to encourage young doctors to relocate to rural communities, where health problems are often exacerbated by a lack of even the most basic care. On Friday, a new medical school campus opened here to provide a novel solution",
                byline: "By A. G. SULZBERGER",
                date: "20110723",
                small_image_height: "75",
                small_image_url: "http://graphics8.nytimes.com/images/2011/07/23/us/DOCTORS/DOCTORS-thumbStandard.jpg",
                title: "New Path for Small-Town Doctors Starts in a Kansas Small Town",
                url: "http://www.nytimes.com/2011/07/23/health/policy/23doctors.html"
            }, {
                body: "In three new rulings, federal judges in different states have acted to block immediate enforcement of measures that restrict abortion rights and women's access to affordable contraception, lifesaving cancer screenings and treatment for sexually transmitted diseases. These rulings are important victories for women's health and reproductive rights.",
                date: "20110714",
                title: "EDITORIAL; The Courts Step In: Judges' recent rulings show how extreme antiabortion measures have become",
                url: "http://www.nytimes.com/2011/07/14/opinion/14thurs1.html"
            }],
            tokens: ["nytd_geo_facet:[Kansas]"],
            total: 167
        },
        concept_uri: "http://data.nytimes.com/48672515640526970881"
    }]
}

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Request**

-   **Search: **For all of the concepts of type 'nytd\_per' that contain the
    substring "Evan" and return the result formatted in JSON.  
    

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/semantic/v2/concept/search.json?query=evan&concept_type=nytd_per&api-key=your-api-key
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Response**

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
{  
    "result_set": {    
         "status": "OK",
         "copyright": "Copyright (c) 2011 The New York Times Company. All Rights Reserved. ",    
         "num_results": "1",    
         "source_database": "slave",    
         "fields": {      
             "field": ["links","search_api_query"]
         },    
         "results": {      
             "result": {
                "concept_name": "Williams College",
                "is_times_tag": "0",
                "concept_status": "Active",
                "concept_type": "nytd_org",
                "first_use": "2005-04-03",
                "last_use": "2010-11-14",
                "use_count": "12",
                "links": {
                    "link": [{"relation": "sameAs","link": "http://rdf.freebase.com/ns/en.williams_college","link_type": "freebase_uri","link_mapping_type": "manual"},
                         {"relation": "sameAs","link": "http://dbpedia.org/resource/Williams_College","link_type": "dbpedia_uri","link_mapping_type": "manual"},
                                 {"relation": "sameAs","link": "http://en.wikipedia.org/wiki/Williams_College","link_type": "wikipedia_uri","link_mapping_type": "manual"}]
                    },        
                 "search_api_query": "http://api.nytimes.com/svc/search/v1/article?format=json&fields=body,date,title,url,byline,small_image_url,small_image_height,small_image_width&query=nytd_org_facet%3A%5BWilliams+College%5D&api-key=","concept_uri": "http://data.nytimes.com/N86135070607995494002"
        }
 }
 }
 }
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
