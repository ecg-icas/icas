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

This URL prefills ad template with title, category, description and attributes.

If the category does not exist server returns **404 Not Found**.
If the category doesn't support prefill or if identifying attribute of prefillable
category is missing, server returns **400 Bad Request**.

.. note::

	This call is only compatible with categories which have enabled prefill feature.

Errors
------

====================    ====    ==============================     ==============================================================================
Field                   Code    Error message                      Description
====================    ====    ==============================     ==============================================================================
categoryId              1006    type mismatch                      not an integer number
categoryId              2000    missing argument                   mandatory field
categoryId              2001    invalid argument                   not a valid category id
categoryId              2029    category prefill not supported     Prefill is not supported for category
attributes              2030    missing identifying attribute      Missing one of the identifying attributes
====================    ====    ==============================     ==============================================================================

Example
-------

.. include:: ../examples/post-ad-prefill-example.rst

