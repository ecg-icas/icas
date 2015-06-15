.. index:: POST /feed/config
.. _post_feed_config:

POST /feed/config
=================

**Required Scope:** ``console_rw``

This URL updates the feed configuration of the current user. The feed configuration object must contain a boolean
field ``enabled``. Depending on its value the feed will be activated or disabled. If the
feed is being activated, the field ``feedUrl`` is mandatory and should contain a valid URL to a feed XML document.

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
feedUrl                 2006    invalid url                 The value of field 'feedUrl' is not a valid url
====================    ====    =======================     ==============================================================================

Example
~~~~~~~

.. include:: ../examples/post-feed-config-example.rst
