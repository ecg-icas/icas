.. index:: PUT /campaign/{id}/linkedAds
.. _put_campaign_linkedads:

PUT /campaign/{id}/linkedAds
============================

It is possible to add/overwrite a :ref:`single <single_linkedad>` linkedAd or :ref:`multiple <list_linkedad>` linkedAds in one go.
If the campaign already has a linkedAd with the same adId, the existing linkedAd will be overwritten with
the provided one.
It is not possible to have multiple linkedAds in one campaign with the same adId.

.. _single_linkedad:

Adding/overwriting a single linkedAd:
-------------------------------------

.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_rw`` or ``console_rw``

 * - Content-Type
   - ``application/sellside.campaign-linkedads-v1+json; charset=utf-8``

Adds a linkedAd to the campaign or overwrites ones with same adIds. If successful, the server responds with `HTTP 200`.

.. include:: ../examples/put-campaign-linkedads-v1-example.rst

.. _list_linkedad:

Adding/overwriting multiple linkedAds:
--------------------------------------

.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_rw`` or ``console_rw``

 * - Content-Type
   - ``application/sellside.campaign-linkedads-list-v1+json; charset=utf-8``

Adds multiple linkedAds to the campaign. Overwrites existing linkedAds with same adIds. If successful, the server responds with `HTTP 200`.

.. include:: ../examples/put-campaign-linkedads-list-v1-example.rst
