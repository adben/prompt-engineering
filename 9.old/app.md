# Sample App extending using prompt engineering

## Original flow/sequences with the ReST API

```mermaid
graph TD
    A[User] --> B[REST API];
    B --> C[Public Endpoint];
    B --> D[Private Endpoint];
    D --> E[GET Method];
    D --> F[POST Method];
```

Sequence Diagram for GET /public Endpoint:

```mermaid
sequenceDiagram
    participant User
    participant Quarkus
    User ->> Quarkus: GET /public
    Quarkus ->> User: Return Public Data
```

Sequence Diagram for GET /private Endpoint:

```mermaid
sequenceDiagram
    participant User
    participant Quarkus
    User ->> Quarkus: GET /private
    Quarkus ->> User: Return Private Data
```

Sequence Diagram for POST /private Endpoint:

```mermaid
sequenceDiagram
    participant User
    participant Quarkus
    User ->> Quarkus: POST /private
    Quarkus ->> User: Return Success/Failure
```

## After authorization stories

```mermaid
graph TD
    A[User] --> B[REST API];
    B --> C[Public Endpoint];
    B --> D[Private Endpoint];
    D --> E[Auth Module];
    E --> F[Keycloak];
    C --> G[GET Method];
    D --> H[GET Method];
    D --> I[POST Method];
    H --> J[Register User];
```

Unfortunately, as an AI language model, I cannot generate diagrams directly. However, I can provide you with the Mermaid
code for the sequence diagram based on the system description you provided:

```mermaid
sequenceDiagram
    participant User
    participant RestAPI
    participant AuthModule
    participant Keycloak

    User ->> RestAPI: GET /public
    RestAPI ->> User: Return public data

    User ->> RestAPI: GET /private
    RestAPI ->> AuthModule: Verify user token
    AuthModule ->> Keycloak: Request user authentication
    Keycloak -->> AuthModule: Return user token
    AuthModule -->> RestAPI: User authenticated
    RestAPI ->> User: Return private data

    User ->> RestAPI: POST /private
    RestAPI ->> AuthModule: Verify user token
    AuthModule ->> Keycloak: Request user authentication
    Keycloak -->> AuthModule: Return user token
    AuthModule -->> RestAPI: User authenticated
    RestAPI ->> User: Register user in the system
```

This Mermaid code will generate a sequence diagram that shows the flow of interactions between the user, the RestAPI,
the AuthModule, and Keycloak for the three possible interactions: GET /public, GET /private, and POST /private.

