.. _campaign_budgets_overview:

Campaign Budgets
================

Budgets are used to limit the spending for an individual campaign. Your actual spent for a campaign may be lower than the limits you set, depending on a lot of factors; however, it can never be higher.
Campaign budgets **must be defined**, even if they are intended to be set to *unlimited*.
When campaign budgets are not set, the ads for this campaign will *not* be live.
When ads in this campaign receive clicks, all budgets of this campaign will be checked for remaining budget. In case the budget
runs out on any one of the configured budgets, all ads in this campaign will be taken offline until the budget(s) are reset or budget(s) limits are increased. The campaign will then be marked with the status *BUDGET_REACHED*.

Budget types
------------

.. _campaign-budget-types:


.. index:: pair: Campaign Budget; Daily
.. _campaign_budget_daily:

DAILY
"""""

This is the maximum the campaign can spend per day. Resets every day.
If no daily budget is set, and you **add** a daily budget after the campaign has already been active, spent for this day will already be taken into account.

.. index:: pair: Campaign Budget; Monthly
.. _campaign_budget_monthly:

MONTHLY
"""""""

This is the maximum the campaign can spend per calendar month. Resets every month, on the 1st of the month.
If no monthly budget is set, and you **add** a monthly budget after the campaign has already been active, spent for this month will already be taken into account.
Please note that the Admarkt Console does not show the monthly limits, even if they are set.

TOTAL
"""""

This is the total the campaign can spend and will **not** be reset periodically. You will explicitly need to change this limit to get the ads of this campaign back online if this limit has been reached. The total spent of the campaign so far will already be taken into account.
Please note that the Admarkt Console does not show the total limits, even if they are set.


.. _campaign-budgets-object:

Campaign Budgets Object
~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: javascript

   "budgets": {
        "daily": {
            "limit": <number>,
            "spent": <number>
            },
        "monthly": {
            "limit": <number>,
            "spent": <number>
        },
        "total": {
            "limit": <number>,
            "spent": <number>
        }
    }


===================  ============================================================================================================================================================================================================================================================================
Parameter             Description
===================  ============================================================================================================================================================================================================================================================================
``daily``              The maximum amount (in cents) that a campaign can spend per day (``limit``), and the current-day ``spent``. The ``spent`` amount value will be reset at midnight every day. If not set, the ``limit`` will be shown as **-1 (Unlimited)**.
``monthly``            The maximum amount (in cents) that a campaign can spend per calendar month (``limit``), and the current-month ``spent``. The ``spent`` value will be reset at the beginning of the month. If not set, the ``limit`` will be shown as **-1 (Unlimited)**.
``total``            The maximum amount (in cents) that a campaign can spend in its lifetime, and the current total ``spent``. The ``spent`` value will never be reset. If not set, the ``limit`` will be shown as **-1 (Unlimited)**.
===================  ============================================================================================================================================================================================================================================================================

