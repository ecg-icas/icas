.. _feed-details:

Feed Fields
===========

A set of required and optional fields defined by a feed for XML and TSV file formats are listed below.

.. collapse:: TSV

    ========================================= ==================================== ===================  ===========
    Field                                     Description                          Restrictions         Mandatory
    ========================================= ==================================== ===================  ===========
    :ref:`feed_vendorId`                      **unique** ad identifier             max. 64 chars        yes
    :ref:`feed_sellerName`                    your company name                    max. 60 chars        no
    :ref:`feed_t`                             item title                           :ref:`feed_t`        yes
    :ref:`feed_descr`                         item description                     :ref:`feed_descr`    yes
    :ref:`feed_categoryId`                    category identifier                  numeric, positive    yes
    :ref:`feed_status`                        desired status (default ACTIVE)      ACTIVE,PAUSED        no
    :ref:`feed_url`                           item URL                             max. 2048 chars      no
    :ref:`feed_vanityUrl`                     displayed URL                        max. 256 chars       no
    :ref:`feed_priceType`                     sales model for item                 enum                 yes
    :ref:`feed_price`                         item price in cents if applicable    positive integer     yes/no
    :ref:`feed_originalPrice`                 original price before discount       positive integer     no
    :ref:`image link <feed_media>`            primary image                        :ref:`feed_media`    no
    :ref:`additional image link <feed_media>` additional images                    :ref:`feed_media`    no
    :ref:`feed_attr`                          collection of item attributes        :ref:`feed_attr`     no
    :ref:`autobid <feed_budget>`              budget details                       :ref:`feed_budget`   no
    :ref:`cpc <feed_budget>`                  budget details                       :ref:`feed_budget`   no
    :ref:`total budget <feed_budget>`         budget details                       :ref:`feed_budget`   no
    :ref:`daily budget <feed_budget>`         budget details                       :ref:`feed_budget`   no
    :ref:`shipping <feed_ship>`               shipping options                     :ref:`feed_ship`     no
    :ref:`pickup location <feed_ship>`        pickup location                      :ref:`feed_ship`     no
    :ref:`feed_phoneNumber`                   phone number                         max. 32 chars        no
    :ref:`feed_emailAdvertiser`               allow emails to the seller           true,false           no
    :ref:`feed_regionId`                      only applicable for Kijiji Canada    numeric              no
    :ref:`feed_microTip`                      tiny item highlight                  max. 18 chars        no
    :ref:`feed_mpn`                           Manufacturer Part Number (MPN)       2-70 chars           no
    :ref:`feed_googleProductCategory`         google category for your item        string               no
    :ref:`feed_productType`                   item product type                    max. 750 chars       no
    :ref:`feed_brand`                         item brand name                      max. 70 chars        no
    :ref:`feed_gtin`                          Global Trade Identification Number   max. 50 chars        no
    :ref:`feed_itemGroupId`                   groups item variants                 max. 50 chars        no
    :ref:`feed_condition`                     condition of item                    enum                 no
    :ref:`feed_material`                      main item fabrics or materials       max. 200 chars       no
    :ref:`feed_energyEfficiencyClass`         energy efficiency class              enum                 no
    :ref:`feed_minEnergyEfficiencyClass`      minimal energy efficiency class      enum                 no
    :ref:`feed_maxEnergyEfficiencyClass`      maximal energy efficiency class      enum                 no
    :ref:`feed_color`                         item colors                          max. 100 chars       no
    :ref:`feed_gender`                        gender item is designed for          enum                 no
    :ref:`feed_ageGroup`                      age group item is intended for       enum                 no
    :ref:`feed_size`                          size information                     enum                 no
    :ref:`feed_unitPricingBaseMeasure`        denominator for item unit price      string               no
    :ref:`feed_unitPricingMeasure`            measure and dimension of item        string               no
    ========================================= ==================================== ===================  ===========

