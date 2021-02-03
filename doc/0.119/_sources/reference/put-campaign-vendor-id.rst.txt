.. index:: PUT /campaign/{id}/vendorId/{vendorId}
.. _put_campaign_vendor_id:

PUT /campaign/{id}/vendorId/{vendorId}
=======================================

.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_rw`` or ``console_rw``

 * - Accept
   - ``application/sellside.campaign-v2+json``


Updates the vendorId for the specified campaign. The value can be any non-empty string with maximum length of 64 characters.
This value is unique per seller, and can either be set when creating the campaign or when updating an existing one.
However, once set, it can no longer be modified. If the update is successful the endpoint returns the full updated campaign paylaod.

.. include:: ../examples/put-campaign-vendor-id-v2-example.rst
