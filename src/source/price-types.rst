.. index::
    single: Price Types
    pair: Price Types; BIDDING
    pair: Price Types; BIDDING_FROM
    pair: Price Types; FIXED_PRICE
    pair: Price Types; FREE
    pair: Price Types; NEGOTIABLE
    pair: Price Types; SEE_DESCRIPTION
    pair: Price Types; SWAP
    pair: Price Types; CREDIBLE_BID
    pair: Price Types; ON_DEMAND
    pair: Price Types; NOT_APPLICABLE
    pair: Price Types; RESERVED



Price Types
-----------

Each advertisement has a price type which determines the type of transaction the seller would like to perform.
The following table lists the valid price types and their descriptions.


.. note::
    Please notice the deprecated price types, after the grace period they will be migrated to ``SEE_DESCRIPTION`` and support will be removed from the API.


================    ================    ===========    ===================================================================================================================
PRICE_TYPE          Price required?     Deprecated     Description
================    ================    ===========    ===================================================================================================================
BIDDING             no                  no             Request a bid on the ad starting from 0 EUR.
BIDDING_FROM        yes                 no             Request a bid with a starting price > 0 EUR. **price** must contain a value in the interval of ``(0,10000000000]``.
FIXED_PRICE         yes                 no             Request a fixed price. **price** must contain a value in the interval of ``(0,10000000000]``.
FREE                no                  no             Request no price.
NEGOTIABLE          no                  yes            Request a negotiation between buyer and seller.
SEE_DESCRIPTION     no                  no             Additional information is in the description of the ad.
SWAP                no                  yes            Request an exchange of one item for another.
CREDIBLE_BID        no                  no             Request for any reasonable offer.
ON_DEMAND           no                  yes            Price is communicated on request.
NOT_APPLICABLE      no                  yes            Price is not applicable for this ad (e.g. a Jobs ad).
RESERVED            no                  yes            Flag for transaction in progress.
================    ================    ===========    ===================================================================================================================

