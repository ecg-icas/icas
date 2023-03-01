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
required and optional fields which are listed below:


======================================   ========== ============= ==================   =========   ========================
Field                                    Type       Deprecated in Constraints          Mandatory   Writable
======================================   ========== ============= ==================   =========   ========================
:ref:`ad_id`                             long       --            positive             --          no
:ref:`ad_title`                          string     --            see below            yes         yes
:ref:`ad_description`                    string     --            see below            yes         yes
:ref:`ad_categoryId`                     int        --            positive             yes         no
:ref:`ad_status`                         string     --            enum                 yes         yes
:ref:`ad_priceobj`                       object     --            yes                  yes         yes
:ref:`ad_priceobj_amountcents`           int        --            >= 0                 no          yes
:ref:`ad_priceobj_pricetype`             string     --            enum                 yes         yes
:ref:`ad_priceobj_priceunit`             string     --            string, see below    no          no
:ref:`ad_priceobj_originalamountcents`   int        --            >= 0, >amountCents   no          yes (if user is allowed)
:ref:`ad_salutation`                     string     --            enum                 yes         yes
:ref:`ad_sellerName`                     string     --            max. 60 chars        yes         yes
:ref:`ad_postcode`                       string     --            max. 6 chars         yes         yes
:ref:`ad_regionId`                       long       --            positive             no          yes (only during create)
:ref:`ad_phoneNumber`                    string     --            max. 32 chars        no          yes
:ref:`ad_allowContactByEmail`            bool       --            --                   no          yes
:ref:`ad_dateCreated`                    date       --            readonly             no          no
:ref:`ad_dateLastUpdated`                date       --            readonly             no          no
:ref:`ad_dateDeleted`                    date       --            readonly             no          no
:ref:`ad_links`                          object     --            see below            no          yes
:ref:`ad_links_self`                     string     --            max. 2048 chars      no          no
:ref:`ad_links_category`                 string     --            max. 2048 chars      no          no
:ref:`ad_links_url`                      string     --            max. 2048 chars      no          yes
:ref:`ad_links_displayUrl`               string     --            max. 256 chars       no          yes
:ref:`ad_images`                         array      --            max. 8 items         no          yes
:ref:`ad_attributes`                     array      --            --                   no          yes
:ref:`ad_shippingOptions`                array      --            see below            yes         yes
:ref:`ad_vendorId`                       string     --            max. 64 chars        no          yes (if not set already)
:ref:`ad_microTip`                       string     --            max. 18 chars        no          yes (if user is allowed)
:ref:`ad_campaignId`                     long       --            positive             see below   yes
:ref:`ad_bidMicros`                      string     --            see below            yes         yes
:ref:`ad_budgetsobj`                     object     --            see below            yes         yes
:ref:`ad_budgetsobj_daily`               object     --            see below            yes         yes
:ref:`ad_budgetsobj_total`               object     --            see below            yes         yes
:ref:`ad_budgetsobj_daily_limitMicros`   string     --            see below            yes         yes
:ref:`ad_budgetsobj_daily_spentMicros`   string     --            see below            no          no
:ref:`ad_budgetsobj_total_limitMicros`   string     --            see below            yes         yes
:ref:`ad_budgetsobj_total_spentMicros`   string     --            see below            no          no
:ref:`ad_externalId`                     string     V5            max. 64 chars        no          yes
:ref:`ad_currency`                       string     V5            cat.Currency         yes         no
:ref:`ad_priceType`                      string     V5            enum                 yes         yes
:ref:`ad_priceUnit`                      string     V5            see below            no          yes
:ref:`ad_price`                          long       V5            see below            see below   yes
:ref:`ad_cpc`                            long       V5            positive             yes	        yes
:ref:`ad_status_reasons`                 string     V5            --                   --          no
:ref:`ad_totalBudget`                    long       V5            positive             no          yes
:ref:`ad_dailyBudget`                    long       V5            positive             no          yes
:ref:`ad_dailySpent`                     long       V5            positive             --          no
:ref:`ad_spentBudget`                    long       V5            positive             --          no
:ref:`ad_pageNumber`                     int        V5            --                   no          no
:ref:`ad_suggestedCpcForPageOne`         long       V5            --                   no          no
:ref:`ad_allowPaypal`                    bool       V3            no                   yes         yes
======================================   ========== ============= ==================   =========   ========================

.. include:: bidding-micros.rst

.. index:: id
.. _ad_id:

id
""

Unique reference to the ad, needs to be omitted in a POST action.

