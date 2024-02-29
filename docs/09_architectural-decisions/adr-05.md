---
title: ADR-05 Configfile
---

# Configfile

## Status - Accepted 🟢

## Context
In compliance with the client's requirements, our project necessitates a dynamic and adaptable configuration approach. This requirement includes the ability to set multiple email addresses for course administrators, configure log levels, and other sensible configurations without hardcoding them in the source code. To address these needs effectively, a configuration file strategy is proposed.

## Desicion
A configuration file (config.go) will be implemented with the capability to:

- Store and manage multiple email addresses for the role of course administrators.
- Configure the log level (Debug, Info, Warn, Error).
- Set additional meaningful configurations dynamically.
Furthermore, in situations where the application is started without an existing configuration file, the system will automatically generate a default configuration file populated with standard parameters. This ensures that the system remains operable and configurable even in the absence of a pre-defined configuration.

## Consequences

__Advantages:__

Enhances flexibility by allowing configuration changes without source code modification.
Simplifies application deployment and setup, especially in varied environments.
Improves maintainability and scalability of the application.

__Disadvantages:__

Potential risk of configuration errors due to incorrect file setup or default values.
Requires robust validation and error handling to prevent misconfiguration issues.

## Guidelines for Implementation:
- The configuration file should be in a human-readable and easily editable format like YAML or JSON.
- Default values in the generated configuration file should represent a safe and minimal operational setup.
- The system should validate the configuration file at startup and log any discrepancies or use of default values.
- Documentation should be provided to administrators on how to modify and manage the configuration file.
- Environment variables should be considered for overriding configuration file settings where appropriate, providing flexibility in different deployment scenarios.

## Technical Implementation Details:
- The config.go file will include a function NewAPIConfig() to generate a configuration with default values.
- The FromFile(path string) function will attempt to read the configuration from a specified path, falling back to generating a default configuration if the file does not exist or is not readable.
- The configuration structure will include fields for host, port, authentication settings, database connection string, and other relevant settings as per project requirements.

For more Informations see [Crosscutting Concepts - Configfile](../08_crosscutting_concepts/04_configfile.md).