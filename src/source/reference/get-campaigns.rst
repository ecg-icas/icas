.. index:: GET /campaigns
.. _get_campaigns:

GET /campaigns
==================

GET /campaigns
---------------------

.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_ro`` or ``console_ro``

 * - Accept
   - ``application/sellside.campaign.list-v2+json``

Returns a list of campaigns which belong to the user.

Parameters
----------

====================    ========    ================================================================================
Name                    Type        Description
====================    ========    ================================================================================
status                  string      Coma-separated list of statuses to filter on. Valid campaign statuses can be found in :ref:`_campaign_status_overview`
====================    ========    ================================================================================

The format of the response is as below:

.. include:: ../examples/get-campaigns-example.rst

