# Laravel Telescope enabled in production

#### Description:

Laravel can expose sensitive data when debug mode is left enabled.

Sensitive data can include (PHP) source code and in severe cases also environment variables, including the `APP_KEY`, a key that is responsible for encrypting all session tokens and even database connection strings.

#### Testing:

Navigate to the following app route:

```
/telescope/requests
```

#### Remediation:

Telescope is a feature intended for development purposes only, it should be disabled in production environments.

#### References:

* [https://laravel.com/docs/10.x/telescope](https://laravel.com/docs/10.x/telescope)
