.. _feed-details:

Feed Fields
===========

A set of required and optional fields defined by a feed for XML and TSV file formats are listed below.

.. collapse:: TSV

    ========================================= ==================================== ===================  =========== 
    Field                                     Description                          Restrictions         Mandatory 
    ========================================= ==================================== ===================  =========== 
    :ref:`feed_vendorId`                      **unique** ad identifier             max. 64 chars        yes
    :ref:`feed_sellerName`                    your company name                          max. 60 chars        no
    :ref:`feed_t`                             product title                        see :ref:`feed_t`    yes
    :ref:`feed_descr`                         product description                  :ref:`feed_descr`    yes       
    :ref:`feed_categoryId`                    category identifier                  numeric, positive    yes       
    :ref:`feed_status`                        desired status (default ACTIVE)      ACTIVE,PAUSED        no       
    :ref:`feed_url`                           product URL                          max. 2048 chars      no        
    :ref:`feed_vanityUrl`                     displayed URL                        max. 256 chars       no        
    :ref:`feed_priceType`                     sales model for product              enum                 yes       
    :ref:`feed_price`                         product price in cents if applicable positive integer     yes/no       
    :ref:`feed_originalPrice`                 original price before discount       positive integer     no        
    :ref:`image link <feed_media>`            primary image                        :ref:`feed_media`    no
    :ref:`additional image link <feed_media>` additional images                    :ref:`feed_media`    no
    :ref:`feed_attr`                          collection of product attributes     :ref:`feed_attr`     no        
    :ref:`autobid <feed_budget>`              budget details                       :ref:`feed_budget`   no        
    :ref:`cpc <feed_budget>`                  budget details                       :ref:`feed_budget`   no        
    :ref:`total budget <feed_budget>`         budget details                       :ref:`feed_budget`   no        
    :ref:`daily budget <feed_budget>`         budget details                       :ref:`feed_budget`   no        
    :ref:`shipping <feed_ship>`               shipping options                     :ref:`feed_ship`     no
    :ref:`pickup locations <feed_ship>`       pickup locations                     :ref:`feed_ship`     no
    :ref:`feed_phoneNumber`                   phone number                         max. 32 chars        no        
    :ref:`feed_emailAdvertiser`               allow emails to the seller           true,false           no
    :ref:`feed_regionId`                      only applicable for Kijiji Canada    numeric              no        
    :ref:`feed_microTip`                      tiny product highlight               max. 18 chars        no
    :ref:`feed_mpn`                           Manufacturer Part Number (MPN)       2-70 chars           no   
    :ref:`feed_googleProductCategory`         google category for your product     string               no
    :ref:`feed_productType`                   customer product type                max. 750 chars       no    
    :ref:`feed_brand`                         product brand name                   max. 70 chars        no
    :ref:`feed_gtin`                          Global Trade Identification Number   max. 50 chars        no  
    :ref:`feed_itemGroupId`                   groups product variants in your      max. 50 chars        no
    :ref:`feed_condition`                     condition of product                 enum                 no
    :ref:`feed_material`                      main product fabrics or materials    max. 200 chars       no
    :ref:`feed_energyEfficiencyClass`         energy efficiency class              enum                 no
    :ref:`feed_minEnergyEfficiencyClass`      minimal energy efficiency class      enum                 no
    :ref:`feed_maxEnergyEfficiencyClass`      maximal energy efficiency class      enum                 no
    :ref:`feed_color`                         product colors                       max. 100 chars       no
    :ref:`feed_gender`                        gender product is designed for       enum                 no
    :ref:`feed_ageGroup`                      age group product is intended for    enum                 no
    :ref:`feed_size`                          size information                     enum                 no
    :ref:`feed_unitPricingBaseMeasure`        denominator for product unit price   string               no
    :ref:`feed_unitPricingMeasure`            measure and dimension of product     string               no
    ========================================= ==================================== ===================  =========== 

