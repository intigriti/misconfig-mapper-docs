# Salesforce Lightning Aura Component Enabled

#### Description:

Salesforce is an extensive CRM software that includes a Ligthening Framework to help developers, admins and IT teams to create responsive (web) applications effortlessly.

Salesforce Lightning also provides support for data storage (Objects), and the creation of custom controllers (functions) through Salesforce's strongly typed programming language (Apex).

Correctly configuring role-based permissions and access controls can be a tedious task for inexperienced users. Security misconfigurations may arise if access controls are not properly enforced. These security issues often result in excessive data leaks (including PII), unwanted data modifications, privilege escalations, etc.

#### Testing:

Replicate the following POST HTTP request verify that the Aura component is enabled:

```http
POST /aura HTTP/2
Host: {TARGET}.force.com
Content-Type: application/json

{}
```

The endpoint should respond with an invalid session error (`aura:invalidSession`)

If the HTTP request above returned a 404 status code, try requesting one of the following app routes:

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

It is recommended to revise the options for Unauthenticated and Guest users and restrict access to only the resources and components that are required.

<figure><img src="../../.gitbook/assets/salesforce/0.png" alt=""><figcaption></figcaption></figure>


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