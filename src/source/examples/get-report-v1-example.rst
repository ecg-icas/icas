.. code-block:: javascript

    GET /report/?date=2014-01-30
    Accept: application/sellside.report-v1+json, application/json

    200 OK
    Content-Type: application/sellside.report-v1+json; charset=utf-8

    [
    	{
    		"id":544023,
    		"date":"2014-01-29T23:00:00Z",
    		"adId":210338,
    		"categoryId":2,
    		"title":"Test Ad 1",
    		"startDate":"2014-01-30T10:05:41Z",
    		"endDate":"2014-01-30T10:11:21Z",
    		"totalBudget":5000,
    		"dailyLimit":1000,
    		"totalSpent":60,
    		"cpc":10,
    		"impressions":120,
    		"clicks":6,
    		"urlClicks":3,
    		"emails":1,
    		"externalId":"f985f7eecc",
    		"vendorId":"vndr"
    	},
    	{
    		"id":544028,
    		"date":"2014-01-29T23:00:00Z",
    		"adId":210339,
    		"categoryId":3,
    		"title":"Test Ad 2",
    		"startDate":"2014-01-30T10:11:28Z",
    		"endDate":null,
    		"totalBudget":5000,
    		"dailyLimit":1000,
    		"totalSpent":20,
    		"cpc":10,
    		"impressions":24,
    		"clicks":2,
    		"urlClicks":0,
    		"emails":0,
    		"externalId":"bffb7103d5",
    		"vendorId":""
    	}
    ]
