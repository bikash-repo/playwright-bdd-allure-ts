# Playwright BDD Automation Framework

## ⚠ Internal Project Notice

This automation framework is strictly intended for **internal use only**.

* No reports, logs, artifacts, or results should be published publicly.
* CI artifacts must remain within internal systems.
* Slack notifications are restricted to internal channels.
* This repository must remain **private**.

---

# Overview

This project is a **production-ready UI and API test automation framework** built using modern automation tools and enterprise architecture principles.

The framework supports **BDD testing**, **data-driven testing**, **parallel execution**, and **rich reporting** while integrating with CI/CD pipelines.

It is designed for scalable automation in enterprise environments.

---

# Tech Stack

* Playwright
* TypeScript
* Cucumber (BDD)
* Allure Reporting
* Winston Logging
* Docker
* GitLab CI
* GitHub Actions (optional)
* Slack Notifications
* JSON based configuration

---

# Key Features

## BDD Test Automation

Tests are written using **Gherkin syntax** for better readability and collaboration.

Example:

```gherkin
Feature: Login functionality

  Scenario: Valid user login
    Given I navigate to the login page
    When I login with valid credentials
    Then I should see the inventory page
```

---

## Environment Configuration

Environment specific settings are stored in JSON files.

Supported environments:

* dev
* qa
* prod

Example:

```
src/config/env/dev.json
src/config/env/qa.json
src/config/env/prod.json
```

These files contain:

* base URL
* browser configuration
* environment settings

---

## Data Driven Testing

Test data is maintained in JSON format.

Example:

```
src/data/loginData.json
```

This allows easy reuse of test data across scenarios.

---

## Logging

The framework uses **Winston Logger** for structured logging.

Logs include:

* test execution information
* errors
* debug data

Log file location:

```
logs/framework.log
```

---

## Reporting

Test execution reports are generated using **Allure**.

Report includes:

* test results
* screenshots
* API responses
* logs
* Playwright traces

Reports are stored as **CI artifacts only**.

---

## Failure Debugging

The framework automatically captures:

* screenshots
* Playwright traces
* error logs
* API responses

This helps diagnose failures quickly.

---

## Parallel Execution

Tests can run in parallel for faster execution.

Configured via:

```
cucumber.js
```

Example:

```
parallel: 4
```

---

## Tag Based Execution

Tests can be filtered using tags.

Example:

Run smoke tests:

```
npx cucumber-js --tags "@smoke"
```

Run regression tests:

```
npx cucumber-js --tags "@regression"
```

---

# Project Structure

```
playwright-bdd-allure-framework

features/
    login.feature

src/
    api/
    config/
        env/
    data/
    hooks/
    pages/
    steps/
    support/
    utils/

logs/
allure-results/
test-results/

cucumber.js
playwright.config.ts
tsconfig.json
package.json
Dockerfile
.gitlab-ci.yml
README.md
```

---

# Installation

Clone the repository.

```
git clone https://github.com/bikash-repo/playwright-test-framework.git
```

Navigate to project directory.

```
cd playwright-test-framework
```

Install dependencies.

```
npm install
```

Install Playwright browsers.

```
npx playwright install
```

---

# Running Tests

Run default test execution:

```
npm run test
```

Run tests in DEV environment:

```
npm run test:dev
```

Run tests in QA environment:

```
npm run test:qa
```

Run tests in PROD environment:

```
npm run test:prod
```

---

# Generate Allure Report

Generate report:

```
npm run allure:generate
```

Open report:

```
npm run allure:open
```

---

# Running Tests with Docker

Build Docker image:

```
docker build -t playwright-bdd .
```

Run tests:

```
docker run playwright-bdd
```

---

# CI/CD Integration

## GitLab CI

Pipeline runs tests automatically and stores reports as artifacts.

Example stages:

* Install dependencies
* Run tests
* Generate Allure report
* Store artifacts

---

## GitHub Actions

GitHub workflow is available for optional CI execution in private repositories.

---

# Slack Notifications

Slack notifications are sent when:

* pipeline fails
* test failures occur

Slack webhook must be configured through environment variables.

---

# Advanced Debugging

The framework supports Playwright tracing.

Trace files include:

* screenshots
* network logs
* DOM snapshots

Trace files are generated automatically on failure.

---

# Best Practices

* Keep test scenarios independent
* Use Page Object Model
* Store test data in JSON
* Avoid hard coded values
* Use tags for test categorization

---

# Maintainer

Automation Framework maintained internally by the QA Engineering team.

---

# License

Internal project – not intended for public distribution.
