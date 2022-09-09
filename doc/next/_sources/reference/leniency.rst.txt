This endpoint allows the client to specify the preferred leniency handling via a special header (https://datatracker.ietf.org/doc/html/rfc7240#section-4.4), for minor errors like wrong casing of names and values of request parameters, as well as
whether to invalidate the request if an unknown parameter is passed. We reserve the right to ignore such leniency preferences under certain conditions.

By default the leniency is ``strict``.

Leniency examples
-----------------

.. include:: ../examples/get-campaign-views-leniency-example-1.rst