.. collapse:: XML

    ====================================== ==================================== ===================  ===========
    Field                                  Description                          Restrictions         Mandatory
    ====================================== ==================================== ===================  ===========
    :ref:`feed_vendorId`                   **unique** ad identifier             max. 64 chars        yes
    :ref:`feed_externalId`                 **deprecated**                       --                   --
    :ref:`feed_sellerName`                 your company name                    max. 60 chars        no
    :ref:`feed_t`                          item title                           :ref:`feed_t`        yes
    :ref:`feed_descr`                      item description                     :ref:`feed_descr`    yes
    :ref:`feed_categoryId`                 category identifier                  numeric, positive    yes
    :ref:`feed_status`                     desired status (default ACTIVE)      ACTIVE,PAUSED        no
    :ref:`feed_url`                        item URL                             max. 2048 chars      no
    :ref:`feed_vanityUrl`                  displayed URL                        max. 256 chars       no
    :ref:`feed_priceType`                  sales model for item                 enum                 yes
    :ref:`feed_price`                      item price in cents if applicable    positive integer     yes/no
    :ref:`feed_originalPrice`              original price before discount       positive integer     no
    :ref:`media <feed_media>`              item images                          :ref:`feed_media`    no
    :ref:`feed_attr`                       collection of item attributes        :ref:`feed_attr`     no
    :ref:`budget <feed_budget>`            budget details                       :ref:`feed_budget`   no
    :ref:`shipping options <feed_ship>`    shipping options                     :ref:`feed_ship`     no
    :ref:`feed_phoneNumber`                phone number                         max. 32 chars        no
    :ref:`feed_emailAdvertiser`            allow emails to the seller           true,false           no
    :ref:`feed_regionId`                   only applicable for Kijiji Canada    numeric              no
    :ref:`feed_microTip`                   tiny item highlight                  max. 18 chars        no
    :ref:`feed_mpn`                        Manufacturer Part Number (MPN)       2-70 chars           no
    :ref:`feed_googleProductCategory`      google category for your item        string               no
    :ref:`feed_productType`                item product type                    max. 750 chars       no
    :ref:`feed_brand`                      item brand name                      max. 70 chars        no
    :ref:`feed_gtin`                       Global Trade Identification Number   max. 50 chars        no
    :ref:`feed_itemGroupId`                groups item variants                 max. 50 chars        no
    :ref:`feed_condition`                  condition of item                    enum                 no
    :ref:`feed_material`                   main item fabrics or materials       max. 200 chars       no
    :ref:`feed_energyEfficiencyClass`      energy efficiency class              enum                 no
    :ref:`feed_minEnergyEfficiencyClass`   minimal energy efficiency class      enum                 no
    :ref:`feed_maxEnergyEfficiencyClass`   maximal energy efficiency class      enum                 no
    :ref:`feed_color`                      item colors                          max. 100 chars       no
    :ref:`feed_gender`                     gender item is designed for          enum                 no
    :ref:`feed_ageGroup`                   age group item is intended for       enum                 no
    :ref:`feed_size`                       size information                     enum                 no
    :ref:`feed_unitPricingBaseMeasure`     denominator for item unit price      string               no
    :ref:`feed_unitPricingMeasure`         measure and dimension of item        string               no
    ====================================== ==================================== ===================  ===========

|


.. index:: vendorId
.. _feed_vendorId:

vendor id
"""""""""

The **vendor id** field is the unique identifier of the ad. It is there to let us know, for consecutive imports, which
ads are the same. This results is allowing us to track and update an existing ad with the same **vendor id** instead
of creating a new ad.

The **vendor id** is mandatory and must be unique for each ad in the feed. Duplicate vendor ids are not allowed and will invalidate the entire feed, preventing further processing.

.. note::
   If an ad in the feed remains unchanged (compared to previous import, including image urls), we will skip over this ad and leave
   it unchanged in our system. This also means we will **not** attempt to download the images and process them again.
   This is an optimization that allows us to speed up processing significantly and cut down on calls to your image server.
   Any change in the ad (including it re-appearing in the feed if it wasn't present the previous time) will update the
   ad and trigger image re-processing.

.. collapse:: TSV

    Stored in **vendor id** column.

    ========= ================================================
     Example

                .. code-block:: text

                    15839942
    ========= ================================================

.. collapse:: XML

    ========= ================================================
    Example:

                .. code-block:: html

                    <admarkt:vendorId>15839942</admarkt:vendorId>
    ========= ================================================

|

Restrictions: Non-empty unique-per-ad string with a maximum of 64 characters.

.. index:: externalId
.. _feed_externalId:

external id
"""""""""""

Deprecated, replaced by vendorId

.. collapse:: XML

    .. warning::

        There is still an **external id** field in the XSD, this field is replaced by **vendor id**.
        Please update your XML to reflect this change. This makes naming consistent between feeds and sellside API.
        The ref:feed_vendorId field in the feeds has the same meaning and constraints as the **vendor id** field in the
        sellside API.

|

.. index:: sellerName
.. _feed_sellerName:

seller name
"""""""""""

Use the **seller name** field to communicate your company name to be displayed.

.. collapse:: TSV

    Stored in **seller name** column.

    ========= ================================================
     Example	 .. code-block:: text

                    Cups, Caps & Craps
    ========= ================================================

.. collapse:: XML

    ======= ======================================================
    Example
            .. code-block:: html

                <admarkt:sellerName>Cups, Caps &amp; Craps</admarkt:sellerName>
    ======= ======================================================

|

Restrictions: Maximum of 60 characters.

.. index:: title
.. _feed_t:

title
"""""

Use the title **title** field to clearly identify the item you are selling.
The title is one of the most prominent parts of your ad or free listing.
A specific and accurate title will help us show your item to the right buyers.

.. collapse:: TSV

    Stored in **title** column.

    ======= ====================================================
    Example
            .. code-block:: text

                Goedkope A-merk herenfietsen
    ======= ====================================================

.. collapse:: XML

    ======= ====================================================
    Example
            .. code-block:: html

                <admarkt:title>Goedkope A-merk herenfietsen</admarkt:title>
    ======= ====================================================

|

Restrictions: Minimum and maximum length determined by category, with a maximum of 1024 characters. See :ref:`categories`.
URLs are not allowed as part of the title.

.. index:: description
.. _feed_descr:

