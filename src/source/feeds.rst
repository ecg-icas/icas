.. _feeds:

Feeds
=====

A feed is a file that contains a list of ads you want to advertise, and is a way to handle repetitive asynchronous bulk uploading of ads.

Once a feed is created you can link your HTTP(s) URL through :ref:`post_feed_config` or the seller console frontend to make our system fetch your file and import your ads. After that, scheduled fetches happen once per day synchronising the system with any updates you may want to introduce to the ads list.  You can stop the feed advertising process using :ref:`post_feed_config`, or the console.

.. note::
    If you have a dedicated account manager, they can also support with ensuring the URL of your feed is properly connected to your account. 

In order to let us download your feed and all the relevant linked content, the access to our outgoing IPs should be whitelisted as described in :ref:`section of the Sellside API<overview_image_downloads>`.


File Format
-----------

We support feed files in either an XML or TSV format.
Feeds are expected to be in UTF-8 encoding.
Information on the most actual set of supported data is described on the :ref:`details <feed-details>` page.

.. note::
    Currently, we have introduced a number of new fields for describing the feed ad. 
    It contains a larger subset of what is considered a 'widely adopted market standard'. 
    The new fieds follow specification stated in manual for `Google Merchant Center <https://support.google.com/merchants/answer/7052112>`__ customers.
    This is a part of our general strategy, to minimize the overhead needed to integrate your feed with ICAS versus the other advertising channels.
    We will gradually decrease the reliance of the ad categorisation algorithms from the tenant specific categories, and attributes, 
    toward the standard fields. For more information see quesions. 

For instructions on how to create your feed in specific formats, please expand the relevant sections.

.. collapse:: XML

    The contents of this XML file need to adhere to the XSD available for sellers
    at :ref:`get_feed_xsd`.
    All the values provided should conform to the rules specified for the valid XML document.
    For the more complex data (that contains, for example HTML tags) we recommend using `character data (CDATA) <https://en.wikipedia.org/wiki/CDATA>`_.
    XML escape characters are also supported.
    
    Currently versions 1.0, and 1.1 of the XML are accepted. You can find more information on XML, and versions in :ref:`feeds_qna` section.

    .. collapse:: Example v.1.0

        .. literalinclude:: examples/feed-xml-v-1-0-example.xml
            :language: xml

        :download:`download example<examples/feed-xml-v-1-0-example.xml>`

    .. collapse:: Example v.1.1

        .. literalinclude:: examples/feed-xml-v-1-1-example.xml
            :language: xml

        :download:`download example<examples/feed-xml-v-1-1-example.xml>`

    |

.. collapse:: TSV

    TSV format follows specification described on `wiki <https://en.wikipedia.org/wiki/Tab-separated_values>`__.
    Column names used in TSV feed must superset :ref:`column names <feed-details>` specified.
    Some complex fields, like :ref:`feed_ship` or :ref:`feed_attr` must follow the specified encoding conventions.

    :download:`download example<examples/feed-tsv-example.tsv>`

|

Errors
------
:ref:`get_feed_import` shows the overview of imported feeds of the user, and
:ref:`get_feed_import_id_detail` can be a good source of information on possible errors
or warnings on ads, such as missing mandatory attributes or too low CPC etc. 


.. _feeds_qna:

Scenario's & Questions
----------------------

Below are some common asked-for scenarios and questions with their explanations/answers.

.. collapse:: What happens if my feed file cannot be fetched?
    :class: larger-collapse

    When a feed file cannot be fetched, nothing will change on the user's ads.
    It's as if the import didn't happen. 
    Since the file represents the desired list of ads to be live, we won't do anything if we can't get the file - we cannot read a change in the desired situation.

.. collapse:: What happens when my feed file is empty?
    :class: larger-collapse

    When a feed file is empty, all ads of the user will be paused. 
    An empty file means the desired list of ads to be live is empty, so all active ads are paused. 
    Note that this also means that all ads which are in statuses BUDGET_REACHED or DAILY_BUDGET_REACHED are also paused.
    If you want to pause your entire ads inventory, you can download and use the file below.

    .. raw:: html

            <embed>
                <form action="https://admarkt.marktplaats.nl/api/sellside/feed/empty">
                    <input type="submit" value="Download Empty File" />
                </form>
                <br><br>
            </embed>


.. collapse:: My feed file contains only new ads. What happens to those I have previously created via frontend / API?
    :class: larger-collapse

    In the spirit of the feed file being the desired set of ads to be live for a user, all currently active ads (including ads in BUDGET_REACHED or DAILY_BUDGET_REACHED)
    will be paused and the supplied ads will be created (with status ACTIVE).

.. collapse:: Can I modify my feed ads via frontend / API?
    :class: larger-collapse

    The feed file considered "the desired set of ads to be live for a user". 
    With every daily import, all the ads will be (re)set to their representing feed values. 
    This means you can see changes made throuh API or frontend undone after a successful feed import.

