# Publicly Accessible Private Repositories

#### Description:

Bitbucket is a source control tool used by software teams to collaborate easily and work simultaneously on code bases.\
\
And in some cases, public access to private repositories are temporarily enabled, this however leaves your company at risk of bad actors cloning your repository data without being authorized to do so.\
\
It is always advisable to cross-check both your workspace and individual repository settings for misconfigured access settings.

#### Testing:

Once you create a Bitbucket Workspace, your workspace gets an ID assigned (this is usually the name of the workspace, for example: `mycompanyname`).\
\
You can visit this URL unauthenticated to cross-check what anonymous users get to view:

```
https://bitbucket.org/{WORKSPACE_ID}
```

The workspace ID can be guessed or can be enumerated through search engines like Google with the use of search filtering/syntax:

```
site:bitbucket.org inurl:/workspace/projects
```

<figure><img src="../../.gitbook/assets/image (25).png" alt=""><figcaption></figcaption></figure>

You'll be able to access each individual public repository by opening it on the Workspace overview page:&#x20;

<figure><img src="../../.gitbook/assets/image (26).png" alt=""><figcaption></figcaption></figure>

You can browse through the code and any previous commits:

<figure><img src="../../.gitbook/assets/image (27).png" alt=""><figcaption></figcaption></figure>

#### Remediation:

For self-hosted Atlassian Bitbucket permises, locate the `bitbucket.properties` file in the home directory of your Bitbucket instance and set `feature.public.access` to `false`.\
\
On the cloud version, navigate to your repository settings:

<figure><img src="../../.gitbook/assets/image (29).png" alt=""><figcaption></figcaption></figure>

And make sure that the "**This is a private repository**" option is checked, and save your changes:

<figure><img src="../../.gitbook/assets/image (28).png" alt=""><figcaption></figcaption></figure>

Additionally, make sure your **Workspace visibility settings** are also set to **private**.\
\
To do so:

1. Navigate to your workspace
2.  Click on the **settings icon** and open **Workspace settings**

    <figure><img src="../../.gitbook/assets/image (31).png" alt=""><figcaption></figcaption></figure>
3.  And make sure the option "**Keep this workspace private**" is checked and **save your settings**:

    <figure><img src="../../.gitbook/assets/image (32).png" alt=""><figcaption></figcaption></figure>

#### Potential Impact:

Most code bases are meant to be private and leaving it publicly accessible can be destructive for some companies.\
\
Most private code bases contain sensitive data, private code (obviously) and/or even clear text credentials.\
\
All this data can be used for further exploitation by bad actors.

#### References:

* [https://confluence.atlassian.com/bitbucketserver/allowing-public-access-to-code-776639799.html#Allowingpublicaccesstocode-Disablingpublicaccessglobally](https://confluence.atlassian.com/bitbucketserver/allowing-public-access-to-code-776639799.html#Allowingpublicaccesstocode-Disablingpublicaccessglobally)
