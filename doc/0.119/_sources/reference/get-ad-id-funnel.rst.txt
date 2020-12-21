.. index:: GET /ad/{id}/funnel
.. _get_ad_id_funnel:

GET /ad/{id}/funnel
===================

.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_ro`` or ``console_ro``

 * - Accept
   - ``application/sellside.funnel-v1+json, application/json``

This URL returns performance predictions such as number of impressions, clicks
and url clicks for a given ad and cpc value.

The endpoint also returns information regarding the current page on which the
ad is displayed (``pageNumber``) and the required cpc value which would place the ad on page
one (``averageCpc``). If ``cpc`` is greater than ``maxCpc`` then this ad does not perform well
enough to be placed on page one.

If the performance of an ad cannot be predicted yet, the server returns a
``204 No Content`` response with an empty body. This can happen when, for
instance, the ad is the only one in a category and no reference ads exist yet
from which to derive a performance prediction.

The ``averageCpc`` field in the response marks the required cpc value to place the ad on page one in its category.
We will rename this field in a future version of the endpoint to make this clearer.

Parameters
----------

=============    ========    ============================================================================
Name             Type        Description
=============    ========    ============================================================================
cpc              integer     The cpc value in euro cents for which to make the prediction. Mandatory field.
_include         string      Comma-separated-list of fields to include. Optional, default is all fields.
_exclude         string      Comma-separated-list of fields to omit. Optional, default empty.
=============    ========    ============================================================================

Errors
------

====================    ====    =======================     ==============================================================================
Field                   Code    Error message               Description
====================    ====    =======================     ==============================================================================
cpc                     2001    invalid argument            the provided value is not a valid number
====================    ====    =======================     ==============================================================================

Example
-------

.. include:: ../examples/get-ad-id-funnel-example.rst
