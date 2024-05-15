# Debug mode enabled

#### Description:

Laravel can expose sensitive data when debug mode is left enabled.

Sensitive data can include (PHP) source code and in severe cases also environment variables, including the `APP_KEY`, a key that is responsible for encrypting all session tokens and even database connection strings.

#### Testing:

Navigate to the following app route and manually examine the response:

<pre><code><strong>/profiles
</strong><strong>/_debugbar
</strong></code></pre>

#### Remediation:

Debug mode should be turned off in production environments and environments that are accessible by everyone on the internet in general.

To disable debug mode in your Laravel app, simply **set the `APP_DEBUG` environment variable in your `.env` file** to **`false`**:

```bash
...
APP_DEBUG=false
...
```

#### Potential Impact:

In case malicious users get hold of the APP\_KEY secret, they'd be able to encrypt any session token and other app secrets introducing a whole new set of security vulnerabilities to the company.

#### References:

* [https://laravel.com/docs/10.x/deployment#debug-mode](https://laravel.com/docs/10.x/deployment#debug-mode)
