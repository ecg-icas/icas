.. index:: single: Campaign Budgets
.. _campaign_budgets_overview:

Campaign Budgets
================

Each campaign can have 0 or more budgets. Without budgets, the ads in the campaign will not be shown.
When ads in this campaign receive clicks, all budgets will be checked for remaining balance. In case balance
runs out on one or more budgets, all ads in this campaign will be taken offline until the balance is reset or
budgets are increased. The campaign will then be in status *BUDGET_REACHED*.

Budget types
------------

.. index:: pair: Campaign Budget; Daily
.. _campaign_budget_daily:

DAILY
"""""

This is the maximum the campaign can spend per day. Resets every day, close to midnight.
If no daily budget is set, and a user _adds_ a daily budget, spent for this day will already be taken into account.

.. index:: pair: Campaign Budget; Monthly
.. _campaign_budget_monthly:

MONTHLY
"""""""

This is the maximum the campaign can spend per month. Resets every month, close to midnight of the 1st of the month.
If no monthly budget is set, and a user _adds_ a monthly budget, spent for this month will already be taken into account.
