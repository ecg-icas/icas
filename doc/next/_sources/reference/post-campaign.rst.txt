.. index:: POST /campaign
.. _post_campaign:

POST /campaign
==================

.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_rw`` or ``console_rw``

 * - Accept
   - ``application/sellside.campaign-v2+json``

 * - Content-Type
   - ``application/sellside.campaign-v2+json``   

Creates a new campaign for the user. If successful, it returns an object representing the campaign, with
default values on certain fields, if not provided. A minimum payload is an empty JSON, as none of the fields
are mandatory.

.. include:: ../examples/post-campaign-example.rst

The full campaign request payload model that can be provided, has the following structure:

.. include:: ../examples/campaign-request.rst


.. include:: ../examples/campaign-targeting.rst


The full campaign payload model that you get as a response, has the following structure:

.. include:: ../examples/campaign-response.rst
