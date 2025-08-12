Ad statuses control whether your ads are eligible for serving and provide insight into why ads might not be active. Understanding these statuses is essential for managing your advertising campaigns effectively through our API.

.. image:: _static/ad-state-machine-api-partner.png
   :alt: Ad State Machine Diagram
   :align: center
   :scale: 80%

Ad Status Values
^^^^^^^^^^^^^^^^

Partner-Controllable Statuses
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

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

System-Managed Statuses
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

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

Status Precedence Rules
^^^^^^^^^^^^^^^^^^^^^^^

.. important::
   When multiple conditions affect an ad, we show the most actionable status for you as the advertiser.

Non-Budget Statuses Take Priority
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

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

Automatic Status Changes
^^^^^^^^^^^^^^^^^^^^^^^^

Budget Exhaustion
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

* **Total Budget**: When your ad's lifetime budget is fully spent, status changes to ``BUDGET_REACHED``
* **Daily Budget**: When today's spending limit is reached, status changes to ``DAILY_LIMIT_REACHED``
* **Reset**: Daily limits automatically reset at midnight; total budgets require manual increase

Domain Verification
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

**Trigger**: When you change an ad's URL to a domain we haven't verified for your account

**Process**:

1. Ad status automatically changes to ``DOMAIN_PENDING`` (overrides any previous status, including ``PAUSED``)
2. Verification email sent to your account
3. Click verification link to approve domain
4. **All ``DOMAIN_PENDING`` ads with that specific domain are set to ``ACTIVE`` status**

.. important::
   Domain verification always activates ads that are pending verification, regardless of their previous state. If you had paused an ad before changing its domain, the ad will become active after domain verification. Only ads currently in ``DOMAIN_PENDING`` status for that specific domain are affected - other ads using the same domain remain unchanged. You'll need to manually pause it again if desired.

.. note::
   **Domain Protection Availability**: 
   
   * Domain protection is currently **only available on Marktplaats**
   * Protection **only applies to ads managed through Console interface**
   * All status values and API responses work consistently across all platforms
   * Only the automatic transition to ``DOMAIN_PENDING`` and email verification process is platform-specific

Policy Enforcement
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

* **Automatic Review**: Our systems may flag ads for policy violations
* **Customer Support Action**: Violating ads may be suspended or removed
* **Recovery**: Suspended ads require content updates and support approval

Common Workflows
^^^^^^^^^^^^^^^^

Budget Management
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: text

   1. Ad serving normally (ACTIVE)
   2. Daily budget reached → DAILY_LIMIT_REACHED
   3. Options:
      - Wait for midnight reset → Returns to ACTIVE
      - Increase daily budget → Returns to ACTIVE
      - Pause campaign → Changes to PAUSED

Domain Change
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: text

   1. Update ad URL to new domain
   2. Status automatically changes to DOMAIN_PENDING (regardless of previous status)
   3. Check email for verification link
   4. Verify domain → Ad becomes ACTIVE (even if it was PAUSED before)
      Note: Only applies to Marktplaats ads managed via Console

Handling Suspensions
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: text

   1. Ad suspended → SUSPENDED_BY_CS
   2. Contact customer support for reason
   3. Update ad content to address violations
   4. Resubmit ad → Returns to ACTIVE (if approved)

API Integration Best Practices
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Status Polling
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

* **Check status regularly** if ad serving is critical
* **Budget statuses** can change throughout the day as spend accumulates
* **Domain pending** requires immediate action to resume serving

Error Handling
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

* **Invalid transitions**: API will reject attempts to set impossible statuses
* **Terminal states**: ``DELETED`` and ``DELETED_BY_CS`` cannot be changed
* **Suspended ads**: Cannot be directly activated - require content updates

Monitoring Recommendations
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

* **Set up alerts** for budget-related status changes
* **Monitor domain pending** notifications in your email
* **Track suspended ads** for policy compliance issues

Troubleshooting
^^^^^^^^^^^^^^^

Ad Not Serving?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

1. **Check status** - Only ``ACTIVE`` ads serve
2. **Budget issues** - Look for ``BUDGET_REACHED`` or ``DAILY_LIMIT_REACHED``
3. **Domain verification** - Check for ``DOMAIN_PENDING`` (Marktplaats Console only)
4. **Policy violations** - Look for ``SUSPENDED_BY_CS``

Status Won't Change?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

1. **Terminal states** (``DELETED``, ``DELETED_BY_CS``) cannot be modified
2. **System-managed statuses** cannot be directly set via API
3. **Suspended ads** require content updates, not just status changes

Unexpected Status Changes?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

1. **Budget exhaustion** happens automatically as spend accumulates
2. **Domain changes** trigger immediate verification requirements
3. **Policy reviews** can suspend ads without prior warning

Support
^^^^^^^

* **Technical integration**: Check API documentation for status field details
* **Policy questions**: Contact customer support for suspension reasons
* **Domain verification**: Check your registered email for verification links