====================    ====    =======================     ==============================================================================
Field                   Code    Error message               Description
====================    ====    =======================     ==============================================================================
allowContactByEmail     2001    invalid argument            must be *true* or *false*
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
cpc                     1006    type mismatch               not an integer number
cpc                     2000    missing argument            mandatory field
cpc                     2002    out of range                value not between category.minCpc and category.maxCpc
currency                2000    missing argument            mandatory field
currency                2001    invalid argument            not "EUR"
dailyBudget             1006    type mismatch               not an integer number
dailyBudget             2002    out of range                value lower than category.minDailyBudget or higher than totalBudget
description             2000    missing argument            mandatory field
description             2005    value too long              max. length is 1000
externalId              2000    missing argument            mandatory field
externalId              2004    value too short             value must not be empty
externalId              2005    value too long              max. length is 64 characters
id                      1006    type mismatch               not an integer number
id                      2001    invalid argument            *id* must be omitted or set to zero
images.size             2002    out of range                too many image URLs
images.url              2006    invalid url                 invalid image URL
link.displayUrl         2005    value too long              max. length is 255 **TODO:VERIFY**
link.url                2005    value too long              max. length is 2048
link.url                2006    invalid url                 is not a valid url
phoneNumber             2005    value too long              max. length is 32
phoneNumber             2010    invalid phone number        not a valid phone number
postcode                2005    value too long              max. length is 6
price                   1006    type mismatch               not an integer number
price                   2000    missing argument            not specifying a price for a priceType which requires a price
price                   2001    invalid argument            specifying a price for a priceType without a price
price                   2002    out of range                price is zero while priceType requires a price greater than zero
priceType               2001    invalid argument            not a valid price type
salutation              2001    invalid argument            not a valid salutation
sellerName              2000    missing argument            must not be empty
sellerName              2005    value too long              max. length is 60
status                  2000    missing argument            mandatory field
status                  2001    invalid argument            must be either *ACTIVE* or *PAUSED*
title                   2000    missing argument            mandatory field
title                   2005    value too long              max. length is 60
totalBudget             1006    type mismatch               not an integer number
totalBudget             2002    out of range                value too low/high
priceType               2014    incompatible price type     price type not compatible with Buy It Now
price                   2015    price too low               price too low for Buy It Now
paypalEmail             2016    invalid email               paypalEmail does not contain a valid email
====================    ====    =======================     ==============================================================================
