---
title: Configfile
---

# Configuration File Overview and Strategy

## Purpose:
The configuration file (configfile) plays a critical role in our application's architecture. It offers a centralized and flexible approach to setting various operational parameters and environment-specific settings.

## Overview:
The configuration file is designed to be easily editable and readable, typically in YAML or JSON format. It allows the customization of numerous aspects of the application without altering the source code.

## Key Features:

1. __Email Addresses for Course Administrators:__

    Allows specifying one or more email addresses associated with course administrator roles.

2. __Log Level Configuration:__

    Enables setting the log level, such as Debug, Info, Warn, or Error, to control the verbosity and detail of application logs.

3. __Authentication Settings:__

    In development environments, authentication is typically disabled for ease of testing and development.
    In production environments, authentication is enabled to secure access.
    
4. __Database Connection Parameters:__

    Specifies database connection strings, migration settings, and other database-related configurations.

5. __Rate Limiting and Request Size:__

    Configures rate limits and maximum request body sizes to manage the load and prevent abuse.

6. __CORS (Cross-Origin Resource Sharing) Configuration:__

    Defines rules for allowing or restricting cross-origin requests.

7. __Mock Data:__

    Option to populate the application with mock data for testing purposes.

## Validation and Security:

- Authentication Configuration:

    For detailed validation and security configurations, refer to the Microsoft Authentication documentation. The configuration ensures compliance with OAuth standards and checks for valid @hftm.ch email addresses.
    
    The link to Microsoft Authentication documentation: [Microsoft Authentication Documentation](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-authentication-authenticator-app)

- Deployment Parameters:

    For specific deployment parameters, please refer to the [README documentation](https://github.com/SmashGrade/backend), which provides detailed guidelines on configuring the application for various environments.

- Adaptability and Environment-Specific Settings:

    The configuration file allows for distinct settings between development and production environments. This adaptability ensures that the application can be tailored to the needs of each environment, enhancing security in production while maintaining ease of use in development.
