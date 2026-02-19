Each error contains a ``code`` and ``text`` attributes providing a numeric error code and a simple English error message. An error may contain a ``field`` attribute describing the field where the error occurred and an additonal ``arg`` attribute further specifying the error.


=======================   ========   =============================   ======================================
  Field                    Code             Message                    Description
=======================   ========   =============================   ======================================
 entire response object    1000        internal error                 Failed to execute query
 entire request object     1005        invalid json                   Could not parse request data
 ``am:date``               2000        missing argument               The field 'aggregate' was missing
 ``am:metrics``            2000        missing argument               The field 'metrics' was missing
 any non-allowed field     2001        invalid argument               The value of field 'dimensions:[am:wrongDimension]' was invalid
=======================   ========   =============================   ======================================

