# Unrestricted email domains

#### Description:

Developers make use of Google's OpenID Connect to implement authentication easily and can add an optional query parameter to the request to limit access to the email domain.\
\
However, this optional query parameter can be altered or even omitted to bypass the whitelist and could allow anyone to sign in using any email (on the condition that no further restrictions are present, read more)

#### Testing:

When you come across a Google Login put infront of a restricted asset, try altering the **`hd`** query parameter to a domain you control (or have access to):

```http
https://accounts.google.com/o/oauth2/v2/auth?
  response_type=code&
  client_id=1234.apps.googleusercontent.com&
  ...
  hd=company.com
```

Change it to **`example.com`**:

```
https://accounts.google.com/o/oauth2/v2/auth?
  response_type=code&
  client_id=1234.apps.googleusercontent.com&
  ...
  hd=example.com
```

#### Remediation:

As Google OpenID Connect documentations specify, do not rely on this parameter to control access as it is solely used for the optimization of the login form:

> Don't rely on this UI optimization to control who can access your app, as client-side requests can be modified.
>
> [_Learn more_](https://developers.google.com/identity/openid-connect/openid-connect#hd-param)



#### References:

* [https://twitter.com/intigriti/status/1383397368691789825](https://twitter.com/intigriti/status/1383397368691789825)
* [https://developers.google.com/identity/openid-connect/openid-connect](https://developers.google.com/identity/openid-connect/openid-connect)
