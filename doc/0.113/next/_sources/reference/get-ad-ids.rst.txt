.. index:: GET /ad/ids
.. _get_ad_ids:

GET /ad/ids
===========

:ref:`get_ad_ids_v1`


.. _get_ad_ids_v1:

GET /ad/ids v1
--------------

.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_ro`` or ``console_ro``

 * - Accept
   - ``application/sellside.ad.ids-v1+json, application/json``

This URL returns a list of adIds of ads with provided status for the current user.
This utility call is intended for uncommon usecases, such as when a client on-boards an already
existing admarkt user and needs to do a one-time import of adIds, or
other cases where data got lost at the client.

The ``status`` parameter allows the user to get only ad ids of ads having given status.

The number of ads returned can be limited with the ``limit`` parameter.
The ``offset`` parameter allows to skip some ads and together with ``limit``
allows for pagination.

Parameters
~~~~~~~~~~

===============  ============     ============================================================================
Name             Type             Description
===============  ============     ============================================================================
limit            int              Limits the number of records returned. Default is 1000 and maximum is 10000.
offset           int              Skips the first N records. Default 0.
status           list<string>     Limits the ad ids returned to ads with given status. Default ``ACTIVE``
===============  ============     ============================================================================

Example
-------

.. include:: ../examples/get-ad-ids-v1-example.rst
