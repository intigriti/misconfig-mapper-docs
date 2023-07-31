# Atlassian Jira Service Desk Open Signups

#### Description:

Atlassian Jira Service Desk may have misconfigured permissions and allow anyone to signup and get access to private or internal company support tickets via the ServiceDesk signup app route.

#### Testing:

Navigate to the following app route and check if signups are enabled:

```
/servicedesk/customer/user/login
```

#### Remediation:

Make sure to disable signups for Service Desk. One way to do so is:

1. Visit your **Jira Service Desk Configuration** (`https://{yourAtlassian}.atlassian.net/jira/settings/products/servicedesk/customer-access`)
2. Next, open up **Customer access** from the side-navigation bar
3. Make the appropriate changes and **remove Portal access for non-authorized users**
4. Save your settings

<figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

To further secure your company from unauthorized access to your Atlassian products, you are recommended to enforce an email domain whitelist:

To do so:

1. Visit your [Atlassian Administrator panel](https://admin.atlassian.com/)
2. Open **User access settings** from the side navigation bar
3. Next, remove all access from **Any domain** if you haven't already
4. Verify and add your own domain to only allow users with your whitelisted domain to get access

<figure><img src="../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

#### References:

* [https://medium.com/@intideceukelaire/hundreds-of-internal-servicedesks-exposed-due-to-covid-19-ecd0baec87bd](https://medium.com/@intideceukelaire/hundreds-of-internal-servicedesks-exposed-due-to-covid-19-ecd0baec87bdhttps://support.atlassian.com/jira-service-management-cloud/docs/customer-permissions-for-your-service-project-and-jira-site/)
* [https://support.atlassian.com/jira-service-management-cloud/docs/customer-permissions-for-your-service-project-and-jira-site/](https://medium.com/@intideceukelaire/hundreds-of-internal-servicedesks-exposed-due-to-covid-19-ecd0baec87bdhttps://support.atlassian.com/jira-service-management-cloud/docs/customer-permissions-for-your-service-project-and-jira-site/)
* [https://support.atlassian.com/user-management/docs/control-how-users-get-access-to-products/](https://support.atlassian.com/user-management/docs/control-how-users-get-access-to-products/)