.. collapse:: XML

    ====================================== ==================================== ===================  =========== 
    Field                                  Description                          Restrictions         Mandatory 
    ====================================== ==================================== ===================  =========== 
    :ref:`feed_vendorId`                   **unique** ad identifier             max. 64 chars        yes
    :ref:`feed_externalId`                 **deprecated**                       --                   --
    :ref:`feed_sellerName`                 your company name                          max. 60 chars  no
    :ref:`feed_t`                          product title                        see :ref:`feed_t`    yes
    :ref:`feed_descr`                      product description                  :ref:`feed_descr`    yes       
    :ref:`feed_categoryId`                 category identifier                  numeric, positive    yes       
    :ref:`feed_status`                     desired status (default ACTIVE)      ACTIVE,PAUSED        no       
    :ref:`feed_url`                        product URL                          max. 2048 chars      no        
    :ref:`feed_vanityUrl`                  displayed URL                        max. 256 chars       no        
    :ref:`feed_priceType`                  sales model for product              enum                 yes       
    :ref:`feed_price`                      product price in cents if applicable positive integer     yes/no       
    :ref:`feed_originalPrice`              original price before discount       positive integer     no        
    :ref:`media <feed_media>`              product images                       :ref:`feed_media`    no
    :ref:`feed_attr`                       collection of product attributes     :ref:`feed_attr`     no        
    :ref:`budget <feed_budget>`            budget details                       :ref:`feed_budget`   no        
    :ref:`shipping options <feed_ship>`    shipping options                     :ref:`feed_ship`     no
    :ref:`feed_phoneNumber`                phone number                         max. 32 chars        no        
    :ref:`feed_emailAdvertiser`            allow emails to the seller           true,false           no
    :ref:`feed_regionId`                   only applicable for Kijiji Canada    numeric              no        
    :ref:`feed_microTip`                   tiny product highlight               max. 18 chars        no
    :ref:`feed_mpn`                        Manufacturer Part Number (MPN)       2-70 chars           no   
    :ref:`feed_googleProductCategory`      google category for your product     string               no
    :ref:`feed_productType`                customer product type                max. 750 chars       no    
    :ref:`feed_brand`                      product brand name                   max. 70 chars        no
    :ref:`feed_gtin`                       Global Trade Identification Number   max. 50 chars        no  
    :ref:`feed_itemGroupId`                groups product variants in your      max. 50 chars        no
    :ref:`feed_condition`                  condition of product                 enum                 no
    :ref:`feed_material`                   main product fabrics or materials    max. 200 chars       no
    :ref:`feed_energyEfficiencyClass`      energy efficiency class              enum                 no
    :ref:`feed_minEnergyEfficiencyClass`   minimal energy efficiency class      enum                 no
    :ref:`feed_maxEnergyEfficiencyClass`   maximal energy efficiency class      enum                 no
    :ref:`feed_color`                      product colors                       max. 100 chars       no
    :ref:`feed_gender`                     gender product is designed for       enum                 no
    :ref:`feed_ageGroup`                   age group product is intended for    enum                 no
    :ref:`feed_size`                       size information                     enum                 no
    :ref:`feed_unitPricingBaseMeasure`     denominator for product unit price   string               no
    :ref:`feed_unitPricingMeasure`         measure and dimension of product     string               no
    ====================================== ==================================== ===================  =========== 

|


.. index:: vendorId
.. _feed_vendorId:

vendor id
"""""""""

The **vendor id** field is the unique identifier of the ad. It is there to let us know, for consecutive imports, which
ads are the same. This results is allowing us to track and update an existing ad with the same **vendor id** instead
of creating a new ad. **vendor id** is mandatory and, unique for each ad in the feed.

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

    Use **vendorId** tag name to encapsulate **vendor id**. 
    
    ========= ================================================
    Example:	
                
                .. code-block:: html
                        
                    <admarkt:vendorId>15839942</admarkt:vendorId>
    ========= ================================================

| 

Restrictions:  Any non-empty string with a maximum length of 64 characters.

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

Restrictions: max. 60 characters

.. index:: title
.. _feed_t:

title
"""""

