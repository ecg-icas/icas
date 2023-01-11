.. _ISO 8601: http://en.wikipedia.org/wiki/ISO_8601
.. index:: Campaigns
.. _campaigns:

Campaigns
=========

A Campaign is a group of ads, sharing a campaign budget. With campaigns, it is possible to control spending for this entire list of ads and,
in one go, start/stop advertising with the entire list of (active) ads.
Campaigns can have their own budgets, both daily and total. If these are not set, they will automatically be set to "UNLIMITED" to
be compatible with the times when campaigns did not exist yet.

For the time being, we allow only 1 campaign per seller, effectively grouping _all_ the ads in that one campaign. 
To make transitions to use campaigns easier, we will ensure that each (new or existing) seller already has a campaign, and if the
seller has ads, these will be part of the campaign. 

You can get your campaign by calling :ref:`get_campaign` or :ref:`get_campaign_id`. Campaign budgets can be modified by using 
:ref:`put_campaign_id_budgets`, and controlling campaign status can be done by :ref:`put_campaign_id_status`. We expect to 
add more campaign functionality in the future.

.. _campaign-fields:

Fields
------

============================================   ========== ==================   =========   ========================
Field                                          Type       Constraints          Mandatory   Writable
============================================   ========== ==================   =========   ========================
:ref:`campaign_id`                             integer    positive,readonly    --          no
:ref:`campaign_status`                         string     enum                 yes         yes
:ref:`campaign_dateCreated`                    string     readonly             --          no
:ref:`campaign_dateLastUpdated`                string     readonly             --          no
:ref:`campaign_budgetsobj`                     []Budget   readonly             yes         yes
:ref:`campaign_budgetsobj_daily`               object     see below            yes         yes
:ref:`campaign_budgetsobj_total`               object     see below            yes         yes
:ref:`campaign_budgetsobj_daily_limitMicros`   string     see below            yes         yes
:ref:`campaign_budgetsobj_daily_spentMicros`   string     see below            no          no
:ref:`campaign_budgetsobj_total_limitMicros`   string     see below            yes         yes
:ref:`campaign_budgetsobj_total_spentMicros`   string     see below            no          no
============================================   ========== ==================   =========   ========================

.. index:: id
.. _campaign_id:

id
""

Unique reference to the campaign, needs to be omitted in a POST action. One of :ref:`campaign_status_overview`

.. index:: status
.. _campaign_status:

status
""""""

The status of the campaign, one of :ref:`campaign_status_overview`.


.. index:: dateCreated
.. _campaign_dateCreated:

dateCreated
"""""""""""

The `ISO 8601`_ UTC date and time the campaign was created.

.. index:: dateLastUpdated
.. _campaign_dateLastUpdated:

datLastUpdated
""""""""""""""

The `ISO 8601`_ UTC date and time the campaign was last updated.

.. index:: budgets
.. _campaign_budgetsobj:

budgets
"""""""

The budgets for this campaign. If either of these run out, ads from this campaign will no longer be
visible on site.

.. index:: budgets.daily
.. _campaign_budgetsobj_daily:

budgets.daily
"""""""""""""

The daily budget for the campaign. Includes :ref:`campaign_budgetsobj_daily_limitMicros` and :ref:`campaign_budgetsobj_daily_spentMicros`.

.. index:: budgets.total
.. _campaign_budgetsobj_total:

budgets.total
"""""""""""""

The total budget for the campaign. Includes :ref:`campaign_budgetsobj_total_limitMicros` and :ref:`campaign_budgetsobj_total_spentMicros`.

.. index:: budgets.daily.limitMicros
.. _campaign_budgetsobj_daily_limitMicros:

budgets.daily.limitMicros
"""""""""""""""""""""""""

The maximum amount all the ads combined in this campaign may spend per day. When this amount is reached, the ads in this campaign
will remain offline for the rest of the day.

.. index:: budgets.total.limitMicros
.. _campaign_budgetsobj_total_limitMicros:

budgets.total.limitMicros
"""""""""""""""""""""""""

The maximum amount all the ads combined in this campaign may spend. When this amount is reached, the ads in this campaign
will remain offline until this limit has been increased.

.. index:: budgets.daily.spentMicros
.. _campaign_budgetsobj_daily_spentMicros:

budgets.daily.spentMicros
"""""""""""""""""""""""""

The amount all the ads combined in this campaign have spent so far, today. This will be reset every day around midnight.

.. index:: budgets.total.spentMicros
.. _campaign_budgetsobj_total_spentMicros:

budgets.total.spentMicros
"""""""""""""""""""""""""

The amount all the ads combined in this campaign have spent so far. This will never be reset.

Example
-------

.. include:: examples/get-campaign-id-v5-example.rst