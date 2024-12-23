.. _ISO 4217: http://en.wikipedia.org/wiki/ISO_4217
.. _ISO 8601: http://en.wikipedia.org/wiki/ISO_8601
.. index:: Ads, Advertisments
.. _ads:

Advertisements
==============

Advertisements or ads are the main resource on the Sellside API. You can
create, update and delete them, change the status and get a list of your ads.
Through the API you only have access to your own ads. Ads from other
advertisers are not accessible to you.

.. _ad-fields:

Fields
------

..  role:: strike

Each ad has a unique identifier by which the ad can retrieved and a set of
required and optional fields, depending on the version of the API.

.. include:: bidding-micros.rst


.. index:: status
.. _ad_status:

status
""""""

Is a valid value from the list of :ref:`ad_status_overview`. The user can set only one
of the user controlled states *ACTIVE*, *PAUSED* or *DELETED*.


vendorId
""""""""

Any non-empty string with a maximum length of 64 characters. Please use simple latin-1 characters only.
Should be unique per customer. Can either be set when creating an ad or when updating an
existing ad. However, once set, it can no longer be modified. When fetching an
existing ad which does not have a **vendorId**, the field is omitted.
When an ad gets set to status ``DELETED``, this does **not** remove the vendorId.
This means that inserting a new ad with the same vendorId will still fail if you
already have an ad with that vendorId, regardless of its status. See :ref:`vendor_ids` for more explanation.

.. index:: microTip
.. _ad_microTip:

microTip
""""""""
A short freeform text with a maximum length of 18 characters, excluding any characters in ``.,/@#<>``.
It is a feature as part of a package that sellers can purchase (currently available only for Marktplaats tenant).
It provides extra attention on the ad in the search results.
At the time of writing, this will only have an effect on ads created via the Console.
However, it can be adjusted through the API.

.. index:: images
.. _ad_images:

Images
------
Each ad can contain up to X images (range is defined per category in the taxonomy)
which can be provided by the caller as a set of URLs. The system will download the images and if they meet the
requirements then they will be stored on our servers in several sizes
so that they can then be used by the user.

An image is valid if it is in JPG, PNG, GIF or BMP format and is smaller than 8MB
in size. Images larger than 1024x1024 px are being scaled down.

The images will be shown in the order they are provided. The first image is
shown in search results and it is the main image on the item page.

.. index:: image objects
.. _ad_image_objects:

Image Objects
"""""""""""""

When an ad is created or updated the caller provides the images as a list of
image objects which contain only the source url.

.. code-block:: javascript

    "images": [
        {
            "src": "http://www.ourshop.com/img/brother_fax_big.jpg",
        },
        ...
     ]

The images are then downloaded by the system and we add some additional
fields which describe the status of the download.

.. code-block:: javascript

    "images": [
        {
            "src": "http://www.ourshop.com/img/brother_fax_big.jpg",
            "status": "OK",
            "dateLastUpdated": "2012-09-10T13:11:05Z",
            "links": {
                "50x70": "//i.marktplaats.nl/image23434_abc.jpg",
                "120x180": "//i.marktplaats.nl/image23434_def.jpg",
            }
        }
        ...
     ]

The server adds a ``status`` field indicating the status of the download. The
status is either **OK** (image was successfully downloaded), **PENDING**
(image is scheduled to be downloaded) or **ERROR** if the image was not found
or invalid.

If the ``status`` is **OK** then a **links** map is added which contains
*protocol agnostic* links to copies on our servers of the uploaded image
in various sizes. The dimensions are specified as *max width* x *max height*.

The server also adds the ``dateLastUpdated`` field which specifies the time
the image was last updated.

.. note::

    The caller can provide all the fields added by the server since
    they will be ignored.

.. index:: attributes
.. _ad_attributes:

attributes
""""""""""

An optional list of :ref:`user_defined_attributes`.

.. index:: shippingOptions
.. _ad_shippingOptions:

shippingOptions
"""""""""""""""

A list of shipping options available for an ad.
Ads can contain maximum one shipping option per shipping option type.
Whether shipping options are disabled/optional/mandatory for an ad is configured per category, see :ref:`category_config_v2`.

Shipping option has the following fields:

.. list-table::
 :widths: 20 30 20 50
 :header-rows: 1

 * - Field
   - Mandatory
   - Deprecated in
   - Description

 * - `type`
   - Mandatory
   -
   - *SHIP* or *PICKUP*. *SHIP* means the item can be delivered to the buyer in the provided `time` and for the provided `cost`. *PICKUP* means the item can be picked up at the provided `location`.

 * - `cost`
   - Optional
   - V5
   - Deprecated, use costCents. Cost of shipping in cents. Only valid when type is *SHIP*. Must be greater than or equal to 0. Field can be omitted if costs are unknown.

 * - `costCents`
   - Optional
   -
   - Cost of shipping in cents. Only valid when type is *SHIP*. Must be greater than or equal to 0. Field can be omitted if costs are unknown.

 * - `time`
   - Optional
   -
   - Time it takes to deliver the ad. Only valid when type is *SHIP*. Supported values are "2d-5d", "6d-10d"  and everything in the form "<number>d" where <number> is > 0. Field can be omitted if time is unknown.

 * - `pickupLocation`
   - Mandatory when type is *PICKUP*
   -
   - Pick up location of the item, in :ref:`ad_postcode` structure.
