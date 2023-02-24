.. _feeds:

XML Feeds
=========
XML feeds are the way for users to handle repetitive asynchronous bulk uploading of ads.
When a user is eligible for feed usage the user can configure an HTTP(s) URL through
:ref:`post_feed_config` or the frontend to make the system, once a day, attempt to download an
XML file. The contents of this XML file need to adhere to the XSD available for sellers
at :ref:`get_feed_xsd`.

Once a day we pull the XML file configured for all applicable users.
We treat the provided XML file as the desired list of ads the user wants to have live.
Any ads not present (referred to by **vendorId**) in the XML file will be paused during
the import of this file.

Fields
------

A set of required and optional fields defined by feed XSD is listed below.
All the values provided should conform to the rules specified for the valid XML document.
For the more complex data (that contains, for example HTML tags) we recommend using `character data (CDATA) <https://en.wikipedia.org/wiki/CDATA>`_.
XML escape characters are also supported.

====================================== ==================================== ===================  =========== 
Field                                  Description                          Restrictions         Mandatory 
====================================== ==================================== ===================  =========== 
:ref:`feed_vendorId`                   **unique** ad identifier             max. 64 chars        yes
:ref:`feed_externalId`                 **deprecated**                       --                   --
:ref:`feed_sellerName`                 seller name                          max. 60 chars        no
:ref:`feed_t`                          product title                        see :ref:`feed_t`    yes
:ref:`feed_descr`                      product description                  :ref:`feed_descr`    yes       
:ref:`feed_categoryId`                 category identifier                  numeric, positive    yes       
:ref:`feed_status`                     desired status (default ACTIVE)      ACTIVE,PAUSED        no       
:ref:`feed_url`                        product URL                          max. 2048 chars      no        
:ref:`feed_vanityUrl`                  displayed URL                        max. 256 chars       no        
:ref:`feed_priceType`                  sales model for product              enum                 yes       
:ref:`feed_price`                      product price in cents if applicable positive integer     yes/no       
:ref:`feed_originalPrice`              original price before discount       positive integer     no        
:ref:`feed_media`                      product images                       :ref:`feed_media`    no
:ref:`feed_attr`                       collection of product attributes     :ref:`feed_attr`     no        
:ref:`feed_budget`                     budget details                       :ref:`feed_budget`   no        
:ref:`feed_ship`                       shipping options                     :ref:`feed_ship`     no
:ref:`feed_phoneNumber`                phone number                         max. 32 chars        no        
:ref:`feed_emailAdvertiser`            allow emails to the seller           true,false           no
:ref:`feed_regionId`                   only applicable for Kijiji Canada    numeric              no        
:ref:`feed_microTip`                   tiny product hightlight              max. 18 chars        no
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

.. index:: vendorId
.. _feed_vendorId:

vendorId
""""""""

The (mandatory) **vendorId** field in the XML file is there to let us know, for consecutive imports, which
ads are the same. This results in allowing us to update an existing ad with the same **vendorId** instead
of creating a new ad. **vendorId** is mandatory and, as specified in the XSD, unique for each ad in the
XML file. Any non-empty string with a maximum length of 64 characters.

