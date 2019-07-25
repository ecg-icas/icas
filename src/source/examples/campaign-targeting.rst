.. _campaign-targeting-object:

Campaign Targeting Object
~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: javascript

	"targeting": {
    		"geos": [
    			{
    				"lat": <number>,
    				"lon": <number>,
    				"radius": <number>,
    				"displayValue": <string>
    			}, ...
    		],
    		"regionIds": [<number>,...]
    }


===================  =========================================================================================
Parameter             Description
===================  =========================================================================================
``geos``              A list of circular areas for geo-targeting. Default is empty, which implies nationwide targeting (no targeting restrictions).
``lat``               Latitude of the center-point of the circular area for geo-targeting
``lon``               Longitude of the center-point of the circular area for geo-targeting
``radius``            Radius (in km) of the circular area for geo-targeting
``diplayValue``       Description of the circular area for geo-targeting. Only visible on your dashboard, it will never be shown to buyers.
``regionIds``         A list of valid regionIds from the Regions taxonomy. Default is ``[0]``, which implies nationwide targeting (no targeting restrictions).
===================  =========================================================================================
