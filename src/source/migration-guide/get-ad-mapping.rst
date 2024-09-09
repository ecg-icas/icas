- New media type: ``application/sellside.ad-v5+json``

- **Price**: ``price`` and ``originalPrice`` map to ``price.amountCents`` and ``price.originalAmountCents`` respectively. The value was already in cents so there is no need for conversion.

- **CPC**: ``cpc`` is replaced by ``bidMicros``, and is stringified. This requires a conversion of the values from a micros unit, when interpreting them as cents.

- **Budget Fields**: ``dailyBudget`` and ``totalBudget`` map to ``budgets.daily.limitMicros`` and ``budgets.total.limitMicros`` respectively. ``dailySpent`` and ``spentBudget`` map to ``budgets.daily.spentMicros`` and ``budgets.total.spentMicros``. All these require conversion of the values from a micros unit (and are stringified), when interpreting them as cents. The limits can also be ``UNLIMITED``.

- **Shipping Cost**: ``cost`` is renamed to ``costCents`` in V5. The value was already in cents so there is no need for conversion.

- **Removed** field(s): ``statusReasons``, ``pageNumber``, ``suggestedCpcForPageOne``, ``currency``, ``allowPayPal``, ``externalId``. The field ``vendorId`` should be used instead of ``externalId``.

- **New** field(s): ``campaignId``: this is an identifier for the campaign which this ad is part of. Campaign management is optional. By default, every seller has one campaign associated with them, with every ad attached to that campaign. See <campaigns> for more.

- If necessary, position (page number and suggested cost per click) funnel information can be obtained from the replacement `GET /ad/{id}/position <https://ecg-icas.github.io/icas/openapi/index.html#/Ads/getAdPosition>`_ endpoint (see below).
