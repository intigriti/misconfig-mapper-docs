# Atlassian Jira Email Visibility

#### Description:

Atlassian Jira may **disclose the user's email addresses** on each user's profile if the **email visibility policy is left misconfigured**.

#### Testing:

Open up any user's profile in your Jira instance as an anonymous user and verify that you can view the email address of the user.

#### Remediation:

Make sure to set the proper setting for email visibility. One way to do so is:

1. Visit your **Atlassian Jira Instance**
2. Next, open up your settings by clicking on the gear icon next to your profile
3. Select **System** under **Jira Settings**
4. Select **General Configuration** in the side-navigation bar and click on **Edit Settings** (top-right of your page)
5. Scroll down to **User email visibility** and select the appropriate setting
6. Save your settings

<figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

#### Potential Impact:

Email-addresses could be used in further targeted exploitation attacks on company employees.

#### References:

*
