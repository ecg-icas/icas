.. _ISO 31-11: http://en.wikipedia.org/wiki/ISO_31-11#Sets
.. _ISO 639: http://en.wikipedia.org/wiki/ISO_639
.. _ISO 3166-1 alpha-2: http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2
.. _ISO 4217: http://en.wikipedia.org/wiki/ISO_4217
.. _ISO 8601: http://en.wikipedia.org/wiki/ISO_8601
.. _categories:

Categories
==========

The category tree contains all the information about category definitions,
attribute definitions and validation rules for placing ads.

The category tree has the following properties:

.. list-table::
 :widths: 70
 :header-rows: 0

 - * categories form a tree with a single root node
 - * each category has a unique id
 - * each category specifies the locales for which it is available
 - * each ad belongs to one and only one category
 - * ads can only be placed in leaf categories
 - * only leaf categories contain attributes

The full tree (or a subtree) can be fetched using `GET /categories <https://ecg-icas.github.io/icas/openapi/index.html#/Categories/get_categories>`_.

Category Ids
------------

The root node has category id 0.

Every other category id is a unique integer value within the range [1..2^53).

Category Levels
---------------

Although the number of sub levels is not limited, the category tree has
up to three levels of categories (L1-3). The root node is considered
special and resides at Level 0 (L0). Performing a search at the root node would
result in a site-wide search across all categories.


Ads can only be placed in leaf categories and leaf objects contain the full
configuration for this category. Leaf categories have by definition no children.
Non-leaf categories only serve as parent nodes
for lower level categories and have no configuration related to ad placement.


Category Configuration
----------------------

Leaf categories provide additional configuration which is provided in
``config`` field of the category. Non-leaf categories do not provide that field.
See the ``config`` field of the response in
`GET /categories <https://ecg-icas.github.io/icas/openapi/index.html#/Categories/get_categories>`_.
Alternatively, directly explore the category configuration
for `leaf categories <https://ecg-icas.github.io/icas/openapi/index.html?url=https://ecg-icas.github.io/icas/openapi/categories/responses.yaml#/components/schemas/LeafV5>`_ in the OpenAPI documentation.
It contains details about the allowed range of values for budgets, allowed range of values for cost per click,
maximum number of active ads that can be placed in that category,
pricing options, as well as other category-specific restrictions on the ad content.

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
of type ``map<locale,...>`` have entries for all of these locales.


Attributes and Attribute Rendering
----------------------------------

Attributes define additional fields for the items in the ads in a category.
Attributes are defined in the ``attributes`` field of the ``attributeGroups`` category object.
Attribute groups combine a list of attributes with a label and an optional tooltip.
Multiple attribute groups allow the user interface to render multiple groups in separate blocks.

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
   - Free text input field of ``length`` characters

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
