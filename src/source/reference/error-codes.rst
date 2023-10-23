.. index:: Error Codes
.. _error_codes:

Error Codes
===========

====    ====    =============================    ==========================================================================================
Code    HTTP    Error message                    Description
====    ====    =============================    ==========================================================================================
1000    500     internal error                   An internal error occurred
1001    500     not implemented                  This call has not been implemented
1003    403     access denied                    Authorization failed
1004    404     not found                        The resource was not found or does not belong to the authenticated user
1005    400     invalid json                     The input is not valid JSON
1007    401     access denied                    The access token is invalid
1008    401     access denied                    The user connected to this access token is invalid
1009    401     missing token                    The Authorization header is missing or in the wrong format
2000    400     missing argument                 A mandatory argument was not provided
2001    400     invalid argument                 A provided value was invalid
2002    400     out of range                     A provided numeric value was out of range
2003    400     not equal                        A provided value was not equal to a required value
2004    400     value too short                  A provided string value was too short
2005    400     value too long                   A provided string value was too long
2006    400     invalid url                      A provided string value does not represent a valid URL
2007    400     unsupported format               A link to an file is in an unsupported format
2008    400     ad body too large                provided (ad) body content is too large
2010    400     invalid phone number             A provided string value does not represent a valid phone number
2011    400     too many active ads              The maximum number of active ads per seller in this category has been reached
2012    400     category change not allowed      Changing the category of an ad is not allowed
2017    400     ad status change not allowed     Changing the status of an ad is not allowed
2018    400     image type not allowed           The uploaded image type is not allowed
2019    400     insufficient budget              The budget for provided ad is insufficient
2020    400     insufficient daily budget        The daily budget for provided ad is insufficient
2021    400     duplicate feed url               The feed URL is already in use
2022    400     category not active              The category is not active and will not allow creation of ads
2023    400     category deleted                 The category is deleted and will not allow creation/updating of ads
2024    400     vendorId change not allowed      The vendorId can only be set once
2025    400     duplicate vendorId               The vendorId is already in use by another entity of the same tyope
2027    400     cannot change seller budget      The provided amount cannot be added/subtracted from current seller level budget
2028    400     regionId change not allowed      Changing the regionId of an ad is not allowed
2030    400     missing identifying attribute    The call requires an identifying attribute, but it is missing
2034    400     campaign already exists          The campaign already exists
2035    400     attribute is not writable        The attribute cannot be set by the user
2037    400     unknown field name               An unrecognised field was provided
2039    400     max #campaigns reached           Seller has reached the maximum amount of campaigns
2040    400     status change not allowed        The requested status change is not allowed
====    ====    =============================    ==========================================================================================