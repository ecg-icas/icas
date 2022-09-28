.. index:: GET /campaign/{id}/ads/histograms
.. _get_campaign_ads/histogram:

GET /campaign/{id}/ads/histograms
====================================
.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_ro`` or ``console_ro``

 * - Accept
   - ``application/sellside.campaign.ads.histograms-v1+json``

Returns histogram values for one or more ad-specific attributes, for all ads in the context of a particular campaign.

Parameters
~~~~~~~~~~

===============  ============     ============================================================================
Name             Type             Description
===============  ============     ============================================================================
attributes        string          Comma-separated list of attributes to return histograms on. Currently supported values are: ``category`` and ``region``.
===============  ============     ============================================================================

Example
-------

.. include:: ../examples/get-campaign-ads-histograms-v1-example.rst


Errors
~~~~~~
.. include:: ../examples/get-campaign-ads-histograms-v1-example-errors.rst
