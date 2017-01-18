.. index:: GET /budget/seller
.. _get_budget_seller:

GET /budget/seller
==================

.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_ro`` or ``console_ro``

 * - Accept
   - ``application/sellside.seller.budget-v1+json, application/json``

In case a seller has a seller-level budget set up, this URL returns a JSON struct with two values.
The current (remaining) value of the seller-level budget of the current user is in the ``amount``
field, and whether ads should be paused or not because of it is in the ``adsPaused`` value.
The value of the (remaining) seller-level budget is in cents.
Please keep in mind that when the ``adsPaused`` value changes,
it can take a little while before the affected ads are all set to the correct status due
to asynchronicity.
If the user has no seller-level budget set up, an empty JSON struct will be returned.

Example
~~~~~~~

.. include:: ../examples/get-budget-seller-v1.rst
