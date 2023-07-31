# Private source code snippets exposed

#### Description:

Your GitLab instance may expose sensitive source code or private repositories if read permissions on Project Snippets have been misconfigured.

#### Testing:

Visit the following application route to check if anonymous users are able to read Project Snippets:

```
/explore/snippets
```

#### Remediation:

Make sure you select the appropriate **visibility level** on your shared code snippets

#### References:

* [https://docs.gitlab.com/ee/user/snippets.html](https://docs.gitlab.com/ee/user/snippets.html)
