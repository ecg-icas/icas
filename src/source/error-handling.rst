.. index:: Error Handling

Error Handling
==============

In the Sellside API all calls are validated and if an error occurs a detailed
machine-readable error message is returned. Since some calls may return more
than one error for a given call, e.g. during the validation of a new ad, all
error responses contain lists of errors with one or more structured error
objects in them.

Each error contains a ``code`` and ``text`` attributes providing a numeric
error code and a simple English error message. An error may contain a
``field`` attribute describing the field where the error occurred and an
additonal ``arg`` attribute further specifying the error, i.e. the maximum
length of a field in case of a "string too long" error.

The validation will first check if the input parameters are of the correct type,
i.e. an integer should be an integer, not a string or a decimal value.
Secondly, the Sellside API will check if the provided input parameters are meaningful
within the context of the call. E.g. a category ID should be a positive integer.
Only the context specific checks are mentioned in the Errors section of the documentation page of
each call, as the type checks are considered generic.

.. code-block:: javascript

    400 Bad Request
    Content-Type: application/sellside.error.list-v1+json;charset=UTF-8

    [
        {
            "code":2005,
            "text":"too long",
            "field":"name",
            "arg":60,
            "msg":"The field 'name' must not be longer than 60 characters."
        }
    ]

