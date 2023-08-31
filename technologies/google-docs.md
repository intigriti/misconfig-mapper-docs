---
description: >-
  Google Docs can be left misconfigured and leak internal company data (like
  documents) if view permissions are left public
---

# Google Docs

### Misconfigured Read Permissions:

#### Description:

Google Docs is a popular web-based document editor and often used within teams to exchange data in documents with each other.\
\
Each document can be **viewed by anyone** if the link ever gets referenced somewhere (for example chats, emails, screenshots, or recordings), indexed or leaked somewhere when the **document's view permissions are not set properly**.

#### Testing:

A Google Docs link is easy recognizable, an example:

```
https://docs.google.com/document/d/{documentId}/edit
```

#### Remediation:

If the document is not meant to be public, cross-check your **General Access** settings for that specific file.\
\
To do so:

1. Open your Google Document file
2. Click on **File**
3. Click on **Share**
4. Select **Share with others**
5. A new popup will appear
6. Make sure to select **Restricted** under General Access
7. Finally, click on **Done** to save your settings

<figure><img src="../.gitbook/assets/image (9).png" alt=""><figcaption><p>As you can see, in this example the full document link was shared (intentionally). This happens more often than expected.</p></figcaption></figure>

<figure><img src="../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

#### Potential Impact:

Team members may occasionally share Google Documents with other co-workers and enable access for anyone. It also happens that they share direct link through various mediums (screenshots, screen recordings, emails, etc.)\
\
If the document happens to contain sensitive company data or data that is meant for internal use only, you introduce the risk of it **being accessed by unauthorized users**.

#### References:

* [https://support.google.com/docs/answer/2494893](https://support.google.com/docs/answer/2494893)
