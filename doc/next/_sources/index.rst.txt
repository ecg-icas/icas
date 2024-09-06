.. _Discord: https://discord.com

.. _index:

.. _introduction:

Introduction
============

This document describes the Sellside API to place ads.

The API is designed as a RESTful API supporting JSON as data formats.
Authentication is provided va OAuth2 to allow simple integration with existing
client libraries.

Help / Feedback
===============

If you have questions or would like to provide feedback, you can do so via our
`Discord`_ channel. Please talk to your contact at the tenant (local marketplace) to get access, this
is an **invite-only** chat channel. This channel is highly interactive, and contains
several of our developers as well so deeper technical support can also be found here.
Notifications about maintenance will also go through this channel.

Contents
========

.. toctree::
   :maxdepth: 2

   overview
   authentication
   ads
   campaigns
   categories
   attributes
   regions
   feeds
   feed-details
   reporting
   error-handling
   OpenAPI reference <https://ecg-icas.github.io/icas/openapi/index.html>
   release-notes
   migration-guide


.. _History:

History
=======

..  role:: strike

* v.0.129 - 6 Nov 2023 - tw

  * added GET /ad/count and GET /ad/histogram to openApi docs

* v.0.128 - 17 Oct 2023 - tw

  * added multi-campaign documentation, only available for Kleinanzeigen now though.
  * extra explanation on the 'vendorId' concept
  * extra explanation on `_include` and `_exclude`
  * fixes on some examples
  * added vendorId, title and isDefault to campaign V5 struct
  * more explanation on usage of pageToken
  * added some error codes

* v.0.127 - 9 May 2023 - pm

  * improved :ref:`feeds` docs
  * added separate :ref:`feed-details` page
  * added collapse feature to docs engine
  * added campaignID to supported dimension in reporting :ref:`metrics_reporting`
  * added error too many ads in the category to PUT /ad/{id}  :ref:`put_ad_id_v5`

* v.0.126 - 26 Apr 2023 - tw

  * improved :ref:`get_ad_v5` docs
  * added explanation about nextPageToken
  * added information about small difference in workings of ``_include`` and ``_exclude``

* v 0.126 - 2 Mar 2023 - pm

  * Improved XML feed description. Added "Fields" section with currently supported, and newly introduced (industry-accepted) fields in :ref:`feeds` section.

* v 0.125 - 26 Feb 2023 - dr

  * Added empty XML file generator API that guarantees a unique file name per download. This avoid the clash of previously pointing to a single hosted empty file. The download button has also been added in the :ref:`feeds` section.

* v.0.124 - 3 Jan 2023 - tw

  * Added ad V5 related endpoints
  * Added campaign related endpoints
  * removed GET /ad/ids docs as it's already gone
  * moved ``deprecation plan`` into :ref:`release_notes`

Indices and tables
==================

* :ref:`genindex`
* :ref:`search`
