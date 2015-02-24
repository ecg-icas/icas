.. index:: GET /ad/{id}/funnel
.. _get_ad_id_funnel:

GET /ad/{id}/funnel
===================

:ref:`scopes` **read**

This URL returns performance predictions (such as number of impressions, clicks and url clicks) for a given ad and
CPC value.

The endpoint also returns information regarding the current page which the given ad
is displayed on and the suggested CPC value which would place the given ad on page 1.

If the performance of an ad cannot be predicted yet, the server returns a ``204 No Content`` response with empty body.
This can happen when, for instance, the ad is the only one in a category and no reference ads exist yet from which to
derive a performance prediction.

Parameters
----------

=============    ========    ============================================================================
Name             Type        Description
=============    ========    ============================================================================
cpc              integer     The CPC value in euro cents for which to make the prediction. Mandatory field.
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