.. index:: title
.. _ad_title:

title
"""""

Any string, with minimum and maximum length determined by the category. See :ref:`categories`. URLs are not allowed as part of the title.

.. index:: description
.. _ad_description:

description
"""""""""""

The description field of the ad.
Any string, with minimum and maximum length determined by the category. See :ref:`categories`. URLs are not allowed as part of the title.
All HTML elements except for the ones below will be removed:

.. code-block:: html

    <i> <em> <b> <strong> <ul> <li> <u> <br/>

.. index:: categoryId
.. _ad_categoryId:

categoryId
""""""""""

The category in which the ad is placed.

Each ad belongs to one and only one region and region of an ad cannot be updated.
This field can only set once during creation of an ad.

An integer value from the category list. Must be an id of a category with a
non-zero parent id.

.. index:: externalId
.. _ad_externalId:

externalId
""""""""""

.. warning::

    externalId is deprecated, please transition to :ref:`ad_vendorId`

Any non-empty string with a maximum length of 64 characters. When fetching
an existing ad which does not have an **externalId**, the field is empty or
omitted.

.. index:: status
.. _ad_status:

status
""""""

Is a valid value from the list of :ref:`ad_status_overview`. The user can set only one
of the user controlled states *ACTIVE*, *PAUSED* or *DELETED*.

.. index:: currency
.. _ad_currency:

currency
""""""""

The `ISO 4217`_ currency code. Currently only *EUR*, and *CAD*  supported.
All values are stored in cents (1/100 parts), i.e. EUR 10.50 are represented as 1050,
CAD 12.34 should be represented as 1234.
Deprecated in V5, all monetary values are in the currency of the country you are placing for.

.. index:: priceType
.. _ad_pricetype:

priceType
"""""""""

Must be a valid price type identifier from the list of :ref:`price_types`.
Deprecated in V5, use :ref:`ad_priceobj_pricetype` instead.

.. index:: priceUnit
.. _ad_priceunit:

priceUnit
"""""""""

Must be a valid price unit identifier from the list of available price units
of the category.
Deprecated in V5, use :ref:`ad_priceobj_priceunit` instead.

.. index:: price (integer)
.. _ad_price:

price
"""""

The meaning of the value depends on :ref:`ad_pricetype`. If it is
`FIXED_PRICE` or `BIDDING_FROM` then **price** has to be greater than 0.
The maximum allowed **price** is ``10000000000`` Euro cents (100.000.000 Euros).
Deprecated in V5, use :ref:`ad_priceobj` instead.

.. index:: price
.. _ad_priceobj:

price
"""""

Price is an object containing all the information about the cost of the item for sale.
This includes :ref:`ad_priceobj_amountcents`, :ref:`ad_priceobj_pricetype` :ref:`ad_priceobj_priceunit`
and :ref:`ad_priceobj_originalAmountCents`.

.. index:: price.amountCents
.. _ad_priceobj_amountcents:

price.amountCents
"""""""""""""""""

The cost of the item (without shipping costs) in cents.
The meaning of the value depends on :ref:`ad_priceobj_priceType`. If it is
`FIXED_PRICE` or `BIDDING_FROM` then **price.amountCents** has to be greater than 0.
The maximum allowed **price.amountCents** is ``10000000000`` Euro cents (100.000.000 Euros).

.. index:: price.priceType
.. _ad_priceobj_pricetype:

price.priceType
"""""""""""""""

Must be a valid price type identifier from the list of :ref:`price_types`.

.. index:: price.priceUnit
.. _ad_priceobj_priceunit:

price.priceUnit
"""""""""""""""

Must be a valid price unit identifier from the list of available price units
of the category.

.. index:: price.originalAmountCents
.. _ad_priceobj_originalAmountCents:

price.originalAmountCents
"""""""""""""""""""""""""

The cost of the item (without shipping costs) in cents, before discount was applied. Not available to
all users. Needs to be larger than :ref:`ad_priceobj_amountCents`.


.. index:: statusReasons
.. _ad_status_reasons:

statusReasons
"""""""""""""

used to indicate the reason why a certain ad might be set to a certain status by our system.
This could be due to, for example, an action (like new website domain approval) pending from the user, which is a mechanism used to prevent account takeovers from setting the website URL to a malicious one.
Deprecated in V4, :ref:`ad_status`'s enums have been expanded.

.. index:: campaignId
.. _ad_campaignId:

campaignId
""""""""""

