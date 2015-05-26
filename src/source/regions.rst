.. _ECMAScript Language Specification: http://www.ecma-international.org/ecma-262/5.1/#sec-4.3.19
.. _ISO 639: http://en.wikipedia.org/wiki/ISO_639
.. _ISO 3166-1 alpha-2: http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2
.. _WGS84: http://en.wikipedia.org/wiki/World_Geodetic_System
.. _regions:

Regions
=======

The Admarkt Sellside API
The Regions Configuration provides the regions tree the tenant wishes to use for ads placed on iCAS.

The requirements for the regions tree are:

* regions form a tree with a single root node
* each region must have a unique id
* each ad belongs to one and only one region
* ads can only be placed in leaf regions
* only leaf regions contain coordinates of the center point

Region Ids
----------

Every region id must be a unique integer value within the range [1..2^53).
Due to limitations in `ECMAScript Language Specification`_ values greater or
equal to 2^53 cannot be represented correctly on all platforms.

Region Levels
-------------

The number of sub levels is not limited. The root node should represent the whole country.
Performing a search at the root node would result in a site-wide search across all regions.

Region label
------------

Each region should have label defined. The ``label`` parameter is of type ``map<locale,...>``.

A locale is defined as ``language[_territory]``.
The language is defined as a `ISO 639`_ language code and the territory is a
`ISO 3166-1 alpha-2`_ country code. Some examples are:
``nl_NL``, ``nl_BE``, ``fr_BE``, ``en_US``, ``en_AU``

This allows for region specific differences in labels.

Region center
-------------

Leaf regions require additional field for the center point.
This allows for radius searches and sorting on distance.
Non-leaf regions must omit that field.

The ``center`` is defined as `WGS84`_ latitude/longitude point.

Data Model
----------

The data model is designed to support the following use cases:

* render a user interface for placing an ad on iCAS
* validate an ad
* allow for region filter and distance search/sort

The regions tree is provided as a JSON object which has the following structure:

.. include:: examples/regions-tree-structure.rst

Ads can only be placed in leaf regions and leaf objects must contain center point.

Non-Leaf Regions
----------------

Non-leaf regions serve as parent nodes for lower level regions.
Ads cannot be placed within them and therefore they have no center point.

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
   - Unique region id.

 * - label
   - map<locale,string>
   - valid json map
   - Display label of the region.

 * - children
   - list<region>
   - not empty
   - Ordered list of child regions.

Example:

.. include:: examples/regions-non-leaf-region.rst

Leaf Regions
------------

Leaf regions are the regions where ads can be placed. They have by definition
no children. Leaf regions should have coordinates of the center point.

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
   - Unique region id.

 * - label
   - map<locale,string>
   - valid json map
   - Display label of the region.

 * - center
   - `WGS84`_ point
   - valid lat/lon
   - Coordinates of the center of the region.

Example:

.. include:: examples/regions-leaf-region.rst