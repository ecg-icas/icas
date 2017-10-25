.. index:: GET /ad/mapping/externalids
.. _get_ad_mapping_externalids:

GET /ad/mapping/externalids
===========================

:ref:`get_ad_mapping_externalids_v1`


.. _get_ad_mapping_externalids_v1:

GET /ad/mapping/externalids v1
------------------------------

.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_ro`` or ``console_ro``

 * - Accept
   - ``application/sellside.ad.external.id.mapping-v1+json, application/json``

This URL returns a map of adIds for the current user to the externalId the ad has.
This utility call is intended for uncommon usecases, such as when a client on-boards an already
existing admarkt user and needs to do a one-time sync of adIds vs externalIds, or
other cases where data got lost at the client.

.. warning::

	This call will only return mappings for non-deleted ads. Ads without externalId
	will also not be present in the resulting map.


The number of ads returned can be limited with the ``limit`` parameter.
The ``offset`` parameter allows to skip some ads and together with ``limit``
allows for pagination.

Parameters
~~~~~~~~~~

===============  ============     ============================================================================
Name             Type             Description
===============  ============     ============================================================================
limit            int              Limits the number of records returned. Default is 1000 and maximum is 10000.
offset           int              Skips the first N records.
===============  ============     ============================================================================

Example
-------

.. include:: ../examples/get-ad-mapping-externalids-v1-example.rst
