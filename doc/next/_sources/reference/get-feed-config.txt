.. index:: GET /feed/config
.. _get_feed_config:

GET /feed/config
================

:ref:`scopes` **console**

This URL returns the feed configuration of the current user. To use it set the
``Accept`` header to ``application/sellside.feedconfig-v1+json``.

.. note::

    Access to the feed functionality is granted per user by the Customer Care Center.
    Request to the this endpoint from unauthorized users will result in a
    **401 Unauthorized** response.

Errors
~~~~~~

====================    ====    =======================     ==============================================================================
Field                   Code    Error message               Description
====================    ====    =======================     ==============================================================================
-                       1008    access denied               The user is invalid
====================    ====    =======================     ==============================================================================

Example
~~~~~~~

.. include:: ../examples/get-feed-config-example.rst
