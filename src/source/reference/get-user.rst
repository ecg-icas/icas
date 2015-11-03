.. index:: GET /user
.. _get_user:

GET /user
=========

.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_ro`` or ``console_ro``

 * - Accept
   - ``application/sellside.user-v1+json, application/json``

This URL returns information of the current user. The ``options.feed`` field
is ``true`` if the user is an XML feed customer. The ``options.vanityUrl``
field is ``true`` if the value of the :ref:`ad_links_displayUrl` field in the
advertisement is shown in the search results.

Example
~~~~~~~

.. include:: ../examples/get-user-v1.rst
