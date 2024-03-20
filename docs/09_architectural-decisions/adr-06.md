---
title: ADR-06 Integratet Swagger-Doc
---

# Integratet Swagger-Doc

## Status - Accepted 🟢

## Context

In the backend development of our project, we faced the challenge of finding an efficient and reliable method for documenting our API endpoints. To ensure continuous accuracy and currency of the API documentation, it was necessary to establish a process that simplifies synchronization between the code and its documentation. Previously, manual maintenance of documentation was time-consuming and prone to errors, leading to discrepancies between the implemented API and its description.

## Decision

After thorough consideration of various options, we decided to integrate Swagger documentation directly into the code. This decision was implemented using the libraries [github.com/swaggo/echo-swagger](https://pkg.go.dev/github.com/swaggo/echo-swagger@v1.4.1) version 1.4.1 and [github.com/swaggo/swag](https://pkg.go.dev/github.com/swaggo/swag@v1.16.3) version 1.16.3. This approach allows us to automatically generate the API documentation from annotations present in the code. An example of such annotations is the marking of the Courses function in the CourseController, which provides detailed information about the corresponding API endpoint, including summary, description, tags, response formats, and possible error responses.

## Consequences

The direct integration of Swagger documentation into the code brings several advantages. The main benefit is that the documentation is always up-to-date and accurately reflects what is implemented in the code. This eliminates the effort of manually updating the documentation, resulting in significant time savings and ensuring consistency between code and documentation. Additionally, the integrated Swagger UI offers an interactive interface that allows developers and end users to test the API directly.

However, there are also downsides to this approach. Writing and maintaining the required annotations in the code can be tedious and requires careful attention to avoid errors. Incorrectly placed or incomplete annotations can lead to incorrect or misleading documentation. Therefore, it is important for developers to be familiar with the syntax and requirements of Swagger annotations and to implement them carefully.