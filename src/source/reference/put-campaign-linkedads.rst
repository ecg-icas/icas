.. index:: PUT /campaign/{id}/linkedAds
.. _put_campaign_linkedads:

PUT /campaign/{id}/linkedAds
============================

It is possible to add/override a :ref:`single <single_linkedad>` linkedAd or :ref:`multiple <list_linkedad>` linkedAds to a campaign in one go.
If the campaign already has a linkedAd with the same adId, the existing linkedAd will be overriden with
the provided one.
It is not possible to have multiple linkedAds in one campaign with the same adId.
Setting linkedAds on a campaign in a ``DELETED`` state is not allowed.

A single linkedAd has the following request model structure:

.. include:: ../examples/campaign-ad-request.rst

.. _single_linkedad:

Adding/overriding a single linkedAd:
-------------------------------------

.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_rw`` or ``console_rw``

 * - Accept
   - ``application/sellside.campaign-linkedad-v1+json; charset=utf-8``

 * - Content-Type
   - ``application/sellside.campaign-linkedad-v1+json; charset=utf-8``

Adds a linkedAd to the campaign or overrides ones with same adIds. If successful, the server responds with `HTTP 200`.

.. include:: ../examples/put-campaign-linkedads-v1-example.rst
.. include:: ../examples/put-campaign-linkedads-v1-example2.rst


.. _list_linkedad:

Adding/overriding multiple linkedAds:
--------------------------------------

.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_rw`` or ``console_rw``

 * - Accept
   - ``application/sellside.campaign-linkedad-list-v1+json; charset=utf-8``

 * - Content-Type
   - ``application/sellside.campaign-linkedad-list-v1+json; charset=utf-8``

Adds multiple linkedAds to the campaign. Overrides existing linkedAds with same adIds. If successful, the server responds with `HTTP 200`.

.. include:: ../examples/put-campaign-linkedads-list-v1-example.rst
.. include:: ../examples/put-campaign-linkedads-list-v1-example2.rst

In the example above, the first linkedAd has no overrides, it merely links the ad to the campaign; the second linkedAd overrides the cpc value that the campaign may have as a setting; the third linkedAd overrides any campaign budgets with ones specific for that ad.