description
"""""""""""

Use the **description** field to tell buyers about the details of the item you are selling.

.. collapse:: TSV

    Stored in **description** column.
    Multiline descriptions must be quoted, or ending line characters, and tabulators escaped with \\n, \\t.

    ======= ====================================================
    Example
            .. code-block:: text

                "<p><strong><u>De goedkoopste webshop</u></strong>
                        <strong>voor tweedehands fietsen met garantie!
                        Gratis en rijklaar thuisbezorgd!</strong>
                    </p>
                    <p><strong><br></strong>
                    </p>
                    <ul>
                        <li><strong>Laagste prijsgarantie</strong></li>
                        <li>Fietsen <strong>100% rijklaar</strong>
                        gratis thuisbezorgd</li>
                        <li><strong>Ruime voorraad</strong>, voor ieder wat wils</li>
                        <li>Snelle <strong>customer service</strong>
                        via Whatsapp, bellen en e-mail</li>
                        <li>1 <strong>maand garantie</strong></li>
                        <li>Aangesloten bij <strong>Webwinkelkeur</strong></li>
                    </ul>
                    <strong><br></strong>
                    <p>Check dus snel onze website en vind de fiets die bij je past!<br>
                    </p>
                    <strong><br></strong>
                    <p>WhatsApp, bel of mail ons voor verdere vragen.
                    </p>"
    ======= ====================================================

.. collapse:: XML

    ======= =================================================================================
    Example .. code-block:: html

                <admarkt:description><![CDATA[
                    <p><strong><u>De goedkoopste webshop</u></strong>
                        <strong>voor tweedehands fietsen met garantie!
                        Gratis en rijklaar thuisbezorgd!</strong>
                    </p>
                    <p><strong><br></strong>
                    </p>
                    <ul>
                        <li><strong>Laagste prijsgarantie</strong></li>
                        <li>Fietsen <strong>100% rijklaar</strong>
                        gratis thuisbezorgd</li>
                        <li><strong>Ruime voorraad</strong>, voor ieder wat wils</li>
                        <li>Snelle <strong>customer service</strong>
                        via Whatsapp, bellen en e-mail</li>
                        <li>1 <strong>maand garantie</strong></li>
                        <li>Aangesloten bij <strong>Webwinkelkeur</strong></li>
                    </ul>
                    <strong><br></strong>
                    <p>Check dus snel onze website en vind de fiets die bij je past!<br>
                    </p>
                    <strong><br></strong>
                    <p>WhatsApp, bel of mail ons voor verdere vragen.
                    </p>]]>
                <admarkt:description/>
    ======= =================================================================================

|

Restrictions: Minimum and maximum length determined by the category. See :ref:`categories`.
URLs are not allowed as part of the description.
All HTML elements except for the ones below will be removed:

.. code-block:: html

    <u> <em> <ul> <li> <p> <strong> <br>


.. index:: categoryId
.. _feed_categoryId:

category id
"""""""""""

Use **category id** to place your item in the :ref:`categories` tree.

Each item belongs to one and only one category.

.. collapse:: TSV

    Stored in **category id** column.

    ========= ========================
     Example	 .. code-block:: text

                    PAUSED
    ========= ========================

.. collapse:: XML

    ======= ===========================================================
    Example .. code-block:: html

                 <admarkt:categoryId>945</admarkt:categoryId>
    ======= ===========================================================

|

Restrictions: An integer value from the category list. Must be an id of a leaf category with a
non-zero parent id.

.. index:: status
.. _feed_status:

status
""""""

Use **status** to change the state of your ad.

Must be one of the following:

====== ====================================================
Name   Description
====== ====================================================
ACTIVE The ad will be active (as long as there is budget for it) and it can be found on the marketplace.
PAUSED The ad will be paused, effectively not found on the marketplace.
====== ====================================================

The provided (desired) **status** may differ from the resulting one, depending on the other conditions.
For instance, budget may be depleted, or you may have too many active ads already in the category.

.. collapse:: TSV

    Stored in **status** column.

    ========= ========================
     Example	 .. code-block:: text

                    PAUSED
    ========= ========================

.. collapse:: XML

    ======= ===========================================================
    Example .. code-block:: html

                 <admarkt:status>PAUSED</admarkt:status>
    ======= ===========================================================

|

Restrictions: Allowed values are *ACTIVE*, *PAUSED*

.. index:: url
.. _feed_url:

url
"""

Utilize the **url** to establish a connection to your item page from the advertisement.
This represents an external URL, which will be displayed on the ad detail page or search result page.

.. collapse:: TSV

    Stored in **url** column.

    ========= ========================
     Example	 .. code-block:: text

                    https://www.bmw.de
    ========= ========================

.. collapse:: XML

    ======= ===========================================================
    Example .. code-block:: html

                 <admarkt:url>https://www.bmw.de</admarkt:url>
    ======= ===========================================================

|

Restrictions: Must be a valid http(s) url.

.. index:: vanityUrl
.. _feed_vanityUrl:

vanity url
"""""""""""

Use **vanity url** to provide the text for the :ref:`feed_url` link.

.. collapse:: TSV

    Stored in **vanity url** column.

    ========= ========================
     Example	 .. code-block:: text

                    BMW
    ========= ========================

.. collapse:: XML

    ======= ===========================================================
    Example .. code-block:: html

                 <admarkt:vanityUrl>BMW</admarkt:vanityUrl>
    ======= ===========================================================

|

.. index:: priceType
.. _feed_priceType:

price type
""""""""""

Use **price type** to define :ref:`pricing model<price_types>` for your item.

.. collapse:: TSV

    Stored in **price type** column.

    ========= ========================
     Example	 .. code-block:: text

                    FIXED_PRICE
    ========= ========================

.. collapse:: XML

    ======= ===========================================================
    Example .. code-block:: html

                 <admarkt:priceType>FIXED_PRICE</admarkt:priceType>
    ======= ===========================================================

|

Restrictions: Allowed Values are *BIDDING*, *BIDDING_FROM*, *FIXED_PRICE*, *FREE*, *NEGOTIABLE*, *SEE_DESCRIPTION*, *SWAP*, *CREDIBLE_BID*, *ON_DEMAND*, *NOT_APPLICABLE*, *RESERVED*

.. index:: price
.. _feed_price:

price
"""""

