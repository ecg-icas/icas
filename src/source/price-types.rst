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
The following table lists the valid price types and their descriptions. Please notice the deprecated price types,
they will be removed after a grace period.

================    ================    ===========    ===================================================================================================================
PRICE_TYPE          Price required?     Deprecated     Description
================    ================    ===========    ===================================================================================================================
BIDDING             no                  No             Request a bid on the ad starting from 0 EUR.
BIDDING_FROM        yes                 No             Request a bid with a starting price > 0 EUR. **price** must contain a value in the interval of ``(0,10000000000]``.
FIXED_PRICE         yes                 No             Request a fixed price. **price** must contain a value in the interval of ``(0,10000000000]``.
FREE                no                  No             Request no price.
NEGOTIABLE          no                  Yes            Request a negotiation between buyer and seller.
SEE_DESCRIPTION     no                  No             Additional information is in the description of the ad.
SWAP                no                  Yes            Request an exchange of one item for another.
CREDIBLE_BID        no                  No             Request for any reasonable offer.
ON_DEMAND           no                  Yes            Price is communicated on request.
NOT_APPLICABLE      no                  Yes            Price is not applicable for this ad (e.g. a Jobs ad).
RESERVED            no                  Yes            Flag for transaction in progress.
================    ================    ===========    ===================================================================================================================

