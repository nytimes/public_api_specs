The Congress API
================

With the Congress API, you can get summaries of roll-call votes in the U.S.
Congress; get lists of members of Congress; and get vote data, floor
appearances, biographical information and role data for individual House and
Senate members. You can also get information about bills (summaries and bill
actions), nominees, committees and schedules.

 

### CONGRESSIONAL DATA

The Congress API returns the following types of data:

-   **Roll-call vote data:** Only roll-call votes (not voice votes or division
    votes) are tracked by official Congressional data sources. Along with basic
    vote data, the Times API returns additional information that is less readily
    available, such as party totals. For general information about roll-call
    votes, see
    the [THOMAS](<http://www.thomas.gov/home/votes/member.html>) site.

-   **Member data:** Along with general biographical information for current and
    past members of Congress, the API returns data about members' Congressional
    roles. Role data includes the Congress number and chamber, as well as the
    member's title, state and party. A single member may have more than one role
    in a particular Congress (for example, the member may switch parties or move
    from the House to the Senate). The API also helps you compare member data,
    including vote positions and bill cosponsorships.

-   **Bill data:** Along with standard bill summaries and details, the API
    returns bill subjects, amendments and related bills. You can also retrieve
    bills by member and view all the cosponsors of a bill.

-   **Nomination data:** The API returns presidential civilian nomination lists
    and details. Military nominations are not included. For general information
    about presidential nominations, see
    the [THOMAS](<http://thomas.loc.gov/home/PN/pnhelp.htm>) site.

-   **Other data:** The API returns various supplemental information, including
    party counts by state; committees and committee rosters; and chamber
    schedules.

 

### DATA SOURCES

The data returned by the Congress API is compiled from the following sources:

-   The official Web site of the [Office of the Clerk of the U.S. House of
    Representatives](<http://clerk.house.gov/legislative/legvotes.html>), for
    vote data

-   The official Web site of the [United States
    Senate](<http://www.senate.gov/pagelayout/legislative/a_three_sections_with_teasers/votes.htm>),
    for vote data

-   The [Biographical Directory of the United States
    Congress](<http://bioguide.congress.gov/biosearch/biosearch.asp>), for
    member biographical information

-   [GovTrack.us](<http://www.govtrack.us/source.xpd>), for member biographical
    information

-   MIT Professor Charles Stewart's collection of [Congressional
    data](<http://web.mit.edu/17.251/www/data_page.html>), for role information

-   [THOMAS](<http://www.thomas.gov/>) (The Library of Congress), for bill data
    and nomination data

-   The [C-SPAN Congressional
    Chronicle](<http://www.c-spanarchives.org/congress/>), for floor appearances

-   The [Sunlight API](<http://services.sunlightlabs.com/api/>), for Twitter and
    YouTube user names in [member
    lists](<http://developer.nytimes.com/docs/congress_api#h3-members>)

Certain fields in the API responses (such as party totals) are calculated by The
Times, based on these data sources.

 

Requests
--------

These examples use an `.json `extension for illustration purposes. Also, these
examples do not include the required `api-key` parameter. Be sure to include
your API key in your request.

 

Members
-------

###  

### MEMBER LISTS

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/politics/v3/us/legislative/congress/109/house/members.json
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/politics/v3/us/legislative/congress/109/house/members.json?state=CA&district=4
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/politics/v3/us/legislative/congress/103/senate/members.json
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/politics/v3/us/legislative/congress/103/senate/members.json?state=NM
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 

### MEMBER BIO AND ROLES

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/politics/v3/us/legislative/congress/members/L000447.json
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

<http://developer.nytimes.com/docs/congress_api/congress_api_examples#member-bio-xml>

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/politics/v3/us/legislative/congress/members/B000444.json
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 

### NEW MEMBERS

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/politics/v3/us/legislative/congress/members/new.json
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 

### CURRENT MEMBERS BY STATE/DISTRICT

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/politics/v3/us/legislative/congress/members/senate/OH/current.json
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/politics/v3/us/legislative/congress/members/house/CO/2/current.json
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 

### MEMBERS LEAVING OFFICE

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/politics/v3/us/legislative/congress/111/senate/members/leaving.json
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 

### MEMBER VOTE POSITIONS

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/politics/v3/us/legislative/congress/members/C001041/votes.json
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

<http://developer.nytimes.com/docs/congress_api/congress_api_examples#member-pos-xml>

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/politics/v3/us/legislative/congress/members/N000147/votes.json
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 

### MEMBER VOTE COMPARISON

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/politics/v3/us/legislative/congress/members/C001041/votes/S001141/109/senate.json
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 

### BILLS COSPONSORED BY A MEMBER

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/politics/v3/us/legislative/congress/members/A000014/bills/cosponsored.json
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 

### MEMBER SPONSORSHIP COMPARISON

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/politics/v3/us/legislative/congress/members/C001041/bills/S001141/109/senate.json
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 

### MEMBER FLOOR APPEARANCES

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/politics/v3/us/legislative/congress/members/A000069/floor_appearances.json
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 

 

Votes
-----

### ROLL-CALL VOTES

Senate:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/politics/v3/us/legislative/congress/110/senate/sessions/2/votes/194.json
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 

House:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/politics/v3/us/legislative/congress/105/house/sessions/2/votes/38.json
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 

### VOTES BY TYPE

**Missed Votes**

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/politics/v3/us/legislative/congress/111/senate/votes/missed.json
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 

**Party Votes**

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/politics/v3/us/legislative/congress/111/house/votes/party.json
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 

**Lone No Votes**

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/politics/v3/us/legislative/congress/108/house/votes/loneno.json
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 

**Perfect Votes**

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/politics/v3/us/legislative/congress/111/house/votes/perfect.json
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 

### VOTES BY DATE

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/politics/v3/us/legislative/congress/house/votes/2008-02-01/2008-02-15.json
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/politics/v3/us/legislative/congress/house/votes/2008/02.json
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 

### NOMINATION VOTES

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/politics/v3/us/legislative/congress/111/nominations.json
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 

Bills
-----

### RECENT BILLS

Recently introduced House bills:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/politics/v3/us/legislative/congress/111/house/bills/introduced.json
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 

Recently updated Senate bills:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/politics/v3/us/legislative/congress/111/senate/bills/updated.json
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 

### BILLS BY MEMBER

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/politics/v3/us/legislative/congress/members/P000587/bills/updated.json
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 

### BILL DETAILS

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/politics/v3/us/legislative/congress/111/bills/hr1866.xml
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 

### BILL SUBJECTS, AMENDMENTS AND RELATED BILLS

 

Bill subjects:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/politics/v3/us/legislative/congress/111/bills/sres88/subjects.json
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 

Bill Amendments:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/politics/v3/us/legislative/congress/111/bills/hr1/amendments.json
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 

Related Bills:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/politics/v3/us/legislative/congress/111/bills/hr381/related.json
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 

### BILL COSPONSORS

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/politics/v3/us/legislative/congress/111/bills/s1230/cosponsors.json
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 

Nominees
--------

### NOMINEE LISTS

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/politics/v3/us/legislative/congress/111/nominees/confirmed.json
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 

### NOMINEE DETAILS

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/politics/v3/us/legislative/congress/111/nominees/PN1020.json
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 

### NOMINEES BY STATE

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/politics/v3/us/legislative/congress/111/nominees/state/CA.json
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 

Other
-----

### STATE PARTY COUNTS

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/politics/v3/us/legislative/congress/states/members/party.json
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 

### COMMITTEES AND ROSTERS

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/politics/v3/us/legislative/congress/111/house/committees.json
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/politics/v3/us/legislative/congress/111/senate/committees/SSFR.json
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 

### CHAMBER SCHEDULE

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http://api.nytimes.com/svc/politics/v3/us/legislative/congress/house/schedule.json
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
