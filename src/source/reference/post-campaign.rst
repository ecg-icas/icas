.. index:: POST /campaign
.. _post_campaign:

POST /campaign
==================

.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_rw`` or ``console_rw``

 * - Accept
   - ``application/sellside.campaign-v2+json``

 * - Content-Type
   - ``application/sellside.campaign-v2+json``   

Creates a new campaign for the user. If successful, it returns an object representing the campaign, with
default values on certain fields, if not provided. A minimum payload is an empty JSON, as none of the fields
are mandatory.


.. include:: ../examples/post-campaign-example.rst

The full campaign payload data model that you can provide, has the following structure:

.. code-block:: javascript

    {
    	"title": <string>,
    	"status": <string>,
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
    				"type": <string>,
    				"value": <string>,
    				"displayValue": <string>
    			}, ...
    		],
    		"regionIds": [<number>,...]
    	},
    	"links": {
    		"linkedAds": <string>
    	}
    }


================  =========================================================================================
Parameter          Description
================  =========================================================================================
``title``          A description of your campaign. Only visible on your dashboard, it will never be shown to buyers.
``status``         The desired state of the campaign. Can be one of the user-controlled status values described in :ref:`User Controlled States <user-controlled-states>`. Default value is ``PAUSED``.
``CPC``            Fixed CPC (in cents) that applies for all linked ads in this campaign.
``budgets``        An object containing the budget limits for this campaign. See :ref:`Budget types <campaign-budget-types>` for more. The limits unit is cents. The default values are set to **-1 (Unlimited)**.
================  =========================================================================================