Use **price** to tell buyers the price of the item you are selling.
The meaning of the value depends on the :ref:`feed_priceType`.

If **price type** is `FIXED_PRICE` or `BIDDING_FROM` then **price** is mandatory and needs to be greater than 0.

.. collapse:: TSV

    Stored in **price** column.

    ========= ========================
     Example	 .. code-block:: text

                    1500
    ========= ========================

.. collapse:: XML

    ======= ===========================================================
    Example .. code-block:: html

                 <admarkt:price>1500</admarkt:price>
    ======= ===========================================================

|

Restrictions: The maximum allowed **price** value is ``10000000000`` given in ``cents`` of the local market currency. (100.000.000,00 EUR / CAD / ... ).

.. index:: originalPrice
.. _feed_originalPrice:

original price
""""""""""""""

Use **original price** to tell your item price before discount.
Ignored if a seller does not have a discount feature enabled.

.. collapse:: TSV

    Stored in **original price** column.

    ========= ========================
     Example	 .. code-block:: text

                    1500
    ========= ========================

.. collapse:: XML

    ======= ===========================================================
    Example .. code-block:: html

                 <admarkt:originalPrice>1500</admarkt:originalPrice>
    ======= ===========================================================

|

Restrictions: Must be greater than :ref:`feed_price`.
The maximum allowed **item price** value is ``10000000000`` given in ``cents`` of the local market currency (100.000.000,00 EUR / CAD / ... ).

.. index:: media
.. _feed_media:

item images
""""""""""""""

You can provide multiple images for your item.

All images will be resized if necessary to a size of maximum 1024px height and 1024px width (preserving the aspect ratio)
The system will download the images and, if they meet the requirements, store them on our servers in several sizes.

The **main image** is shown in search results and acts as the first image on the item page.
Additional images will be presented in the provided order in the item page.


.. collapse:: TSV

    Use **image link** column to provide the link to the **main image** of your item.

    ========= ========================
     Example	 .. code-block:: text

                    https://images.pexels.com/photos/62289.jpeg
    ========= ========================

    Use **additional image link** for more images of your item. Multiple values should be separate with commas.

    ========= ========================
     Example	 .. code-block:: text

                    https://images.pexels.com/photos/62290.jpeg,https://images.pexels.com/photos/62291.jpeg
    ========= ========================


.. collapse:: XML

    Use **<media>** tag for grouping your item images.
    **<media>** should contain from 0 to N **<image>** ordered elements.

    The first element is considered the **main image**

    ======= ===========================================================
    Example .. code-block:: html

                <admarkt:media>
                    <admarkt:image url="https://images.pexels.com/photos/62289/62289.jpeg"/>
                    <admarkt:image url="https://images.pexels.com/photos/47547/47547.jpeg"/>
                <admarkt:media/>
    ======= ===========================================================

|

Restrictions: Image number limit depends on the category in the tenant taxonomy

All URLs links must be complete, and pointing to an image on a publicly available web server.

Allowed image formats: JPEG, JPG, PNG, GIF\*, BMP.

\* Please note that GIFs are not recommended format as they are only 256 colors or less.
Also, animated GIFs and PNGs are not supported.

.. index:: attributes
.. _feed_attr:

