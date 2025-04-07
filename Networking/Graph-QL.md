# Graph QL

## Intro

In REST, we create a specific content for a particular data. 
For a requirement which involves getting continents, countries and languages, we would do something like this:
```
/api/continents
/api/countries
/api/languages
```
We make these three requests to get the required data.

In GraphQL, we do only one request to ```/graphql``` endpoint. The processing is moved from the client side to the server side.

The hierarchy of the data looks something like this:
```
continents
  - countries
      - languages
```

We can see that there is a graph-like relation between the data. This is where Graph QL helps.
Example: https://studio.apollographql.com/public/countries/variant/current/explorer

## What is Graph QL?
Graph QL stands for Graph Query Language. It was developed by Facebook in 2012 and open sourced in 2015.
It is an open source data query and manipulation language for APIs.
Example query:
```graphql
query ExampleQuery {
  countries {
    currency
  }
}
```

## Why GraphQL? What are its benefits?
- It helps in avoiding **over-fetching** or **under-fetching** of data.
- Better **mobile performance** (you can choose to show less data in mobile)
- It allows you to structure your data as you like in a structured / hierarchical data. In other words, it allows **Declarative Data Fetching**.
  For example, you can have something like this:
  ```graphql
  query ExampleQuery {
    continents {
      name
    }
    countries {
      name
    }
    languages {
      name
    }
  }
  ```
  You can also choose to show the data like this:
  ```graphql
  query ExampleQuery {
    continents {
      name
      countries {
        name
        languages {
          name
        }
      }
    }
  }
  ```
- It is **strongly typed**
- It has **real-time** capabilities (subscriptions)
- **Introspection**: clients can query the schema itself to understand the structure, making it self-documenting.
- Almost all of the graphQL queries are HTTP POST requests.

  
## REST vs GraphQL

| **Aspect** | **REST** | **GraphQL** |
|------------|----------|--------------|
| **Core Idea** | Like visiting different food stalls—one for each item. | Like ordering everything at one counter—get exactly what you need in one go. |
| **Data Fetching** | Multiple endpoints (e.g., `/users`, `/users/1/posts`)—requires multiple trips. | One endpoint. Send a query and get all related data in a single request. |
| **Request Style** | Uses HTTP methods like `GET`, `POST`, `DELETE`, etc. Request details are spread across URL, headers, and body. | Usually a `POST` request with a structured query or mutation inside the request body. |
| **Over/Under-fetching** | Common. May get too much or too little, requiring extra requests. | Eliminated. Clients ask for exactly what they need—nothing more, nothing less. |
| **Response Size** | Decided by the server. Can include unnecessary fields. | Defined by the client—only the requested fields are returned. |
| **Versioning** | Common (e.g., `/api/v1/`). Can lead to multiple maintained versions. | Rarely needed. Schema evolves by adding fields. Older fields can be deprecated. |
| **Schema Definition** | No built-in schema. Often documented with tools like Swagger/OpenAPI. | Strong type system and schema built-in. Introspectable and self-documenting. |
| **Real-time Support** | Not built-in. Requires hacks like polling, SSE, or WebSockets. | Built-in support via subscriptions (usually over WebSockets). |
| **Tooling** | Mature and robust. Tools like Postman, Swagger, and curl are common. | Rapidly evolving. Tools like GraphiQL, Apollo Studio, and Relay offer rich features. |
| **Caching** | Easy with HTTP standards (`Cache-Control`, `ETag`, CDNs). | More complex. Relies on smart client-side libraries (e.g., Apollo cache). |
| **Client Control** | Low. Server decides the shape of the response. | High. Client defines the response structure precisely. |
| **Community & Adoption** | Battle-tested, widely used for years. Huge community and resources. | Growing fast, ideal for modern apps. Strong community and ecosystem. |


## Building blocks of GraphQL

### Schema / Types

### Query / Mutations

### Resolver

## Building a small GraphQL App

## Calling GraphQL from client

## Tooling

## Advanced
