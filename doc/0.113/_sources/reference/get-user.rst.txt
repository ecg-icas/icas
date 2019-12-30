.. index:: GET /user
.. _get_user:

GET /user
=========
:ref:`get_user_v3` | :ref:`get_user_v1`

.. _get_user_v3:

GET /user v3
------------

.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_ro`` or ``console_ro``

 * - Accept
   - ``application/sellside.user-v3+json, application/json``

This URL returns information of the current user. The ``id`` field contains
a unique user identifier. The ``options.feed`` field is ``true`` if the user
is an XML feed customer. The ``options.vanityUrl`` field is ``true`` if the
value of the :ref:`ad_links_displayUrl` field in the advertisement is shown
in the search results. The ``hasAds`` field is ``false`` if the user has no ads at all (not even deleted).
The ``locations`` field contains the user (or webshop) locations.

Example
~~~~~~~

.. include:: ../examples/get-user-v3.rst

.. _get_user_v1:

GET /user v1
------------

.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_ro`` or ``console_ro``

 * - Accept
   - ``application/sellside.user-v1+json, application/json``

This URL returns information of the current user. The ``id`` field contains
a unique user identifier. The ``options.feed`` field is ``true`` if the user
is an XML feed customer. The ``options.vanityUrl`` field is ``true`` if the
value of the :ref:`ad_links_displayUrl` field in the advertisement is shown
in the search results.

Example
~~~~~~~

.. include:: ../examples/get-user-v1.rst
