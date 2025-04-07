# Graph QL

## Introduction to GraphQL

In traditional REST APIs, each type of data is typically accessed through its own dedicated endpoint. For example, if an application needs to display continents, countries, and languages, it might require three separate HTTP requests:

```
/api/continents
/api/countries
/api/languages
```
Each request returns a separate piece of the puzzle, and the client is responsible for stitching the data together.

GraphQL takes a different approach. Instead of multiple endpoints, it uses a **single endpoint**, usually `/graphql`, to serve all types of data. The client sends a structured query describing exactly what it needs, and the server responds with just that data—nothing more, nothing less.

In this model, the responsibility of selecting and shaping the data is shifted from the server to the client. The data is returned in a hierarchical format that often mirrors how it will be used in the UI. For instance, instead of separate requests, a GraphQL query can request continents, their countries, and each country's languages in one go:
The hierarchy of the data looks something like this:
```
continents
  - countries
      - languages
```

This reflects a **graph-like relationship** between entities—hence the name *GraphQL*.

GraphQL is particularly powerful when data entities are interrelated and the client needs flexibility in how it fetches and structures data. A good example of this in action can be seen in the [Apollo GraphQL Explorer](https://studio.apollographql.com/public/countries/variant/current/explorer), where clients can compose custom queries to explore complex, nested data structures with ease.

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
![GraphQL_features](https://github.com/user-attachments/assets/c22d753c-0f4b-4f4d-bbb8-1e4ac1f33df7)



**1. No Over-Fetching or Under-Fetching**

With REST, you often get *too much* data or *not enough*, which means extra calls and wasted bandwidth.

GraphQL flips that. You *ask for exactly what you need*, and that’s all you get.

```graphql
query {
  user {
    name
    email
  }
}
```

**2. Optimized for Mobile**

Mobile apps thrive on lightweight data. With GraphQL, you can fetch less data for mobile screens and more for desktop, all from the same endpoint.

Smaller payloads = faster load times = better UX.


**3. You Shape the Response, Not the Server**

GraphQL lets you structure your data in a hierarchical, nested way, just like your UI.

Here’s a flat query:
```graphql
query {
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
Here’s a deeply nested one that mirrors real-world relationships:
```graphql
query {
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
This is called **declarative data fetching** — you say what you want, not how to get it.


**4. Strongly Typed**

GraphQL APIs are backed by a strong type system. That means:
- You always know what fields exist
- You know their types (e.g., String, Int, Boolean)
- Errors can be caught early—great for IDEs and tooling


**5. Real-Time updates with Subscriptions**

Ideal for live updates—like chat messages, notifications, or stock prices

GraphQL supports subscriptions, which let clients listen to events and receive real-time data over WebSockets.


**6. Built-in Introspection**

GraphQL is **self-documenting**. Clients can query the schema itself to explore available types, fields, and operations.
```graphql
query {
  __schema {
    types {
      name
    }
  }
}
```
This powers tools like GraphiQL, enabling autocomplete, field descriptions, and more.


**7. Consistent Request Style**

Almost all GraphQL operations use a single HTTP POST request to one endpoint.

No more managing a dozen REST routes—just one door, and you choose what comes through.



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
