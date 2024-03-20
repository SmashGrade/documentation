---
title: Backend Security
---

# Backend Security

## Authentication
Our backend authentication is currently implemented with Microsoft's OpenID Connect but is designed for flexibility to switch to other providers as needed. This approach uses JSON Web Tokens (JWT) for secure and efficient user identity verification, allowing easy adaptation to different authentication providers through configurable OIDC settings.

## Cross-Origin Resource Sharing (CORS)
Regarding CORS, we have intentionally limited the accepted headers to those specific to our application's requirements. This targeted configuration helps ensure a high level of security by allowing only the headers and sources necessary for our application logic.

## Authorization
Authorization in our system is managed through Role-Based Access Control (RBAC), based on JWT Claims obtained from Microsoft Azure. These claims contain role information provided by Azure's "entraID," enabling secure and precise access control based on user roles.

## OWASP Security Assessment
While regular assessments of OWASP backend risks are not conducted, we have performed a current review and identified no vulnerabilities. This targeted check ensures that our system meets current security standards and addresses known weaknesses.

## Rate Limiting, Logging, and Encryption in Transit
As previously described, we continue to implement rate limiting to protect the backend system, automated audit and error logging in JSON format for efficient monitoring, and SSL (Secure Socket Layer) for data transmission encryption using certificates from Let's Encrypt. These measures collectively contribute to the overall security and robustness of our backend architecture.

## Interesting Links

[What is CORS?](https://portswigger.net/web-security/cors)

[OWASP Top Ten](https://owasp.org/www-project-top-ten/)