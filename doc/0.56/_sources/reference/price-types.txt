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
    pair: Price Types; RESERVED
    
.. _price_types:

Price Types
===========

Each advertisement has a price type which determines the type of transaction the seller would like to perform.
The following table lists the valid price types and their descriptions.

================    ================    ============================================================================================
PRICE_TYPE          Price required?     Description
================    ================    ============================================================================================
BIDDING             no                  Request a bid on the ad starting from 0 EUR. **price** must be omitted.
BIDDING_FROM        yes                 Request a bid with a starting price > 0 EUR. **price** must contain a value > 0.
FIXED_PRICE         yes                 Request a fixed price. **price** must contain a value > 0.
FREE                no                  Request no price. **price** must be omitted.
NEGOTIABLE          no                  Request a negotiation between buyer and seller. **price** must be omitted.
SEE_DESCRIPTION     no                  Additional information is in the description of the ad. **price** must be omitted.
SWAP                no                  Request an exchange of one item for another. **price** must be omitted.
CREDIBLE_BID        no                  Request for any reasonable offer. **price** must be omitted.
ON_DEMAND           no                  Price is communicated on request. **price** must be omitted.
RESERVED                                Flag for transaction in progress.
================    ================    ============================================================================================

