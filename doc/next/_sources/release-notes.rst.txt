.. index:: Release Notes
.. _release_notes:

Release Notes
=============

This section attempts to give a little more insight on what our various releases contain, as compared to previous versions.

Feb 2023: 'Campaigns & Micros'
------------------------------

Synopsis
""""""""

* For bid, budgets & spent values we now report in micros: 1 cent == 10000 micros. These fields will now also be named accordingly, mentioning whether they represent a value in cents or micros. This is also represented in the categories data, where the interval of allowed values is defined. Mind, this does not include values like 'AUTOMATIC' or 'UNLIMITED'.
* Introduced campaigns, campaign ID not (yet) mandatory while placing ads. Campaigns have their own daily/total budgets. Since currently only 1 campaign is allowed per user, this effectively represents the seller's complete budget.
* Moved price and related fields into a struct.
* removed externalID, use vendorID instead.
* removed currency, 1 country == 1 currency anyway. Monetary values always in local currency.
* removed pageNumber & suggestedCpcForPageOne: Numbers are unreliable and only work for the leaf category browse action, which by now is only a very small portion of our traffic on any of our marketplaces. Therefore, these numbers are not representative anymore, and we chose to remove them.
* Use the V2 version of /metrics/ads and /metrics/report to get spent and bid values in micros too, to avoid confusion. V1 is deprecated.
* User endpoint updated to V4, this adds 1 new field to V3 (which added 1 field to V2).

Ads
"""

See :ref:`ads` for full details.

.. list-table::
 :widths: 20 80
 :header-rows: 1

 * - Field
   - Change synopsis
 * - cpc 		            
   - moved to bidMicros. Now allows for 'AUTOMATIC' too.
 * - totalBudget            
   - moved to budgets.total.limitMicros. Now allows 'UNLIMITED' too.
 * - spentBudget               
   - moved to budgets.total.spentMicros
 * - dailyBudget            
   - moved to budgets.daily.limitMicros. Now allows 'UNLIMITED' too.
 * - dailySpent            
   - moved to budgets.daily.spentMicros
 * - campaignId          
   - new, not yet mandatory.
 * - status             
   - can now contain "DOMAIN_PENDING", requiring the seller to confirm the new clickout url domain before the can go active.
 * - price                
   - moved to price.amountCents
 * - priceType            
   - moved to price.priceType
 * - priceUnit            
   - moved to price.priceUnit
 * - originalPrice       
   - moved to price.originalAmountCents
 * - currency             
   - removed
 * - externalId           
   - removed
 * - statusReasons        
   - removed, status is expanded
 * - pageNumber           
   - removed
 * - suggestedCpcForPageOne
   - removed
 * - allowPaypal            
   - removed


Categories
""""""""""

See :ref:`categories` for full details.

.. list-table::
 :widths: 20 80
 :header-rows: 1

 * - Field
   - Change synopsis
 * - currency               
   - removed
 * - cpc
   - moved to bidMicros.
 * - totalBudget            
   - moved to totalBudgetMicros.
 * - minDailyBudget
   - moved to dailyBudgetMicros. This is now an interval instead of min value.
 * - paypalEnabled
   - removed
 * - paypalBpEnabled
   - removed
 * - suggestedCpcForPageOne
   - removed

Campaigns
"""""""""
Added first campaign support. See :ref:`campaigns` for full details.

* :ref:`get_campaign`  GET /campaign with application/sellside.campaign.list-v5+json to get list of campaigns for a user. Expected 0 or 1 result.
* :ref:`get_campaign_id` to fetch the individual campaign.
* :ref:`put_campaign_id_status` to manage the campaign status (ACTIVE,PAUSED).
* :ref:`put_campaign_id_budgets` to manage the campaign's budgets.

.. note::
 We will create a campaign underwater for users who start placing ads without having a campaign, be sure to check the budgets of that campaign as 
 a default campaign will have unlimited budget.
 Deleting a campaign is currently not allowed.

User
""""

See :ref:`get_user` for full details.

Start using V4. There are 2 new fields in comparison with V2:
``hasAds`` (**bool**), whether a user has ads in the system and 
``isApiManaged`` (**bool**), whether we see API partners managing ads for the user (not true if an api partner is using RO scopes only)


Deprecation list
""""""""""""""""

The following calls are deprecated and scheduled to be removed on July 1st, 2023:

.. list-table::
 :widths: 80 80
 :header-rows: 1

 - * deprecated endpoint
   * replaced by 
 - * :ref:`get_ad_v4`
   * :ref:`get_ad_v5`
 - * :ref:`get_ad_id_v3`
   * :ref:`get_ad_id_v5`
 - * :ref:`get_ad_id_v2`
   * :ref:`get_ad_id_v5`
 - * :ref:`get_ad_vendor_id_v3`
   * :ref:`get_ad_vendor_id_v5`
 - * :ref:`get_ad_vendor_id_v2`
   * :ref:`get_ad_vendor_id_v5`
 - * :ref:`post_ad_v3`
   * :ref:`post_ad_v5`
 - * :ref:`post_ad_v2`
   * :ref:`post_ad_v5`
 - * :ref:`put_ad_id_v3`
   * :ref:`put_ad_id_v5`
 - * :ref:`put_ad_id_v2`
   * :ref:`put_ad_id_v5`
 - * :ref:`get_user_v2`
   * :ref:`get_user_v4`
 - * :ref:`get_user_v3`
   * :ref:`get_user_v4`
 - * :ref:`get_category_id_v2`
   * :ref:`get_category_id_v5`
 - * :ref:`get_categories_v1`
   * :ref:`get_categories_v5`

Feb 2020
--------

Deprecation list
""""""""""""""""

The following calls are deprecated and scheduled to be removed on the 15th of July 2020:

.. list-table::
 :widths: 80 80
 :header-rows: 1

 - * deprecated endpoint
   * replaced by

 - * :ref:`get_ad_v3`
   * :ref:`get_ad_v4`

Dec 2019: 'Reporting V2'
------------------------

Deprecation list
""""""""""""""""

The following calls are deprecated and scheduled to be removed after 1st of March 2020:

* :ref:`get_report`
* :ref:`get_report_detail`
* :ref:`get_report_detail_id`
* :ref:`get_report_summary_v2`
* :ref:`get_report_summary_v1`
* :ref:`post_report_detail`
* :ref:`get_user_v1`
* :ref:`get_categories_statistics`
