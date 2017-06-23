# JWT Token

## What is a JWT token?
JSON Web Tokens are an open, industry standard RFC 7519 method for representing claims securely between two parties.
More info is available  [here](https://jwt.io/introduction/)

## What claims do we require?

We have decided to use the following claims:

"exp" (Expiration Time) Claim

   > The "exp" (expiration time) claim identifies the expiration time on
   or after which the token MUST NOT be accepted for processing.  The
   processing of the "exp" claim requires that the current date/time
   MUST be before the expiration date/time listed in the "exp" claim.
   Implementers MAY provide for some small leeway, usually no more than
   a few minutes, to account for clock skew.  Its value MUST be a number
   containing an IntDate value.

"iss" (Issuer) Claim

   > The "iss" (issuer) claim identifies the principal that issued the
   JWT.  The processing of this claim is generally application specific.
   The "iss" value is case sensitive.  Its value MUST be a string.

 "prn" (Principal) Claim

   > The "prn" (principal) claim identifies the subject of the JWT.  The
   processing of this claim is generally application specific.  The
   "prn" value is case sensitive.  Its value MUST be a string.


## Libraries for JWT toke creation
There are libraries for most  langauges at http://jwt.io/#libraries-io
JWT token flows.
## Self created JWT token.
### Create JWT token
The developer must create a valid JWT bearer token that conforms to **RSA SHA256** according to the following rules:

* The issuer (iss) must be the X-Ordercloud-Organisation token.
* The subject (prn) username (Can be either email or mobile number with country code +27827868336)
* The validity (exp) must be the expiration time of the assertion, within 10 minutes, expressed as the number of seconds from 1970-01-01T0:0:0Z measured in UTC.
* The JWT must be signed using HMAC SHA-256.
* The JWT must conform with the general format rules specified here: http://tools.ietf.org/html/draft-jones-json-web-token.
* The JWT signature should be signed using the organisation secret (WdegFJ5Vm is used in example).

### Steps to create a JWT token:

1. Construct a JWT Header in the following format:

> Example Header
```json
{"alg": "HS256"}
```

1. Base64url encode the JWT Header as defined [here](http://tools.ietf.org/html/rfc4648#page-7). The result should be similar to this: eyJhbGciOiAiSFMyNTYifQ.
1. Construct a JSON Claims Set for the JWT with the iss, prn,  and exp:

>Example Claim Set
```json
{
    "iss": "8d51ed79b191864846e3daf437327314",
    "exp": "1333685628",
    "prn": "my@email.com"
}
```

1. Base64url encode the JWT Claims Set without any line breaks. For example:

> Example encoded claim
```
eyJpc3MiOiAiOGQ1MWVkNzliMTkxODY0ODQ2ZTNkYWY0MzczMjczMTQiLCJleHAiOiAiMTMzMzY4NTYyOCIsInBybiI6ICJteUBlbWFpbC5jb20ifQ
```

1. Create a new string for the encoded JWT Header and the encoded JWT Claims Set, in this format:

`encoded_JWT_Header + "." + encoded_JWT_Claims_Set`

In the following example, the encoded JWT Header is highlighted:

> Example encoded header
```
eyJhbGciOiAiSFMyNTYifQ.eyJpc3MiOiAiOGQ1MWVkNzliMTkxODY0ODQ2ZTNkYWY0MzczMjczMTQiLCJleHAiOiAiMTMzMzY4NTYyOCIsInBybiI6ICJteUBlbWFpbC5jb20ifQ
```

1. Sign the resulting string using SHA256 with RSA.
1. Create a new string of the string from step 5 in the following format:

`existing_string + "." + base64_encoded_signature`

> Example
```
eyJhbGciOiAiSFMyNTYifQ.eyJpc3MiOiAiOGQ1MWVkNzliMTkxODY0ODQ2ZTNkYWY0MzczMjczMTQiLCJleHAiOiAiMTMzMzY4NTYyOCIsInBybiI6ICJteUBlbWFpbC5jb20ifQ.**IH2csBlTTCEEy6J8OVT63ZTBjmLUF1lZhnnqfsxDtk8**
```

1. Token is sent to the api using the Authorization header like the following

>Header:
```
Authorization : BEARER eyJhbGciOiAiSFMyNTYifQ.eyJpc3MiOiAiOGQ1MWVkNzliMTkxODY0ODQ2ZTNkYWY0MzczMjczMTQiLCJleHAiOiAiMTMzMzY4NTYyOCIsInBybiI6ICJteUBlbWFpbC5jb20ifQ.IH2csBlTTCEEy6J8OVT63ZTBjmLUF1lZhnnqfsxDtk8
```

<aside class="info">
A claim debugger is available [here](http://jwt.io/)
</aside>


## User Creation
 Self Signed JWT User creation


## Ordercloud generated JWT token.
