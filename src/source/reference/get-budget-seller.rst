.. index:: GET /budget/seller
.. _get_budget_seller:

GET /budget/seller
==================

.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_ro`` or ``console_ro``

 * - Accept
   - ``application/sellside.amount-v1+json, application/json``

This URL returns the current value of the seller-level budget of the current
user. The ``amount`` field contains the value in cents. A ``null`` value for
``amount`` means there is no seller-level budget set for this seller.

Example
~~~~~~~

.. include:: ../examples/get-budget-seller-v1.rst
