.. index:: Error Codes
.. _error_codes:

Error Codes
===========

====    ====    ============================    ==================================================================================
Code    HTTP    Error message                   Description
====    ====    ============================    ==================================================================================
1000    500     internal error                  An internal error occurred
1001    500     not implemented                 This call has not been implemented
1003    403     access denied                   Authorization failed
1004    404     not found                       The resource was not found or does not belong to the authenticated user
1005    400     invalid json                    The input is not valid JSON
1006    400     type mismatch                   A value of a field was provided as wrong type
2000    400     missing argument                A mandatory argument was not provided
2001    400     invalid argument                A provided value was invalid
2002    400     out of range                    A provided numeric value was out of range
2003    400     not equal                       A provided value was not equal to a required value
2004    400     value too short                 A provided string value was too short
2005    400     value too long                  A provided string value was too long
2006    400     invalid url                     A provided string value does not represent a valid URL
2007    400     unsupported format              A link to an file is in an unsupported format
2008    400     file too large                  A link to a file points to a file that is too large
2010    400     invalid phone number            A provided string value does not represent a valid phone number
2011    400     too many active ads             The maximum number of active ads per seller in this category has been reached
2012    400     category change not allowed     Changing the category of an ad is not allowed
2017    400     ad status change not allowed    Changing the status of an ad is not allowed
2018    400     image type not allowed          The uploaded image type is not allowed
2022    400     category not active             The category is not active and will not allow creation of ads
2023    400     category deleted                The category is deleted and will not allow creation/updating of ads
====    ====    ============================    ==================================================================================
