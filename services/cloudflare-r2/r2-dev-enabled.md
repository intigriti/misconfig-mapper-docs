# R2.DEV Enabled

#### Description:

Cloudflare R2 storage is a high-performance, zero-egress fees storage service that allows developers to store (private) unstructured data objects (such as invoices or backups) and also use it as a CDN to store publicly accessible files (such as images, videos and even static HTML and JavaScript files).

R2.DEV is a simple feature within Cloudflare R2 that provides developers the ability to make their buckets publicly accessible for testing purposes. If this feature is left enabled (by accident), it can open up a new attack surface and allow bad actors to view sensitive data on the bucket. This often leads to PII or other excessive data leaks.

#### Testing:



#### Remediation:

To verify that public access

#### Potential Impact:



#### References:

* [https://blog.intigriti.com/hacking-tools/hacking-misconfigured-cloudflare-r2-buckets-a-complete-guide](https://blog.intigriti.com/hacking-tools/hacking-misconfigured-cloudflare-r2-buckets-a-complete-guide)
* 