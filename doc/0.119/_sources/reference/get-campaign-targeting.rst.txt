.. index:: GET /campaign/{id}/targeting

GET /campaign/{id}/targeting
============================

.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_ro`` or ``console_ro``

 * - Accept
   - ``application/sellside.campaign.targeting-v2+json, application/json``

Returns a :ref:`Campaign Targeting Object <campaign-targeting-object>` for the specified campaign. If the ``id`` is invalid, i.e., not a positive integer, the server returns *400 Bad Request.*

If the campaign is in DELETED status, `404 Not Found` is returned.

..  include:: /campaign-restrictions.rst

Example:
--------

.. include:: ../examples/get-campaign-targeting-example-v2.rst


TODO: after deciding on the interplay (see Campaign Targeting), maybe put additional stuff here
