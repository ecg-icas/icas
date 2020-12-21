.. index:: GET /campaigns
.. _get_campaigns:

GET /campaigns
==================

.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_ro`` or ``console_ro``

 * - Accept
   - ``application/sellside.campaign.list-v2+json``

Returns a list of campaigns which belong to the user. At the moment there is a restriction of *at most* one campaign per seller. This restriction will be lifted-off in later stages.

..  include:: /campaign-restrictions.rst

Parameters
----------

====================    ========    =================================================================================================================================================
Name                    Type        Description
====================    ========    =================================================================================================================================================
status                  string      Coma-separated list of statuses to filter on. Valid campaign statuses are `ACTIVE` and `PAUSED`. By default no status filter is applied.
offset                  integer     Skips the first N campaigns. Default is 0.
limit                   integer     Indicates the number of campaigns to return. Default is 100. Valid values are positive numbers (>0).
====================    ========    =================================================================================================================================================

Example:
~~~~~~~~~

.. include:: ../examples/get-campaigns-example.rst

===================  =========================================================================================
Field                 Description
===================  =========================================================================================
``campaigns``         A list of campaign objects that match the request parameters filtering
``total``             The total number of campaigns that match the request parameters filtering 
===================  =========================================================================================

The full campaign object model has the following structure:

.. include:: ../examples/campaign-response.rst

