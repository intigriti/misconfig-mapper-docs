# Symfony Profiler Enabled

#### Description:

Symfony is a popular PHP web framework that bundles and provides several ready-to-use components out of the box.\
\
By default, newer versions have Profiler debug mode disabled however, some older versions do tend to enable it even in production environments.\
\
Symfony Profiler enables a set of tools to help developers debug their Symfony PHP app but this can also disclose several app environments via stack traces (including secrets) as mentioned by Symfony's official docs:

{% hint style="danger" %}
_"**Never** enable the profiler in production environments as it will lead to major security vulnerabilities in your project."_\
\
\- [https://symfony.com/doc/current/profiler.html](https://symfony.com/doc/current/profiler.html)
{% endhint %}

#### Testing:

Profiler can be loaded conditionally or on any page by default. However, you can navigate to one of the following app routes to list all profiles:

```
/app_dev.php
/app_dev.php/_profiler
/_profiler
```

Observe each response. You should be able to access Symfony Profiler and should have a tool bar present at the top of the page.

#### Remediation:

Make sure to set pass the --dev flag when installing using composer:

```bash
composer require --dev symfony/profiler-pack
```

And in your configuration file, make sure to disable it for certain environments like (test and prod):

```yaml
# app/config/config_prod.yml
framework:
    profiler:
        enabled: false # Disable Symfony/Profiler
    
    web_profiler:
        toolbar: false # Disable the tool bar as well for production environment

```

And in case you use Symfony Profiler in a controller and wish to disable it programmatically:

```php
use Symfony\Component\HttpKernel\Profiler\Profiler;

class DefaultController {
    public function testMethod(?Profiler $profiler): Response {
        $profiler->disable(); // Disable Symfony/Profiler
    }
}
```

It is also highly recommended to **disable debug mode** in production environments, to do so if you haven't already, simply set the `APP_DEBUG` environment variable to `false`:

```bash
APP_DEBUG=false
```

#### Potential Impact:

Symfony Profiler can expose several app environments and other secrets that can allow a bad actor to perform further attacks using the credentials.

#### References:

* [https://symfony.com/doc/current/profiler.html](https://symfony.com/doc/current/profiler.html)
* [https://infosecwriteups.com/how-i-was-able-to-find-multiple-vulnerabilities-of-a-symfony-web-framework-web-application-2b82cd5de144](https://infosecwriteups.com/how-i-was-able-to-find-multiple-vulnerabilities-of-a-symfony-web-framework-web-application-2b82cd5de144)
* [https://www.synacktiv.com/en/publications/looting-symfony-with-eos](https://www.synacktiv.com/en/publications/looting-symfony-with-eos)