attributes
""""""""""

Use **attributes** field to provide additional information on your item in a structured way,
by providing a list of item :ref:`user_defined_attributes` that can be used to influence the ad relevance.
You can provide an arbitrary number of **attributes** sharing the same structure.
When **attributes** are processed we check if there are is a match to any **attribute** defined at category level.
User-defined attributes that match a category's predefined key and value are automatically recognized as :ref:`category_attributes`.
For more information on **category attributes**, see :ref:`category_attributes_v2`.

.. collapse:: TSV

    .. note::
        In TSV format there is no way to directly specify the **attribute locale**.
        If the **attribute** is a  :ref:`category_attributes` (attributes that match category defined attributes),
        then the **attribute locale** defined at category level will be used.


    Use **attributes** column to provide a list of item attributes using the the format: *name*:*value*.

    ========= ========================
     Example	 .. code-block:: text

                    model:GXS32
    ========= ========================

    You can provide multiple attributes in a comma- separated list.

    ========= ========================
     Example	 .. code-block:: text

                    model:GXS32,screen size:32",touch:FALSE
    ========= ========================

    If the value represents a list, each list entry should be split by a comma, and the value needs to be enclosed in quotes.

    ========= ========================
     Example	 .. code-block:: text

                    model:GXS32,touch:FALSE,screen size:32",resolutions:"1024x768:24dpi,800x600:18dpi",type:"Slim,Pro"
    ========= ========================

.. collapse:: XML


    ======= ===========================================================
    Example .. code-block:: html

                <admarkt:attributes>
                    <admarkt:attribute>
                        <admarkt:attributeName>model</admarkt:attributeName>
                        <admarkt:attributeLocale>nl</admarkt:attributeLocale>
                        <admarkt:attributeLabel>model</admarkt:attributeLabel>
                        <admarkt:attributeValue>GXS32</admarkt:attributeValue>
                    </admarkt:attribute>
                    <admarkt:attribute>
                        <admarkt:attributeName>screen size</admarkt:attributeName>
                        <admarkt:attributeLocale>nl</admarkt:attributeLocale>
                        <admarkt:attributeLabel>screen size</admarkt:attributeLabel>
                        <admarkt:attributeValue>32"</admarkt:attributeValue>
                    </admarkt:attribute>
                    <admarkt:attribute>
                        <admarkt:attributeName>touch screen</admarkt:attributeName>
                        <admarkt:attributeLocale>nl</admarkt:attributeLocale>
                        <admarkt:attributeLabel>touch screen</admarkt:attributeLabel>
                        <admarkt:attributeValue>FALSE"</admarkt:attributeValue>
                    </admarkt:attribute>
                    <admarkt:attribute>
                        <admarkt:attributeName>resolutions</admarkt:attributeName>
                        <admarkt:attributeLabel>resolutions</admarkt:attributeLabel>
                        <admarkt:attributeValue>1024x768:24dpi</admarkt:attributeValue>
                        <admarkt:attributeValue>800x600:18dpi</admarkt:attributeValue>
                    </admarkt:attribute>
                    <admarkt:attribute>
                        <admarkt:attributeName>type</admarkt:attributeName>
                        <admarkt:attributeValue>Slim</admarkt:attributeValue>
                        <admarkt:attributeValue>Pro</admarkt:attributeValue>
                    </admarkt:attribute>
                </admarkt:attributes>
    ======= ===========================================================

|

.. index:: budgetDetails
.. _feed_budget:

budget details
""""""""""""""

Use *budget details* to tell us what is your preferred model for budgeting your ad.
Use the following values to describe your model:

============= ========================================== ========
Name          Description                                Mandatory
============= ========================================== ========
autobid       use auto bidding option true/false         No
cpc           CPC for the given ad in cents              No
total budget  total budget for the given ad in cents     No
daily budget  daily budget for the given ad in cents     No
============= ========================================== ========


.. collapse:: TSV

    Use **autobid** column for your choice on that option.

    ========= ========================
     Example	 .. code-block:: text

                    true
    ========= ========================

    Use **cpc** to provide your cost per click in cents.

    ========= ========================
     Example	 .. code-block:: text

                    105
    ========= ========================

    Use **total budget** column to determine total budget for your ad.

    ========= ========================
     Example	 .. code-block:: text

                    5000
    ========= ========================

    Use **daily budget** column to determine daily budget for your ad.

    ========= ========================
     Example	 .. code-block:: text

                    1000
    ========= ========================

.. collapse:: XML

    ======= ===========================================================
    Example .. code-block:: html

                <admarkt:budget>
                    <admarkt:totalBudget>5000</admarkt:totalBudget>
                    <admarkt:dailyBudget>1000</admarkt:dailyBudget>
                    <admarkt:cpc>2</admarkt:cpc>
                </admarkt:budget>
    ======= ===========================================================

|

Restrictions: The minimum and maximum values for the total budget depend on the category.

If the total budget provided in the ad is lower than the total amount already spent, the ad will automatically be paused.

When this value of the daily budget is reached the ad will be offline for the rest of the day, and re-activated at the beginning of the following day, unless more money is added during the same day.
The minimum value depends on the category.

The minimum and maximum values of the cost per click (CPC) depend on the category.

.. index:: shippingOptions
.. _feed_ship:

shipping & pick-up
""""""""""""""""""

Use **shipping options** to inform buyers about item delivery details
Each option can be described with the following information:

============= ========================================== ========
Name          Description                                Mandatory
============= ========================================== ========
shippingType  SHIP, PICKUP                               Yes
cost          cost of shipping in cents                  No
time          time it takes to deliver the item          No
location      pick up location of the item               Yes if PICKUP
============= ========================================== ========

*SHIP* means the item can be delivered to the buyer in the provided `time` and for the provided `cost`.
*PICKUP* means the item can be picked up by the buyer in the provided `location`.
For *SHIP* provide 'cost' in cents and 'time' in days, 'location' is ignored.
For *PICKUP* provide 'location', 'cost' and 'time' are ignored.

The **'time'** field must be represented through the following formats, applicable for both TSV and XML:

   - literal values: **2d-5d** and **6d-10d**. These default values represent [*minimum transit time in days*]-[*maximum transit time in days*] options.
   - format: **<number (not starting with 0)>d**. The format represents [*transit time in days*] only (without minimum/maximum components).


.. collapse:: TSV

    Use **shipping** field to tell buyers about the different cost vs. time options for your item delivery.

    Each option should be formatted as follows:

       [*cost in cents*]:[*<time>*]


    ========= ========================
     Example	 .. code-block:: text

                    695:2d-5d
                    695:6d-10d
                    695:1d
                    695:12d
                    695:123d
    ========= ========================


    Use **pickup location** field to tell buyers the `location` your item can be picked up at.
    Location is given as a postal code.

    ========= ========================
     Example	 .. code-block:: text

                    1097DN
    ========= ========================

.. collapse:: XML


    ======= ===========================================================
    Example .. code-block:: html

                <admarkt:shippingOptions>
                    <admarkt:shippingOption>
                        <admarkt:shippingType>SHIP</admarkt:shippingType>
                        <admarkt:cost>695</admarkt:cost>
                        <admarkt:time>6d-10d</admarkt:time>
                    </admarkt:shippingOption>
                </admarkt:shippingOptions>

                <admarkt:shippingOptions>
                    <admarkt:shippingOption>
                        <admarkt:shippingType>PICKUP</admarkt:shippingType>
                        <admarkt:location>1097DN</admarkt:location>
                    </admarkt:shippingOption>
                </admarkt:shippingOptions>
    ======= ===========================================================

|

Restrictions: Shipping options can be disabled/optional/mandatory for an item.
An item can contain a maximum one shipping option per shipping option type (SHIP/PICKUP).
Shipping options are configured per category, see :ref:`category_config_v2`.

.. index:: phoneNumber
.. _feed_phoneNumber:

phone number
""""""""""""

Use the **phone number** field to allow buyers to call you and ask about the item.

.. collapse:: TSV

    Stored in **phone number** column.

    ========= ========================
     Example	 .. code-block:: text

                    +31207894561
    ========= ========================

.. collapse:: XML

    ======= ===========================================================
    Example .. code-block:: html

                 <admarkt:phoneNumber>+31207894561</admarkt:phoneNumber>
    ======= ===========================================================

|

Restrictions: The number should be given as an international phone number format, e.g. +31207894561 or as a local phone number, e.g. 06789456612.

.. index:: emailAdvertiser
.. _feed_emailAdvertiser:

email advertiser
""""""""""""""""

