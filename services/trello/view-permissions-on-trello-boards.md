---
layout:
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# View Permissions on Trello Boards

#### Description:

Trello is a popular cloud-based list-making app often used by companies to manage for example tasks.\
\
By default, Trello boards are only visible to other members in your workspace. However, Trello also allows users to set the board visibility to public. Making it public for anyone to view and for search engines and web archives like Google and Wayback Machine to index.\
\
As sensitive data like internal company data can be shared between team members, it is best practice to cross-check the board's visibility settings and make sure only authorized users have read access.

#### Testing:

To check for public access for any Trello board, simply visit the board URL and observe the response:

```
https://trello.com/b/{BOARD_ID}
```

There are various ways to enumerate Trello boards, the most common way to do so is making use of Google's search syntax and searching for any company related terms:

```
site:trello.com "company"
```

{% hint style="info" %}
Google may have already taken actions to prevent Trello boards from getting indexed on their search engine.\
\
Always cross-check with multiple others like DuckDuckGo, Bing, StartPage, etc.
{% endhint %}

#### Remediation:

It is recommended to set the visibility to **Private** so that **only board members can see and edit this board**.\
\
To do so:

1. Sign in to your Trello account
2. Open your board
3. Next to your board name, click on the visibility button to change the visibility
4. Finally, make sure to select **Private**

<figure><img src="../../.gitbook/assets/image (24).png" alt=""><figcaption></figcaption></figure>

#### Potential Impact:

Unauthorized users may be able to gather sensitive internal information about your company or even plain text credentials (if shared) through various search engines as your boards are public and indexed.\
\
This information is often used for further attacks.

#### References:

* [https://support.atlassian.com/trello/docs/changing-the-visibility-of-a-b](https://support.atlassian.com/trello/docs/changing-the-visibility-of-a-b)
