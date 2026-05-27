# CallOut: Accessibility Navigator for Playwright

[![Python](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/)
[![Playwright](https://img.shields.io/badge/playwright-v1.0+-green.svg)](https://playwright.dev/)
[![License: MIT](https://img.shields.io/badge/license-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## Overview

**CallOut** is a custom testing utility for Playwright and `pytest-bdd`. While standard automated scanners (like Axe) are excellent for identifying static rule violations, they often miss logical accessibility failures in dynamic, state-dependent web applications. 

CallOut bridges that gap by providing **State-Aware Accessibility Testing**, allowing QA engineers to verify the **Accessibility Tree** and **keyboard navigation flow** as the application state changes.

## Why Use CallOut?

Standard scanners answer: *"Is this HTML valid?"*
**CallOut** answers: *"Can a user with assistive technology actually navigate this state to complete a task?"*

| Feature | Standard Scanners | CallOut |
| :--- | :---: | :---: |
| **State Awareness** | Low | High |
| **Logic/Flow Verification** | No | Yes |
| **Test Noise** | High | Low (Marker-based) |

## Implementation

Tag your scenarios with `@accessibility_audit` to trigger the CallOut auditor:

```gherkin
@accessibility_audit
Scenario: User triggers validation error
  Given I am on the login page
  When I submit an empty username
  Then I should see an "Required" error message