Use the **email advertiser** flag to allow buyers to contact you via email (or the other platform defined form of contact), and ask about the item.
The default value is false.

.. collapse:: TSV

    Stored in **email advertiser** column.

    ========= ========================
     Example	 .. code-block:: text

                    true
    ========= ========================

.. collapse:: XML

    ======= ===========================================================
    Example .. code-block:: html

                 <admarkt:emailAdvertiser>true</admarkt:emailAdvertiser>
    ======= ===========================================================

|

Restrictions: Allowed values *true* and *false*

.. index:: regionId
.. _feed_regionId:

region id
"""""""""

The region in which the ad is placed. (only applicable for Kijiji Canada)

Each ad belongs to one and only one region and region of an ad cannot be updated.
This field can only be set once during creation of an ad.

.. collapse:: TSV

    Stored in **region id** column.

    ========= ========================
     Example	 .. code-block:: text

                    1700274
    ========= ========================

.. collapse:: XML

    ======= ===========================================================
    Example .. code-block:: html

                 <admarkt:regionId>1700274</admarkt:regionId>
    ======= ===========================================================

|

Restrictions: An integer value from the region tree. Must be the id of a leaf region.

This field is mandatory if the `region` field of category configuration is ``MANDATORY``
and optional if the `region` field is ``OPTIONAL``.
This field must be omitted if the `region` field of category configuration is ``DISABLED``.

Please refer to :ref:`categories` and :ref:`regions`

.. index:: microTip
.. _feed_microTip:

micro tip
"""""""""

**Micro tip** is a short freeform text, that can be shown as a highlight on your ad image.
It is a feature enabled as part of a package that sellers can purchase (currently available only for Marktplaats tenant).
It provides extra attention on the ad in the search results.

If *micro tip* feature is not enabled for the seller, the field will be ignored.

.. collapse:: TSV

    Stored in **micro tip** column.

    ========= ========================
     Example	 .. code-block:: text

                    TODAY 15% SALE
    ========= ========================

.. collapse:: XML

    ======= ===========================================================
    Example .. code-block:: html

                 <admarkt:microTip>TODAY 15% SALE</admarkt:microTip>
    ======= ===========================================================

|

Restrictions: Maximum of 18 characters.
The characters ``.,/@#<>`` are not allowed.

.. index:: mpn
.. _feed_mpn:

MPN
"""

Manufacturer Part Number (MPN), definition follows `Google Merchant Center <https://support.google.com/merchants/answer/6324482>`__ guidelines.

.. collapse:: TSV

    Stored in **mpn** column.

    ========= ========================
     Example	 .. code-block:: text

                    AB12345R89TN6E
    ========= ========================

.. collapse:: XML

    ======= ===========================================================
    Example .. code-block:: html

                 <admarkt:mpn>AB12345R89TN6E</admarkt:mpn>
    ======= ===========================================================

|

Restrictions: Maximum of 70 characters.

.. index:: googleProductCategory
.. _feed_googleProductCategory:

google product category
"""""""""""""""""""""""

Use this field to describe your item category in Google's product taxonomy.
See `Google Merchant Center <https://support.google.com/merchants/answer/6324436>`__


.. collapse:: TSV

    Stored in **google product category** column.

    ========= ========================
     Example	 .. code-block:: text

                    Apparel > Accessories > Clothing > Dresses
     Example	 .. code-block:: text

                    2271
    ========= ========================

.. collapse:: XML

    ======= ===========================================================
    Example .. code-block:: html

                 <admarkt:googleProductCategory>
                    Apparel &amp; Accessories &gt; Clothing &gt; Dresses
                </admarkt:googleProductCategory>
    Example .. code-block:: html

                 <admarkt:googleProductCategory>2271</admarkt:googleProductCategory>
    ======= ===========================================================

|

Restrictions: Should be a valid category. You can provide it using the identifier, or the full category path.

.. index:: productType
.. _feed_productType:

