---
title: Frontend building block view
---

# Frontend building block view

## Overview / Structure:
This diagram describes the subsystems needed in context of a frontend application. It illustrates the actors, systems, and their relationships.

* User: Represents the individual interacting with the application.
* Identity Provider (IdP): An external system responsible for user authentication and authorization, providing access tokens to authorized users.
* Frontend Application: The web-based interface that users interact with, providing the user interface and functionalities.
* Backend API: The server-side component that provides data and functionalities to the frontend application, often accessed through REST APIs.
* Database: The system storing application data accessed and manipulated by the backend API.

```mermaid
graph TD
    user[User<br>A user of the application]
    idp[Identity Provider<br>Provides authentication and authorization services]
    frontend[Frontend Application<br>Provides user interface and interacts with backend API]
    backend[Backend API<br>Provides data and functionalities to the frontend]
    database[Database<br>Stores application data]
    user <-->|Authenticates with OIDC/OAuth2| idp
    user <-->|Uses HTTPS and access token| frontend
    frontend <-->|Uses REST API JSON/HTTPS| backend
    backend <-->|Reads from and writes to JDBC/ODBC| database
```

## Frontend Components View
The diagram illustrates the architecture of a frontend application, highlighting its key building blocks and technologies:

* React as frontend framework
* i18 for internationalization
* TanStack Router for routing 
* Microsoft Authentication Library (MSAL) authentication module for user authentication 
* Ant Design (AntD) as a UI framework
* Axios for handling HTTP requests
* Zod for data validation


```mermaid
graph TD;
  subgraph "React Frontend"
    
    App -->|Internationalization| react-intl
    App -->|Routing| TanStack
    App -->|Authentication| MSAL
    App -->|Data Fetching| axios
    App -->|UI Components Library| AntD
    App -->|Data Validation| zod
  end
```

The decisions regarding the selected components are recorded in the following ADRs:

* [ADR-02 - Internationalization](../09_architectural-decisions/adr-02.md)
* [ADR-03 - Routing](../09_architectural-decisions/adr-03.md)
* [ADR-04 - Authentication](../09_architectural-decisions/adr-04.md)