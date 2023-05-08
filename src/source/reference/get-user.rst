.. index:: GET /user
.. _get_user:

GET /user
=========
:ref:`get_user_v4` | :ref:`get_user_v3` | :ref:`get_user_v2`

.. warning::

    :ref:`get_user_v2` is now officially deprecated and scheduled for removal on May, 1st 2023. Please move to use :ref:`get_user_v4`.

    :ref:`get_user_v3` is now officially deprecated and scheduled for removal on May, 1st 2023. Please move to use :ref:`get_user_v4`.

This URL returns information of the current user. The ``id`` field contains
a unique user identifier. The ``options.feed`` field is ``true`` if the user
is an XML feed customer. The ``options.vanityUrl`` field is ``true`` if the
value of the :ref:`ad_links_displayUrl` field in the advertisement is shown
in the search results. The ``hasAds`` field is ``false`` if the user has no ads at all (not even deleted).
The ``locations`` field contains the user (or webshop) locations.
The ``isAPIManaged`` field is ``true`` when there is (at least one) API partner
using ``api-rw`` scope for this customer. API partners using ``api-ro`` only will not
count towards this value being ``true``.

.. _get_user_v4:

GET /user v4
------------

.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_ro`` or ``console_ro``

 * - Accept
   - ``application/sellside.user-v4+json, application/json``

Example
"""""""

.. include:: ../examples/get-user-v4.rst

.. _get_user_v3:

GET /user v3
------------

.. warning::

	This call is scheduled to be deprecated. Please use :ref:`get_user_v4` instead.

.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_ro`` or ``console_ro``

 * - Accept
   - ``application/sellside.user-v3+json, application/json``


Example
"""""""

.. include:: ../examples/get-user-v3.rst

.. _get_user_v2:

GET /user v2
------------

.. warning::

	This call is scheduled to be deprecated. Please use :ref:`get_user_v4` instead.

.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_ro`` or ``console_ro``

 * - Accept
   - ``application/sellside.user-v2+json, application/json``


Example
"""""""

.. include:: ../examples/get-user-v2.rst
