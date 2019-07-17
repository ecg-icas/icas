.. index:: POST /campaign
.. _get_campaigns:

POST /campaign
==================

POST /campaign
---------------------

.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_rw`` or ``console_rw``

 * - Accept
   - ``application/sellside.campaign-v2+json``

 * - Content-Type
   - ``application/sellside.campaign-v2+json``   

Creates a new campaign for the user. If successful, it returns an object representing the campaign, with  default values on certain fields, if not provided. A minimum payload is an empty JSON.


.. include:: ../examples/post-campaign-example.rst

