# TaxClarity — Indian Income Tax Calculator

A guided tax-planning application for salaried individuals in India. Enter your financial details, estimate tax under the Old and New Tax Regimes, compare the results, and generate a shareable PDF summary.

**🚀 [Live Demo — Indian Tax Calculator (FY 2025-26)](https://tax-calculator-app-wugm.vercel.app/)**

> **Important:** TaxClarity is an educational and estimation tool, not professional tax advice. Tax rules can change. Verify results against current guidance from the Income Tax Department of India or consult a qualified Chartered Accountant before making financial decisions or filing a tax return.

## What Problem Does It Solve?

Tax calculations can become difficult to navigate because the result depends on many inputs — salary, other income, HRA, investments, insurance, home loans, TDS, capital gains, and the selected tax regime.

TaxClarity turns that complexity into a guided experience and presents the outcome in a form that is easier to understand and compare.

## What You Can Do

### Guided Tax Calculation

Instead of presenting users with one large tax form, the application walks through the information step by step.

Users can provide relevant details about:

- Financial year and age group
- Salary and salary components
- Other and side income
- Capital gains
- Rent and HRA
- Tax-saving investments
- Health insurance
- Home loans
- TDS

### Compare Old vs New Regime

The application calculates the estimated tax under both supported regimes using the same financial information.

The results make it easy to see:

- Estimated tax under each regime
- Difference between the two outcomes
- Which regime produces the lower estimated tax for the entered scenario
- Potential savings from the comparison

### Handle Common Tax Inputs

The calculation flow supports a range of scenarios, including:

- Standard deductions
- HRA-related calculations
- Section 80C investments
- Health insurance deductions
- NPS-related deductions
- Home-loan interest
- Savings and deposit interest
- Supported equity and property capital-gain scenarios
- Rebates, surcharge and cess
- TDS and estimated refund/payable position

### Generate a Shareable Summary

After completing the calculation, users can generate a PDF summary of the results.

The summary can be saved or shared for discussion with a Chartered Accountant or other finance professional.

## User Journey

~~~text
Your Financial Details
        ↓
Income & Salary
        ↓
Other / Side Income
        ↓
Capital Gains
        ↓
Rent & HRA
        ↓
Investments & Insurance
        ↓
Home Loan & TDS
        ↓
Tax Calculation
        ↓
Old Regime vs New Regime
        ↓
Tax Summary
        ↓
Download / Share PDF
~~~

The goal is to turn a complicated calculation into a clear sequence of questions followed by an understandable result.

## Product Experience

The application is designed around a practical question:

> **How much tax might I pay, and which supported tax regime results in the lower estimated tax for my situation?**

The experience therefore emphasizes:

- Simple step-by-step data collection
- Clear progress through the calculation
- A direct comparison of the two regimes
- A concise result after completing the required inputs
- A downloadable summary for further discussion

## Calculation Engine

The financial rules are separated from the user interface in src/taxEngine.js, with tax-related constants maintained separately.

The calculation engine covers the supported income, deduction, exemption, regime, capital-gain, rebate, surcharge, cess and TDS scenarios.

This separation allows the product experience and the underlying financial rules to be maintained independently.

## AI-Assisted Development

TaxClarity was built using an **AI-assisted / vibe-coding workflow**.

AI was used extensively for implementation, iteration, debugging and UI refinement, while development was driven by the product requirements, financial-domain rules, expected behavior and validation of the resulting application.

The project demonstrates taking a domain-specific idea through:

~~~text
Problem
  ↓
Requirements
  ↓
Financial Rules
  ↓
AI-Assisted Implementation
  ↓
Testing & Validation
  ↓
Iteration
  ↓
Deployment
~~~

The emphasis is on the resulting working product and the process of refining it against real-world requirements.

## Live Application

**[Open TaxClarity — FY 2025-26](https://tax-calculator-app-wugm.vercel.app/)**

The application is deployed publicly on Vercel and can be used directly in the browser.

## Run Locally

### Prerequisites

- Node.js
- npm

### Installation

~~~bash
git clone https://github.com/stharesh/tax-calculator-app.git
cd tax-calculator-app
npm install
npm run dev
~~~

Then open the local Vite development URL shown in the terminal.

### Production Build

~~~bash
npm run build
npm run preview
~~~

## Current Scope

TaxClarity currently focuses on supported FY 2025-26 scenarios for salaried users.

The application is a client-side estimation tool and does not require:

- Login
- A backend service
- A database

The supported tax scenarios and rules are represented in the application's calculation engine and should be reviewed whenever tax legislation changes.

## Future Improvements

Possible next steps include:

- Automated test coverage for tax-engine edge cases
- Versioned rules for multiple financial years
- Regression testing against official examples
- Expanded income and capital-gain scenarios
- Accessibility and mobile UX improvements
- Automated validation when tax rules change

## Project Structure

~~~text
src/
├── components/
│   └── steps/              # Guided input and result screens
├── constants.js            # Tax rules, limits and rates
├── taxEngine.js            # Core calculation logic
├── utils.js                # Shared utilities
├── App.jsx                 # Application flow and state
├── main.jsx                # React entry point
└── index.css               # Global styles
~~~

## Disclaimer

**TaxClarity is an educational and estimation tool, not professional tax advice.**

Tax rules, thresholds, deductions, rebates and rates can change. Always verify calculations against current guidance from the Income Tax Department of India or consult a qualified Chartered Accountant before making financial decisions or filing a tax return.

## Author

**Tharesh S**

This project is part of my portfolio exploring **Data Analytics, Finance, AI-assisted development, automation, and practical software products**.
