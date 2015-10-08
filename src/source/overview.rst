.. _Authorization Code Grant: http://tools.ietf.org/html/rfc6749#section-4.1
.. _eBay Classifieds iCAS Community: https://plus.google.com/communities/110150351420667771335
.. _ISO 4217: http://en.wikipedia.org/wiki/ISO_4217
.. _ISO 8601: http://en.wikipedia.org/wiki/ISO_8601
.. _overview:

Overview
========

The iCAS Sellside API is a RESTful API to manage ads on iCAS either for your
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

 * - DBA
   - Sandbox
   - https://dba.lp.icas.ecg.so/api/sellside

 * -
   - Production
   - https://topannoncer.dbabusiness.dk/api/sellside

 * - Kijiji Canada
   - Sandbox
   - https://cas.qa.kijiji.ca/api/sellside

 * -
   - Production
   - https://cas.kijiji.ca/api/sellside

With this the full URL for retrieving ad 1234 for the
current customer on Marktplaats Production becomes::

    https://admarkt.marktplaats.nl/api/sellside/ad/1234

.. _overview_image_downloads:

Image Downloads
---------------

Images are downloaded from the following ip addresses. Ensure that all image
URLs are accessible by these ip addresses and that there is no rate limit.

 * 5.255.156.110 (production)
 * 5.255.156.126 (production)
 * 91.211.74.6   (sandbox)

To reduce the latency when updating an ad we suggest that the response
contains either an ``ETag`` and/or ``Last-Modified`` header which only changes
when the image itself has changed. It should also be possible to check these
headers using a ``HEAD`` request.

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

.. _overview_authentication:

Authentication
--------------

Authentication is provided using *OAuth2* tokens and the so called
`Authorization Code Grant`_
which means that you need a client id and client secret to access the api with
an access token that the API provides. It is not possible to use username and
password to get an access token.

To request a client id and secret please send a request to the
`eBay Classifieds iCAS Community`_.

See the :ref:`authentication` section for the full details and also
the `OAuth 2.0 website <http://oauth.net/2/>`_.

.. _overview_customize_response_body:

Customize response body
-----------------------

Every call which returns a response body can have this customized using
``_include`` and ``_exclude`` parameters. These parameters define which fields
to include in or exclude from the response body. When both ``_include`` and
``_exclude`` have a value, the ``_exclude`` value will be ignored. By default,
``_include`` is set to all fields and ``_exclude`` is empty.

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

All monetary amounts like prices and budgets are currently in Euros and stored as euro cents.
Currencies are specified as three character `ISO 4217`_ code.

.. _overview_http_response_codes_and_error_handling:

HTTP Response Codes and Error Handling
--------------------------------------

To retrieve, update and delete resources with the Sellside API you use the
standard HTTP verbs ``GET``, ``PUT`` and ``DELETE``. If the resource exists
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
