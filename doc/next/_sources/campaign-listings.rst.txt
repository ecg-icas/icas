.. _campaign_listings_overview:

Campaign Listings
=================

Campaign Listings define which ads are part of the campaign. It is possible to add / remove ads from a campaign using
:ref:`put_campaign_listings` / :ref:`delete_campaign_listings`.
Listings are stored as part of the campaign, and have a reference to the Ad ID. A listing consists two parts:
the Ad ID and optional overrides.
Using Listings, it is possible to add a single ad to multiple campaigns (which may have different budgets and targeting criteria).
It is, however, not possible to add a single ad multiple times to the same campaign.

Ads that are not referred to by any listing in any active campaign will **not** be shown on site.

Ad ID
"""""
The ID of the ad that this listing refers to. This is the unique identifier of the ad, described in :ref:`ad_id`.


Overrides
"""""""""
A Listing can have certain overrides as well; for instance, a campaign can have a CPC defined of 5 cents, but
one ad is allowed to spend more (6 cents) - this is defined on the listing.
Another option is to set a specific budget for an ad in a campaign; if the campaign has a daily budget of 20 euros,
it is possible to limit the spent of a single ad in that campaign to 10 euros, making sure that the budget of the campaign
is at least spread out over multiple ads (in case the seller has one very high performing ad in the campaign).
See :ref:`put_campaign_listings` for more details.
