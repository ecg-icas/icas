.. index:: single: Ad Status
.. _ad_status_overview:

Ad Status
=========

Each advertisement can be in one of the following states. Some of the states can be set by the user, others
are set by the system or by customer service.

User Controlled States
----------------------

.. index:: pair: Ad Status; ACTIVE
.. _ad_status_active:

ACTIVE
""""""

The ad is shown on the site.

.. index:: pair: Ad Status; PAUSED
.. _ad_status_paused:

PAUSED
""""""

The ad is not shown on the site and can be re-activated.

.. index:: pair: Ad Status; DELETED
.. _ad_status_deleted:

DELETED
"""""""

The ad has been deleted by the user and cannot be re-activated.

Customer Service States
-----------------------

.. index:: pair: Ad Status; DELETED_BY_CS
.. _ad_status_deleted_by_cs:

DELETED_BY_CS
"""""""""""""

The ad has been deleted by Customer Service and cannot be re-activated by the user. The seller should have received an email with an explanation for this status change.

.. index:: pair: Ad Status; SUSPENDED_BY_CS
.. _ad_status_suspended_by_cs:

SUSPENDED_BY_CS
"""""""""""""""

The ad has been paused by Customer Service and can be re-activated by the user by updating the ad to comply to the terms and conditions. The seller should have received an email with an explanation for this status change.

System States
-------------

.. index:: pair: Ad Status; BUDGET_REACHED
.. _ad_status_budget_reached:

BUDGET_REACHED
""""""""""""""

The **ad.spentBudget** has reached the **ad.totalBudget**. Therefore the ad is no longer shown on the site.

.. index:: pair: Ad Status; DAILY_BUDGET_REACHED
.. _ad_status_daily_budget_reached:

DAILY_BUDGET_REACHED
""""""""""""""""""""

The daily budget of the ad has been reached. For the rest of the day the ad will not be shown on the site.

.. index:: pair: Ad Status; DOMAIN_PENDING
.. _ad_status_domain_pending:

DOMAIN_PENDING
""""""""""""""

The ad will be put live after the seller confirms the domain the :ref:`ad_links_url` is pointing to.
The first time a seller uses a new domain, they will receive an email to confirm they want to create
an ad directing people to that domain (for security reasons).


