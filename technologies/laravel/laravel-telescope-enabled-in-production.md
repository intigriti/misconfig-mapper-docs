# Laravel Telescope enabled in production

#### Description:

Laravel Telescope is a debugging tool often only enabled in local environments to help developers debug Laravel applications.\
\
Telescope can help developers look at incoming HTTP requests, view exceptions, logs, database queries and much more.\
\
It can sometimes happens that Telescope is enabled on production.

#### Testing:

Navigate to the following app route:

```
/telescope/requests
```

#### Remediation:

Telescope is a feature intended for development purposes only, it should be disabled in production environments.\
\
Just as the official documentation states, when installing Laravel Telescope, make sure to pass the `--dev` CLI flag to only install it locally (or in your development environment):

```basic
composer require laravel/telescope --dev
```

Afterwards, it is **required to only register Telescope service in local environments**:

```php
/**
 * Register any application services.
 */
public function register(): void
{
    if ($this->app->environment('local')) {
        $this->app->register(\Laravel\Telescope\TelescopeServiceProvider::class);
        $this->app->register(TelescopeServiceProvider::class);
    }
}
```

#### Potential Impact:

Laravel Telescope prints provides several debugging features including logs and database queries for example that may contain sensitive information.\
\
This information can be used against a company in further attacks (think about sensitive tokens and app secrets being logged).

#### References:

* [https://laravel.com/docs/10.x/telescope](https://laravel.com/docs/10.x/telescope)
* [https://laravel.com/docs/10.x/telescope#local-only-installation](https://laravel.com/docs/10.x/telescope#local-only-installation)
