.. _migration-guide:

Migration Guide
===============

**Purpose**: This guide is designed to help API partners migrate from older deprecated API versions (``v2``, ``v3``, ``v4``) to the latest version (``v5``) of the Sellside API.

Key changes and benefits of migrating
-------------------------------------

* ○ Introducing **micros** as the monetary unit enables more precise cost management, allowing finer granularity in ad spending and budget allocation. **1 cent is equal to 10000 micros.**

* ○ **Autobidding** allows the use of an automated (smart) bidding strategy.

* ○ **Improved pagination** with the more efficient industry-standard ``pageToken``, as a replacement for the old ``offset/limit`` pagination mechanism.

* ○ Optional **campaign (and campaign budget)** management allows for better control over spending, by setting a campaign-level budget as well as pausing an entire campaign, effectively taking all the ads in the campaign offline.

* ○ Budgets and price fields are streamlined into a clear format, improving accuracy and consistency across the API.

* ○ **Removal of** ``pageNumber`` & ``suggestedCpcForPageOne`` from ad and category endpoints.

    **Context**: In the desktop era, most traffic came from leaf category browse actions, leading to the introduction of the "suggested CPC for page one." However, as traffic sources have diversified to include search actions and personalized recommendations, the relevance of these fields has decreased.

    The removal reflects the shift towards a more dynamic and diverse traffic landscape where different ranking methods are more effective. This simplifies ad management by removing outdated metrics.


Step by step guide
------------------
.. include:: migration-guide/step-by-step.rst



Campaigns
---------
The Campaigns API helps you manage your campaign(s) efficiently. Think of a campaign as a container for ads, with key details like the campaign ID, name, creation date, and daily and total budget limits. Each campaign also has a status field that shows whether it is active or inactive.

By default, campaign management is largely automated behind the scenes. All seller ads are automatically grouped into a single default campaign that is created and managed under the hood. However, as an API partner, you have the flexibility to create, update, and manage campaigns yourself, allowing for more granular control over your advertising strategy.

When using the campaigns API for the first time, it’s handy to remember to:

 * ○ `Get a list of campaigns <https://ecg-icas.github.io/icas/openapi/index.html#/Campaigns/get_campaigns>`_ to check if the user already has an automatic “default” campaign created by the system. It will provide you with a campaign identifier can then use for the rest of the endpoints.

 * ○ `Update a campaign budgets <https://ecg-icas.github.io/icas/openapi/index.html#/Campaigns/put_campaign__id__budgets>`_ to set or change a daily and total budget for the campaign. This is a prerequisite for using the autobidding feature. Beware that the budget limits apply to all ads within the campaign, which means that when the budget limit is reached, all ads in the campaign will be taken offline.

 * ○ You can also `work with a vendorId <https://ecg-icas.github.io/icas/openapi/index.html#/Campaigns/getCampaignByVendorId>`_ in case you manage multiple campaigns and want to keep track of them in your own system too.

Q&A
---

○ **What should I do with the** ``externalId`` **? I need it for keeping track of ads.**

    Please move to using ``vendorId``, keep in mind that it needs to be unique per seller.


○ **What happened to the ad funnel information, it is no longer in the payload?**

    The ad funnel information is now available in the new `GET /ad/{id}/position <https://ecg-icas.github.io/icas/openapi/index.html#/Ads/getAdPosition>`_ endpoint.


○ **How do I handle the new** ``bidMicros`` **field?**

    The ``bidMicros`` field is a replacement for the old ``cpc`` field. It is a value in micros, which is 1/10000 of a cent. When interpreting the value, you should convert it to cents by dividing by 10000.


○ **What is the new** ``campaignId`` **field in the ad payload?**

    The ``campaignId`` field is an identifier for the campaign which this ad is part of. Campaign management is optional. By default, every seller has one campaign associated with them, with every ad attached to that campaign. See <campaigns> for more.


○ **What does the status value** ``DOMAIN_PENDING`` **in ads mean?**

    This status is related to a phishing protection measure we implemented for sellers using the Admarkt Console UI. This protection helps prevent scammers from adding phishing URLs to ads when taking over a seller account, by requiring sellers to confirm that the domain associated with the ad is valid, via email.
    It's important to note that this protection is currently only active for sellers who manage their ads through the Console UI. As a result, API partners should not typically encounter the ``DOMAIN_PENDING`` status.


○ **Do I have to use the campaign related endpoints?**

    No, campaign management is optional. By default, every seller has one campaign associated with them, with every ad attached to that campaign. However, if you plan to leverage our autobidding features, you'll need to use the campaign-related endpoints, specifically to set a daily budget limit at the campaign level. This is a prerequisite for using the autobidding.
    Setting a daily limit also helps you optimize your cost per click and maximize conversions while controlling your budget from being depleted too quickly.


○ **What happens when I pause a campaign?**

    When you set the status of a campaign to ``PAUSED``, all  ads within that campaign will no longer be visible online on our marketplace, and your budget will immediately stop spending. However, this does not change the individual status of each ad; it only affects their effective visibility for the buyers on our marketplace. When you reactivate the campaign by setting its status to ``ACTIVE`` or by adding a budget, only the ads with an individual status of ``ACTIVE`` will become visible on our marketplace again.