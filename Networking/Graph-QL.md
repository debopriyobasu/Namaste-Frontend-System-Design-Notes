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

| Aspect                     | REST (Representational State Transfer)                                     | GraphQL (Graph Query Language)                                                                 |
| :------------------------- | :------------------------------------------------------------------------- | :--------------------------------------------------------------------------------------------- |
| **Data fetching** | Uses multiple endpoints (URLs) to access different resources. Fetching related data often requires multiple round trips/requests. | Typically uses a single endpoint. Clients send a query specifying the exact data needed, including relationships, in a single request. |
| **Request Structure** | Relies on HTTP verbs (GET, POST, PUT, DELETE, etc.) and URL paths to define operations on resources. Parameters can be in URL, query string, or body. | Usually uses POST requests. The request body contains a query (for reading data) or a mutation (for writing data) written in the GraphQL language. |
| **Over-fetching/ Under-fetching** | Prone to both. Over-fetching occurs when an endpoint returns more data than the client needs. Under-fetching occurs when an endpoint doesn't return enough data, requiring additional requests. | Designed to prevent this. The client specifies exactly the fields it needs, eliminating over-fetching. All required data can be requested in one query, avoiding under-fetching. |
| **Response size** | Response size is determined by the server for each endpoint. Can be larger than needed due to fixed data structures (over-fetching). | Response size is determined by the client's query. Generally smaller and optimized as it only contains the requested data. |
| **Versioning** | Commonly handled via URL (e.g., `/v1/`, `/v2/`), custom headers, or query parameters. Can lead to maintaining multiple API versions. | Typically avoids explicit versioning. The schema can evolve by adding new fields/types without breaking existing clients. Deprecating fields is preferred over removing them. |
| **Schema Definition** | No built-in standard. Often relies on external specifications like OpenAPI (Swagger) to describe the API structure and data formats. | Has a strong type system and a Schema Definition Language (SDL). The schema defines all available types, queries, mutations, and subscriptions, acting as a contract. Schema is introspectable. |
| **Real-time capabilities** | Not inherently built-in. Requires separate techniques like polling, long-polling, Server-Sent Events (SSE), or WebSockets. | Supports real-time data via "Subscriptions," allowing clients to subscribe to specific events and receive updates, usually implemented over WebSockets. |
| **Tooling Support** | Mature and extensive ecosystem due to its longevity and alignment with HTTP standards. Wide range of tools for testing, documentation, mocking, clients, etc. | Rapidly growing ecosystem. Strong tooling often centered around the schema (e.g., Apollo Studio, GraphiQL). Client libraries like Apollo Client and Relay provide powerful features. |
| **Caching** | Can leverage standard HTTP caching mechanisms effectively (browser cache, CDNs, reverse proxies) based on URLs and HTTP headers (e.g., `Cache-Control`, `ETag`). | Caching is more complex as most requests go to a single endpoint (often via POST). Relies more heavily on client-side library caching (e.g., normalized caches in Apollo/Relay) or complex server-side strategies. |
| **Client Control** | Limited client control over the response data structure. The server defines the structure for each resource endpoint. | High degree of client control. The client precisely dictates the shape and fields of the data it wants to receive in the response. |
| **Adoption and community** | Extremely widely adopted, the de facto standard for web APIs for many years. Massive community and vast amount of documentation and resources. | Growing rapidly, especially favoured for complex applications, microservices, and mobile clients. Strong community support, initially developed by Facebook, now open-source. |

## Building blocks of GraphQL

## Building a small GraphQL App

## Calling GraphQL from client

## Tooling

## Advanced
