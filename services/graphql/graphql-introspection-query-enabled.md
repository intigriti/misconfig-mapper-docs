# GraphQL Introspection Query Enabled

#### Description:

GraphQL is a popular query language for APIs to help developers query for data using strongly typed queries.\
\
By default, GraphQL comes with the Introspection query enabled and requires no additional authentication or authorization.\
\
The introspection query returns a GraphQL schema with all the information about the GraphQL API,   including what queries it supports like schemas, mutations, fields, but also in some cases, private fields.\
\
This can help a bad actor to learn everything about your API with one single request to the GraphQL API.\
\
It's a best practice to disable this for unauthenticated users and only allow access by your IDE or in your development environment as that's the intended use for it.

#### Testing:

To test if the introspection query is enabled in GraphQL, you'll first need to enumerate the API endpoint. Usually, this is one of the following API endpoints:

```
/graphql
/graph
/graphiql
/api/graphql
/v1/explorer
/v1/graphiql
/graphql/console
/graphql.php
/graphiql.php
```

Once you identified the API endpoint, you can send the following query as a HTTP POST request in the response body:

```
  query IntrospectionQuery {
    __schema {
      queryType { name }
      mutationType { name }
      subscriptionType { name }
      types {
        ...FullType
      }
      directives {
        name
        description
        args {
          ...InputValue
        }
        onOperation
        onFragment
        onField
      }
    }
  }

  fragment FullType on __Type {
    kind
    name
    description
    fields(includeDeprecated: true) {
      name
      description
      args {
        ...InputValue
      }
      type {
        ...TypeRef
      }
      isDeprecated
      deprecationReason
    }
    inputFields {
      ...InputValue
    }
    interfaces {
      ...TypeRef
    }
    enumValues(includeDeprecated: true) {
      name
      description
      isDeprecated
      deprecationReason
    }
    possibleTypes {
      ...TypeRef
    }
  }

  fragment InputValue on __InputValue {
    name
    description
    type { ...TypeRef }
    defaultValue
  }

  fragment TypeRef on __Type {
    kind
    name
    ofType {
      kind
      name
      ofType {
        kind
        name
        ofType {
          kind
          name
        }
      }
    }
  }
```

This query should return all mutations, types, queries and (depreciated) fields.

{% hint style="info" %}
You can help visualize and understand the returned data using a tool like **GraphQL Voyager**.
{% endhint %}

#### Remediation:

Depending on your development tools and environment, there are several ways to disable the introspection query.\
\
In Node.JS, it's simply passing the **NoIntrospection** to the GraphQL **validationRules** config field:

```javascript
const schema = { };

app.use('/graphql', graphqlHTTP({
    schema: schema,
    validationRules: [NoIntrospection],

    // Disable GraphiQL for non-dev environments
    graphiql: !!(process.env.NODE_ENV === 'development'),
}));
```

In case you use **Apollo Server**:

```javascript
const server = new ApolloServer({
  typeDefs,
  resolvers,
  introspection: !!(process.env.NODE_ENV !== 'production')
});
```

And for **PHP**:

```php
use GraphQL\GraphQL;
use GraphQL\Validator\Rules\DisableIntrospection;
use GraphQL\Validator\DocumentValidator;

// Add rule to disable Introspection query
$rule = new DisableIntrospection(DisableIntrospection::ENABLED);
DocumentValidator::addRule($rule);

$query = "...";

GraphQL::executeQuery($query);
```

#### Potential Impact:

A malicious actor is able to enumerate your entire GraphQL API and return back all possible queries, mutations, fields, etc.\
\
This information is often later used for further exploitation to aid in finding broken access control vulnerabilities or other methods that the API supports and can be abused by a bad actor.

#### References:

* [https://graphql.org/learn/introspection/](https://graphql.org/learn/introspection/)
* [https://cheatsheetseries.owasp.org/cheatsheets/GraphQL\_Cheat\_Sheet.html#introspection-graphiql](https://cheatsheetseries.owasp.org/cheatsheets/GraphQL\_Cheat\_Sheet.html#introspection-graphiql)
* [https://www.apollographql.com/blog/graphql/security/why-you-should-disable-graphql-introspection-in-production/](https://www.apollographql.com/blog/graphql/security/why-you-should-disable-graphql-introspection-in-production/)
