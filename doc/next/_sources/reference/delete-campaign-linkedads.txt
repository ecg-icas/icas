.. index:: DELETE /campaign/{id}/linkedAds
.. _delete_campaign_linkedads:

DELETE /campaign/{id}/linkedAds
===============================

It is possible to remove a :ref:`single <delete-single-linked-ad>` linkedAd or :ref:`multiple <delete-multiple-linked-ads>` linkedAds from a campaign in one go. Removing the linkedAd from a campaign does not remove the ad from your inventory; it only takes the ad offline for that particular campaign.


.. _delete-single-linked-ad:

Removing a single linkedAd:
-----------------------------

.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_rw`` or ``console_rw``

 * - Content-Type
   - ``application/sellside.campaign.linkedad-v1+json; charset=utf-8``

Removes a linkedAd from the campaign. If successful, the server responds with `HTTP 204`. TODO: yes or no (silently ignore nonexisting links): If the linkedAd does not exist, the server responds with `HTTP 404`.

.. include:: ../examples/delete-campaign-linkedads-v1-example.rst


.. _delete-multiple-linked-ads:

Removing multiple linkedAds:
-----------------------------

.. include:: ../examples/delete-campaign-linkedads-list-v1-example.rst
