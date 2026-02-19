- **Deprecated** media type(s): ``application/sellside.ad-v2+json`` ``application/sellside.ad-v3+json``
- New media type: ``application/sellside.ad-v5+json``

- **Price**: ``price`` and ``originalPrice`` map to ``price.amountCents`` and ``price.originalAmountCents`` respectively. The value was already in cents so there is no need for conversion.

- **CPC**: ``cpc`` is replaced by ``bidMicros``. This requires a conversion of the values to a micros unit, and supplying it as string type, instead of integer.

- **Budget Fields**: ``daiyBudget`` and ``totalBudget`` map to ``budgets.daily.limitMicros`` and ``budgets.total.limitMicros`` respectively. ``dailySpent`` and ``spentBudget`` map to ``budgets.daily.spentMicros`` and ``budgets.total.spentMicros``. **Beware that they are now mandatory to supply.**
  Values should be supplied in string type, instead of integer, and at micro precision, instead of cents. The budget limits can also be ``"UNLIMITED"``.

- **Shipping Cost**: ``cost`` is renamed to ``costCents``. The value was already in cents so there is no need for conversion.

- **Removed** field(s): ``currency,`` ``allowPayPal``. ``externalId`` is marked as deprecated and planned for removal, please use ``vendorId`` instead.