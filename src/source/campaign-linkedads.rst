.. _campaign_linkedads_overview:

Campaign Linked Ads
===================

.. _campaign-linked-ads:


Campaign's linkedAds component defines which ads are part of the campaign. It is possible to add / remove (link / unlink) ads from a campaign using
:ref:`put_campaign_linkedads` / :ref:`delete_campaign_linkedads`. Deleting a linkedAd from a campaign does not remove the ad from your inventory, it merely takes it offline in the context of the particular campaign.

LinkedAds are stored as part of the campaign, and have a reference to an Ad using its ID. A linkedAd consists of two parts:
the Ad ID and some possible overrides from the campaign defaults.
Using linkedAds, it is possible to add a single ad to multiple campaigns (which may have different budgets, CPC and targeting criteria).
It is, however, not possible to add a single ad multiple times to the same campaign.

Ads that are not referred to by any linkedAd in any active campaign will **not** be shown on site.

Ad ID
"""""
The ID of the ad that this linkedAd refers to. This is the unique identifier of the ad itself, described in :ref:`ad_id`.


Overrides
"""""""""
A linkedAd can have certain overrides as well. For instance, it is possible to set a specific budget for an ad in a campaign, in addition to an overal campaign budget; if the campaign has a daily budget of 20 euros,
it is possible to limit the spent of a single ad in that campaign to 10 euros, making sure that the budget of the campaign
is more fairly spread out over the remaining campaign ads (in case you have a very high performing ad in the campaign, for example).
It is also possible to let a bidding agent automatically manage the CPC and budgets on a particular linkedAd, in a more optiomal way.
See :ref:`put_campaign_linkedads` for more details.
