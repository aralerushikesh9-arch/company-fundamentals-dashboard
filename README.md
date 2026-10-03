# Company Fundamentals Dashboard

A financial analysis dashboard for exploring company fundamentals, financial ratios, and valuation metrics using user-provided financial data.

## Features

- Financial statement and company performance analysis
- Profitability, liquidity, leverage, and return metrics
- Valuation multiples and peer comparison support
- Input validation and automated calculations
- Claude-assisted financial interpretation using the project's `skill/SKILL.md` instructions

## Project structure

```text
company-fundamentals-dashboard/
├── api/
│   └── fundamentals.js
├── public/
│   └── company_fundamentals_dash.html
├── skill/
│   └── SKILL.md
├── package.json
├── vercel.json
└── README.md
```

## Run and deploy

This project is configured for deployment on Vercel. Upload the project files to a GitHub repository, import that repository into Vercel, and follow the deployment prompts.

If the application uses an external AI service, configure the required API key as a Vercel environment variable. Never commit API keys, passwords, or `.env` files to a public repository.

## Notes

The dashboard's outputs depend on the financial data and assumptions entered by the user. Review inputs and calculations before relying on results. This project is intended for learning and financial analysis; it does not provide investment advice.
