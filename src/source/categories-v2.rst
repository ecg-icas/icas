.. _ISO 31-11: http://en.wikipedia.org/wiki/ISO_31-11#Sets
.. _ISO 639: http://en.wikipedia.org/wiki/ISO_639
.. _ISO 3166-1 alpha-2: http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2
.. _ISO 4217: http://en.wikipedia.org/wiki/ISO_4217
.. _ISO 8601: http://en.wikipedia.org/wiki/ISO_8601
.. _ECMAScript Language Specification: http://www.ecma-international.org/ecma-262/5.1/#sec-4.3.19
.. _categories_v2:

Categories V2
=============

The Tenant Taxonomy Configuration provides the category tree, attribute definitions and
validation rules the tenant wishes to use for ads placed on iCAS.

The requirements for the category tree are:

* categories form a tree with a single root node
* each category must have a unique id
* each category must specify the locales for which it is available
* each ad belongs to one and only one category
* ads can only be placed in leaf categories
* only leaf categories contain attributes

Category Ids
------------

The root node has category id 0.

Every other category id must be a unique integer value within the range [1..2^53).
Due to limitations in `ECMAScript Language Specification`_ values greater or
equal to 2^53 cannot be represented correctly on all platforms.

Category Levels
---------------

The number of sub levels is not limited but for practical purposes we assume that
the tenant provides up to three levels of categories (L1-3). The root node is considered
special and resides at Level 0 (L0). Performing a search at the root node would
result in a site-wide search across all categories.

Category Status
---------------

Each category has a status of one of the following values:

.. list-table::
 :widths: 30 70
 :header-rows: 1

 * - Status
   - Description

 * - ACTIVE
   - The category is visible. This should be the default for all categories
     on every level.

 * - CLOSED
   - The category is visible but no ads can be placed. This status should be
     used for leaf categories where no new ads are accepted and which are
     in transition to ``DELETED``.

 * - DELETED
   - The category is no longer visible and no ads can be placed in it. It is
     still possible for ads to be in this category but they can no longer be
     found through a category search.

Category Configuration
----------------------

Leaf categories require additional configuration which is provided in
``config`` field of the category. Non-leaf categories must omit that field.

.. list-table::
 :widths: 5 15 10 70
 :header-rows: 1

 * - Key
   - Type
   - Constraints
   - Info

 * - currency
   - string
   - not empty
   - The `ISO 4217`_ currency code. Must be the same for all categories.

 * - priceTypes
   - set<string>
   - not empty
   - The list of available `Price Types`_ for this category.

 * - page1CpcPosition
   - int
   - ``> 0``
   - Which page 1 ad to use for cpc references.

 * - cpc
   - interval
   - ``(0,+∞)``
   - CPC value for ads in this category.

 * - totalBudget
   - interval
   - ``(0,+∞)``
   - Total budget for ads in this category.

 * - minDailyBudget
   - int
   - ``>= 0``
   - Min daily budget for ads in this category. Default is 0 == no daily budget.
     Max should be ``totalBudget`` of the ad.

 * - activeAds
   - interval
   - ``(0,+∞)``
   - Max active ads per seller in this category.

 * - images
   - interval
   - ``[0,32]``
   - Max number of images for ads in this category.

 * - titleLength
   - interval
   - ``(0,120]``
   - Max length of the title for ads in this category.

 * - descriptionLength
   - interval
   - ``(0,65535]``
   - Max length of the description for ads in this category.

 * - shippingEnabled
   - bool
   -
   - If ``true``, shipping options are enabled for ads in this category.

 * - paypalEnabled
   - bool
   -
   - If ``true``, Paypal is a payment option for ads in this category.

 * - paypalBpEnabled
   - bool
   -
   - If ``true``, Paypal Buyer Protection is enabled for ads in this category.

 * - tags
   - map<locale, set<string>>
   -
   - Optional localized set of additional keywords that are indexed with ads in this category.

 * - verticals
   - set<string>
   -
   - Optional set of verticals (groups) this category belongs to. The following verticals are
     allowed: ``CARS``, ``CONTACTS``, ``JOBS``, ``HOUSES``, ``SERVICES``, ``VACATIONS``

 * - relatedPaths
   - set<string>
   -
   - Optional set of paths from related existing categories used for search strategies and/or
     fallback scenarios to expand the search parameters when too few results are returned.

