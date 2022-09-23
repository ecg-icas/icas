.. index:: Authentication
.. _authentication:

Authentication
==============

Authentication is provided using *OAuth2* to allow easy integration with
existing libraries. For more information please refer to the `OAuth 2.0
website <http://oauth.net/2/>`_. The latest version of the OAuth 2.0
specification can be found `here <http://tools.ietf.org/html/draft-ietf-
oauth-v2-31>`_.

What is OAuth 2.0
-----------------

OAuth 2.0 is an open authorization protocol which enables applications to
access each others data. OAuth 2.0 specification replaces and obsoletes the
OAuth 1.0 protocol and is *not* backward compatible with OAuth 1.0.

.. _oauth2_roles:

OAuth 2.0 Roles
---------------
OAuth 2.0 defines the following roles of users and applications:

* **Resource Owner:** This is the person or application that owns the data
  that is to be shared. In this context *resource owner*
  is the Admarkt user.

* **Resource Server:** This is the server hosting the resource owned by the
  resource owner. In this context *resource server* is the server hosting
  Admarkt Sellside API.

* **Client:** This is the application requesting access to the resources stored
  on the resource server. In this context *client* is the application wanting
  to use the Admarkt Sellside API.

* **Authorization Server:** The authorization server is the server
  authorizing the client app to access the resources of the resource owner.
  This allows fine-grained access to resources owned by the **resource owner**.

In our OAuth 2.0 flow we rely on the *tenant* (local market) as providing the **Authentication Server**, the
one that confirms the user identity through the use of some kind of credentials (usually username/password).
The authentication server is hosting the authentication of a user account (resource owner).


.. _oauth2_endpoints:

OAuth 2.0 Endpoints
-------------------

**Authorization Endpoint:** This is the endpoint on the authorization server
where the resource owner logs in, and grants authorization to the client
application.

**Token Endpoint:**  This is the endpoint on the authorization server where
the client application exchanges the authorization code, client ID and client
secret, for an access token.

The endpoint URLs per tenant and environment are as follows:

.. list-table::
 :widths: 20 10 70
 :header-rows: 1

 * - Tenant
   - Env
   - Endpoint

 * - Marktplaats
   - Sandbox
   - https://admarkt.demo.qa-mp.so/accounts/oauth/authorize

 * -
   -
   - https://admarkt.demo.qa-mp.so/accounts/oauth/token

 * -
   - Production
   - https://admarkt.marktplaats.nl/accounts/oauth/authorize

 * -
   -
   - https://admarkt.marktplaats.nl/accounts/oauth/token

 * - Kijiji Canada
   - Sandbox
   - https://admarkt.qa10.kjdev.ca/accounts/oauth/authorize

 * -
   -
   - https://admarkt.qa10.kjdev.ca/accounts/oauth/token

 * -
   - Production
   - https://admarkt.kijiji.ca/accounts/oauth/authorize

 * -
   -
   - https://admarkt.kijiji.ca/accounts/oauth/token

 * - 2dehands Belgium
   - Sandbox
   - https://admarkt.demo-2dehands.qa-mp.so/accounts/oauth/authorize

 * -
   -
   - https://admarkt.demo-2dehands.qa-mp.so/accounts/oauth/token

 * -
   - Production
   - https://admarkt.2dehands.be/accounts/oauth/authorize

 * -
   -
   - https://admarkt.2dehands.be/accounts/oauth/token


.. note::

    The Sandbox environments may use a self-signed certificate for the SSL
    encryption. You need to disable certificate verification in your client
    library.

.. _obtaining_an_access_token:

Getting an Access Token
-----------------------

The steps for getting an access token are as follows:

If the user is not logged-in with the tenant:

