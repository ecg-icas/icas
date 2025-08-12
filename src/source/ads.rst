.. index:: Ads, Advertisments
.. _ads:

Advertisements
==============

Advertisements or ads are the main resource on the Sellside API. You can
create (calling `POST /ad <https://ecg-icas.github.io/icas/openapi/index.html#/Ads/postAd>`_),
update and delete them (`PUT /ad/{adId} <https://ecg-icas.github.io/icas/openapi/index.html#/Ads/updateAdById>`_
and `PUT /ad/{adId}/status/{status} <https://ecg-icas.github.io/icas/openapi/index.html#/Ads/postAdStatus>`_ respectively),
and get a list of your ads matching various criteria (`GET /ad/ <https://ecg-icas.github.io/icas/openapi/index.html#/Ads/getListOfAdsWithFilters>`_)
Through the API you only have access to your own ads. Ads from other
advertisers are not accessible to you.

.. include:: bidding-micros.rst

.. _ad_status_guide:

.. include:: ad-status-guide.rst

.. _price_types:
..  include:: price-types.rst