.. note::
   If an ad in the feed remains unchanged (compared to previous import, including image urls), we will skip over this ad and leave
   it unchanged in our system. This also means we will **not** attempt to download the images and process them again.
   This is an optimisation that allows us to speed up processing significantly and cut down on calls to your image server.
   Any change in the ad (including it re-appearing in the feed if it wasn't present the previous time) will update the
   ad and trigger image re-processing.

======= ====================================================
Example	.. code-block:: html
        
          <ad:vendorId>15839942</ad:vendorId>
======= ====================================================

.. index:: externalId
.. _feed_externalId:

externalId
""""""""""
.. warning::
   There is still an **externalId** field in the XSD, this field is replaced by **vendorId**.
   Please update your XML to reflect this change. This makes naming consistent between feeds and sellside API.
   The **vendorId** field in the feeds has the same meaning and constraints as the **vendorId** field in the
   sellside API.

.. index:: sellerName
.. _feed_sellerName:

sellerName
""""""""""

Display name of the seller (max. 60 characters).

======= ======================================================
Example	.. code-block:: html
        
         <ad:sellerName>Cups, Caps &amp; Craps</ad:sellerName>
======= ======================================================

.. index:: title
.. _feed_t:

title
"""""

Any string, with minimum and maximum length determined by the category, with a maximum cap of 1024 characters. See :ref:`categories`. URLs are not allowed as part of the title.

======= ====================================================
Example	.. code-block:: html
        
         <ad:title>Goedkope A-merk herenfietsen</ad:title>
======= ====================================================

.. index:: description
.. _feed_descr:

description
"""""""""""

The description field of the ad.
Any string, with minimum and maximum length determined by the category. See :ref:`categories`. URLs are not allowed as part of the description.
All HTML elements except for the ones below will be removed:

.. code-block:: html

    <u> <em> <ul> <li> <p> <strong> <br>
    

======= =================================================================================
Example .. code-block:: html 
    
            <ad:description><![CDATA[
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
            <ad:description/>
======= =================================================================================


.. index:: categoryId
.. _feed_categoryId:

categoryId
""""""""""

The leaf category in which the product is placed in the :ref:`categories` tree.

Each product belongs to one and only one category.

An integer value from the category list. Must be an id of a leaf category with a
non-zero parent id.

======= ====================================================
Example	.. code-block:: html
        
         <ad:categoryId>945</ad:categoryId>
======= ====================================================

.. index:: status
.. _feed_status:

status
""""""

Ad status. One of the following:

====== ====================================================
Name   Description
====== ====================================================
ACTIVE The ad will be active (as long as there is budget for it) and it can be found on the marketplace.
PAUSED The ad will be paused, effectively not found on the marketplace.
====== ====================================================

The provided (desired) status may differ from the resulting one, depending on the other conditions.
For instance, budget may be depleted, or the seller may have too many active ads already in the category.

======= =============================
Example .. code-block:: html
        
         <ad:status>PAUSED</ad:status>
======= =============================

.. index:: url
.. _feed_url:

url
"""

An external URL that is shown on the ad page. This must be a valid http(s)
url.

======= =======================================
Example .. code-block:: html
        
         <ad:url>https://www.bmw.de</ad:url>
======= =======================================

.. index:: vanityUrl
.. _feed_vanityUrl:

vanityUrl
"""""""""

The text/url that will be displayed instead of the url in :ref:`feed_url`.

======= ==================================
Example .. code-block:: html
        
         <ad:vanityUrl>BMW</ad:vanityUrl>
======= ==================================

.. index:: priceType
.. _feed_priceType:

priceType
"""""""""

Must be a valid price type identifier from the list of :ref:`price_types`.

======= ============================================
Example .. code-block:: html
        
         <ad:priceType>FIXED_PRICE</ad:priceType>
======= ============================================

.. index:: price
.. _feed_price:

price
"""""

The meaning of the value depends on the :ref:`feed_priceType`. 

If it is `FIXED_PRICE` or `BIDDING_FROM` then **price** is mandatory and needs to be greater than 0.
The maximum allowed **price** value is ``10000000000`` given in ``cents`` of the local market currency. (100.000.000,00 EUR / CAD / ... ).

======= =============================
Example .. code-block:: html
        
         <ad:price>1500</ad:price>
======= =============================

.. index:: originalPrice
.. _feed_originalPrice:

originalPrice
""""""""""""""

Product price before discount. Ignored if a seller does not have a discount feature enabled. Must be greater than :ref:`feed_price`.
The maximum allowed **originalPrice** value is ``10000000000`` given in ``cents`` of the local market currency. (100.000.000,00 EUR / CAD / ... ).

======= ============================================
Example .. code-block:: html
        
         <ad:originalPrice>1500</ad:originalPrice>
======= ============================================

.. index:: media
.. _feed_media:

media
"""""

Complex type used currently for product images. **<media>** should contain from 0 to N **<image>** ordered elements, where the exact limit depends on the category in taxonomy. **<image>** elements must contain a complete URL link pointing to an image on a publicly available webserver.

Allowed image formats: JPEG, JPG, PNG, GIF\*, BMP.

\* Please note that GIFs are not recommended format as they are only 256 colors or less. Also animated gif are not supported.

All images will be resized if necessary to a size of maximum 1024px height and 1024px width (preserving the aspect ratio)
The system will download the images and, if they meet the requirements, store them on our servers in several sizes.

The images will be presented in the order as provided. The first image is shown in search results and acts as the main image on the item page.

======= ========================================================================================================================
Example .. code-block:: html 

            <ad:media>
                <ad:image url="https://images.pexels.com/photos/62289/yemen-chameleon-chamaeleo-calyptratus-chameleon-reptile-62289.jpeg"/>
                <ad:image url="https://images.pexels.com/photos/47547/squirrel-animal-cute-rodents-47547.jpeg?auto=compress&amp;cs=tinysrgb&amp;w=1260&amp;h=750&amp;dpr=2"/>
            <ad:media/>
======= ========================================================================================================================

.. index:: attributes
.. _feed_attr:

attributes
""""""""""

Optional collection of product :ref:`user_defined_attributes` (category-dependent), that can be used to influence the ad relevance. 

======= =========================================================
Example .. code-block:: html 

            <ad:attributes>
                <ad:attribute>
                    <ad:attributeName>color</ad:attributeName>
                    <ad:attributeLocale>nl</ad:attributeLocale>
                    <ad:attributeLabel>Kleur</ad:attributeLabel>
                    <ad:attributeValue>Rood</ad:attributeValue>
                </ad:attribute>
                <ad:attribute>
                    <ad:attributeName>color</ad:attributeName>
                    <ad:attributeLocale>en</ad:attributeLocale>
                    <ad:attributeLabel>Color</ad:attributeLabel>
                    <ad:attributeValue>Red</ad:attributeValue>
                </ad:attribute>
                <ad:attribute>
                    <ad:attributeName>Model</ad:attributeName>
                    <ad:attributeValue>Slim</ad:attributeValue>
                    <ad:attributeValue>Pro</ad:attributeValue>
                </ad:attribute>
            </ad:attributes>

======= =========================================================

.. index:: budgetDetails
.. _feed_budget:

budgetDetails
"""""""""""""

Section with budget details

============= ========================================== ========
Name          Description                                Required
============= ========================================== ========
autobid       use auto bidding option true/false         No
cpc           CPC for the given ad in cents              No
totalBudget   total budget for the given ad in cents     No
dailyBudget   daily budget for the given ad in cents     No
============= ========================================== ========

The minimum and maximum values for the total budget depend on the category. 
If the total budget is not returned with the ad, it means there is an unlimited total budget.

When this value of the daily budget is reached the ad will be offline for the rest of the day, and re-activated at the beginning of the following day. 
The minimum value depends on the category.

The minimum and maximum values of the cost per click (CPC) depend on the category.

======= =========================================================================================================
Example .. code-block:: html 

            <ad:budget>
                <ad:totalBudget>5000</ad:totalBudget>
                <ad:dailyBudget>1000</ad:dailyBudget>
                <ad:cpc>2</ad:cpc>
            </ad:budget>

======= =========================================================================================================

.. index:: shippingOptions
.. _feed_ship:

shippingOptions
"""""""""""""""

Section with shipping options available for a product.
Options can be defined for single selected shippingType or both.

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

Whether shipping options are disabled/optional/mandatory for an ad is configured per category, see :ref:`category_config_v2`.

======= ==============================================================
Example .. code-block:: html 

            <ad:shippingOptions>
                <ad:shippingOption>
                    <ad:shippingType>PICKUP</ad:shippingType>
                    <ad:location>1097DN</ad:location>
                </ad:shippingOption>
            </ad:shippingOptions>
======= ==============================================================

.. index:: phoneNumber
.. _feed_phoneNumber:

phoneNumber
"""""""""""

The phone number of the seller as international phone number format, e.g.
+31207894561 or as a local phone number, e.g. 06789456612. 0900 and 0800
numbers are not allowed.

======= =================================================
Example .. code-block:: html
        
         <ad:phoneNumber>+31207894561</ad:phoneNumber>
======= =================================================

.. index:: emailAdvertiser
.. _feed_emailAdvertiser:

emailAdvertiser
"""""""""""""""

Flag which enables emails, (or the other tenant defined forms of contact) to the seller.
The default value is false.

======= =================================================
Example .. code-block:: html
        
         <ad:emailAdvertiser>true</ad:emailAdvertiser>
======= =================================================

.. index:: regionId
.. _feed_regionId:

regionId
""""""""

The region in which the ad is placed. (only applicable for Kijiji Canada)
An integer value from the region tree. Must be the id of a leaf region.

Each ad belongs to one and only one region and region of an ad cannot be updated.
This field can only be set once during creation of an ad.

This field is mandatory if the `region` field of category configuration is ``MANDATORY``
and optional if the `region` field is ``OPTIONAL``.
This field must be omitted if the `region` field of category configuration is ``DISABLED``.

Please refer to :ref:`categories` and :ref:`regions`

======= =======================================
Example .. code-block:: html
        
         <ad:regionId>1700274</ad:regionId>
======= =======================================

.. index:: microTip
.. _feed_microTip:

microTip
""""""""

A short freeform text with a maximum length of 18 characters, excluding any characters in ``.,/@#<>``.
It is a feature as part of a package that sellers can purchase (currently available only for Marktplaats tenant).
It provides extra attention on the ad in the search results.

======= ===========================================
Example .. code-block:: html
        
         <ad:microTip>TODAY 15% SALE</ad:microTip>
======= ===========================================

.. index:: mpn
.. _feed_mpn: 

MPN
"""

Manufacturer Part Number (MPN), definition follows `Google Merchant Center <https://support.google.com/merchants/answer/6324482>`_ guidelines.
String identifier max 2-70 chars.

======= ==================================
Example .. code-block:: html
        
         <ad:mpn>AB12345R89TN6E</ad:mpn>
======= ==================================

.. index:: googleProductCategory
.. _feed_googleProductCategory: 

googleProductCategory
""""""""""""""""""""""

Product category from Google's product taxonomy. See `Google Merchant Center <https://support.google.com/merchants/answer/6324436>`_

========= ===========================================================
Example   .. code-block:: html
        
           <ad:googleProductCategory>
              Apparel &amp; Accessories &gt; Clothing &gt; Dresses
           </ad:googleProductCategory>

Example   .. code-block:: html

           <ad:googleProductCategory>2271</ad:googleProductCategory>

========= ===========================================================

.. index:: productType
.. _feed_productType: 

productType
""""""""""""""""""""""

Definition follows `Google Merchant Center <https://support.google.com/merchants/answer/6324406>`_ guidelines.
String identifier max 750 chars.

======= =====================================================
Example .. code-block:: html
        
         <ad:productType>
            Home &gt; Women &gt; Dresses &gt; Maxi Dresses
         </ad:productType>
======= =====================================================

.. index:: brand
.. _feed_brand: 

brand
""""""""""""""""""""""

Brand definition follows `Google Merchant Center <https://support.google.com/merchants/answer/6324351>`_ guidelines.
String identifier max 70 chars.

======= ============================================
Example .. code-block:: html
        
         <ad:brand>iPhone</ad:brand>
======= ============================================

.. index:: gtin
.. _feed_gtin: 

GTIN
""""""""""""""""""""""

GTIN (Your product’s Global Trade Item Number), definition follows `Google Merchant Center <https://support.google.com/merchants/answer/6324461>`_ guidelines.
String identifier max 50 chars.

======= ==================================
Example .. code-block:: html
        
         <ad:gtin>44320194113475</ad:gtin>
======= ==================================

.. index:: itemGroupId
.. _feed_itemGroupId: 

itemGroupId
""""""""""""""""""""""

Item Group Id definition follows `Google Merchant Center <https://support.google.com/merchants/answer/6324507>`_ guidelines.
String identifier max 1-50 chars.

======= ============================================
Example .. code-block:: html
        
         <ad:itemGroupId>BC23456</ad:itemGroupId>
======= ============================================

.. index:: condition
.. _feed_condition: 

condition
""""""""""""""""""""""

Condition definition follows `Google Merchant Center <https://support.google.com/merchants/answer/6324469>`_ guidelines.
Accepted values: *new*, *refurbished*, *used*

======= ==================================
Example .. code-block:: html
        
         <ad:condition>used</ad:condition>
======= ==================================

.. index:: material
.. _feed_material: 

material
""""""""""""""""""""""

Material definition follows `Google Merchant Center <https://support.google.com/merchants/answer/6324410>`_ guidelines.
String identifier max 200 chars.
  
======= ==================================
Example .. code-block:: html
        
         <ad:material>Wool</ad:material>
======= ==================================

.. index:: energyEfficiencyClass
.. _feed_energyEfficiencyClass: 

energyEfficiencyClass
""""""""""""""""""""""

Energy Efficiency Class See `Google Merchant Center <https://support.google.com/merchants/answer/7562785>`_

Allowed values: *A+++*, *A++*, *A+*, *A++*, *B*, *C*, *B*, *E*, *F*, *G*

======= ===========================================================
Example .. code-block:: html
        
         <ad:energyEfficiencyClass>A+</ad:energyEfficiencyClass>
======= ===========================================================

.. index:: minEnergyEfficiencyClass
.. _feed_minEnergyEfficiencyClass: 

minEnergyEfficiencyClass
""""""""""""""""""""""""

Minimal energy efficiency class. 
Used in combination with *maxEnergyEfficiencyClass* to describe the product energy efficiency label. 
Possible values defined in :ref:`feed_energyEfficiencyClass`

======= ================================================================
Example .. code-block:: html
        
         <ad:minEnergyEfficiencyClass>E</ad:minEnergyEfficiencyClass>
======= ================================================================

.. index:: maxEnergyEfficiencyClass
.. _feed_maxEnergyEfficiencyClass: 

maxEnergyEfficiencyClass
""""""""""""""""""""""""

Maximal energy efficiency class. 
Used in combination with *minEnergyEfficiencyClass* to describe the product energy efficiency label. 
Possible values defined in :ref:`feed_energyEfficiencyClass`

======= ================================================================
Example .. code-block:: html
        
         <ad:maxEnergyEfficiencyClass>B</ad:maxEnergyEfficiencyClass>
======= ================================================================

.. index:: color
.. _feed_color: 

color
""""""""""""""""""""""""

Color definition follows `Google Merchant Center <https://support.google.com/merchants/answer/6324487>`_ guidelines.
String identifier max 1-100 chars.

======= ==================================
Example .. code-block:: html
        
         <ad:color>Black/Grey</ad:color>
======= ==================================

.. index:: gender
.. _feed_gender: 

gender
""""""""""""""""""""""""

Gender definition follows `Google Merchant Center <https://support.google.com/merchants/answer/6324479>`_ guidelines.

Allowed values: *male*, *female*, *unisex*

======= =============================
Example .. code-block:: html
        
         <ad:gender>unisex</ad:gender>
======= =============================

.. index:: ageGroup
.. _feed_ageGroup: 

ageGroup
""""""""""""""""""""""""

Age group definition follows `Google Merchant Center <https://support.google.com/merchants/answer/6324463>`_ guidelines.

Allowed values: *newborn*, *infant*, *toddler*, *children*, *adult*

======= ==================================
Example .. code-block:: html
        
         <ad:ageGroup>adult</ad:ageGroup>
======= ==================================

.. index:: size
.. _feed_size: 

size
""""""""""""""""""""""""

Size definition follows `Google Merchant Center <https://support.google.com/merchants/answer/6324497>`_ guidelines.
String identifier max 1-100 chars.

======= =============================
Example .. code-block:: html
        
         <ad:size>S</ad:size>
======= =============================

.. index:: unitPricingBaseMeasure
.. _feed_unitPricingBaseMeasure: 

unitPricingBaseMeasure
""""""""""""""""""""""""

The denominator for product unit price. See `Google Merchant Center <https://support.google.com/merchants/answer/6324490>`_

======= ===========================================================
Example .. code-block:: html
        
         <ad:unitPricingBaseMeasure>1kg</ad:unitPricingBaseMeasure>
======= ===========================================================

.. index:: unitPricingMeasure
.. _feed_unitPricingMeasure:         

unitPricingMeasure
""""""""""""""""""""""""

Defines the measure and dimension of the product. Example 125ml, 100g. See `Google Merchant Center <https://support.google.com/merchants/answer/6324455>`_

======= ======================================================
Example .. code-block:: html
        
         <ad:unitPricingMeasure>15kg</ad:unitPricingMeasure>
======= ======================================================

Errors
------
:ref:`get_feed_import` shows the overview of imported feeds of the user, and
:ref:`get_feed_import_id_detail` can be a good source of information on possible errors
or warnings on ads, such as missing mandatory attributes or too low CPC etc. If your XML
does not pass the XSD at :ref:`get_feed_xsd` this is where you will see why.
After the XSD validates, it will handle the ads inside it separately, and a failure on one ad
will then not impact other ads.


Character encoding & Line terminators
-------------------------------------
Feeds are expected to be in UTF-8 encoding without Byte Order Marker (BOM) with Unix (LF) line terminators.
Feed files with a BOM marker and/or different line terminators (e.g. CRLF on Windows) will not be processed.


Whitelisting
------------

As mentioned in :ref:`overview_image_downloads` our outgoing IPs for downloading images (also the ones
defined in the feed) should be whitelisted. We also download the XML file itself using these IPs.


Example XML
-----------

.. code-block:: xml

    <?xml version="1.0" encoding="UTF-8"?>
    <admarkt:ads xmlns:admarkt="http://admarkt.marktplaats.nl/schemas/1.0">
        <admarkt:ad>
            <admarkt:vendorId>jh2fi82wqjckw</admarkt:vendorId>
            <admarkt:title>New white leather sofa</admarkt:title>
            <admarkt:description>This leather sofa is very well suited to sell online. Has happened 12 times
            already, profit guaranteed! The charming white color and stylish design makes it irresistable
            for buyers, whether they need it or not.
            </admarkt:description>
            <admarkt:categoryId>1234</admarkt:categoryId>
            <admarkt:url>http://irresistiblecouch.com/charming-white.html?source=marktplaats</admarkt:url>
            <admarkt:vanityUrl>http://irresistiblecouch.com</admarkt:vanityUrl>
            <admarkt:price>129900</admarkt:price>
            <admarkt:priceType>FIXED_PRICE</admarkt:priceType>
            <admarkt:media>
                <admarkt:image url="http://irresistiblecouch.com/ProductPhotos/Large/jh2fi82wqjckw.jpg"/>
            </admarkt:media>
            <admarkt:budget>
                <admarkt:totalBudget>1000000</admarkt:totalBudget>
                <admarkt:dailyBudget>2500</admarkt:dailyBudget>
                <admarkt:cpc>3</admarkt:cpc>
            </admarkt:budget>
            <admarkt:emailAdvertiser>true</admarkt:emailAdvertiser>
        </admarkt:ad>
        <admarkt:ad>
            <admarkt:vendorId>bvl202kfm2-123</admarkt:vendorId>
            <admarkt:title>Nice bike</admarkt:title>
            <admarkt:description>Decent women's bike. A little old, but good enough. Has seen some mileage,
            been used regularly, but is well maintained. Last month had a large check-up where some key
            parts were replaced.
            </admarkt:description>
            <admarkt:categoryId>43</admarkt:categoryId>
            <admarkt:url>http://supabike.com/oldie.html?foo=bar</admarkt:url>
            <admarkt:vanityUrl>http://supabike.com</admarkt:vanityUrl>
            <admarkt:price>8900</admarkt:price>
            <admarkt:priceType>FIXED_PRICE</admarkt:priceType>
            <admarkt:media>
                <admarkt:image url="http://supabike.com/files/colored/fiets.jpg"/>
            </admarkt:media>
            <admarkt:budget>
                <admarkt:totalBudget>200000</admarkt:totalBudget>
                <admarkt:dailyBudget></admarkt:dailyBudget>
                <admarkt:cpc>2</admarkt:cpc>
            </admarkt:budget>
            <admarkt:emailAdvertiser>true</admarkt:emailAdvertiser>
            <admarkt:microTip>Lease 499 per mnd</admarkt:microTip>
        </admarkt:ad>
    </admarkt:ads>


Scenario's & Questions
----------------------

Below are some common asked-for scenarios and questions with their explanations/answers.

- Feed file cannot be fetched

When a feed file cannot be fetched, nothing will change on the user's ads.
It's as if the import didn't happen. Since the file represents the desired
list of ads to be live, we won't do anything if we can't get the file -
we cannot read a change in the desired situation.

- Feed file is empty

When a feed file is empty, all ads of the user will be paused. An empty
file means the desired list of ads to be live is empty, so all active ads
are paused. Note that this also means that all ads which are in statuses
BUDGET_REACHED or DAILY_BUDGET_REACHED are also paused.

- Feed file contains only new ads

In the spirit of the feed file being the desired set of ads to be live for
a user, all currently active ads (including ads in BUDGET_REACHED or DAILY_BUDGET_REACHED)
will be paused and the supplied ads will be created (with status ACTIVE).

- Editing ads through frontend / API

In the spirit of the feed file being the desired set of ads to be live for
a user, all ads will be (re)set to their representing feed values. This means
you can see changes made throuh API or frontend undone after a successful feed import.

- XML does not validate against XSD

If the fetched XML filed does not validate against the XSD there will not be any changes
to your ads. Existing ads will remain unchanged and no new ads will be created.

- How to validate XML against XSD

Next to various online capabilities where you can provide both your XML and XSD files,
a way to check quickly and locally is to use a tool called xmllint. With this tool
you can use our XSD downloaded from :ref:`get_feed_xsd` to test whether your feed is
working before you let our system fetch it using the following command:

.. code-block:: bash

  xmllint --debug --noout --schema /path/to/admarkt1.0.xsd /path/to/yourfeed.xml

For small chunks of XML you can use online validators as well, such as `<http://www.utilities-online.info/xsdvalidation/>`_ or `<https://www.freeformatter.com/xml-validator-xsd.html>`_. Note that these have a
limit on the size of the XML you can check, but it should be more than enough to be able
to test correctness of your structure.

- Image updates are not processed after successful feed import

If you're changing the images without changing the URLs, the changes may not be picked up,
in case the rest of the ad is also unchanged. We suggest adding a bogus parameter to the
image URL to force a re-processing of the ad and its images. Make sure to not change this
for every feed import, but only when you require images to be re-processed.
