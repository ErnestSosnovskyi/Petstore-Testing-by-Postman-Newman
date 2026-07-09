# Postman + Newman + GitHub Actions API Testing

This repository contains an automated API testing framework. It demonstrates the ability to write comprehensive integration tests in Postman, run them locally against a mock server, and execute them automatically in a CI/CD pipeline using Newman and GitHub Actions.

## 🚀 Project Overview

The project is divided into two main parts:
1. **Local & Automated API Testing:** Testing a locally hosted mock REST API (`store.collection.json`) using the AAA (Arrange, Act, Assert) pattern and API Chaining for dynamic data extraction.
2. **CI/CD Pipeline:** Automated test execution for both `petstore` and `store` APIs upon pushing or creating a Pull Request to the `main` branch, with results published as interactive HTML reports to GitHub Pages.

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
npm run turn-on-api
```

3. Open Postman, import the `store.collection.json` file, and run the collection using the Postman Runner. The server runs on http://localhost:3000.

## ⚙️ CI/CD Pipeline & Reporting

This repository is configured with a GitHub Actions workflow (`.github/workflows/newman.yml`).

Every time a push or a pull request is made to the `main` branch, the pipeline automatically:

1. Sets up a Node.js environment.
2. Installs dependencies, including Newman and the `newman-reporter-htmlextra` package.
3. Executes the `petstore.collection.json` tests.
4. Starts the local mock API server in the background, waits for it to be active, and executes the `store.collection.json` tests.
5. Generates an index page and detailed, interactive HTML reports for both test suites.
6. Deploys the reports to the `gh-pages` branch.

# 📊 View the Test Report

The latest automated test report can be viewed here:

👉 **[Click to view the Newman HTML Report](https://ernestsosnovskyi.github.io/Petstore-Testing-by-Postman-Newman/)**

*(Note: replace the link above with your actual GitHub Pages URL once deployed).*