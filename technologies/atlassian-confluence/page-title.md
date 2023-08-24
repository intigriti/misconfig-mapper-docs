# Anonymous access to Remote API

#### Description:

Atlassian Confluence provides a Remote XML-RPC and SOAP API to change and read data in Confluence.\
\
This API is depreciated and replaced with a REST API since version 5.5 but can still be in use in some instances.\
\
It is in that case recommended to **disable anonymous access to the API** and **prevent bots from making destructive changes in bulk**.

#### Testing:

Both XML-RPC and SOAP API are currently depreciated and replaced by the REST API since Confluence v5.5.\
\
Both APIs are accessible through the following endpoints on your Confluence instance:

**XML-RPC:**

```
/rpc/xmlrpc
```

#### SOAP:

```
/rpc/soap-axis/confluenceservice-v2
```

#### Remediation:

It is always recommended to **upgrade and use the latest version available** of Atlassian Confluence.

1. Navigate to your Confluence instance and sign in
2. Open your **Administrator Settings** by clicking on the gear icon next to your profile picture
3. In your side navigation bar, scroll down to **Security** and open **Security Configurations**
4. Make sure that **Anonymous Access to Remote API** is **disabled**
5. Save your changes

<figure><img src="../../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>



#### References:

* [https://developer.atlassian.com/server/confluence/confluence-xml-rpc-and-soap-apis/](https://developer.atlassian.com/server/confluence/confluence-xml-rpc-and-soap-apis/)
* [https://confluence.atlassian.com/doc/anonymous-access-to-remote-api-151028.html](https://confluence.atlassian.com/doc/anonymous-access-to-remote-api-151028.html)