product type
""""""""""""""""""""""

The **product type** field allows you to incorporate your item unique product type classification system into the dataset.
Definition follows `Google Merchant Center <https://support.google.com/merchants/answer/6324406>`__ guidelines.

.. collapse:: TSV

    Stored in **product type** column.

    ========= ========================
    Example	  .. code-block:: text

                    Home > Women > Dresses > Maxi Dresses
    ========= ========================

.. collapse:: XML

    ======= ===========================================================
    Example .. code-block:: html

                 <admarkt:productType>
                    Home &gt; Women &gt; Dresses &gt; Maxi Dresses
                </admarkt:productType>
    ======= ===========================================================

|

Restrictions: Maximum of 750 characters.

.. index:: brand
.. _feed_brand:

brand
""""""""""""""""""""""

Use the **brand** field to help buyers identify your item.
Brand definition follows `Google Merchant Center <https://support.google.com/merchants/answer/6324351>`__ guidelines.

.. collapse:: TSV

    Stored in **brand** column.

    ========= ========================
     Example	 .. code-block:: text

                    iPhone
    ========= ========================

.. collapse:: XML

    ======= ===========================================================
    Example .. code-block:: html

                 <admarkt:brand>iPhone</admarkt:brand>
    ======= ===========================================================

|

Restrictions: Maximum of 70 characters.

.. index:: gtin
.. _feed_gtin:

GTIN
""""""""""""""""""""""

GTIN (Your item’s Global Trade Item Number), definition follows `Google Merchant Center <https://support.google.com/merchants/answer/6324461>`__ guidelines.

.. collapse:: TSV

    Stored in **gtin** column.

    ========= ========================
     Example	 .. code-block:: text

                    44320194113475
    ========= ========================

.. collapse:: XML

    ======= ===========================================================
    Example .. code-block:: html

                 <admarkt:gtin>44320194113475</admarkt:gtin>
    ======= ===========================================================

|

Restrictions: Maximum of 50 characters.

.. index:: itemGroupId
.. _feed_itemGroupId:

item group id
""""""""""""""""""""""

Use this field to group item variants in your item data.
Item group id definition follows `Google Merchant Center <https://support.google.com/merchants/answer/6324507>`__ guidelines.

.. collapse:: TSV

    Stored in **conditionitem group id** column.

    ========= ========================
     Example	 .. code-block:: text

                    BC23456
    ========= ========================

.. collapse:: XML

    ======= ===========================================================
    Example .. code-block:: html

                <admarkt:itemGroupId>BC23456</admarkt:itemGroupId>
    ======= ===========================================================

|

Restrictions: Maximum of 50 characters.

.. index:: condition
.. _feed_condition:

condition
""""""""""""""""""""""

Use this field to inform buyers about the condition of your item. Condition definition follows `Google Merchant Center <https://support.google.com/merchants/answer/6324469>`__ guidelines.

.. collapse:: TSV

    Stored in **condition** column.

    ========= ========================
     Example	 .. code-block:: text

                    used
    ========= ========================

.. collapse:: XML

    ======= ===========================================================
    Example .. code-block:: html

                <admarkt:condition>used</admarkt:condition>
    ======= ===========================================================

|

Restrictions: Accepted values are *new*, *refurbished*, *used*

.. index:: material
.. _feed_material:

material
""""""""""""""""""""""

**Material** field describes the main fabric or material that your item is made of.
Material definition follows `Google Merchant Center <https://support.google.com/merchants/answer/6324410>`__ guidelines.

.. collapse:: TSV

    Stored in **material** column.

    ========= ========================
     Example	 .. code-block:: text

                    Cotton/Silk
    ========= ========================

.. collapse:: XML

    ======= ===========================================================
    Example .. code-block:: html

                <admarkt:material>Cotton/Silk</admarkt:material>
    ======= ===========================================================

|

Restrictions: Use human readable material names. Provide up to 3 materials.
When providing multiple materials separate each entry with a slash (“/”).
Maximum of 70 characters.


.. index:: energyEfficiencyClass
.. _feed_energyEfficiencyClass:

energy efficiency class
"""""""""""""""""""""""

Use this field to tell buyers how your item rates on a given energy efficiency range.
See `Google Merchant Center <https://support.google.com/merchants/answer/7562785>`__

.. collapse:: TSV

    Stored in **energy efficiency class** column.

    ========= ========================
     Example	 .. code-block:: text

                    A+
    ========= ========================

.. collapse:: XML

    ======= ===========================================================
    Example .. code-block:: html

                <admarkt:energyEfficiencyClass>A+</admarkt:energyEfficiencyClass>
    ======= ===========================================================

|

Allowed values: *A+++*, *A++*, *A+*, *A*, *B*, *C*, *B*, *E*, *F*, *G*

.. index:: minEnergyEfficiencyClass
.. _feed_minEnergyEfficiencyClass:

min energy efficiency class
"""""""""""""""""""""""""""

Used in combination with **max energy efficiency class** to describe the item energy efficiency label.
Possible values defined in :ref:`feed_energyEfficiencyClass`

.. collapse:: TSV

    Stored in **min energy efficiency class** column.

    ========= ========================
     Example	 .. code-block:: text

                    G
    ========= ========================

.. collapse:: XML

    ======= ===========================================================
    Example .. code-block:: html

                <admarkt:minEnergyEfficiencyClass>G</admarkt:minEnergyEfficiencyClass>
    ======= ===========================================================

|

.. index:: maxEnergyEfficiencyClass
.. _feed_maxEnergyEfficiencyClass:

