.. code-block:: javascript

    {
    	"title": <string>,
    	"dateCreated": <string>,
    	"status": <string>,
        "vendorId": <string>,
    	"cpc": <number>,
    	"budgets": {
    		"daily": {
    			"limit": <number>,
    			"spent": <number>
    		},
    		"monthly": {
    			"limit": <number>,
    			"spent": <number>
    		},
    		"total": {
    			"limit": <number>,
    			"spent": <number>
    		}
    	},
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
    	},
    	"links": {
    		"linkedAds": <string>
    	}
    }


===================  =========================================================================================
Field                 Description
===================  =========================================================================================
``title``             A description of your campaign. Only visible on your dashboard, it will never be shown to buyers.
``dateCreated``       The ISO 8601 UTC date and time the campaign was created.
``dateLastUpdated``   The ISO 8601 UTC date and time the campaign was last updated
``status``            The desired state of the campaign. Can be one of the user-controlled status values described in :ref:`User Controlled States <user-controlled-states>`. Default value is ``PAUSED``.
``vendorId``          Seller-provided unique reference the campaign. Once set, it cannot be modified.
``CPC``               Fixed CPC (in cents) that applies for all linked ads in this campaign.
``budgets``           An object containing the budget limits for this campaign. See :ref:`Budget types <campaign-budget-types>` for more. The limits unit is cents. The default values are set to **-1 (Unlimited)**.
``targeting``         A :ref:`Campaign Targeting Object <campaign-targeting-object>`, containing the targeting settings for this campaign. See :ref:`Campaign Targeting <campaign-targeting>` for more. The default value is an empty targeting, indicating that the targeting is nationwide (no limitations).
``links``             An object containing RESTful links to other related resources
===================  =========================================================================================

