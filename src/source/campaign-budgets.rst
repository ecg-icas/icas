.. _campaign_budgets_overview:

Campaign Budgets
================

Budgets are used to limit the spending for an individual campaign. Your actual spent for a campaign may be lower than the limits you set, depending on a lot of factors; it can never be higher. Having no budgets means having **no** limits on the spending of a campaign.
When ads in this campaign receive clicks, all budgets of this campaign will be checked for remaining balance. In case balance
runs out on any one of the configured budgets, all ads in this campaign will be taken offline until the budget(s) balance is reset or budgets are increased. The campaign will then be in status *BUDGET_REACHED*.

**TODO: what are sane default values for budgets? Google gives some tips: start small if you're beginner**

Budget types
------------

.. index:: pair: Campaign Budget; Daily
.. _campaign_budget_daily:

DAILY
"""""

This is the maximum the campaign can spend per day. Resets every day, close to midnight.
If no daily budget is set, and you **add** a daily budget after the campaign has already been active, spent for this day will already be taken into account.

.. index:: pair: Campaign Budget; Monthly
.. _campaign_budget_monthly:

MONTHLY
"""""""

This is the maximum the campaign can spend per calendar month. Resets every month, close to midnight on the 1st of the month.
If no monthly budget is set, and you **add** a monthly budget after the campaign has already been active, spent for this month will already be taken into account.

TOTAL
"""""

This is the total the campaign can spend and will **not** be reset periodically. You will explicitly need to change this limit to get the ads of this campaign back online if this limit has been reached.
