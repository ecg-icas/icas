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

Category attributes are provided as part of the category in the **attributes**
link. Each category attribute has a **key**, a **label**, a **locale** for the label and values,
a **type** and depending on the type one or more additional properties describing the constraints.


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

.. code-block:: javascript

    [
        {
            "key": "Levering",
            "label": "Levering",
            "locale": "nl",
            "type" : "STRING",
            "values" : ["Ophalen", "Verzenden", "Ophalen of Verzenden"]
            "mandatory" : false
        },
        {
            "key": "Eigenschappen",
            "label": "Eigenschappen",
            "locale": "nl",
            "type" : "LIST",
            "values" : ["Met bandje", "Met ketting", "Verguld"],
            "mandatory" : false
        },
        {
            "key": "Motorinhoud",
            "label": "Motorinhoud",
            "locale": "nl",
            "type" : "NUMBER",
            "minValue" : 1,
            "maxValue" : 8500,
            "mandatory" : true
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
iCAS the **recognized** flag is set to **true**.

Currently, the user-defined attributes will only be stored. At a later stage
the iCAS system will automatically start indexing the user-defined
attributes and update the ads accordingly without user interaction.

Example
^^^^^^^

.. code-block:: javascript

    [
        { 
            "key" : "color",
            "label" : "kleur",
            "locale" : "nl",
            "type": "STRING", 
            "value" : "Zwart"
        },
        {
            "key" : "color",
            "label" : "color",
            "locale" : "en",
            "type": "STRING",
            "value" : "Black"
        },
        { 
            "key" : "size",
            "label" : "size",
            "locale" : "en",
            "type" : "NUMBER",
            "value" : 6
        },
        {
            "key" : "daysOfWeek",
            "label" : "Days of the week",
            "locale" : "en",
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

