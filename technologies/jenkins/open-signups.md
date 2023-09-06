# Open Signups

#### Description:

In case signups are not turned off, any user can create an account on the Jenkins instance and gain (privileged) access to (internal) developer resources.

#### Testing:

Navigate to the following route and check if signups are enabled:

```
/signup
```

#### Remediation:

Make sure to disable signups for Jenkins. You can easily do so by:

1. Navigate to **Configure Global Security** page over at `/configureSecurity`
2. And make sure that the option **Allow users to signup** is disabled
3. Finally, **Apply** and **Save** your changes

<figure><img src="../../.gitbook/assets/image (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

#### Potential Impact:

Unauthorized users are able to create an account, this often introduces no potential risk.\
\
However, if the in-app permissions are not set and give newly signed up users too much privileges, it could result in a new attack vector.\
\
This could introduce several new security anomalies to your company (especially code execution as Jenkins CI/CD tool).

#### References:

* [https://rohit-soni.medium.com/chaining-multiple-vulnerabilities-leads-to-remote-code-execution-rce-on-paytm-e77f2fd2295e](https://rohit-soni.medium.com/chaining-multiple-vulnerabilities-leads-to-remote-code-execution-rce-on-paytm-e77f2fd2295e)
