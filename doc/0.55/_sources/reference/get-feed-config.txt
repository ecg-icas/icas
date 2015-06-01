.. index:: GET /feed/config
.. _get_feed_config:

GET /feed/config
================

:ref:`scopes` **console**

This URL returns the feed configuration of the current user. To use it set the
``Accept`` header to ``application/sellside.feedconfig-v1+json``.

An iCAS user can update his or her ads by describing them in an XML document, called **feed**.
The iCAS platform reads all user feeds once per day and synchronizes ads in the system.

The feed configuration object contains an ``enabled`` field. It is **true** when the current user
has enabled feed publication and **false** otherwise. When feed publication is enabled, the
feed configuration object contains a field ``feedUrl`` which contains the configured
feed url for the current user.

.. note::

    Access to the feed functionality may be granted per user by the Customer Service.
    Unauthorized user requests to the this endpoint will result in **401 Unauthorized**
    responses.

Errors
~~~~~~

====================    ====    =======================     ==============================================================================
Field                   Code    Error message               Description
====================    ====    =======================     ==============================================================================
--                      1008    access denied               The user is invalid
====================    ====    =======================     ==============================================================================

Example
~~~~~~~

.. include:: ../examples/get-feed-config-example.rst
