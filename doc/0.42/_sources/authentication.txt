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
  In this context *authorization server* is the server hosting authentication
  and token endpoints.

.. _oauth2_endpoints:

OAuth 2.0 Endpoints
-------------------

**Authorization Endpoint:** This is the endpoint on the authorization server
where the resource owner logs in, and grants authorization to the client
application. The authorization endpoint urls are as follows:

* *Sandbox:* https://auth.demo.qa-mp.so/accounts/oauth/authorize
* *Production:* https://auth.marktplaats.nl/accounts/oauth/authorize

**Token Endpoint:**  This is the endpoint on the authorization server
where the client application exchanges the authorization code,
client ID and client secret, for an access token.
The token endpoint urls are as follows:

* *Sandbox:* https://auth.demo.qa-mp.so/accounts/oauth/token
* *Production:* https://auth.marktplaats.nl/accounts/oauth/token

.. note::

    The Sandbox environment uses a self-signed certificate for the
    SSL encryption. You need to disable certificate verification in
    your client library.

.. _obtaining_an_access_token:

Obtaining an Access Token
-------------------------

The steps for obtaining an access token are as follows:

Step 1: Redirect to the authorization url
`````````````````````````````````````````

Redirect the resource owner (user) to the authorization url with the following GET parameters

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
   - The requested scope. Should be set to ``read write``

 * - redirect_uri
   - Optional
   - The URL to which the authorization server redirects the user with an authorization
     code after successful authorization. If not provided, the redirect URL specified
     with the client registration is used.

 * - state
   - Optional, but recommended
   - Any client state that needs to be passed on to the client request URI

.. code-block:: http

    GET /accounts/oauth/authorize?response_type=code&client_id=YOUR_CLIENT_ID&scope=read+write&redirect_uri=https://yoursite.com/code&state=YOUR_STATE
    Host: auth.demo.qa-mp.so

Step 2: Redirect to the redirect_uri
````````````````````````````````````

After the resource owner logs in and confirms access request of the client
the authorization server redirects the resource owner to the ``redirect_uri``
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

.. code-block:: http

    GET /code?code=AUTH_CODE&state=YOUR_STATE
    Host: yoursite.com

Step 3: POST to the token endpoint
``````````````````````````````````

After obtaining the authorization code at step 2 the client needs to make
a *POST* request to the *token endpoint* with the following parameters:

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
   - Required, if present in step 1
   - If present, should be identical to the redirect_uri specified in step 1

.. code-block:: http

    POST /accounts/oauth/token
    Host: auth.demo.qa-mp.so
    Content-Type: application/www-form-urlencoded

    grant_type=code&code=AUTH_CODE&client_id=YOUR_CLIENT_ID&client_secret=YOUR_CLIENT_SECRET&redirect_uri=https://yoursite.com/code

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
   - The scope of the access token

.. note::

    Every time you request a new access token you also receive a **new refresh token**.
    This automatically invalidates the existing refresh token even if it has not
    expired yet.

.. code-block:: http

    POST /accounts/oauth/token
    Host: auth.demo.qa-mp.so
    Content-Type: application/www-form-urlencoded

    grant_type=code&code=AUTH_CODE&client_id=YOUR_CLIENT_ID&client_secret=YOUR_CLIENT_SECRET&redirect_uri=https://yoursite.com/code

    200 OK
    Content-Type: application/json

    {
        "access_token"  : "1dc19b97-fd12-4feb-8c9d-042b4ba80747",
        "token_type"    : "bearer",
        "expires_in"    : 300,
        "refresh_token" : "7432aa20-97d1-4426-bab7-dbeed8b5d997",
        "scope"         : "read write"
    }

.. _using_an_access_token:

Using an Access Token
---------------------

To use the access token for an actual API call you have to provide it in the ``Authorization``
header as follows:

.. code-block:: http

    GET /api/sellside/ad
    Host: mp.lp.icas.ecg.so
    Authorization: Bearer 1dc19b97-fd12-4feb-8c9d-042b4ba80747

.. _refreshing_an_access_token:

Refreshing an Access Token
--------------------------

The refresh token is used to obtain a new access token once the access token is no longer valid.
In order to obtain a new access token the following *POST* request to the *token endpoint*
with the following parameters is necessary.

.. list-table::
 :widths: 10 30 60
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

If the refresh token request is valid the authorization server returns a new access token. The token
response is identical to the token response explained at step 4 of :ref:`obtaining_an_access_token`.

.. note::

    Every time you request a new access token you also receive a **new refresh token**.
    This automatically invalidates the existing refresh token even if it has not
    expired yet.

.. code-block:: http

    POST /accounts/oauth/token
    Host: auth.demo.qa-mp.so
    Content-Type: application/www-form-urlencoded

    grant_type=refresh_token&refresh_token=YOUR_CURRENT_REFRESH_TOKEN&client_id=YOUR_CLIENT_ID&client_secret=YOUR_CLIENT_SECRET

    200 OK
    Content-Type: application/json

    {
        "access_token"  : "52f1492d-8ad7-4d4c-88aa-2c38da2d45a2",
        "token_type"    : "bearer",
        "expires_in"    : 300,
        "refresh_token" : "fc668806-739d-4089-a9b0-f8ee10e53ded",
        "scope"         : "read write"
    }


Expiration Times
----------------

Both access and refresh tokens expire after the time listed in the table below. After this period the token
is no longer valid.

Also note that every time you request a new access token you also receive a new refresh token and
your current refresh token is automatically invalidated even if it has not expired yet.

.. list-table::
 :widths: 20  40 40
 :header-rows: 1

 * - Environment
   - Access Token
   - Refresh Token

 * - Sandbox
   - 12 hours/43200 seconds
   - 30 days/2592000 seconds

 * - Production
   - 5 minutes/300 seconds
   - 1 day/86400 seconds
