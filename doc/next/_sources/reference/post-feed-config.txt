.. index:: POST /feed/config
.. _post_feed_config:

POST /feed/config
=================

:ref:`scopes` **console**

The URL updates the feed configuration of the current user.

Parameters
~~~~~~~~~~

===============  ========    ============================================================================
Name             Type        Description
===============  ========    ============================================================================
_exclude         string      Comma-separated-list of fields to omit. Optional, default empty.
===============  ========    ============================================================================

Errors
~~~~~~

====================    ====    =======================     ==============================================================================
Field                   Code    Error message               Description
====================    ====    =======================     ==============================================================================
remainingBudget         2001    invalid argument            remaining budget is not an integer or an integer percentage (e.g. **10%**)
====================    ====    =======================     ==============================================================================

Example
~~~~~~~

.. include:: ../examples/post-feed-config-example.rst