Intervals
---------

Parameters which are defined as type ``interval`` use one of the `ISO 31-11`_ notations for
describing intervals.  The supported notation is ``[a,b]``, ``(a,b)``, ``(a,b]``
and ``[a,b)``. ``a`` and ``b`` must be valid numbers.

Locales
-------

Categories have support for multiple locales. A locale is defined as ``language[_territory]``.
The language is defined as a `ISO 639`_ language code and the territory is a
`ISO 3166-1 alpha-2`_ country code. Some examples are:
``nl_NL``, ``nl_BE``, ``fr_BE``, ``en_US``, ``en_AU``

The ``locales`` parameter defines for which locale a category is available.
This allows for region specific differences within the same taxonomy tree.

If the ``locales`` parameter contains multiple entries then all multi-lingual fields
of type ``map<locale,...>`` must have entries for all of these locales.

Price Types
-----------

Each leaf category must have one or more price types configured which define the payment
options the seller wants to offer. The valid list of price types is:

.. list-table::
 :widths: 20 10 70
 :header-rows: 1

 * - Price type
   - Price required
   - Description

 * - BIDDING
   - no
   - Request a bid on the ad starting from price 0.

 * - BIDDING_FROM
   - yes
   - Request a bid with a starting price > 0.

 * - FIXED_PRICE
   - yes
   - Request a fixed price.

 * - NEGOTIABLE
   - no
   - Request a negotiation between buyer and seller.

 * - SEE_DESCRIPTION
   - no
   - Additional information is in the description of the ad.

 * - SWAP
   - no
   - Request an exchange of one item for another.

 * - CREDIBLE_BID
   - no
   - Request for any reasonable offer.

 * - ON_DEMAND
   - no
   - Price is communicated on request.

 * - RESERVED
   - no
   - Flag for transaction in progress. **We should expose this as flag in the ad.**

Data Model
----------

The data model is designed to support the following use cases:

* render a user interface for placing an ad on iCAS
* validate an ad that is placed via the iCAS Sellside API

The category tree is provided as a JSON object which has the following structure:

.. literalinclude:: examples/category-tree-v2.json
   :tab-width: 2
   :language: javascript


Ads can only be placed in leaf categories and leaf objects contain the full
configuration for this category.

Non-Leaf Categories
-------------------

Non-leaf categories only serve as parent nodes for lower level categories.
Ads cannot be placed within them and therefore they have no configuration
related to ad placement.

.. list-table::
 :widths: 5 15 10 70
 :header-rows: 1

 * - Field
   - Type
   - Constraints
   - Info

 * - id
   - long
   - ``> 0``
   - Unique category id.

 * - locales
   - list<locale>
   - not empty
   - Locales for which the category is available.

 * - label
   - map<locale,string>
   - one entry per locale
   - Display name of the category.

 * - status
   - string
   - not empty
   - One of ``ACTIVE``, ``CLOSED``, ``DELETED``

 * - children
   - list<category>
   - not empty
   - Ordered list of child categories.

Example:

.. literalinclude:: examples/category-nonleaf-v2.json
   :tab-width: 2
   :language: javascript


Leaf Categories
---------------

Leaf categories are the categories where ads can be placed. They have by definition
no children. Leaf categories contain the full configuration for ads placed in this
category.

.. list-table::
 :widths: 5 15 10 70
 :header-rows: 1

 * - Field
   - Type
   - Constraints
   - Info

 * - id
   - long
   - ``> 0``
   - Unique category id.

 * - locales
   - list<locale>
   - not empty
   - Locales for which the category is available.

 * - label
   - map<locale,string>
   - one entry per locale
   - Display name of the category.

 * - status
   - string
   - not empty
   - One of ``ACTIVE``, ``CLOSED``, ``DELETED``

 * - config
   - config
   - not empty
   - The category configuration

 * - attributeGroups
   - list<attributeGroup>
   -
   - Ordered list of attribute groups.