Use the title **title** field to clearly identify the product you are selling. 
The title is one of the most prominent parts of your ad or free listing. 
A specific and accurate title will help us show your product to the right customers.

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

Restrictions: Any string, with minimum and maximum length determined by the category, with a maximum cap of 1024 characters. See :ref:`categories`. URLs are not allowed as part of the title.

.. index:: description
.. _feed_descr:

description
"""""""""""

Use the **description** field to tell customers about the details of the product you are selling.

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

Restrictions: Any string, with minimum and maximum length determined by the category. See :ref:`categories`. URLs are not allowed as part of the description.
All HTML elements except for the ones below will be removed:

.. code-block:: html

    <u> <em> <ul> <li> <p> <strong> <br>
    

.. index:: categoryId
.. _feed_categoryId:

category id
"""""""""""

Use **category id** to place your product in the :ref:`categories` tree. 

Each product belongs to one and only one category.

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

Allowed values: *ACTIVE*, *PAUSED*

.. index:: url
.. _feed_url:

url
"""

Utilize the **url** to establish a connection to your product page from the advertisement.
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

Use **price type** to define :ref:`pricing model<price_types>` for your product.

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

Allowed Values: BIDDING, BIDDING_FROM, FIXED_PRICE, FREE, NEGOTIABLE, SEE_DESCRIPTION, SWAP, CREDIBLE_BID, ON_DEMAND,RESERVED

.. index:: price
.. _feed_price:

price
"""""

Use **price** to tell customers the price of the product you are selling.
The meaning of the value depends on the :ref:`feed_priceType`. 

If it is `FIXED_PRICE` or `BIDDING_FROM` then **price** is mandatory and needs to be greater than 0.

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

Use **original price** to tell your product price before discount.
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
The maximum allowed **product price** value is ``10000000000`` given in ``cents`` of the local market currency (100.000.000,00 EUR / CAD / ... ).

.. index:: media
.. _feed_media:

product images
""""""""""""""

You can provide multiple images for your product.

All images will be resized if necessary to a size of maximum 1024px height and 1024px width (preserving the aspect ratio)
The system will download the images and, if they meet the requirements, store them on our servers in several sizes.

.. collapse:: TSV

    Use **image link** column to give us a link to the best picture of your product.

    ========= ========================
     Example	 .. code-block:: text
            
                    https://images.pexels.com/photos/62289.jpeg
    ========= ========================

    Use **additional image link** for even more pictures of your product.
    If there are more than one, separate them with commas. 
    
    ========= ========================
     Example	 .. code-block:: text
            
                    https://images.pexels.com/photos/62290.jpeg,https://images.pexels.com/photos/62291.jpeg
    ========= ========================

    All URLs must be complete links pointing to an image on a publicly available web server.

.. collapse:: XML

    Use **<media>** tag for grouping your product images. 
    **<media>** should contain from 0 to N **<image>** ordered elements, where the exact limit depends on the category in taxonomy. 
    **<image>** elements must contain a complete URL link pointing to an image on a publicly available web server.
    
    ======= ===========================================================
    Example .. code-block:: html
            
                <admarkt:media>
                    <admarkt:image url="https://images.pexels.com/photos/62289/62289.jpeg"/>
                    <admarkt:image url="https://images.pexels.com/photos/47547/47547.jpeg"/>
                <admarkt:media/>
    ======= ===========================================================

    The images will be presented in the provided order. The first image is shown in search results and acts as the main image on the item page.

|

Allowed image formats: JPEG, JPG, PNG, GIF\*, BMP.

\* Please note that GIFs are not recommended format as they are only 256 colors or less. 
Also, animated GIFs and PNGs are not supported.

.. index:: attributes
.. _feed_attr:

attributes
""""""""""

Use **attributes** field to provide additional information on your product in a structured way.

.. collapse:: TSV

    Define your attribute as *name*:*value* pair in the **attributes** column.

    ========= ========================
     Example	 .. code-block:: text
            
                    model:Adams Family
    ========= ========================

    You can provide multiple attributes in a comma- separated list.

    ========= ========================
     Example	 .. code-block:: text
            
                    model:Adams Family,multiball:TRUE,screen size:32"
    ========= ========================

    If the name, or the value of your attribute contains commas, use quotes to escape it.

    ========= ========================
     Example	 .. code-block:: text
            
                    resolutions:"1024x768:24dpi,800x600:18dpi"
    ========= ========================

.. collapse:: XML

    **attributes** tag contains collection of product :ref:`user_defined_attributes` (category-dependent), that can be used to influence the ad relevance. 

    ======= ===========================================================
    Example .. code-block:: html
            
                <admarkt:attributes>
                    <admarkt:attribute>
                        <admarkt:attributeName>color</admarkt:attributeName>
                        <admarkt:attributeLocale>nl</admarkt:attributeLocale>
                        <admarkt:attributeLabel>Kleur</admarkt:attributeLabel>
                        <admarkt:attributeValue>Rood</admarkt:attributeValue>
                    </admarkt:attribute>
                    <admarkt:attribute>
                        <admarkt:attributeName>color</admarkt:attributeName>
                        <admarkt:attributeLocale>en</admarkt:attributeLocale>
                        <admarkt:attributeLabel>Color</admarkt:attributeLabel>
                        <admarkt:attributeValue>Red</admarkt:attributeValue>
                    </admarkt:attribute>
                    <admarkt:attribute>
                        <admarkt:attributeName>Model</admarkt:attributeName>
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
Name          Description                                Required
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

Provide the information on how your product can be delivered to customers.

.. collapse:: TSV

    Use **shipping** field to tell customers about the different cost vs. time options for your product delivery.
    Each option should be formatted as follows:

    [*cost in cents*]:[*minimum transit time in days*]-[*maximum transit time in days*]

    You can provide multiple shipping options in a comma-separated list.
    
    ========= ========================
     Example	 .. code-block:: text
            
                    695:2d-5d;1195:1d-2d
    ========= ========================


    Use **pickup locations** field to tell customers `location(s)` your product can be picked up at.
    Location is given as a postal code.
    You can provide multiple locations in a comma-separated list.
    
    ========= ========================
     Example	 .. code-block:: text
            
                    1097DN,1055AB
    ========= ========================

.. collapse:: XML

    You can provide multiple shipping/ pick-up options for each product.
    Each option can be described with the following information: 

    ============= ========================================== ========
    Name          Description                                Required
    ============= ========================================== ========
    shippingType  SHIP, PICKUP                               Yes
    cost          cost of shipping in cents                  No
    time          time it takes to deliver the product       No
    location      pick up location of the product            No
    ============= ========================================== ========

    *SHIP* means the item can be delivered to the buyer in the provided `time` and for the provided `cost`. 
    For shippingType 'SHIP' provide 'cost' in cents and 'time' in days. 'location' is ignored.

    *PICKUP* means the item can be picked up at the provided `location`
    For shippingType 'PICKUP' provide 'location'. Both 'cost' and 'time' are ignored.

    ======= ===========================================================
    Example .. code-block:: html
            
                <admarkt:shippingOptions>
                    <admarkt:shippingOption>
                        <admarkt:shippingType>PICKUP</admarkt:shippingType>
                        <admarkt:location>1097DN</admarkt:location>
                    </admarkt:shippingOption>
                </admarkt:shippingOptions>
    ======= ===========================================================

|

Restrictions: Shipping options can be disabled/optional/mandatory for an ad. 
It is configured per category, see :ref:`category_config_v2`.

.. index:: phoneNumber
.. _feed_phoneNumber:

phone number
""""""""""""

Use the **phone number** field to allow customers call you and ask about the product.

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

Use the **email advertiser** flag to allow customers to contact you via email (or the other platform defined form of contact), and ask about the product.
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

Allowed values: *true*, *false*

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

Restrictions: Limit your text to a maximum length of 18 characters.
The following characters ``.,/@#<>`` are not allowed.

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

Restrictions: String identifier max 70 characters long.

.. index:: googleProductCategory
.. _feed_googleProductCategory: 

google product category
"""""""""""""""""""""""

