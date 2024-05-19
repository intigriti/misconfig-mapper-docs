# Open User Registration

#### Description:

It is possible that anyone can signup in your Freshworks Freshservice instance due to a misconfiguration in the domain allow list.

#### Testing:

You can cross-check if user registration is open for anyone by navigating to the following app route:

```
https://<companyName>.freshservice.com/
```

#### Remediation:

Make sure to set the proper setting for new signups. One way to do so is:

1. Visit your **Freshworks Freshservice Instance**
2. Next, navigate to **Admin**
3. Click on **Channels**
4. Next, click on **Portals**
5. And click on **Settings**
6. Finally, select the option **No** under **"Allow users to Sign Up from the customer portal"**

<figure><img src="../../.gitbook/assets/freshdesk/freshservice/0.png" alt=""><figcaption></figcaption></figure>

#### Potential Impact:

In case registrations are left open for anyone to signup to your Freshworks Freshservice instance, depending on the in-app permissions set, it could mean that new users get access to internal-only resources, such as support tickets, company metrics or even personal identifiable information (PII) of customers or clients.


#### References:

* [https://infosecwriteups.com/hundreds-of-companies-internal-data-exposed-part-2-the-freshservice-misconfiguration-a9432c0b5dc8](https://infosecwriteups.com/hundreds-of-companies-internal-data-exposed-part-2-the-freshservice-misconfiguration-a9432c0b5dc8)
* [https://partnersupport.freshworks.com/en/support/solutions/articles/225287-how-can-i-disable-the-option-for-requesters-to-sign-up-to-our-helpdesk-](https://partnersupport.freshworks.com/en/support/solutions/articles/225287-how-can-i-disable-the-option-for-requesters-to-sign-up-to-our-helpdesk-)