identifier of the campaign this ad belongs to. See :ref:`campaigns` for more info.
For the time being this is not mandatory, and we will add the ad to the one-and-only campaign the seller has.
Once we will start allowing multiple campaigns for a seller, we will change this to become mandatory.
For the time being, we will also create the campaign underwater if the seller has no campaign created yet, to ensure
there is one for the seller.

.. index:: bidMicros
.. _ad_bidMicros:

bidMicros
"""""""""

The cost per click (bid) in micro-euros/micro-dollars as defined by the seller (10000 micro-euros == 1 cent). The minimum and maximum values
depend on the category. The type is string, allowing the seller to specify "AUTOMATIC", to let our system
take care of the bid and try to optimise costs vs clicks.


.. index:: cpc
.. _ad_cpc:

cpc
"""

The cost per click in cents as defined by the seller in cents. The minimum and maximum values
depend on the category. Deprecated, replaced by :ref:`ad_bidMicros` in V5.

.. index:: budgets
.. _ad_budgetsobj:

budgets
"""""""

a struct encapsulating both :ref:`ad_budgetsobj_daily` and :ref:`ad_budgetsobj_total`.

.. index:: ad_budgetsobj_daily
.. _ad_budgetsobj_daily:

budgets.daily
"""""""""""""

a struct encapsulating both :ref:`ad_budgetsobj_daily_limitMicros` and :ref:`ad_budgetsobj_daily_spentMicros`

.. index:: ad_budgetsobj_total
.. _ad_budgetsobj_total:

budgets.total
"""""""""""""

a struct encapsulating both :ref:`ad_budgetsobj_total_limitMicros` and :ref:`ad_budgetsobj_total_spentMicros`

.. index:: ad_budgetsobj_daily_limitMicros
.. _ad_budgetsobj_daily_limitMicros:

budgets.daily.limitMicros
"""""""""""""""""""""""""

the maximum amount this ad can spend today in micros, after which it will be taken offline for the remainder of the day.

.. index:: ad_budgetsobj_total_limitMicros
.. _ad_budgetsobj_total_limitMicros:

budgets.total.limitMicros
"""""""""""""""""""""""""

the maximum amount this ad can spend in micros, after which it will be taken offline until the seller increases the limit.

.. index:: ad_budgetsobj_daily_spentMicros
.. _ad_budgetsobj_daily_spentMicros:

budgets.daily.spentMicros
"""""""""""""""""""""""""

the amount spent in micros on this ad sofar, for today. Will be reset back to 0 at midnight.

.. index:: ad_budgetsobj_total_spentMicros
.. _ad_budgetsobj_total_spentMicros:

budgets.total.spentMicros
"""""""""""""""""""""""""

the amount spent in micros on this ad in its lifetime. Will be ever increasing and cannot be reset.

.. index:: totalBudget
.. _ad_totalBudget:

totalBudget
"""""""""""

The total budget for the ad. The minimum and maximum values depend on the
category. When an ad is updated this value cannot be lower than the
:ref:`ad_spentBudget`.
If the total budget is not returned with the ad, it means there is an unlimited total budget.
Deprecated, replaced by :ref:`ad_budgetsobj_total` in V5.

.. index:: dailyBudget
.. _ad_dailyBudget:

dailyBudget
"""""""""""

The daily budget for the ad. When this value is reached the ad will be paused
for the rest of the day. The minimum value depends on the category. Maximum value
cannot be higher than the :ref:`ad_totalBudget`
To disable the dailyBudget for an ad set it to ``null``.
Deprecated, replaced by :ref:`ad_budgetsobj_daily` in V5.

.. index:: dailySpent
.. _ad_dailySpent:

dailySpent
""""""""""

The budget spent for the ad since midnight.
Only provided when the :ref:`ad_dailyBudget` is not ``null`` and ``> 0``.
Deprecated, replaced by :ref:`ad_budgetsobj_daily_spentMicros` in V5.

.. index:: spentBudget
.. _ad_spentBudget:

spentBudget
"""""""""""

The total amount of the budget that has been used so far.
Deprecated, replaced by :ref:`ad_budgetsobj_total_spentMicros` in V5.

.. index:: salutation
.. _ad_salutation:

salutation
""""""""""

The salutation as used in emails. Must be a valid salutation identifier from
**MALE**, **FEMALE**, **COMPANY** or **FAMILY**

.. index:: sellerName
.. _ad_sellerName:

sellerName
""""""""""

Display name of the seller (max. 60 characters).

