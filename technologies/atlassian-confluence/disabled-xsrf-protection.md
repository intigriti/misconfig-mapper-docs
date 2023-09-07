# Disabled XSRF Protection

#### Description:

Atlassian Confluence provides users the ability to include themes and external plugins.\
\
Some older themes or plugins may require users to disable XSRF Protection as pointed out below:

> _Some third-party or deprecated Confluence themes will not work with the new Confluence XSRF protection. You may disable XSRF protection to support old themes at the cost of reducing security._\
> \
> _- Atlassian Confluence Docs_

\
However, **turning off the built-in XSRF Protection** in your Confluence instance can **open up new attack vectors** for bad actors to abuse!

#### Testing:

In case XSRF Protection is turned off, bad actors could post comments on other user's behalf by just sending them a link to an attacker controlled site that replicates the POST request.\
\
The POST request will request the server to create a comment on the victim's behalf without their knowledge.

#### Remediation:

It is always recommended to **upgrade and use the latest version available** of Atlassian Confluence.

1. Navigate to your Confluence instance and sign in
2. Open your **Administrator Settings** by clicking on the gear icon next to your profile picture
3. In your side navigation bar, scroll down to **Security** and open **Security Configurations**
4. Make sure that **XSRF Protection for adding comments** is **enabled**
5. Save your changes

<figure><img src="../../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

#### Potential Impact:

When **XSRF-protection** is **turned off**, it is possible for malicious users to target authenticated users by sending them a **specially crafted link that'd automatically** for example **post a comment** on the **victim's behalf**.

#### References:

* [https://confluence.atlassian.com/doc/configuring-xsrf-protection-218276695.html](https://confluence.atlassian.com/doc/configuring-xsrf-protection-218276695.html)

