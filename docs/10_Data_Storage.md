# Data Storage

## Purpose

Storage is not just a technical detail. It defines whether this product can become a reusable client platform or only a one-time demo.

The product should separate display, calculation, client records, adviser notes, and uploaded source documents.

## Storage layers

```text
Source Documents
        ↓
Extracted Financial Data
        ↓
Calculated Metrics
        ↓
Dashboard Views
        ↓
Review Notes and Recommendations
```

## V1 storage approach

For the first prototype, keep storage simple.

Use local JSON files or mock data modules.

Suggested structure:

```text
/data
├── clients.json
├── financial-summary.json
├── net-worth.json
├── cash-flow.json
├── protection.json
├── goals.json
├── recommendations.json
└── assumptions.json
```

V1 should prove the experience first. Do not build a complex backend too early.

## V2 storage approach

Once the UI is validated, move to a real database.

Suggested entities:

- Client
- Household
- Review
- Goal
- Asset
- Liability
- CashFlowItem
- InsurancePolicy
- InvestmentAccount
- CPFAccount
- MetricSnapshot
- Recommendation
- AdviserNote
- UploadedDocument
- SimulationScenario

## Client

Stores basic client profile.

Suggested fields:

- id
- fullName
- dateOfBirth
- residencyStatus
- occupation
- annualIncome
- adviserId
- createdAt
- updatedAt

## Review

A review represents one financial health report cycle.

Suggested fields:

- id
- clientId
- reviewDate
- reviewYear
- status
- sourceDocumentId
- overallScore
- summaryInsight
- createdAt
- updatedAt

## Goal

Stores financial goals.

Suggested fields:

- id
- clientId
- reviewId
- type
- title
- targetAmount
- currentAmount
- targetDate
- priority
- fundingGap
- successProbability
- notes

## Asset

Stores assets by category.

Suggested fields:

- id
- clientId
- reviewId
- category
- name
- value
- source
- liquidityLevel
- notes

Examples of categories:

- Cash
- CPF OA
- CPF SA
- CPF MA
- Unit Trust
- Stocks
- Insurance Cash Value
- Property
- Business
- Personal Asset

## Liability

Stores debts and obligations.

Suggested fields:

- id
- clientId
- reviewId
- category
- name
- outstandingAmount
- monthlyPayment
- interestRate
- endDate
- notes

## CashFlowItem

Stores income and expenses.

Suggested fields:

- id
- clientId
- reviewId
- direction
- category
- name
- monthlyAmount
- annualAmount
- paymentSource
- isFixed
- notes

Direction:

- inflow
- outflow

Payment source:

- cash
- CPF
- CPF OA
- Medisave

## InsurancePolicy

Stores protection plans and savings or investment-linked plans.

Suggested fields:

- id
- clientId
- reviewId
- provider
- planName
- policyType
- startDate
- premiumAmount
- premiumFrequency
- paymentSource
- benefitType
- sumAssured
- status
- remarks

Benefit types:

- Hospital
- Life
- TPD
- Critical Illness
- Early Critical Illness
- Disability Income
- Personal Accident
- Savings
- Investment
- Passive Income

## MetricSnapshot

Stores calculated dashboard metrics for each review.

Suggested fields:

- id
- clientId
- reviewId
- metricName
- metricValue
- benchmarkValue
- status
- explanation
- createdAt

Examples:

- Emergency Fund Months
- Savings Rate
- Debt to Asset
- Monthly Debt Commitment
- Net Investment Assets Ratio
- Cash Annual Surplus
- CPF Annual Surplus

## Recommendation

Stores action items.

Suggested fields:

- id
- clientId
- reviewId
- timing
- title
- reason
- priority
- impact
- effort
- relatedSection
- status
- adviserNote

Timing:

- Now
- Next
- Later

## SimulationScenario

Stores what-if scenarios.

Suggested fields:

- id
- clientId
- reviewId
- scenarioName
- assumptions
- resultSummary
- riskLevel
- createdAt

Examples:

- Income stops for 6 months
- Retire at 55
- Lower investment return
- Higher inflation
- Major illness

## UploadedDocument

Stores source documents and parsed extraction metadata.

Suggested fields:

- id
- clientId
- fileName
- fileType
- storagePath
- uploadedAt
- extractionStatus
- extractedTextVersion
- checksum

## Important privacy rule

Do not store real NRIC, full policy numbers, or sensitive identifiers in the prototype.

For demo, use masked or fake data.

Example:

- S****123A
- Policy ending 1234

## Versioning

Every annual review should be stored as a separate Review record.

Do not overwrite last year's data.

This is needed for:

- What changed since last review
- Trend chart
- Net worth growth
- Cash flow movement
- Protection changes
- Recommendation history

## Audit trail

For a serious product, store important changes.

Examples:

- Who changed the data
- When it was changed
- What field changed
- Previous value
- New value

## Do not overbuild too early

For V1, avoid building login, database, document upload, OCR, or complex permission system before the dashboard experience is proven.

Recommended V1 order:

1. Static mock data
2. Interactive dashboard
3. Clear data model
4. Import from JSON
5. Backend only after the prototype is validated

## Brutal product warning

Bad storage design will make the product impossible to scale.

But overbuilding storage before validating the user experience will also kill momentum.

The correct move is to define the data model clearly now, then implement the simplest version first.
