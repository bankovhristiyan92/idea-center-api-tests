# Idea Center API Tests

A lightweight Postman/Newman test suite for validating the core Idea Center backend workflows, including user registration, authentication, and idea lifecycle operations.

## Overview

This repository contains:

- `Idea Center.postman_collection.json` — Postman collection with automated API tests
- `Idea Center-*.html` — generated HTML test report from Newman
- `README.md` — setup and usage documentation

The collection is designed to exercise the main API flows for the Idea Center application and verify expected responses for successful operations.

## Included API checks

The collection covers the following endpoints and scenarios:

- User creation
- User authentication
- Create a new idea
- List all ideas
- Edit the last created idea
- Delete the edited idea

Each request includes basic test assertions such as:

- status code validation
- response structure checks
- success message verification
- non-empty result validation for list endpoints

## Repository structure

```text
.idea-center-api-tests/
├── README.md
├── Idea Center.postman_collection.json
├── Idea Center-2026-10-31-16-38-43-722-0.html
└── ...generated Newman reports
```

## Prerequisites

Before running the tests, make sure you have:

- Node.js and npm installed
- Newman installed globally
- A running Idea Center API instance
- Access to the correct base URL and credentials

## Install Newman

```bash
npm install -g newman
```

If you want HTML reporting:

```bash
npm install -g newman-reporter-html
```

## Run the collection

From the repository root:

```bash
newman run "Idea Center.postman_collection.json"
```

To generate a readable HTML report:

```bash
newman run "Idea Center.postman_collection.json" \
  --reporters cli,html \
  --reporter-html-export "idea-center-report.html"
```

## Collection configuration

The Postman collection uses variables such as:

- `baseURL` — API base URL
- `token` — bearer auth token
- `randomTitle` — generated title for new idea creation
- `lastIdeaId` — targeted idea ID used in edit/delete requests

If needed, update these values in Postman or via CLI environment variables before running the suite.

## Example with custom base URL

```bash
newman run "Idea Center.postman_collection.json" \
  --env-var "baseURL=http://localhost:5000"
```

## Notes

- The collection is best suited for smoke testing or validating backend behavior during development.
- For production use, consider separating environment-specific values from the collection and managing them with a Postman environment file.
- The HTML report is useful for sharing validation results with teammates or reviewers.

## License

This project is provided as-is for API testing and validation purposes.

## Contributing

Feel free to extend the collection with additional endpoints, negative test cases, or richer assertions as the API evolves.
