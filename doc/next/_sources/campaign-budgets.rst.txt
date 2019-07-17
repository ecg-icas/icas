.. _campaign_budgets_overview:

Campaign Budgets
================

Budgets are used to limit spending for a campaign. Having no budgets means having **no** limits on the spending of a campaign.
When ads in this campaign receive clicks, all budgets of this campaign will be checked for remaining balance. In case balance
runs out on one or more budgets, all ads in this campaign will be taken offline until the balance is reset or
budgets are increased. The campaign will then be in status *BUDGET_REACHED*.

**TODO: what are sane default values for budgets?**

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

TOTAL
"""""

This is the total the campaign can spend and will **not** be reset periodically. The seller will explicitly need to change
this limit to get the ads of this campaign back online if this limit has been reached.
