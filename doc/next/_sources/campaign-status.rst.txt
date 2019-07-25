.. _campaign_status_overview:

Campaign Status
===============

Each campaign can be in one of the following states. Some of the states can be set by the user, others
are set by the system or by customer service.

User Controlled States
----------------------

.. list-table::
 :widths: 20 80
 :header-rows: 1

 * - Status
   - Description

 * - **ACTIVE**
   - The campaign is active and its linked ads are shown on the site.

 * - **PAUSED**
   - The campaign is not active and its linked ads are not shown on the site. The campaign can be re-activated, if there is sufficient budget. By default (unless explicitely set) the status of a newly-created campaign is ``PAUSED``.

System States
-------------

.. list-table::
 :widths: 20 80
 :header-rows: 1

 * - Status
   - Description

 * - **BUDGET_REACHED**
   - One or more of the campaign's budgets have been reached and its linked ads are not shown on site. In case of recurring budgets, like Daily or Monthly budgets, the budgets will be periodically automatically reset and the campaign will become active again. This status has a precedence only over the user-controlled status ``ACTIVE``; in other words, if the campaign is ``PAUSED`` (or ``DELETED``), while a campaign budget is reached (``BUDGET_REACHED``), the campaign will be shown as ``PAUSED`` (or ``DELETED``).


.. image:: _static/CampaignStates.png
  :align: center
  :alt: Campaign states
