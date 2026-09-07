# TaxClarity — Indian Income Tax Calculator

> A finance-focused web application that helps salaried individuals in India estimate income tax, compare the Old and New Tax Regimes, and generate a shareable PDF summary.

**🚀 [Live Demo — Indian Tax Calculator (FY 2025-26)](https://tax-calculator-app-wugm.vercel.app/)**

[![React](https://img.shields.io/badge/React-18.3-61DAFB?logo=react&logoColor=white)](https://react.dev/)
[![Vite](https://img.shields.io/badge/Vite-6-646CFF?logo=vite&logoColor=white)](https://vitejs.dev/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-3-06B6D4?logo=tailwindcss&logoColor=white)](https://tailwindcss.com/)
[![Live Demo](https://img.shields.io/badge/Live-Demo-success)](https://tax-calculator-app-wugm.vercel.app/)

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

## 🤖 AI-Native / Vibe-Coded Development

This was one of my first **AI-native application development projects**, built using a "vibe coding" workflow.

I used **Google Gemini Pro through Antigravity** as the primary development partner. Instead of manually implementing the entire application from scratch, I drove development through natural-language prompts, product requirements, financial rules, expected behavior, iterative feedback, debugging requests, UI refinement, and feature requests.

My primary contribution was defining the **business problem, finance-domain requirements, user experience, expected behavior, acceptance criteria, and validation needs**, while AI generated, modified, debugged, and refined much of the implementation.

The important part of the workflow was not simply asking AI to "build an app." It was an iterative process of specifying the requirement, reviewing the result, identifying gaps or incorrect behavior, prompting targeted changes, running the application, validating the calculations and UX, and repeating the cycle.

### Development workflow

```text
Business Problem
      ↓
Research & Requirements
      ↓
Financial Rules + Expected Behaviour
      ↓
Prompts / Product Specifications
      ↓
Gemini Pro + Antigravity
      ↓
Generated Implementation
      ↓
Run / Inspect / Test
      ↓
Identify Issues & Edge Cases
      ↓
Prompt-Based Refinement
      ↓
Validate Tax Calculations & UX
      ↓
Deploy
```

### What this project demonstrates

- Translating a finance problem into structured software requirements
- Researching and representing domain rules in an application
- Breaking a complex product into manageable development steps
- Writing effective prompts and specifications for AI coding tools
- Reviewing and iterating on AI-generated implementation
- Debugging through an AI-assisted development loop
- Validating business outputs instead of blindly trusting generated code
- Using AI as a development accelerator across planning, implementation, debugging, and refinement
- Moving from **idea → requirements → working application → iteration → deployment**

This repository is **not presented as evidence of deep React expertise**. It demonstrates something different and increasingly important: the ability to take a real-world domain problem, communicate requirements precisely, use modern AI development tools effectively, evaluate their output, and drive a working application to completion.

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

| Area | Technology | How it was used |
|---|---|---|
| Frontend | React | AI-assisted application implementation and iterative refinement |
| Build tool | Vite | Development and production build tooling |
| Styling | Tailwind CSS | AI-assisted UI implementation and refinement |
| Language | JavaScript / JSX | Application and calculation logic |
| State management | React `useState` | Guided application flow and user-input state |
| PDF / document generation | jsPDF + html2canvas | Generate a shareable tax summary |
| Tax logic | Custom JavaScript calculation engine | Explicit finance-domain calculations |
| AI development | Google Gemini Pro + Antigravity | Planning, implementation, debugging, refinement, and iteration |
| Deployment | Vercel | Public live application deployment |

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

## Deployment

The application is deployed as a public web application on **Vercel**.

**Live application:** [tax-calculator-app-wugm.vercel.app](https://tax-calculator-app-wugm.vercel.app/)

## What I learned

This project helped me move beyond building a UI and work through a domain-driven application where correctness of business rules matters.

Key learning areas:

- Translating financial rules into deterministic program logic
- Separating domain logic from presentation code
- Designing multi-step data collection for complex calculations
- Handling conditional deductions and exemptions
- Comparing alternative business outcomes from the same input data
- Generating a practical document from application results
- Using AI throughout the software-development lifecycle
- Writing requirements and prompts that guide AI toward a specific business outcome
- Reviewing and validating AI-generated implementation rather than treating AI output as automatically correct

## Future improvements

Potential next steps include:

- Automated unit-test coverage for tax-engine edge cases
- A versioned rules layer for different financial years
- Validation against a larger set of official examples
- Better treatment of additional income and capital-gain scenarios
- Automated regression tests whenever tax rules change
- Accessibility and mobile UX improvements
- A more formal test suite for AI-generated changes

## Disclaimer

**TaxClarity is an educational and estimation tool, not professional tax advice.** Tax rules, thresholds, deductions, rebates, and rates can change. Always verify calculations against current guidance from the Income Tax Department of India or consult a qualified Chartered Accountant before making financial decisions or filing a tax return.

## Author

**Tharesh S**

This project is part of my portfolio exploring **Data Analytics, Finance, AI-assisted development, automation, and practical software engineering**.
