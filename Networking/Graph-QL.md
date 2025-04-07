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

## Building blocks of GraphQL

## Building a small GraphQL App

## Calling GraphQL from client

## Tooling

## Advanced
