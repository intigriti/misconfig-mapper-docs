# Public Groovy Script Console

#### Description:

Groovy Script Console provides developers a way to run Groovy Script code right from their browser. However, in case permissions aren't configured properly, it could introduce another attack vector and often lead to remote code execution.

#### Testing:

Navigate to the following app route and check if Groovy Script Console is publicly accessible:

```
/script
```

You can also send a **POST** HTTP request to the **`/script`** or **`/scriptText`** app routes with your script contents in the **script** body parameter (make sure to change the positional variables with your own values):

```bash
curl -s 'https://jenkins.{HOST}/script' -X 'POST' --data 'script={SCRIPT}'
```

or:

```bash
curl -s 'https://jenkins.{HOST}/scriptText' -X 'POST' --data 'script={SCRIPT}'
```

#### Remediation:

Make sure to enforce proper account access restrictions and prevent non-administrator or non-privileged accounts from accessing the script console.

To cross-check this, check the individual user and group permissions:

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1).png" alt=""><figcaption><p><strong>Anonymous Users shouldn't have Administrator access</strong></p></figcaption></figure>

Additionally, learn more about the capabilities of the [Script Console](https://www.jenkins.io/doc/book/managing/script-console/) and how to set [proper permissions based on each user or group role](https://www.jenkins.io/doc/book/security/access-control/permissions/).

#### Potential Impact:

Jenkin's Groovy Script Console is capable of several high-level execution tasks and thereby can allow malicious users to directly access the Jenkins runtime and practically do anything.

#### References:

* [https://www.jenkins.io/doc/book/managing/script-console/](https://www.jenkins.io/doc/book/managing/script-console/)
* [https://www.jenkins.io/doc/book/security/access-control/permissions/](https://www.jenkins.io/doc/book/security/access-control/permissions/)
* [https://rohit-soni.medium.com/chaining-multiple-vulnerabilities-leads-to-remote-code-execution-rce-on-paytm-e77f2fd2295e](https://rohit-soni.medium.com/chaining-multiple-vulnerabilities-leads-to-remote-code-execution-rce-on-paytm-e77f2fd2295e)