Step 1: Redirect to the authorization url
`````````````````````````````````````````

Redirect the resource owner (user) to the authorization url with the following
GET parameters

.. list-table::
 :widths: 10 30 60
 :header-rows: 1

 * - Field
   - Required
   - Description

 * - response_type
   - Required
   - Must be set to ``code``

 * - client_id
   - Required
   - Your client id

 * - scope
   - Required
   - The scope requested by the client as in :ref:`scopes`

 * - redirect_uri
   - Required
   - The URL to which the authorization server redirects the user with an authorization
     code after successful authorization. This url can be matched against a list of
     expressions, in case the client is experiencing or generating abuse. This list
     should then be discussed with your contact point.

 * - state
   - Optional, but recommended
   - Any client state that needs to be passed on to the client request URI

.. code-block:: javascript

    GET /accounts/oauth/authorize?response_type=code&client_id=YOUR_CLIENT_ID&scope=api_ro+api_rw&redirect_uri=https://yoursite.com/code&state=YOUR_STATE
    Host: admarkt.demo.qa-mp.so

Step 2: Redirect to the redirect_uri
````````````````````````````````````

After the resource owner logs in and confirms access request of the client, the
authorization server redirects the resource owner to the ``redirect_uri``
specified in the request at step 1 with the following GET parameters

.. list-table::
 :widths: 10 30 60
 :header-rows: 1

 * - Field
   - Required
   - Description

 * - code
   - Required
   - The authorization code

 * - state
   - Required, if present in step 1
   - The same value as sent by the client in the state parameter at step 1, if any

.. code-block:: javascript

    GET /code?code=AUTH_CODE&state=YOUR_STATE
    Host: yoursite.com

This is how your client gets the short-lived authorization code to subsequently get a refresh & access token.

Step 3: POST to the token endpoint
``````````````````````````````````

After obtaining the authorization code at step 2 the client needs to make a
*POST* request to the *token endpoint* with the following parameters:

.. list-table::
 :widths: 10 30 60
 :header-rows: 1

 * - Field
   - Required
   - Description

 * - grant_type
   - Required
   - Must be set to ``authorization_code``

 * - code
   - Required
   - The authorization code received from the authorization server at step 2

 * - client_id
   - Required
   - Your client id

 * - client_secret
   - Required
   - Your client secret

 * - redirect_uri
   - Required
   - Must be identical to the redirect_uri specified in step 1

.. code-block:: javascript

    POST /accounts/oauth/token
    Host: admarkt.demo.qa-mp.so
    Content-Type: application/x-www-form-urlencoded

    grant_type=authorization_code&code=AUTH_CODE&client_id=YOUR_CLIENT_ID&client_secret=YOUR_CLIENT_SECRET&redirect_uri=https://yoursite.com/code

Step 4: Receive token response
``````````````````````````````

The authentication server returns the following token response in JSON
format if the token request at step 3 is valid.

.. list-table::
 :widths: 10 60
 :header-rows: 1

 * - Field
   - Description

 * - access_token
   - The access token as assigned by the authorization server

 * - token_type
   - The token type assigned by the authorization server. In this context set to ``bearer``.

 * - expires_in
   - Expiration time in seconds after which the access token becomes invalid

 * - refresh_token
   - The refresh token for obtaining a new access token

 * - scope
   - The scope of the access token as in :ref:`scopes`

.. note::

    Check `Refresh Tokens and Token Expiration`_ on the behavior of the ``refresh_token`` field.

.. code-block:: javascript

    POST /accounts/oauth/token
    Host: admarkt.demo.qa-mp.so
    Content-Type: application/x-www-form-urlencoded

    grant_type=authorization_code&code=AUTH_CODE&client_id=YOUR_CLIENT_ID&client_secret=YOUR_CLIENT_SECRET&redirect_uri=https://yoursite.com/code

    200 OK
    Content-Type: application/json

    {
        "access_token"  : "1dc19b97-fd12-4feb-8c9d-042b4ba80747",
        "token_type"    : "bearer",
        "expires_in"    : 300,
        "refresh_token" : "7432aa20-97d1-4426-bab7-dbeed8b5d997",
        "scope"         : "api_ro api_rw"
    }

.. _using_an_access_token:

Using an Access Token
---------------------

To use the access token for an actual API call you have to provide it in the
``Authorization`` header as follows:

.. code-block:: javascript

    GET /api/sellside/ad
    Host: admarkt.demo.qa-mp.so
    Authorization: Bearer 1dc19b97-fd12-4feb-8c9d-042b4ba80747

.. _refreshing_an_access_token:

Getting another Access Token
----------------------------

Access tokens are short lived and expire quickly. The refresh token is used to
obtain a new access token once the access token is no longer valid. In order
to obtain a new access token the following *POST* request to the *token
endpoint* with the following parameters is necessary.

.. list-table::
 :widths: 20 30 60
 :header-rows: 1

 * - Field
   - Required
   - Description

 * - refresh_token
   - Required
   - Refresh token obtained when the original access token was received

 * - grant_type
   - Required
   - Must be set to ``refresh_token``

 * - client_id
   - Required
   - Your client id

 * - client_secret
   - Required
   - Your client secret

If the refresh token request is valid the authorization server returns a new
access token. The token response is identical to the token response explained
at step 4 of :ref:`obtaining_an_access_token`.

.. code-block:: javascript

    POST /accounts/oauth/token
    Host: admarkt.demo.qa-mp.so
    Content-Type: application/x-www-form-urlencoded

    grant_type=refresh_token&refresh_token=YOUR_CURRENT_REFRESH_TOKEN&client_id=YOUR_CLIENT_ID&client_secret=YOUR_CLIENT_SECRET

    200 OK
    Content-Type: application/json

    {
        "access_token"  : "52f1492d-8ad7-4d4c-88aa-2c38da2d45a2",
        "token_type"    : "bearer",
        "expires_in"    : 300,
        "refresh_token" : "fc668806-739d-4089-a9b0-f8ee10e53ded",
        "scope"         : "api_ro api_rw"
    }

.. _expiration_times:

Refresh Tokens and Token Expiration
-----------------------------------

Access tokens expire after **5 minutes** on all environments and for every
tenant.

Refresh tokens expire after not being used for **60 days** and remain unique
per client_id, user and scope combination during the lifetime of the token.

.. _scopes:

Scopes
------

Scopes determine whether you can access a certain resource.

The scopes are modeled per user group and include access to resources for that
user group. The list of resources that can be accessed with a scope can change
over time but does not require the user to go through the grant flow again.

The actual scope for a token is the intersection between the scope requested
by the client as described in `Getting an Access Token`_ and the scope
granted by the user which is part of the user record.

.. list-table::
 :widths: 20 80
 :header-rows: 1

 * - Scope
   - Description

 * - api_ro
   - Grants read access for API partners

 * - api_rw
   - Grants write access for API partners

 * - console_ro
   - Grants read access for console applications

 * - console_rw
   - Grants write access for console applications

 * - reporting
   - Grants access to reporting endpoints only. Allows creation of detailed downloadable reports


You can find a generalized sequence diagram of the Oauth2 flow below (click to expand).

.. image:: _static/oauth2Flow.png
   :scale: 100%