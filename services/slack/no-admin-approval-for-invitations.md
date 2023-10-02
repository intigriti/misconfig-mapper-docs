# No Admin Approval for Invitations

#### Description:

Slack is a popular instant-messaging platform mainly used by companies for work-related communications between team members.\
\
It can also pose as a unintentional potential security threat to companies if access is not monitored and internal-only data is shared among members in Slack.\
\
By default anyone can send invitations to invite new members. It is a best practice to only allow administrators to send and accept invitations.

#### Testing:

To check if you have permissions to invite a new member:

1. Sign in to your Slack Workspace
2. Open any channel
3. Click on **Add people**
4. A popup will open up, enter the user's email address
5. Finally, click **Add**

These reproduction steps prove that you're able to invite new members without approval from an administrator.

<figure><img src="../../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

#### Remediation:

It is a best practice to allow only workspace administrators to invite new members.\
\
To do so:

1. Sign in as the workspace administrator
2. Next, navigate to `/admin/settings` on your Slack workspace (or click on your workspace name, hover over **Tools & Settings** and click on **Workspace Settings**)
3. Open **Permissions**
4. Expand **Invitations**
5. Check the **Require admin approval** box, additionally, select the channel to receive requests in.
6. Finally click **Save** to save your changes

<figure><img src="../../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

#### Potential Impact:

As team members often share internal company data between each other, Slack can become a potential target or attack vector to your organization.\
\
Other members can unintentionally invite unauthorized users and provide them internal access.

#### References:

* [https://slack.com/help/articles/115004854783-Require-admin-approval-for-workspace-invitations](https://slack.com/help/articles/115004854783-Require-admin-approval-for-workspace-invitations)
* [https://slack.com/intl/en-in/help/articles/115004155306-Security-tips-to-protect-your-workspace](https://slack.com/intl/en-in/help/articles/115004155306-Security-tips-to-protect-your-workspace)
