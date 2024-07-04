# Salesforce Lightning Aura Component Enabled

#### Description:

Salesforce is an extensive CRM software that includes [Lightning Framework](https://www.salesforce.com/eu/campaign/lightning/), a framework with a set of reusable components to help developers, admins and IT teams to create responsive (web) applications effortlessly.

Salesforce Lightning also provides support for data storage (Objects), and the creation of custom controllers (functions) through Salesforce's strongly typed programming language (Apex).

The Aura component enables the Aura API endpoint and allows (external) users to interact with Salesforce Objects and Controllers.

Since correctly configuring role-based permissions and access controls can be a tedious task for inexperienced users. Security misconfigurations may arise if access controls are not properly enforced. These security issues often result in excessive data leaks (including PII), unwanted data modifications, privilege escalations, etc. through the Aura endpoint.

{% hint style="info" %}
[As outlined in the official documentation](https://developer.salesforce.com/docs/atlas.en-us.lightning.meta/lightning/intro_benefits.htm), the [Aura component](https://developer.salesforce.com/docs/component-library/bundle/aura:component) is only recommended to be enabled when Salesforce Lightning does not provide built-in support for the required feature or functionality.
{% endhint %}

#### Testing:

Replicate the following POST HTTP request verify that the Aura component is enabled:

```http
POST /aura HTTP/2
Host: {TARGET}.force.com
Content-Type: application/json

{}
```

The endpoint should respond with a 401 Unauthorized status code indicating an invalid session error (`aura:invalidSession`):

```http
HTTP/2 401 Unauthorized
Strict-Transport-Security: max-age=63072000; includeSubDomains
X-Content-Type-Options: nosniff
X-Robots-Tag: none
Referrer-Policy: origin-when-cross-origin
Cache-Control: no-cache,must-revalidate,max-age=0,no-store,private
Content-Type: application/json

{"event":{"descriptor":"markup://aura:invalidSession","attributes":{"values":{}},"eventDef":{"descriptor":"markup://aura:invalidSession","t":"APPLICATION","xs":"I","a":{"newToken":["newToken","aura://String","I",false]}}},"exceptionEvent":true}
```

If the HTTP request above returned a 404 status code, try requesting one of the following API endpoints:

```
/sfsites/aura
/s/sfsites/aura
```

The target instance can also be pointed to one of the following FQDNs:
```
*.force.com
*.secure.force.com
*.live.siteforce.com
```

#### Remediation:

Salesforce Lightning employs a role-based security model and essentially allows admins to configure security access controls on CRUD operations on 3 different levels; Object (database), Field (column) and Record (data-entry) level.

It is essential to revise the current options for each (custom) object and set up strict access controls for each role based on their scope.

<figure><img src="../../.gitbook/assets/salesforce/0.png" alt=""><figcaption></figcaption></figure>

{% hint style="danger" %}
**Do not only set permissions for Guest users.** A common mistake made by admins is only enforcing access controls for non-authenticated users while self-signup is enabled.
{% endhint %}

#### Potential Impact:

Unauthorized users may retrieve sensitive data, perform unwanted actions and/or even escalate their current privileges when insufficient access controls are enforced on Salesforce Lightning.

It is necessary to revise all access controls and prevent any unauthorized users from viewing or performing any type of action beyond what is required in their scope or role.

#### References:

* [https://www.enumerated.ie/index/salesforce](https://www.enumerated.ie/index/salesforce)
* [https://www.enumerated.ie/index/salesforce-lightning-tinting-the-windows](https://www.enumerated.ie/index/salesforce-lightning-tinting-the-windows)
* [https://infosecwriteups.com/in-simple-words-pen-testing-salesforce-saas-application-part-1-the-essentials-ffae632a00e5](https://infosecwriteups.com/in-simple-words-pen-testing-salesforce-saas-application-part-1-the-essentials-ffae632a00e5)
* [https://infosecwriteups.com/in-simple-words-pen-testing-salesforce-saas-application-part-2-fuzz-exploit-eefae11ba5ae](https://infosecwriteups.com/in-simple-words-pen-testing-salesforce-saas-application-part-2-fuzz-exploit-eefae11ba5ae)
* [https://infosecwriteups.com/salesforce-bug-hunting-to-critical-bug-b5da44789d3](https://infosecwriteups.com/salesforce-bug-hunting-to-critical-bug-b5da44789d3)
* [https://www.biswajeetsamal.com/blog/salesforce-object-key-prefix-list/](https://www.biswajeetsamal.com/blog/salesforce-object-key-prefix-list/)
* [https://www.varonis.com/blog/abusing-salesforce-communities](https://www.varonis.com/blog/abusing-salesforce-communities)
* [https://web.archive.org/web/20210116171949/https://mcafee.com/blogs/enterprise/cloud-security/17-must-enable-salesforce-security-capabilities-and-other-best-practices/](https://web.archive.org/web/20210116171949/https://mcafee.com/blogs/enterprise/cloud-security/17-must-enable-salesforce-security-capabilities-and-other-best-practices/)
* [https://developer.salesforce.com/docs/atlas.en-us.lightning.meta/lightning/intro_lightning.htm](https://developer.salesforce.com/docs/atlas.en-us.lightning.meta/lightning/intro_lightning.htm)
* [https://help.salesforce.com/s/articleView?id=ind.media_asm_Disable_Lightning_Web_Security.htm&type=5](https://help.salesforce.com/s/articleView?id=ind.media_asm_Disable_Lightning_Web_Security.htm&type=5)
* [https://trailhead.salesforce.com/content/learn/modules/data_security/data_security_records](https://trailhead.salesforce.com/content/learn/modules/data_security/data_security_records)