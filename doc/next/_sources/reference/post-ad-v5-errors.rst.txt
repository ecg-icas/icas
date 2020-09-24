====================    ====    =======================     ===========================================================================================
Field                   Code    Error message               Description
====================    ====    =======================     ===========================================================================================
allowContactByEmail     2001    invalid argument            must be *true* or *false*
allowPaypal             2001    invalid argument            must be *true* or *false*
attribute.name          2000    missing argument            one of the attributes is wrong: missing the field 'name'
attribute.name          2004    value too short             one of the attributes is wrong: need at least 1 non-space character
attribute.name          2005    value too long              one of the attributes is wrong: max. length is 32 characters
attribute.type          2000    missing argument            one of the attributes is wrong: missing the field 'type'
attribute.type          1006    type mismatch               one of the attributes is wrong: unknown type
attribute.value         2000    missing argument            one of the attributes is wrong: missing the field 'value'
attribute.value         2004    value too short             one of the attributes is wrong: need at least 1 non-space character
attribute.value         2005    value too long              one of the attributes is wrong: max. length is 512 characters
attribute.value         2001    invalid argument            one of the attributes has a wrong value type for provided 'type'
categoryId              1006    type mismatch               not an integer number
categoryId              2000    missing argument            mandatory field
categoryId              2001    invalid argument            not a valid category id
categoryId              2022    category not active         category is not active and will not allow creation of ads
categoryId              2023    category deleted            category is deleted and will not allow creation/updating of ads
currency                2000    missing argument            mandatory field
currency                2001    invalid argument            not "EUR", "DKK" or "CAD"
description             2000    missing argument            mandatory field
description             2002    out of range                too short or too long; see :ref:`categories_v2` about the constraints.
externalId              2005    value too long              too short or too long; see :ref:`categories_v2` about the constraints.
id                      1006    type mismatch               not an integer number
id                      2001    invalid argument            *id* must be omitted or set to zero
images.size             2002    out of range                too many image URLs
images.url              2006    invalid url                 invalid image URL
links.displayUrl        2005    value too long              max. length is 255
links.url               2005    value too long              max. length is 2048
links.url               2006    invalid url                 is not a valid url
phoneNumber             2005    value too long              max. length is 32
phoneNumber             2010    invalid phone number        not a valid phone number
postcode                2005    value too long              max. length is 6
price                   1006    type mismatch               not an integer number
price                   2000    missing argument            not specifying a price for a priceType which requires a price
price                   2001    invalid argument            specifying a price for a priceType without a price
price                   2002    out of range                price is not in the interval of ``(0,10000000000]`` while priceType requires a valid price
priceType               2001    invalid argument            not a valid price type
salutation              2001    invalid argument            not a valid salutation
sellerName              2000    missing argument            must not be empty
sellerName              2005    value too long              max. length is 60
status                  2000    missing argument            mandatory field
status                  2001    invalid argument            must be *ACTIVE*
title                   2000    missing argument            mandatory field
title                   2002    out of range                max. length is 60
vendorId                2005    value too long              max. length is 64 characters
====================    ====    =======================     ===========================================================================================
