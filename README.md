# TaxClarity — Indian Income Tax Calculator

> A finance-focused web application that helps salaried individuals in India estimate income tax, compare the Old and New Tax Regimes, and generate a shareable PDF summary.

[![React](https://img.shields.io/badge/React-18.3-61DAFB?logo=react&logoColor=white)](https://react.dev/)
[![Vite](https://img.shields.io/badge/Vite-6-646CFF?logo=vite&logoColor=white)](https://vitejs.dev/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-3-06B6D4?logo=tailwindcss&logoColor=white)](https://tailwindcss.com/)

## Why I built this

Tax planning is often difficult to understand because the final decision depends on salary, deductions, investments, exemptions, age, other income, capital gains, and TDS. I built TaxClarity to turn that multi-step calculation into a guided experience and present the result in plain language.

The project combines **finance-domain rules, deterministic calculation logic, user-focused UI, and document generation** in one application.

## What it does

- Collects financial information through a guided multi-step flow
- Calculates estimated tax under the **Old Tax Regime** and **New Tax Regime**
- Considers salary and multiple income sources
- Handles HRA-related inputs and exemptions
- Supports common investment and insurance deductions under the Old Regime
- Handles home-loan interest and TDS inputs
- Supports specified equity/property capital-gain scenarios
- Calculates rebates, surcharge and cess where implemented by the tax engine
- Compares the regimes and identifies the lower-tax option
- Produces a PDF summary that can be saved or shared with a Chartered Accountant or finance professional

## Example user journey

```text
Financial Year
      ↓
Age & Salary
      ↓
Salary Components
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
Tax Calculation Engine
      ↓
Old Regime vs New Regime
      ↓
Recommendation + PDF Summary
```

## Tax calculation engine

The core calculation logic is separated from the UI in [`src/taxEngine.js`](src/taxEngine.js).

The engine uses pure calculation functions and centralizes tax-related constants in [`src/constants.js`](src/constants.js). This separation makes the financial rules easier to inspect, test, and update independently of the React components.

Key calculation areas include:

- Gross income calculation
- Taxable income calculation
- Standard deduction
- Old/New regime slab calculations
- HRA exemption
- Section 80C deductions
- Section 80D deductions
- NPS-related deductions
- Home-loan interest deduction
- Section 80TTA / 80TTB treatment
- Capital-gain tax treatment for supported scenarios
- Section 87A rebate
- Surcharge
- Marginal relief logic
- Health & Education Cess
- TDS and final payable/refund presentation

> **Important:** Tax legislation changes over time. The current implementation is tied to the financial year documented in the source code and should be reviewed against official tax guidance before being used for an actual filing or financial decision.

## Product design

The application intentionally uses a guided flow rather than presenting users with one large tax form. The current React application breaks the experience into dedicated steps for financial year, age, salary, income, capital gains, rent/HRA, investments, insurance, home loans, TDS, calculation, and results.

The result is designed around a practical question:

> **Which regime is better for me, and approximately how much tax will I pay?**

## AI-assisted development

This was one of my early **AI-assisted application development projects**. I used AI tools during the development process for tasks such as product planning, implementation support, UI iteration, debugging, and refining the application workflow.

The project demonstrates how I use AI as an engineering productivity tool while keeping the important domain logic explicit in the codebase.

## Architecture

```text
React UI
  │
  ├── Guided input components
  │       └── Collect financial data
  │
  ├── Application state
  │       └── User inputs + calculation state
  │
  ├── Tax Engine
  │       ├── Income calculations
  │       ├── Deductions / exemptions
  │       ├── Old Regime
  │       ├── New Regime
  │       ├── Capital gains
  │       └── Rebate / surcharge / cess
  │
  └── Results & PDF generation
          └── Shareable tax summary
```

### Design characteristics

- **Client-side:** calculations run in the browser
- **No login required:** designed as a lightweight utility
- **No backend dependency:** user inputs are not sent to a server by the application architecture
- **Deterministic rules:** financial calculations are represented explicitly in JavaScript
- **Componentized UI:** individual stages of the user journey are separated into React components

## Tech stack

| Area | Technology |
|---|---|
| Frontend | React |
| Build tool | Vite |
| Styling | Tailwind CSS |
| Language | JavaScript / JSX |
| State management | React `useState` |
| PDF / document generation | jsPDF + html2canvas |
| Tax logic | Custom JavaScript calculation engine |

## Project structure

```text
src/
├── components/
│   └── steps/              # Guided user-input and result screens
├── constants.js             # Tax slabs, limits and rates
├── taxEngine.js             # Core tax calculation logic
├── utils.js                 # Shared utilities
├── App.jsx                  # Application flow and state
├── main.jsx                 # React entry point
└── index.css                # Global styles
```

## Run locally

### Prerequisites

- Node.js
- npm

### Installation

```bash
git clone https://github.com/stharesh/tax-calculator-app.git
cd tax-calculator-app
npm install
npm run dev
```

Then open the local Vite development URL shown in the terminal.

### Production build

```bash
npm run build
npm run preview
```

## What I learned

This project helped me move beyond building a UI and work through a domain-driven application where correctness of business rules matters.

Key learning areas:

- Translating financial rules into deterministic program logic
- Separating domain logic from presentation code
- Designing multi-step data collection for complex calculations
- Handling conditional deductions and exemptions
- Comparing alternative business outcomes from the same input data
- Generating a practical document from application results
- Using AI throughout the software-development lifecycle without hiding the underlying implementation

## Future improvements

Potential next steps include:

- Automated unit-test coverage for tax-engine edge cases
- A versioned rules layer for different financial years
- Validation against a larger set of official examples
- Better treatment of additional income and capital-gain scenarios
- Automated regression tests whenever tax rules change
- Deployment with a public demo
- Accessibility and mobile UX improvements

## Disclaimer

**TaxClarity is an educational and estimation tool, not professional tax advice.** Tax rules, thresholds, deductions, rebates, and rates can change. Always verify calculations against current guidance from the Income Tax Department of India or consult a qualified Chartered Accountant before making financial decisions or filing a tax return.

## Author

**Tharesh S**

This project is part of my portfolio exploring **Data Analytics, Finance, AI-assisted development, automation, and practical software engineering**.
