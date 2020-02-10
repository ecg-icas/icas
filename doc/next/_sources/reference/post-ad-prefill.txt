.. index:: POST /ad/prefill

.. _post_ad_prefill:

POST /ad/prefill
================

.. list-table::
 :widths: 20 80

 * - Scope
   - ``console_rw``

 * - Accept
   - ``application/sellside.ad.template-v1+json, application/json``

 * - Content-Type
   - ``application/sellside.ad.template-v1+json; charset=utf-8``

This URL returns a template for an ad, to be used for prefilling.
This template can contain suggestions for title, category, description and attributes.

Retrieving prefill information is possible only for ads from categories that have
defined identifying attributes. Identifying attributes are attributes that
can uniquely identify advertised items. An example of identifying attribute is ISBN,
which can be used to uniquely identify a specific version of a book.

When requesting prefill information, clients must provide valid category ID and
identifying attribute for that category. If identifying attribute is missing
server will respond with **400 Bad Request**. Server will respond with the same
status code if provided category doesn't have any identifying attributes defined,
if category doesn't exist or the category id is missing or invalid.

Errors
------

====================    ====    ==============================     ===============================================
Field                   Code    Error message                      Description
====================    ====    ==============================     ===============================================
categoryId              1006    type mismatch                      not an integer number
categoryId              2000    missing argument                   mandatory field
categoryId              2001    invalid argument                   not a valid category id
categoryId              2029    category prefill not supported     Prefill is not supported for category
attributes              2030    missing identifying attribute      Missing one of the identifying attributes
====================    ====    ==============================     ===============================================

Example
-------

.. include:: ../examples/post-ad-prefill-example.rst

