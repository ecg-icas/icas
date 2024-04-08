.. _Authorization Code Grant: http://tools.ietf.org/html/rfc6749#section-4.1
.. _ISO 4217: http://en.wikipedia.org/wiki/ISO_4217
.. _ISO 8601: http://en.wikipedia.org/wiki/ISO_8601
.. _windows-1252: https://en.wikipedia.org/wiki/Windows-1252
.. _Discord: http://https://discordapp.com
.. _overview:

Overview
========

The Sellside API is a RESTful API to manage ads either for your
own account or on behalf of other users. The base URLs for the API are:

.. list-table::
 :widths: 20 10 70
 :header-rows: 1

 * - Tenant
   - Env
   - Endpoint

 * - Marktplaats
   - Sandbox
   - https://admarkt.demo.qa-mp.so/api/sellside

 * -
   - Production
   - https://admarkt.marktplaats.nl/api/sellside

 * - Kijiji Canada
   - Sandbox
   - https://admarkt.qa10.kjdev.ca/api/sellside

 * -
   - Production
   - https://admarkt.kijiji.ca/api/sellside

 * - 2dehands Belgium
   - Sandbox
   - https://admarkt.demo-2dehands.qa-mp.so/api/sellside

 * -
   - Production
   - https://admarkt.2dehands.be/api/sellside

 * - Kleinanzeigen.de
   - Sandbox
   - https://internet.ka.pre-prod.icas.io/api/sellside

 * -
   - Production
   - https://admarkt.kleinanzeigen.de/api/sellside

With this the full URL for retrieving ad 1234 for the
current customer on Marktplaats Production becomes::

    https://admarkt.marktplaats.nl/api/sellside/ad/1234

.. _overview_authentication:

Authentication
--------------

Authentication is provided using *OAuth2* tokens and the so called
`Authorization Code Grant`_
which means that you need a client id and client secret to access the api with
an access token that the API provides. It is not possible to use username and
password to get an access token.

To request a client id and secret please ask your contact at the respective tenant
(marktplaats, kijiji.ca, tweedehands). Your contact can also send you an invite
for our `Discord`_ channel, where you can go for maintenance notifications and
support.

See the :ref:`authentication` section for the full details and also
the `OAuth 2.0 website <http://oauth.net/2/>`_.

.. _overview_media_types:

Media Types
-----------

Each resource has a specific media type of the following form to support
*content negotiation* and *versioning*::

    application/sellside.{entity}-{version}+json;charset=utf-8

The ``version`` field is mandatory.

The media type is used for the ``Content-Type`` and ``Accept`` headers.

This allows us to change the structure of a response without breaking existing
code since you have to request the new content type while the old version is
still available for some time. For backwards compatible changes like adding a
new field to an existing structure we will not change the version number.

.. _overview_accept_headers:

Content-Type and Accept Headers
-------------------------------

Every request must set the ``Accept`` header to::

    <Expected Media Type>, application/json

This permits the server to generate the response in the format the caller expects.
``application/json`` is required to return the error response.

Additionally, each ``POST`` and ``PUT`` request must also set the ``Content-Type``
header to::

    <Media Type of the body content>

.. _overview_image_downloads:

Image Downloads
---------------

Images & feeds are downloaded from the following ip addresses. Ensure that all image
URLs are accessible by these ip addresses and that there is no rate limit.

 * 5.255.156.110  (Production)
 * 5.255.156.126  (Production)
 * 3.64.37.25     (Production)
 * 18.194.96.182  (Production)
 * 3.72.155.39    (Production)
 * 34.253.123.82  (Production)
 * 34.246.217.218 (Production)
 * 52.214.29.214  (Production)
 * 3.98.109.128   (Production - Canada IP for Clients with Geo-blocking)
 * 3.99.27.64     (Production - Canada IP for Clients with Geo-blocking)
 * 3.97.250.121   (Production - Canada IP for Clients with Geo-blocking)
 * 3.68.139.10    (Sandbox)
 * 3.77.63.23     (Sandbox)
 * 3.77.131.63    (Sandbox)
 * 91.211.74.6    (Sandbox)

To reduce the latency when updating an ad we suggest that the response
contains either an ``ETag`` and/or ``Last-Modified`` header which only changes
when the image itself has changed. It should also be possible to check these
headers using a ``HEAD`` request.

Keep in mind that when feeds are imported, we potentially have to download
many images. Make sure your hosting can handle bursts of image downloads.

.. _overview_feed_downloads:

Feed Downloads
--------------

Feeds & images are downloaded following ip addresses. Ensure that all feed
URLs are accessible by these ip addresses and that there is no rate limit.

 * 5.255.156.110  (Production)
 * 5.255.156.126  (Production)
 * 3.64.37.25     (Production)
 * 18.194.96.182  (Production)
 * 3.72.155.39    (Production)
 * 34.253.123.82  (Production)
 * 34.246.217.218 (Production)
 * 52.214.29.214  (Production)
 * 3.98.109.128   (Production - Canada IP for Clients with Geo-blocking)
 * 3.99.27.64     (Production - Canada IP for Clients with Geo-blocking)
 * 3.97.250.121   (Production - Canada IP for Clients with Geo-blocking)
 * 3.68.139.10    (Sandbox)
 * 3.77.63.23     (Sandbox)
 * 3.77.131.63    (Sandbox)
 * 91.211.74.6    (Sandbox)

