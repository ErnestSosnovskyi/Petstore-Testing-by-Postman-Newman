# Postman + Newman + GitHub Actions API Testing

This repository contains an automated API testing framework. It demonstrates the ability to write comprehensive integration tests in Postman, run them locally against a mock server, and execute them automatically in a CI/CD pipeline using Newman and GitHub Actions.

## 🚀 Project Overview

The project is divided into two main parts:
1. **Local API Testing (`store.collection.json`):** Testing a locally hosted mock REST API using the AAA (Arrange, Act, Assert) pattern.
2. **CI/CD Pipeline (`petstore.collection.json`):** Automated test execution upon pushing to the `main` branch, with results published as an interactive HTML report to GitHub Pages.

## 🛠️ Features & Test Coverage

The Postman test suite covers various API testing scenarios:
- **Status Code Validation:** Ensuring correct responses (e.g., `200 OK`, `400 Bad Request`, `404 Not Found`).
- **Response Time Testing:** Verifying that endpoints respond within acceptable time limits (e.g., `< 200ms`).
- **JSON Schema Validation:** Checking the exact structure and data types of the returned JSON objects.
- **Pagination Testing:** Validating `page` and `pageSize` query parameters.
- **Sorting Validation:** Ensuring data is returned in the correct order (e.g., `sortOrder=ASC&sortKey=firstName`).
- **Data Extraction & Environment Variables:** Passing variables between requests.

## 💻 Local Setup & Execution

To run the tests locally against the mock server, follow these steps:

### Prerequisites

- [Node.js](https://nodejs.org/) installed on your machine.
- [Postman](https://www.postman.com/) desktop application.

### Installation

1. Clone the repository:

```bash
git clone <your-repository-url>
cd <repository-folder>
```

2. Start the local mock server:

```bash
npm run tern-on-api
```

*Note for Windows users: If you encounter an error with the `cp` command, run this script using Git Bash.*

3. Open Postman, import the `store.collection.json` file, and run the collection using the Postman Runner. The server runs on http://localhost:3000.

## ⚙️ CI/CD Pipeline & Reporting

This repository is configured with a GitHub Actions workflow (`.github/workflows/newman.yml`).

Every time a push is made to the main branch, the pipeline automatically:

1. Sets up a Node.js environment.
2. Installs Newman (Postman CLI) and the `newman-reporter-htmlextra` package.
3. Executes the `petstore.collection.json` tests.
4. Generates a detailed, interactive HTML report.
5. Deploys the report to the `gh-pages` branch.

# 📊 View the Test Report

The latest automated test report can be viewed here:

👉 Click to view the Newman HTML Report

*(Note: replace the link above with your actual GitHub Pages URL once deployed).*