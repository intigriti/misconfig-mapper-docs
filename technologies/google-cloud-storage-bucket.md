---
description: >-
  GCP Storage Bucket can be left misconfigured and allow anyone to access files
  and objects potentially containing sensitive data if access permissions aren't
  properly enforced
---

# Google Cloud Storage Bucket

### Misconfigured Access Controls:

#### Description:

Google Cloud Storage Bucket can have misconfigured access control settings and list all objects of a company's storage bucket:

#### Testing:

Visit the following URLs to check whether access is properly set. Make sure to replace `companyName` with your target name:

```
https://{companyName}.storage.googleapis.com/
https://storage.googleapis.com/{companyName}
```

Indexing can also be allowed, to cross-check, you can make use of search filters that search engines like Google provide:

```
site:storage.googleapis.com "{companyName}"
```

#### Remediation:

It is always recommended to make sure that if in case your Storage Bucket is set to host private files that aren't meant to be exposed online, that it is only accessible to those who have permission.

By default Storage Buckets are private and only accessible by you (the owner).

To verify that proper permissions are set:

1. Go to your Storage Bucket on [Google Cloud](https://console.cloud.google.com/storage/browser)
2. Select the **Permissions** tab
3. And review your permissions set for that Storage Bucket. Make sure that **allUsers** setting is not selected.

To further secure your assets, it is advisable to make use of and set proper [IAM roles](https://cloud.google.com/iam).

#### Potential Impact:

Depending on what data is stored on the GCP Storage Bucket, this could lead to several high-severity issues such as sensitive data leak, including personal identifiable information (PII) but also other type of documents that may contain internal company data.

#### References:

* [https://cloud.google.com/storage/docs/access-control/making-data-public#buckets](https://cloud.google.com/storage/docs/access-control/making-data-public#buckets)
* [https://cloud.google.com/storage/docs/public-access-prevention](https://cloud.google.com/storage/docs/public-access-prevention)
