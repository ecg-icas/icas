.. index:: GET /category/{id}/funnel
.. _get_category_id_funnel:

GET /category/{id}/funnel
=========================

.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_ro`` or ``console_ro``

 * - Accept
   - ``application/sellside.funnel-v1+json, application/json``

This URL returns performance predictions such as number of impressions, clicks
and url clicks for a given category and cpc value.

The endpoint also returns information regarding the page on which a new ad
will be displayed if placed in the given category and with the given cpc
value (``pageNumber``). The response also contains a suggested cpc value to place an ad on page
one in this category (``averageCpc``). If ``cpc`` is greater than ``maxCpc`` then the ads of
this seller generally do not perform well enough to place new ads on the first
page.

If the expected performance of a category cannot be predicted yet, the server
returns a ``204 No Content`` response with empty body. This can happen when,
for instance, the category contains no ads yet from which to derive a
performance prediction.

The ``averageCpc`` field in the response marks the suggested cpc value to have place an ad on page one in this category.
We will rename this field in a future version of the endpoint to make this clearer.

Parameters
----------

====================    ========    ================================================================================
Name                    Type        Description
====================    ========    ================================================================================
cpc                     integer     The cpc value in euro cents for which to make the prediction. Mandatory field.
_include                string      Comma-separated-list of fields to include. Optional, default is all fields.
_exclude                string      Comma-separated-list of fields to omit. Optional, default empty.
====================    ========    ================================================================================

Errors
------

====================    ====    =======================     ==============================================================================
Field                   Code    Error message               Description
====================    ====    =======================     ==============================================================================
cpc                     2001    invalid argument            the provided value is not a valid number
====================    ====    =======================     ==============================================================================

Example
-------

.. include:: ../examples/get-category-id-funnel-example.rst