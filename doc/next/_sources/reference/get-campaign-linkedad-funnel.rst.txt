.. index:: GET /campaign/{id}/linkedAds/{adId}
.. _get_campaign_linkedads_funnel:

GET /campaign/{id}/linkedAds/{adId}/funnel
============================================

.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_ro`` or ``console_ro``

 * - Accept
   - ``application/sellside.campaign.linkedad.funnel-v1+json``

Returns several funnel metrics groups for the corresponding ad in the given campaign:

  (1) **performance**: provides predictions about the daily conversion activities (such as clicks, impressions) on the ad within the campaign.
  (2) **cpc**: provides a benchmark for a better guidance on setting an optimal CPC value, in the form of ``low``, ``medium`` (moderate), and ``high`` (more aggressive) field values, in cents. These numbers are based on CPC values that have been recently used by other competing ads. At the moment the competition encompasses other relevant ads within the same category, however, we reserve the right to change and improve the meaning. The ``firstPage`` field gives the currently required CPC value which would place the ad on the first page. If the suggested value is higher than the maximum allowed CPC value for the category, the ad currently does not perform well enough to be placed on the first page. **Note**: the ``high`` CPC suggestion can sometimes be even higher than the ``firstPage`` suggested one. The benchmark values are dependent on the current, as well as recent historical, competition dynamics.
  (3) **position**: provides the current position (page number) on which the ad is shown. This value can be highly volatile depending on the ad performance, as well as the competition dynamics.


If the performance of the ad within the campaign cannot be predicted yet, the server returns a ``204 No Content`` response.

If a ``cpc`` parameter value is supplied, that value is used (instead of the linkedAd one) for all the funnel numbers.

Parameters
~~~~~~~~~~

===============  ============     ===================================================================================
Name             Type             Description
===============  ============     ===================================================================================
cpc               integer          Optional cpc value, in euro cents, for which to provide the funnel calculations
===============  ============     ===================================================================================


Example:
--------

.. include:: ../examples/get-campaign-linkedads-funnel-example.rst

