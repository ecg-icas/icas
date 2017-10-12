.. _ISO 639: http://en.wikipedia.org/wiki/ISO_639
.. _ISO 3166-1 alpha-2: http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2
.. _WGS84: http://en.wikipedia.org/wiki/World_Geodetic_System
.. _regions:

Regions
=======

.. warning::

   Regions are currently only applicable to Kijiji Canada.


The region tree contains all the information about region definitions
for placing ads on iCAS.

The region tree has the following properties:

* regions form a tree with a single root node
* each region has a unique id
* each ad belongs to one and only one region
* ads can only be placed in leaf regions
* only leaf regions contain coordinates of the center point

Region Ids
----------

Every region id must be a unique integer value within the range [1..2^53).

Region Levels
-------------

The number of sub levels is not limited. The root node represents the whole country.
Performing a search at the root node would result in a site-wide search across all regions.

Region label
------------

Each region has a label. The ``label`` parameter is of type ``map<locale,string>``.

A locale is defined as ``language[_territory]``.
The language is defined as a `ISO 639`_ language code and the territory is a
`ISO 3166-1 alpha-2`_ country code. Some examples are:
``nl_NL``, ``nl_BE``, ``fr_BE``, ``en_US``, ``en_AU``

This allows localization of labels for different supported languages.

Region center
-------------

Leaf regions provides an additional field for the center point.
This allows for radius searches and sorting on distance.
Non-leaf regions *do not have* that field.

The ``center`` is defined as `WGS84`_ latitude/longitude point.

Data Model
----------

The data model is designed to support the following use cases:

* render a user interface for placing an ad on iCAS
* validate an ad
* allow for region filter and distance search/sort

The regions tree is provided as a JSON object which has the following structure:

.. include:: examples/regions-tree-structure.rst

Ads can only be placed in leaf regions and all leaf regions contain a center point.

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

 * - links
   - map<string,string>
   - not empty
   - A link to the current region and if level > 1 a link to the parent region.

 * - id
   - long
   - ``> 0``
   - Unique region id.

 * - parentId
   - long
   - ``> 0``
   - Parent id of the region.

 * - level
   - int
   - ``> 0``
   - Level at which the region is defined.

 * - path
   - string
   - not empty
   - Ids of all ancestors (except the root) and the current region separated by ``_``

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
no children. Leaf regions have coordinates of the center point.

.. list-table::
 :widths: 5 15 10 70
 :header-rows: 1

 * - Field
   - Type
   - Constraints
   - Info

 * - links
   - map<string,string>
   - not empty
   - A link to the current region and if level > 1 a link to the parent region.

 * - id
   - long
   - ``> 0``
   - Unique region id.

 * - parentId
   - long
   - ``> 0``
   - Parent id of the region.

 * - level
   - int
   - ``> 0``
   - Level at which the region is defined.

 * - path
   - string
   - not empty
   - Ids of all ancestors (except the root) and the current region separated by ``_``

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