Use this field to describe your product category in Google's product taxonomy.
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

Restrictions: Should be a valid category. You can provide it, either with identifier, or giving full category path.

.. index:: productType
.. _feed_productType: 

product type
""""""""""""""""""""""

The **product type** field provides an opportunity for you to incorporate your unique product classification system into the dataset.
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

Restrictions: Do not exceed 750 characters limit for your text.

.. index:: brand
.. _feed_brand: 

brand
""""""""""""""""""""""

Use the **brand** field to help customers identify your product. 
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

Restrictions: Do not exceed 70 characters limit for your text.

.. index:: gtin
.. _feed_gtin: 

GTIN
""""""""""""""""""""""

GTIN (Your product’s Global Trade Item Number), definition follows `Google Merchant Center <https://support.google.com/merchants/answer/6324461>`__ guidelines.

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

Restrictions: String identifier max 50 chars.

.. index:: itemGroupId
.. _feed_itemGroupId: 

item group id
""""""""""""""""""""""

Use this field to group product variants in your product data.
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

Restrictions: Text max. length 50 characters.

.. index:: condition
.. _feed_condition: 

condition
""""""""""""""""""""""

Use this field to inform customers about the condition of your product. Condition definition follows `Google Merchant Center <https://support.google.com/merchants/answer/6324469>`__ guidelines.

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

Accepted values: *new*, *refurbished*, *used*

.. index:: material
.. _feed_material: 

material
""""""""""""""""""""""

**Material** field describes the main fabric or material that your product is made of.
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
Separate materials with a slash (“/”) character when there are multiple.
Do not exceed 200 characters limit for your text.

.. index:: energyEfficiencyClass
.. _feed_energyEfficiencyClass: 

energy efficiency class
"""""""""""""""""""""""

Use this field to tell customers how your product rates on a given energy efficiency range.
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

Allowed values: *A+++*, *A++*, *A+*, *A++*, *B*, *C*, *B*, *E*, *F*, *G*

.. index:: minEnergyEfficiencyClass
.. _feed_minEnergyEfficiencyClass: 

min energy efficiency class
"""""""""""""""""""""""""""

Used in combination with **max energy efficiency class** to describe the product energy efficiency label. 
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

Used in combination with **min energy efficiency class** to describe the product energy efficiency label. 
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

Use **color** field to tell customers about the dominant colors of your product. 
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
Separate colors with / if more than one. 
Do not exceed 100 characters limit for your text.  
 
.. index:: gender
.. _feed_gender: 

gender
""""""""""""""""""""""""

Use **gender** field to describe the gender your product is designed for.
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

Allowed values: *male*, *female*, *unisex*

.. index:: ageGroup
.. _feed_ageGroup: 

age group
""""""""""""""""""""""""

Use **age group** field to describe the age group your product is targeted at. 
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

Use **size** field to describe standardized size of your product.
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

Restrictions: String identifier max 1-100 chars.

.. index:: unitPricingBaseMeasure
.. _feed_unitPricingBaseMeasure: 

unit pricing base measure
"""""""""""""""""""""""""

The denominator for product unit price. 
See `Google Merchant Center <https://support.google.com/merchants/answer/6324490>`__.
This field attribute tells the customer how the price of your product translates per unit. 

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

Defines the measure and dimension of the product. That value helps the customers to understand the exact price per unit for your product.
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

