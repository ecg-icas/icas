.. index:: GET /categories/statistics
.. _get_categories_statistics:

GET /categories/statistics
==========================


.. warning::

	This call is scheduled to be deprecated. Please
	use the faster and more flexible generic endpoint :ref:`post_metrics_data` instead, with the following payload to get the equivalent data:
    .. include:: ../examples/get-categories-statistics-replacement.rst

    As you can see, the date range in this call is not limited to a single date parameter.


GET /categories/statistics
--------------------------

.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_ro`` or ``console_ro``

 * - Accept
   - ``application/sellside.category.statistics-v1+json, application/json``

This URL returns a list of category statistics elements with statistics per category
for the provided day. It is also possible to request only statistics for certain
categories by using the parameter ``categoryIds``.

If the parameter ``categoryIds`` contains invalid data, i.e. not a positive
integer, the server returns **400 Bad Request**.

If the parameter ``date`` contains an invalid date, the server returns **400 Bad Request**.
The ``date`` parameter is mandatory, the ``categoryIds`` parameter is not. By default
all data for all categories (having data) is returned. Categories which have no data for the
specified day will not have a statistics object in this result.

This method only allows 1 date parameter and not a date range is to make sure the individual calls
are still manageable in both time and amount of data to process internally.

Parameters
----------

====================    ========    ================================================================================
Name                    Type        Description
====================    ========    ================================================================================
categoryIds             string      Comma-separated-list of integer id's of the categories to get statistics for. Optional, default is for all categories.
date                    string      Mandatory date for the statistics. Must be a valid date in format 'yyyy-MM-dd'
_include                string      Comma-separated-list of fields to include. Optional, default is all fields.
_exclude                string      Comma-separated-list of fields to omit. Optional, default empty.
====================    ========    ================================================================================

Errors
------

====================    ====    =======================     ==============================================================================
Field                   Code    Error message               Description
====================    ====    =======================     ==============================================================================
date                    2000    missing argument            The date parameter needs to be present
date                    2001    invalid argument            The date parameter is not a correct date
categoryIds             2001    invalid argument            The comma-separated-list contains one or more non-integer values
categoryIds             2004    too short                   The value needs to be non-empty
====================    ====    =======================     ==============================================================================

Example
-------

.. include:: ../examples/get-categories-statistics-example.rst