.. index:: postcode
.. _ad_postcode:

postcode
""""""""

Must be an non empty string.

.. index:: regionId
.. _ad_regionId:

regionId
""""""""

The region in which the ad is placed.
A long value from the region tree. Must be the id of a leaf region.

Each ad belongs to one and only one region and region of an ad cannot be updated.
This field can only set once during creation of an ad.

This field is mandatory if the `region` field of category configuration is ``MANDATORY``
and optional if the `region` field is ``OPTIONAL``.
This field must be omitted if the `region` field of category configuration is ``DISABLED``.

Please refer to :ref:`categories` and :ref:`regions`

.. index:: pageNumber
.. _ad_pageNumber:

pageNumber
""""""""""

Page number on which this ad is shown. Page number is highly volatile and
might change very quickly depending on the performance of the ad.

The fields :ref:`ad_pageNumber` and :ref:`ad_suggestedCpcForPageOne` are
currently expensive to compute. If you do not need their values consider
excluding them to speed up the response. To exclude the fields add the
following parameter to the request URL. ::

    ?_exclude=pageNumber,suggestedCpcForPageOne

Deprecated, removed in V5.

.. index:: suggestedCpcForPageOne
.. _ad_suggestedCpcForPageOne:

suggestedCpcForPageOne
""""""""""""""""""""""

Suggested CPC value in (euro/dollar) cents for this ad to be shown on page one.
This value is very volatile and might change very quickly depending on the
performance of the ad.

The fields :ref:`ad_pageNumber` and :ref:`ad_suggestedCpcForPageOne` are
currently expensive to compute. If you do not need their values consider
excluding them to speed up the response. To exclude the fields add the
following parameter to the request URL. ::

    ?_exclude=pageNumber,suggestedCpcForPageOne

Deprecated, removed in V5.

.. index:: phoneNumber
.. _ad_phoneNumber:

phoneNumber
"""""""""""

The phone number of the advertiser as international phone number format, e.g.
+31207894561 or as a local phone number, e.g. 06789456612. 0900 and 0800
numbers are not allowed.

.. index:: allowContactByEmail
.. _ad_allowContactByEmail:

allowContactByEmail
"""""""""""""""""""

Flag for allowing emails to be sent to the advertiser.

.. index:: allowPaypal
.. _ad_allowPaypal:

allowPaypal
"""""""""""

Flag for allowing PayPal as a payment option.
Deprecated, removed in V3.

.. index:: dateCreated
.. _ad_dateCreated:

dateCreated
"""""""""""

The `ISO 8601`_ UTC date and time the ad was created.

.. index:: dateLastUpdated
.. _ad_dateLastUpdated:

dateLastUpdated
"""""""""""""""

The `ISO 8601`_ UTC date and time the ad was last updated.

.. index:: dateDeleted
.. _ad_dateDeleted:

dateDeleted
"""""""""""

The `ISO 8601`_ UTC date and time the ad was deleted. Omitted if the ad is
still active or paused.

.. _ad_links:

links
"""""

An object encapsulating :ref:`ad_links_self`, :ref:`ad_links_category`, :ref:`ad_links_url` and :ref:`ad_links_displayUrl`

.. index:: links.self
.. _ad_links_self:

links.self
""""""""""

A link referencing the current ad. This will be provided by the Sellside API.

.. index:: links.category
.. _ad_links_category:

links.category
""""""""""""""

A link referencing the category the ad is placed in. This will be provided by
the Sellside API.

.. index:: links.url
.. _ad_links_url:

links.url
"""""""""

An external URL that is shown on the ad page. This must be a valid http(s)
url.

.. index:: links.displayUrl
.. _ad_links_displayUrl:

links.displayUrl
""""""""""""""""

The text/url that will be displayed instead of the url in :ref:`ad_links_url`.

.. index:: vendorId
.. _ad_vendorId:

vendorId
""""""""

Any non-empty string with a maximum length of 64 characters. Should be unique
per customer. Can either be set when creating an ad or when updating an
existing ad. However, once set, it can no longer be modified. When fetching an
existing ad which does not have a **vendorId**, the field is omitted.

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

shippingOptions example
"""""""""""""""""""""""

.. code-block:: javascript

    "shippingOptions": [
        {"type": "SHIP", "costCents": 0, "time":"2d-5d"},
        {"type": "PICKUP", "pickupLocation":"1097DN"}
     ]

.. _ad_example:

Ad Example
----------

.. include:: examples/get-ad-id-v5-example.rst