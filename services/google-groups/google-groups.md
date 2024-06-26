# Misconfigured read permissions

#### Description:

Google Groups can serve as a public forum to bring up issues or other company or organisation-related news to members but can also be used for internal use only.\
\
These permissions can be misconfigured and it's always recommended to check if the company you're targeting has a private Google Group setup that has misconfigured access control settings.

#### Testing:

You can easily do so by using search filters that search engines like Google provides:

```
site:groups.google.com "{companyName}"
```

#### Remediation:

It is always recommended to make sure that in case your Google Group is intended for a select few members only, to **properly set your privacy settings**.

When, for instance, you create a group, the second step prompts you to select Privacy settings. Make sure to revise your options before unintentionally making changes that could introduce a new attack vector.

<figure><img src="../../.gitbook/assets/google/groups/0.png" alt=""><figcaption><p>Choose privacy settings for a new Google Group</p></figcaption></figure>

#### Potential Impact:

Misconfigured Google Groups permissions can lead to several other issues within the organization. Especially if sensitive data is exchanged on non-private (without the members knowledge) fora.

#### References:

* [https://workspaceupdates.googleblog.com/2018/06/configure-your-google-groups-settings.html](https://workspaceupdates.googleblog.com/2018/06/configure-your-google-groups-settings.html)
