# Rick and Morty GraphQL API

Welcome to the Rick and Morty GraphQL API! This endpoint allows you to query detailed information about characters, episodes, and locations from the popular animated series "Rick and Morty."

## Base URL

```
https://rickandmortyapi.com/graphql
```

## Overview

This API uses GraphQL, a query language for APIs that enables you to request only the data you need. With this endpoint, you can:

- Retrieve detailed character information.
- Fetch episodes by name, air date, or other attributes.
- Query locations, including their residents and type.

## Getting Started

To use the API, you'll need to send a POST request to the base URL with your GraphQL query in the request body. Here's a simple example:

### Sample Query

#### Fetching Characters
```graphql
query {
  characters(page: 1) {
    results {
      id
      name
      status
      species
      gender
      origin {
        name
      }
      location {
        name
      }
    }
  }
}
```

#### Response Example
```json
{
  "data": {
    "characters": {
      "results": [
        {
          "id": "1",
          "name": "Rick Sanchez",
          "status": "Alive",
          "species": "Human",
          "gender": "Male",
          "origin": {
            "name": "Earth (C-137)"
          },
          "location": {
            "name": "Earth (Replacement Dimension)"
          }
        }
      ]
    }
  }
}
```

## Available Queries

### Characters
- **Query**: `characters`
- **Parameters**:
  - `page`: Int (Optional) - The page number of the results.
  - `filter`: Object (Optional) - Filter characters by name, status, species, type, or gender.
- **Fields**:
  - `id`, `name`, `status`, `species`, `type`, `gender`, `origin`, `location`, `image`, `episode`

#### Example Query
```graphql
query {
  characters(filter: { name: "Rick" }) {
    results {
      name
      status
      species
    }
  }
}
```

### Episodes
- **Query**: `episodes`
- **Parameters**:
  - `page`: Int (Optional) - The page number of the results.
  - `filter`: Object (Optional) - Filter episodes by name or episode code.
- **Fields**:
  - `id`, `name`, `air_date`, `episode`, `characters`

#### Example Query
```graphql
query {
  episodes(filter: { name: "Pilot" }) {
    results {
      name
      air_date
      episode
      characters {
        name
      }
    }
  }
}
```

### Locations
- **Query**: `locations`
- **Parameters**:
  - `page`: Int (Optional) - The page number of the results.
  - `filter`: Object (Optional) - Filter locations by name or type.
- **Fields**:
  - `id`, `name`, `type`, `dimension`, `residents`

#### Example Query
```graphql
query {
  locations(filter: { name: "Citadel" }) {
    results {
      name
      type
      dimension
      residents {
        name
      }
    }
  }
}
```

## Tools and Libraries

To interact with this GraphQL API, you can use:

- **GraphQL Playground**: A built-in interactive environment available at the base URL.
- **Apollo Client** (JavaScript):
  ```bash
  npm install @apollo/client graphql
  ```
- **Postman**: Add a new request, set the method to POST, and include your query in the body.

## Rate Limiting
The API has rate limits to ensure fair usage. Please refer to the [Rick and Morty API documentation](https://rickandmortyapi.com/documentation) for details.

## Contributions

This API is a public service provided by [Rick and Morty API](https://rickandmortyapi.com). If you encounter issues or have suggestions, feel free to open an issue on the [GitHub repository](https://github.com/axelarnal/rickandmortyapi).

---

Enjoy exploring the multiverse of Rick and Morty!

