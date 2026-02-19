- **Deprecated** media type(s): ``application/sellside.ad.list-v4+json``
- New media type: ``application/sellside.ad.list-v5+json``

- **Ads**: the list of ads under ``ads`` is now of the v5 format.

- **Removed** field(s): ``offset``, ``paremainingBudget``

- **New** field(s): ``nextPageToken``: this replaces the usage of ``offset`` for pagination. The value is a string that should be used as a query parameter in the next request to get the next page of results.
