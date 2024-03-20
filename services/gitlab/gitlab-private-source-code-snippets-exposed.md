# Gitlab Private Source Code Snippets Exposed

#### Description:

Your GitLab instance may expose sensitive source code or private repositories if read permissions on Project Snippets have been misconfigured.

#### Testing:

Visit the following application route to check if anonymous users are able to read Project Snippets:

```
/explore/snippets
```

#### Remediation:

Make sure you select the appropriate **visibility level** on your shared code snippets

When for instance, you create a new code snippet, the visibility level will be set to **Private** by default:

<figure><img src="../../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>

Make sure to cross-check your saved settings before accidentally exposing any sensitive data.

#### Potential Impact:

Unintentionally exposing private source code snippets can introduce a risk to your company in case the code snippet includes hard coded secrets that can be used in further attacks, or just private source in general as it can allow unauthorized users to manually examine it.

#### References:

* [https://docs.gitlab.com/ee/user/snippets.html](https://docs.gitlab.com/ee/user/snippets.html)