Attribute Groups
----------------

Attribute groups combine a list of attributes with a label and an optional tooltip.
Multiple attribute groups allow the user interface to render multiple groups in
separate blocks. Expect that attributes are rendered in the order given therefore
the order in the ``attributes`` field matters. The same applies to the order of the
attribute groups themselves.

.. list-table::
 :widths: 5 15 10 70
 :header-rows: 1

 * - Field
   - Type
   - Constraints
   - Info

 * - label
   - map<locale,string>
   - one entry per locale
   - Localized label of the group.

 * - tooltip
   - map<locale,string>
   - one entry per locale
   - Optional tooltip/help text for the label. Can be empty.

 * - attributes
   - list<attribute>
   - not empty
   - Ordered list of attributes.


Attributes
----------

Attributes define additional fields for ads in this category. The configuration
parameters allow to render the attribute in a certain way depending on the
``type`` and the content of the ``values`` field. See `Attribute Rendering`_ below.

.. list-table::
 :widths: 5 15 10 70
 :header-rows: 1

 * - Field
   - Type
   - Constraints
   - Info

 * - key
   - string
   - not empty, unique in category
   - Attribute key.

 * - label
   - map<locale,string>
   - one entry per locale
   - Localized label of the attribute.

 * - tooltip
   - map<locale,string>
   - one entry per locale
   - Optional tooltip/help text for the label. Can be empty.

 * - type
   - string
   - not empty
   - One of ``STRING``, ``NUMBER``, ``LIST`` or ``BOOL``

 * - values
   - map<locale,list<string>>
   -
   - Localized values for the attribute.
     The length of the JSON representation of all values for one locale
     must not exceed 512 bytes.

 * - mandatory
   - bool
   -
   - If ``true``, this attribute is mandatory.

 * - searchable
   - bool
   -
   - If ``true``, this attribute is indexed.

 * - updatable
   - bool
   -
   - If ``true``, this attribute can be changed after creation.

 * - writable
   - bool
   -
   - If ``true``, this attribute can be set during creation.

 * - range
   - interval
   -
   - Range for ``NUMBER`` attributes.

 * - precision
   - int
   - ``>= 0``
   - Precision for ``NUMBER`` fields. ``0`` means value is an ``int``. Default is ``0``.
     Note that floats with large precision values are difficult to compare.

 * - length
   - interval
   - ``[0,512]``
   - Length range for ``STRING`` attributes without values.

 * - prefix
   - map<locale,string>
   - ``[0,16]``
   - Optional localized prefix for rendering. Default is empty.

 * - postfix
   - map<locale,string>
   - ``[0,16]``
   - Optional localized postfix for rendering. Default is empty.

 * - hints
   - list<string>
   -
   - Optional list of rendering hints.

Attribute Rendering
-------------------

How the attribute is rendered and which result type the selected value has depends on
the combination of the ``type`` and the ``values`` parameters. The following table lists
the valid combinations.

The ``hints`` field can provide additional information on how to render the field. For example,
a text input field should be rendered as a textarea field or rich text input field.

The list of rendering hints still needs to be provided.

.. list-table::
 :widths: 5 5 5 5 80
 :header-rows: 1

 * - Type
   - Values
   - Result Type
   - Rendering
   - Info

 * - STRING
   - empty
   - string
   - text input
   - Free text input field of ``maxLength`` characters

 * - STRING
   - not empty
   - string
   - drop-down
   - Single select field. ``values`` contains the options.

 * - LIST
   - not empty
   - list<string>
   - check boxes
   - Multi select field. ``values`` contains the options.

 * - NUMBER
   - empty
   - int or float
   - text input
   - Numeric input field with a value defined by ``range``.
     Result type is ``int`` if ``precision == 0``, otherwise ``float``

 * - BOOL
   - not empty
   - string
   - radio buttons
   - Boolean input field. ``values`` contains the options.


Below is a complete example of a non-leaf category:

.. literalinclude:: examples/category-leaf-v2.json
   :tab-width: 2
   :language: javascript


