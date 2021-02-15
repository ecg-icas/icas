.. index:: DELETE /campaign/{id}
.. _delete_campaign:

DELETE /campaign/{id}
===============================

It is possible to remove a campaign in one go. This does not remove the ads from your inventory; it only takes them offline for that particular campaign.

.. _delete-campaign:

.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_rw`` or ``console_rw``

 * - Content-Type
   - ``application/sellside.campaign-v2+json; charset=utf-8``

Removes a campaign completely. If successful, the server responds with `HTTP 204`.
If the campaign does not exist or does not belong to the user the server returns **404 Not Found**.

.. include:: ../examples/delete-campaign-v2-example.rst