We typically run our feed import at 07:00 in the morning (local time), but we can trigger
additional import runs at any time if we deem it necessary (due to maintenance, tests, whutnot). 

Feed files usually contain links for the images of the ads too, so make sure you have your
whitelisting and/or rate limiting in order.

.. _overview_customize_response_body:

Customize response body
-----------------------

Every call which returns a response body can have this customized using
``_include`` and ``_exclude`` parameters. These parameters define which fields
to include in or exclude from the response body. When both ``_include`` and
``_exclude`` have a value, the ``_exclude`` value will be ignored. By default,
``_include`` is set to all fields and ``_exclude`` is empty.


Using ``_include``  will require you to specify *each key in the path* of the data 
that you wish. For example, if you're calling :ref:`get_ad_v5` and you
want the ad ID and title, you'll have to provide ``_include=ads,id,title``. 

.. include:: examples/include-exclude-example.rst

When providing `_exclude` then you don't need to provide the full path; any element
with a key that matches an element of the `_exclude` parameter will be omitted.

Furthermore, some calls allow for a ``_body`` parameter, defining whether
there should be any data in the response body at all. Default of ``_body`` is
true (returning data). When ``_body`` is false, ``_include`` and ``_exclude``
will be ignored.

.. _overview_dates_and_times:

Dates and Times
---------------

All date/time values are specified in `ISO 8601`_ Combined date and time in
UTC format.

.. _overview_prices_and_currencies:

Prices and Currencies
---------------------

Monetary amounts like prices and budgets are currently undergoing changes; newer
versions of endpoints mention whether the amount is either in cents or in micro 
units of the currency the local markets. If this is not mentioned, this is 
represented as (euro/dollar) cents. Currencies are specified as three character `ISO 4217`_ code.
1 euro/dollar == 100 cents == 1000000 micros.

.. _overview_http_response_codes_and_error_handling:

HTTP Response Codes and Error Handling
--------------------------------------

To retrieve, update and delete resources with the Sellside API you use the
standard HTTP verbs ``GET`` and ``PUT``. If the resource exists
and the request was successful the server responds with ``200 OK``. If the
resource does not exist the server responds with ``404 Not Found``.

To create a new resource you perform a ``POST`` request to which the server
responds with ``201 Created`` and a ``Location`` header containing the URL of
the new resource.

All requests are validated before they are being executed by the server. If
the validation fails the server responds with ``400 Bad Request`` and an error
response which contains a list of the errors. More information can be found under
:doc:`error-handling`.

.. _dryrun_validation:

Dry-Run Request Validation
--------------------------

The API supports dry-run validation of requests which modify resources. To
validate a request without executing it add ``_validate=true`` to the request
URL. If the validation succeeds the server returns ``200 OK`` and an empty
body. Otherwise, the server returns ``400 Bad Request`` with the list of
errors. The following endpoints support dry-run validation:

 * :ref:`post_ad`
 * :ref:`put_ad_id`
 * :ref:`put_ad_id_status`

.. _vendor_ids:

Vendor Ids
----------

For :ref:`ads<ad_vendorId>` and :ref:`campaigns<campaign_vendorId>`, it is possible to provide a so-called `vendorId`.
The intention of this `vendorId` is to allow the API partner to use their own primary key on this ad or campaign. 
The API partner can also fetch the ad or campaign _by_ `vendorId` - see :ref:`get_ad_vendor_id` and :ref:`get_campaign_vendor_id` 
for details - to  get the necessary primary key to perform other operations through the API.
This means the API partner does not need to keep an explicit mapping between their own primary key and the one generated
by our system, making integration simpler.

Such a vendorId cannot, once set, be changed or removed. It has become as strong as the primary key, in combination with the seller account
that's being used. This also means that within all ads of a seller, the vendorIds must be unique. Similarly, within all campaigns
of a seller, the vendorIds must be unique.

Keep in mind that vendorId is case-insensitive and only allows `windows-1252`_ (also known as Latin-1) characters. For example, an ad is created with vendorId "abc123", 
and this ad can be retrieved by vendorId "Abc123". If you want to create another ad with vendorId "aBc123", the creation will fail. Because "abc123", "Abc123" and "aBc123" 
are identical. The retrieval will have the same capitalization used on insertion. For example: an ad is created with vendorID "Abc123", the ad can be retrieved by 
vendorID "abc123" (lower case A) but the payload will returned with vendorID "Abc123", same case as insertion.

.. _page_tokens:

Page tokens
-----------

In some calls, while calling for a list of items, you get a response containing a `nextPageToken`. This encoded token is necessary for
efficient pagination. To get the next list (page) of items, you repeat the exact same call, but you add the `&pageToken=<encoded value>`
parameter to the call.
In essence, it contains encoded information on where the returned result ended, so it can serve as additional filters in the call for the next result set, making
that call more efficient. For the very first page, a pageToken should not be provided. For any following page, callers should use the exact same request with an added `pageToken` parameter.
The value for the ``pageToken`` parameter for page N+1 is the ``nextPageToken`` field in the response of your call to fetch page N.
When a response does not contain a ``nextPageToken`` you have reached the last page of results and there are no more to fetch.
