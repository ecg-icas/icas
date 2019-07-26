.. code-block:: javascript

    {
    	"title": <string>,
    	"status": <string>,
        "vendorId": <string>,
    	"cpc": <number>,
    	"budgets": {
    		"daily": {
    			"limit": <number>
    		},
    		"monthly": {
    			"limit": <number>
    		},
    		"total": {
    			"limit": <number>
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
    	}
    }


===================  =========================================================================================
Field                 Description
===================  =========================================================================================
``title``             A description of your campaign. Only visible on your dashboard, it will never be shown to buyers.
``status``            The desired state of the campaign. Can be one of the user-controlled status values described in :ref:`User Controlled States <user-controlled-states>`. Default value is ``PAUSED``.
``vendorId``          Seller-provided unique reference the campaign. Once set, it cannot be modified.
``CPC``               Fixed CPC (in cents) that applies for all :ref:`Campaign Linked Ads <campaign-linked-ads>` in this campaign.
``budgets``           An object containing the budget limits for this campaign. See :ref:`Budget types <campaign-budget-types>` for more. The limits unit is cents. The default values are set to **-1 (Unlimited)**.
``targeting``         A :ref:`Campaign Targeting Object <campaign-targeting-object>`, containing the targeting settings for this campaign. See :ref:`Campaign Targeting <campaign-targeting>` for more. The default value is an empty targeting, indicating that the targeting is nationwide (no limitations).
===================  =========================================================================================