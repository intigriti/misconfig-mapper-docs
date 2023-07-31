# Drupal Nodes

#### Description:

The way Drupal is built is made for flexibility, all content are stored separately in a new node. Including a page, an article, topic or blog entry.\
\
Nodes can contain sensitive data and if permissions are not enforced, they can leak private data to unauthorized users.

#### Testing:

Each node gets an individual ID assigned, in a black-box scenario where you have limited access to amount of nodes available. It is recommended to check thousands of IDs by making use of targeted bruteforcing\
\
To do so, replace the positional **`{ID}`** parameter and replace it with a numerical value (for example: `1`):

```
/node/{ID}
```

Keep incrementing the ID until you come an existing node ID and examine the response manually.

#### Remediation:



#### References:

* [https://twitter.com/adrien\_jeanneau/status/1273952564430725123](https://twitter.com/adrien\_jeanneau/status/1273952564430725123)

