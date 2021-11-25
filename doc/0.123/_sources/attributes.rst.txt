.. index:: Attributes
.. _attributes:

Attributes
==========

The iCAS Sellside API supports attributes for both categories and
advertisements to specify additional properties of a product like *size* and
*color*.

.. _category_attributes:

Category Attributes
-------------------

Category attributes are recommended attribute names and values for a given
category. They help constructing automatic user interfaces in which sellers
can select one or more values from a pre-defined list of attributes.

They serve as a basis for the attributes the seller can supply in addition
to his own user-defined attributes. You cannot post/put category attributes.
In order to add attributes to an ad you need to supply user defined attributes (See below).

Category attributes are provided as part of the category taxonomy tree, in the **attributes**
subsection. Each category attribute has a **key**, a **label**, a **locale** for the label and values,
a **type** and depending on the type one or more additional properties describing the constraints.
For more information on category attributes, see :ref:`category_attributes_v2`.

The following types are supported:

========    ===========================================================================
type        description
========    ===========================================================================
STRING      User can select a single value from  **values**
LIST        User can select one or more values from **values**
NUMBER      User can provide a number between **minValue** and **maxValue**
========    ===========================================================================

Example
^^^^^^^
Below is an excerpt from the attributes section of a category tree, for a particular category

.. code-block:: javascript

    [
        {
            "key": "delivery",
            "label": {
                "nl_NL": "Levering",
                "en_NL": "Delivery"
            }
            "type" : "STRING",
            "values" : {
                "nl_NL": ["Ophalen", "Verzenden", "Ophalen of Verzenden"],
                "en_NL": ["Pickup", "Deliver", "Pickup or Deliver"]

            },
            "defaults": {
                "nl_NL": "Ophalen",
                "en_NL": "Pickup"
            }
            "mandatory" : true,
            "writable": true,
            "updatable": true
        },
        {
            "key": "subtitles",
            "label": {
                "nl_NL": "Ondertiteling",
                "en_NL": "Subtitles"
            },
            "type" : "LIST",
            "values" : {
                "nl_NL": ["Engels", "Duits", "Nederlands"],
                "en_NL": ["English", "German", "Dutch"]
            },
            "defaults":{},
            "mandatory" : false,
            "writable": true,
            "updatable": true
        },
        {
            "key": "motorinhoud",
            "label": {
                "nl_NL": "Motorinhoud",
                "en_NL":"Engine capacity"
            }
            "type" : "NUMBER",
            "range" : [1,8500],
            "mandatory" : true,
            "writable": true,
            "updatable": false
        },
        ...
    ]

.. _user_defined_attributes:

User-Defined Attributes
-----------------------

User-defined attributes are the actual names and values provided by the user
for a given ad. They contain any valid key/value combination as described
below and are not limited by the category attributes. This means the user can
determine not only the value of the attribute, but also the name of the key.
The maximum length of the key is 32 characters, and it should contain at least one 
non-whitespace character. The possible values for the type are described below, and
the maximum character length for the value is 512 characters. User defined attributes
must also contain a **label** and a **locale**. The locale specifies the language
for the label and the value. The maximum length of the label is 32 characters.
The label can contain the same value as the key.
Locale must contain a valid locale string (e.g. one of en, nl, fr, en_US, en_GB, da_dk, no_NO_NY)

All of the user attributes will be stored with the ad. After placing an ad the
iCAS system will analyze the user-defined attributes for familiarities with respect to
category attributes. If a user-defined attribute is recognized by
iCAS, the **recognized** flag is set to **true**. An attribute is recognized if the provided
type and value(s) for that particular attribute key match the type and possible values
as defined in the category tree. The recognized attributes can be used to apply the desired
filtering criteria supplied by potential buyers searching on the tenant marketplace.

Beware that category attributes which are marked as ``mandatory`` in the category tree must
be supplied with the ad, otherwise the ad will be invalidated. Attributes that are not ``updatable``
cannot be changed, once they are supplied. An attempt to change the value of such attribute will also result in ad invalidation.

Example
^^^^^^^

.. code-block:: javascript

    [
        { 
            "key" : "color",
            "label" : "kleur",
            "locale" : "nl_NL",
            "type": "STRING", 
            "value" : "Zwart"
        },
        {
            "key" : "color",
            "label" : "color",
            "locale" : "en_NL",
            "type": "STRING",
            "value" : "Black"
        },
        { 
            "key" : "size",
            "label" : "size",
            "locale" : "en_NL",
            "type" : "NUMBER",
            "value" : 6
        },
        {
            "key" : "daysOfWeek",
            "label" : "Days of the week",
            "locale" : "en_NL",
            "type" : "LIST",
            "value" : ["Monday", "Tuesday", "Friday"]
        },
        ...
    ]


For user-defined attributes the following types are supported:

========    ========================    ===============================================================
type        constraints                 description
========    ========================    ===============================================================
STRING      max. 512 chars              A single string value, e.g. "rood"
LIST        max. 512 chars [#f1]_       A list of string or number values, e.g. ["S", "M", "L", "XL"]
NUMBER      int or double               A single number value, e.g. 1500 or 46.5
========    ========================    ===============================================================

.. [#f1] The JSON representation **of the value** of a *list* attribute must not exceed 512 characters.

