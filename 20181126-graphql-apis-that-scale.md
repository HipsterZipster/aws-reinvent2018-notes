# Graphql APIs that Scale

Speaker: Nader Dabit
Developer Advocate, AWS Mobile

# Getting Started
- AWS AppSync
- Apollo Client / Server


## Naming Matters

- no code names or lingo
- design the schema to the needs of the UI
- make type names as specific as possible (NewsArticles  vs Articles)
- name queries and mutations "entityAction" (userCreate, userDelete) instead of "actionEntity" ("createUser", deleteUser)
- dont make your schema a 1:1 mapping of your data achitecture

## Use Input Types



API Gateway - Resolvers

Interesting Use Cases

- microservices
- dynamic delivery of image assets for AR / VR applicatoins
- interacting with AI / ML services via a lambda function
- turning an exsting rest api into a graphql api
