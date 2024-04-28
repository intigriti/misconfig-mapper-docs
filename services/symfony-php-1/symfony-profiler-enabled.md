# Public Workspaces

#### Description:

Postman API is a popular collaboration platform used by developer teams to help them develop APIs faster. Workspaces are a way to share code between developers on Postman.

Postman Workspaces can contain hard-coded data that have been accidentally saved for testing purposes for example.

That means that your public Postman API workspace may expose sensitive data if you share your workspace with the public.

<figure><img src="../../.gitbook/assets/image (39).png" alt=""><figcaption></figcaption></figure>

#### Testing:

You can cross-check if your target uses Postman API and if it has a public workspace by visiting their public Postman profile:

```
https://www.postman.com/{companyName}/?tab=workspaces
```

#### Remediation:

To change the visibility of your Postman API workspace:

1. From your profile, go to your **Workspaces**:

<figure><img src="../../.gitbook/assets/image (36).png" alt=""><figcaption></figcaption></figure>

2. Next, open the Workspace you'd like to change the visibility of
3. Click on **Workspace Settings**
4. And click on **Who can access this workspace?** to unfold the available options
5. Finally, make sure you select **Only me** to change the visibility of your workspace and make it only accessible to you.

<figure><img src="../../.gitbook/assets/image (38).png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
_It is a best practice to not have any hard-coded credentials in your code._
{% endhint %}

#### Potential Impact:

Hard-coded (testing) credentials and other sensitive data can often be used by bad actors for further exploitation or infiltration into your network.\
An example would be a hard-coded Github API key that provides access to private Github repositories.

#### References:

* [https://trufflesecurity.com/blog/postman-carries-lots-of-secrets](https://trufflesecurity.com/blog/postman-carries-lots-of-secrets)
* [https://learning.postman.com/docs/collaborating-in-postman/public-api-network/sharing-your-workspace/](https://learning.postman.com/docs/collaborating-in-postman/public-api-network/sharing-your-workspace/)
* [https://learning.postman.com/docs/collaborating-in-postman/using-workspaces/managing-workspaces/](https://learning.postman.com/docs/collaborating-in-postman/using-workspaces/managing-workspaces/)

