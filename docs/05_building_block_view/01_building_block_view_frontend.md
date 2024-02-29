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
C4Context
    title System Context Diagram for Frontend Application

    Person(user, "User", "A user of the application")
    System_Ext(idp, "Identity Provider", "Provides authentication and authorization services")

    System(frontend, "Frontend Application", "Provides user interface and interacts with backend API")

    System_Ext(backend, "Backend API", "Provides data and functionalities to the frontend")
    SystemDb(database, "Database", "Stores application data")

    Rel(user, idp, "Authenticates with", "OIDC/OAuth2")
    Rel(idp, frontend, "Provides access token to", "HTTPS")
    Rel(user, frontend, "Uses", "HTTPS")
    Rel(frontend, backend, "Uses", "REST API (JSON/HTTPS)")
    Rel(backend, database, "Reads from and writes to", "JDBC/ODBC")

```
