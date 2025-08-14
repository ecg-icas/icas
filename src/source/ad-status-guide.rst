Ad statuses control whether your ads are eligible for serving and provide insight into why ads might not be active. Understanding these statuses is essential for managing your advertising campaigns effectively through our API.

.. image:: _static/ad-state-machine-api-partner.png
   :alt: Ad State Machine Diagram
   :align: center
   :scale: 80%

Ad status values
^^^^^^^^^^^^^^^^

API-controllable statuses
^^^^^^^^^^^^^^^^^^^^^^^^^

These statuses can be set directly through the API:

.. list-table::
   :header-rows: 1
   :widths: 15 25 15 25

   * - Status
     - Meaning
     - Ad Serving
     - Available Actions
   * - ``ACTIVE``
     - Ad is running and eligible for serving
     - ✅ **Serves**
     - Can pause or delete
   * - ``PAUSED``
     - Ad is temporarily stopped by you
     - ❌ Does not serve
     - Can activate or delete
   * - ``DELETED``
     - Ad is permanently removed by you
     - ❌ Does not serve
     - Cannot be changed

System-managed statuses
^^^^^^^^^^^^^^^^^^^^^^^

These statuses are set automatically by our system and cannot be directly changed via API:

.. list-table::
   :header-rows: 1
   :widths: 20 25 15 20

   * - Status
     - Meaning
     - Ad Serving
     - Resolution
   * - ``BUDGET_REACHED``
     - Total ad budget is exhausted
     - ❌ Does not serve
     - Increase total budget
   * - ``DAILY_LIMIT_REACHED``
     - Daily ad budget is exhausted
     - ❌ Does not serve
     - Wait for new day or increase daily budget
   * - ``DOMAIN_PENDING``
     - New domain requires verification (Marktplaats Console only)
     - ❌ Does not serve
     - Verify domain via email
   * - ``SUSPENDED_BY_CS``
     - Ad violates platform policies
     - ❌ Does not serve
     - Contact support and update ad content
   * - ``DELETED_BY_CS``
     - Ad permanently removed for violations
     - ❌ Does not serve
     - Cannot be restored

Status precedence rules
^^^^^^^^^^^^^^^^^^^^^^^

.. important::
   When multiple conditions affect an ad, we show the most actionable status for you as the advertiser.

Non-budget statuses take priority
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

If your ad has multiple issues, we prioritize showing you the status you can directly act upon:

.. list-table::
   :header-rows: 1
   :widths: 20 20 20 20

   * - Your Ad State
     - Budget Condition
     - Status Shown
     - Why
   * - You paused it
     - Daily budget reached
     - ``PAUSED``
     - You can unpause it
   * - Domain pending (Marktplaats Console)
     - Budget reached
     - ``DOMAIN_PENDING``
     - You need to verify domain
   * - Currently active
     - Daily budget reached
     - ``DAILY_LIMIT_REACHED``
     - Budget is the blocking issue
   * - Currently active
     - Total budget reached
     - ``BUDGET_REACHED``
     - Budget is the blocking issue

.. note::
   Budget-related statuses (``BUDGET_REACHED``, ``DAILY_LIMIT_REACHED``) are only shown when your ad would otherwise be ``ACTIVE``.

Automatic status changes
^^^^^^^^^^^^^^^^^^^^^^^^

Budget exhaustion
^^^^^^^^^^^^^^^^^

* **Total budget exhausted** → ``BUDGET_REACHED``
* **Daily budget exhausted** → ``DAILY_LIMIT_REACHED`` (resets at midnight)

Domain verification
^^^^^^^^^^^^^^^^^^^

1. URL changed to unverified domain → ``DOMAIN_PENDING``
2. Verify via email link → All pending ads for that domain become ``ACTIVE``

.. note::
   Domain verification activates all pending ads for that domain, regardless of previous status.

.. note::
   Domain protection only available on Marktplaats Console interface.

Policy enforcement
^^^^^^^^^^^^^^^^^^

* Policy violations → ``SUSPENDED_BY_CS`` or ``DELETED_BY_CS``
* Recovery requires content updates and support approval

Campaign status impact
^^^^^^^^^^^^^^^^^^^^^^

.. important::
   For an ad to be **visible to buyers**, both the ad status AND campaign status must allow serving:
   
   * **Campaign must be active** (not paused or out of budget)
   * **Ad must have a serving status** (``ACTIVE`` and not affected by budget/domain/CS restrictions)

Campaign status affects **ad visibility** (whether ads appear to buyers), not ad status itself. Individual ad statuses remain unchanged when campaign status changes.

**Key behaviors:**

* **Campaign paused or out of budget** → All ads in campaign become invisible to buyers
* **Individual ad statuses are never modified** by campaign status changes  
* **When campaign returns to active** → Ads return to visibility based on their individual statuses

Common workflows
^^^^^^^^^^^^^^^^

Budget management
^^^^^^^^^^^^^^^^^

* Daily budget reached → ``DAILY_LIMIT_REACHED`` (resets at midnight)
* Total budget reached → ``BUDGET_REACHED`` (increase budget to resume)

Domain change
^^^^^^^^^^^^^

* New domain → ``DOMAIN_PENDING`` (Marktplaats Console only)
* Verify via email → Becomes ``ACTIVE``

Handling suspensions
^^^^^^^^^^^^^^^^^^^^

* ``SUSPENDED_BY_CS`` → Update content and contact support → ``ACTIVE``

API integration best practices
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Status polling
^^^^^^^^^^^^^^

* Check status regularly for critical ads
* Budget statuses change as spend accumulates
* ``DOMAIN_PENDING`` requires immediate action

Error handling
^^^^^^^^^^^^^^

* API rejects invalid status transitions
* ``DELETED`` and ``DELETED_BY_CS`` are terminal states
* ``SUSPENDED_BY_CS`` requires content updates, not status changes

Monitoring recommendations
^^^^^^^^^^^^^^^^^^^^^^^^^^

* Alert on budget status changes
* Monitor ``DOMAIN_PENDING`` email notifications
* Track ``SUSPENDED_BY_CS`` for policy issues

Troubleshooting
^^^^^^^^^^^^^^^

Ad not serving?
^^^^^^^^^^^^^^^

1. Check ad status - only ``ACTIVE`` ads serve
2. Check campaign status - must be active
3. Look for ``BUDGET_REACHED``, ``DAILY_LIMIT_REACHED``, ``DOMAIN_PENDING``, ``SUSPENDED_BY_CS``

Status won't change?
^^^^^^^^^^^^^^^^^^^^

1. ``DELETED`` and ``DELETED_BY_CS`` are terminal
2. System-managed statuses cannot be set via API
3. ``SUSPENDED_BY_CS`` requires content updates

Unexpected status changes?
^^^^^^^^^^^^^^^^^^^^^^^^^^

1. Budget exhaustion happens automatically
2. Domain changes trigger verification
3. Policy reviews can suspend ads

Support
^^^^^^^

* Technical integration: API documentation
* Policy questions: Customer support
* Domain verification: Check email