max energy efficiency class
""""""""""""""""""""""""""""

Used in combination with **min energy efficiency class** to describe the item energy efficiency label.
Possible values defined in :ref:`feed_energyEfficiencyClass`

.. collapse:: TSV

    Stored in **max energy efficiency class** column.

    ========= ========================
     Example	 .. code-block:: text

                    B
    ========= ========================

.. collapse:: XML

    ======= ===========================================================
    Example .. code-block:: html

                <admarkt:maxEnergyEfficiencyClass>B</admarkt:maxEnergyEfficiencyClass>
    ======= ===========================================================

|

.. index:: color
.. _feed_color:

color
""""""""""""""""""""""""

Use **color** field to tell buyers about the dominant colors of your item.
Color definition follows `Google Merchant Center <https://support.google.com/merchants/answer/6324487>`__ guidelines.

.. collapse:: TSV

    Stored in **color** column.

    ========= ========================
     Example	 .. code-block:: text

                    Black/Grey
    ========= ========================

.. collapse:: XML

    ======= ===========================================================
    Example .. code-block:: html

                <admarkt:color>Black/Grey</admarkt:color>
    ======= ===========================================================

|

Restrictions: Use human readable color names. Provide up to 3 colors.
When providing multiple colors separate each entry with a slash (“/”).
Maximum of 100 characters.

.. index:: gender
.. _feed_gender:

gender
""""""""""""""""""""""""

Use **gender** field to describe the gender your item is designed for.
Gender definition follows `Google Merchant Center <https://support.google.com/merchants/answer/6324479>`__ guidelines.

.. collapse:: TSV

    Stored in **gender** column.

    ========= ========================
     Example	 .. code-block:: text

                    unisex
    ========= ========================

.. collapse:: XML

    ======= ===========================================================
    Example .. code-block:: html

                <admarkt:gender>unisex</admarkt:gender>
    ======= ===========================================================

|

Restrictions: Allowed values are *male*, *female*, *unisex*

.. index:: ageGroup
.. _feed_ageGroup:

age group
""""""""""""""""""""""""

Use **age group** field to describe the age group your item is targeted at.
Definition follows `Google Merchant Center <https://support.google.com/merchants/answer/6324463>`__ guidelines.

.. collapse:: TSV

    Stored in **age group** column.

    ========= ========================
     Example	 .. code-block:: text

                    adult
    ========= ========================

.. collapse:: XML

    ======= ===========================================================
    Example .. code-block:: html

                <admarkt:ageGroup>adult</admarkt:ageGroup>
    ======= ===========================================================

|

Allowed values: *newborn*, *infant*, *toddler*, *kids*, *adult*

.. index:: size
.. _feed_size:

size
""""""""""""""""""""""""

Use **size** field to describe standardized size of your item.
Size definition follows `Google Merchant Center <https://support.google.com/merchants/answer/6324492>`__ guidelines.

.. collapse:: TSV

    Stored in **size** column.

    ========= ========================
     Example	 .. code-block:: text

                    XXL
    ========= ========================

.. collapse:: XML

    ======= ===========================================================
    Example .. code-block:: html

                <admarkt:size>S</admarkt:size>
    ======= ===========================================================

|

Restrictions: Non-empty string with a maximum of 100 characters.

.. index:: unitPricingBaseMeasure
.. _feed_unitPricingBaseMeasure:

unit pricing base measure
"""""""""""""""""""""""""

The denominator for item unit price.
See `Google Merchant Center <https://support.google.com/merchants/answer/6324490>`__.
This field attribute tells the buyers how the price of your item translates per unit.

.. collapse:: TSV

    Stored in **unit pricing base measure** column.

    ========= ========================
     Example	 .. code-block:: text

                    1kg
    ========= ========================

.. collapse:: XML

    ======= ===========================================================
    Example .. code-block:: html

                <admarkt:unitPricingBaseMeasure>1kg</admarkt:unitPricingBaseMeasure>
    ======= ===========================================================

|

Restrictions: Value should be an integer number with unit.

Supported unit values:
    * **Weight**: *oz, lb, mg, g, kg*
    * **Volume**: *floz, pt, qt, gal, ml, cl, l, cbm*
    * **Length**: *in, ft, yd, cm, m*
    * **Area**: *sqft, sqm*
    * **Per unit**: *ct*

.. index:: unitPricingMeasure
.. _feed_unitPricingMeasure:

unit pricing measure
""""""""""""""""""""

Defines the measure and dimension of the item. That value helps buyers to understand the exact price per unit for your item.
Example 125ml, 100g.
See `Google Merchant Center <https://support.google.com/merchants/answer/6324455>`__.

.. collapse:: TSV

    Stored in **unit pricing measure** column.

    ========= ========================
     Example	 .. code-block:: text

                    15kg
    ========= ========================

.. collapse:: XML

    ======= =================================================================
    Example .. code-block:: html

                <admarkt:unitPricingMeasure>15kg</admarkt:unitPricingMeasure>
    ======= =================================================================

|

Restrictions: Value should be an integer number with a unit.

Supported unit values:
    * **Weight**: *oz, lb, mg, g, kg*
    * **Volume**: *floz, pt, qt, gal, ml, cl, l, cbm*
    * **Length**: *in, ft, yd, cm, m*
    * **Area**: *sqft, sqm*
    * **Per unit**: *ct*