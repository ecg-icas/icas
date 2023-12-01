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

.. _price_types:

Price Types
===========

Each advertisement has a price type which determines the type of transaction the seller would like to perform.
The following table lists the valid price types and their descriptions.

================    ================    ===================================================================================================================
PRICE_TYPE          Price required?     Description
================    ================    ===================================================================================================================
BIDDING             no                  Request a bid on the ad starting from 0 EUR.
BIDDING_FROM        yes                 Request a bid with a starting price > 0 EUR. **price** must contain a value in the interval of ``(0,10000000000]``.
FIXED_PRICE         yes                 Request a fixed price. **price** must contain a value in the interval of ``(0,10000000000]``.
FREE                no                  Request no price.
NEGOTIABLE          no                  Request a negotiation between buyer and seller.
SEE_DESCRIPTION     no                  Additional information is in the description of the ad.
SWAP                no                  Request an exchange of one item for another.
CREDIBLE_BID        no                  Request for any reasonable offer.
ON_DEMAND           no                  Price is communicated on request.
NOT_APPLICABLE      no                  Price is not applicable for this ad (e.g. a Jobs ad).
RESERVED                                Flag for transaction in progress.
================    ================    ===================================================================================================================

