.. _campaign_targeting_overview:

Campaign Targeting
==================

.. _campaign-targeting:

Campaigns allow you to target specific groups of buyers. Buyers not in these target groups will typically not
see any ads from this campaign (some exceptions apply). Currently, only geographic targeting is supported but we
are looking to add other forms of targeting. See :ref:`post_campaign` for more details.

.. note::
    **At the moment, we are still in an experimental stage with the campaign targeting options.** Please do not use this field yet, setting it can cause unexpected behaviours. Do shout out to us on Discord if you are interested in using it, we would love to hear.

Geo Targeting
"""""""""""""

Geo targeting allows you to specify one or more (circular) areas in the targeting criteria of a campaign
to have the ads of that campaign only be shown to buyers located in any of the geographical areas specified.

Region Targeting
""""""""""""""""

For tenants that use regions (currently Kijiji Canada), you can specify one or more regions in the targeting criteria of a campaign
to have the ads of that campaign only be shown to buyers located in that region.

Geo-circles and regions **cannot and should not** be used in combination on the same campaign. This is currently not supported.

.. _campaign-targeting-object:

Campaign Targeting Object
~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: javascript

	{
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
``geos``              A list of circular areas for geo-targeting. Default is empty array, which implies nationwide targeting (no targeting restrictions).
``lat``               Latitude of the center-point of the circular area for geo-targeting
``lon``               Longitude of the center-point of the circular area for geo-targeting
``radius``            Radius (in km) of the circular area for geo-targeting
``diplayValue``       Description of the circular area for geo-targeting. Only visible on your dashboard, it will never be shown to buyers.
``regionIds``         A list of valid regionIds from the :ref:`Regions <regions>` taxonomy. Default is empty array or ``[0]``, either of which implies nationwide targeting (no targeting restrictions).
===================  =========================================================================================
