.. note::
    iCas introduces a new unit of micros across our product, where **one cent equals 10000 micros**. **One micro is 1-millionth of the local tenant currency**. This will allow for a higher level of granularity when specifying the cost (per click). 

    iCas is substituting the current CPC values across the API with a bid value, and the actual (incurred) billed cost value - this to allow for better differentiation between the two. This split between bid and billed values is currently utilised for an experimental feature which adjusts the bid value for the quality of the traffic. 

    This new micros unit, as well as the distinction between bid and billed cost, are to become a core part of the product. iCas will gradually deprecate any fields with cents and local currency units across the API.