.. collapse:: I have updated my feed images, and after the successful import there is no change.
    :class: larger-collapse

    If you're changing the images without changing the URLs, the changes may not be picked up,
    in case the rest of the ad is also unchanged. We suggest adding a bogus parameter to the
    image URL to force a re-processing of the ad and its images. Make sure to not change this
    for every feed import, but only when you require images to be re-processed.

.. collapse:: What does happens when my XML does not validate against XSD?
    :class: larger-collapse

    If the fetched XML filed does not validate against the XSD there will not be any changes
    to your ads. Existing ads will remain unchanged and no new ads will be created.

.. collapse:: How to validate XML against XSD?
    :class: larger-collapse

    Next to various online capabilities where you can provide both your XML and XSD files,
    a way to check quickly and locally is to use a tool called xmllint. With this tool
    you can use our XSD downloaded from :ref:`get_feed_xsd` to test whether your feed is
    working before you let our system fetch it using the following command:

    .. code-block:: bash

        xmllint --debug --noout --schema /path/to/admarkt1.0.xsd /path/to/yourfeed.xml

    For small chunks of XML you can use online validators as well, such as `<http://www.utilities-online.info/xsdvalidation/>`_ or `<https://www.freeformatter.com/xml-validator-xsd.html>`_. Note that these have a
    limit on the size of the XML you can check, but it should be more than enough to be able
    to test correctness of your structure.

.. collapse:: What ist the difference between version 1.0, and 1.1 of the XML format?
    :class: larger-collapse

    Version 1.1 introduces a number of new fields, that can be used to describe your add more preciesly, and improve display relevancy.
    The new fields follow commonly adopted market standards for product description.

    Version 1.1 of the schema is backward compatible with 1.0. 
    So the only thing you need to do to start using it, is to change the namespace (see next question)
    at the beginning of your file, and start using the new fields. 

.. _feeds_migrate:
.. collapse:: How to migrate from version 1.0, to 1.1 of the XML format?
    :class: larger-collapse

    Change `http://admarkt.marktplaats.nl/schemas/1.0`  
    to  `http://admarkt.marktplaats.nl/schemas/1.1`
    At the very top of your XML feed file.

    .. code-block:: xml
        :emphasize-lines: 2
        
        <?xml version="1.0" encoding="UTF-8"?>
        <admarkt:ads xmlns:admarkt="http://admarkt.marktplaats.nl/schemas/1.1">
            <admarkt:ad>
        ...

.. collapse:: When I create an XML feed, do I need to use 'admarkt' prefix for all the tags, as shown in the examples?
    :class: larger-collapse

    The prefix (or more preciesly the namespace) is something invented by XML creators, with some intention of differentating domain concepts, that can have the same name, but a different meaning.

    Look at the very first lines of yours (or example) xml:

    .. code-block:: xml
        :emphasize-lines: 2
        
        <?xml version="1.0" encoding="UTF-8"?>
        <admarkt:ads xmlns:admarkt="http://admarkt.marktplaats.nl/schemas/1.1">
            <admarkt:ad>
        ...

    xmlns:**admarkt** there can be changed to any word:

    .. code-block:: xml
        :emphasize-lines: 2
        
        <?xml version="1.0" encoding="UTF-8"?>
        <xyz:ads xmlns:xyz="http://admarkt.marktplaats.nl/schemas/1.1">
            <xyz:ad>
        ...

    or event skipped:

    .. code-block:: xml
        :emphasize-lines: 2
        
        <?xml version="1.0" encoding="UTF-8"?>
        <ads xmlns="http://admarkt.marktplaats.nl/schemas/1.1">
            <ad>
        ...

    It is up to you! The only thing that matters to us is the text "http://admarkt.marktplaats.nl/schemas/1.1",
    which determines which schema version, we should use processing your file. 

.. collapse:: How to use TSV format?
    :class: larger-collapse

    We introduced TSV format in our system, to simplify the integration path. 
    Our customers commonly use spreadsheets to store and manipulate the data, 
    and "TSV export" is a standard option for the majority of the spreadsheet programs.

    The three important things to remember for successful integration:

    1. There are some :ref:`column names <feed-details>`, that we will look for, and expect to find in your TSV feed.
    2. Multiline fields need to be escaped with double quotes, or all the line breakes, and tabulators changed to \\n, \\t.
    3. Some complex fields, like :ref:`feed_ship` or :ref:`feed_attr` must follow the specified encoding conventions.

.. collapse:: What are the newly added fields?
    :class: larger-collapse

    Those fields are considered a 'widely adopted market standard', required, or recommended for advertising on many other channels:
    :ref:`feed_mpn`, :ref:`feed_googleProductCategory`, :ref:`feed_productType`, :ref:`feed_brand`, :ref:`feed_gtin`, 
    :ref:`feed_itemGroupId`, :ref:`feed_condition`, :ref:`feed_material`, :ref:`feed_energyEfficiencyClass`, :ref:`feed_minEnergyEfficiencyClass`,
    :ref:`feed_maxEnergyEfficiencyClass`, :ref:`feed_color`, :ref:`feed_gender`, :ref:`feed_ageGroup`, :ref:`feed_size`, :ref:`feed_unitPricingBaseMeasure`, :ref:`feed_unitPricingMeasure`.
