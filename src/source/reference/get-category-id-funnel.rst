.. index:: GET /category/{id}/funnel
.. _get_category_id_funnel:

GET /category/{id}/funnel
=========================

:ref:`scopes` **read**

This URL returns performance predictions (such as number of impressions, clicks and url clicks) for a given category
and CPC value.

The endpoint also returns information regarding the page on which a new ad will be displayed on (if placed in the given
category and with the given CPC value). Suggested CPC value is also returned to indicate what CPC value should an ad have
in order to be placed on the first page.

If the expected performance of a category cannot be predicted yet, the server returns a ``204 No Content`` response
with empty body. This can happen when, for instance, the category contains no ads yet from which to derive a performance
prediction.

Parameters
----------

====================    ========    ================================================================================
Name                    Type        Description
====================    ========    ================================================================================
cpc                     integer     The CPC value in euro cents for which to make the prediction. Mandatory field.
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