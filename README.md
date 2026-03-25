# Deal Sorter and Analyzer

Powerful M&A deal analysis and comparable company research platform for private equity teams.

## What it does

This application helps PE/VC M&A teams analyze deals, sort financial data, run business analysis, research comparable transactions, and compare similar companies. Built specifically for investment professionals who need secure, comprehensive deal evaluation tools with seamless integration to their existing workflow.

## Who it's for

- **Analysts**: Import and analyze deal data, generate comps
- **Associates**: Create financial models and scoring matrices  
- **Partners**: Review dashboards and investment committee materials

## Tech Stack

- **Frontend**: Next.js 15, TypeScript, Tailwind CSS
- **Backend**: Supabase (PostgreSQL + Auth + RLS)
- **Integrations**: Salesforce, QuickBooks, Google Sheets, Airtable, Zapier, Notion, BigQuery
- **Deployment**: Vercel

## Prerequisites

- Node.js 18+ and npm
- Supabase CLI installed globally: `npm install -g supabase`
- Git

## Local Development Setup

1. **Clone and install dependencies**:
   bash
   git clone <repo-url>
   cd deal-sorter-analyzer
   npm install
   

2. **Environment setup**:
   bash
   cp .env.example .env.local
   # Fill in your environment variables (see table below)
   

3. **Start Supabase**:
   bash
   supabase start
   

4. **Run development server**:
   bash
   npm run dev
   

5. **Open** http://localhost:3000

## Environment Variables

| Variable | Description | Required |
|----------|-------------|---------|
| `NEXT_PUBLIC_SUPABASE_URL` | Supabase project URL | Yes |
| `NEXT_PUBLIC_SUPABASE_ANON_KEY` | Supabase anonymous key | Yes |
| `SUPABASE_SERVICE_ROLE_KEY` | Supabase service role key (server-side only) | Yes |
| `SALESFORCE_CLIENT_ID` | Salesforce OAuth client ID | Yes |
| `SALESFORCE_CLIENT_SECRET` | Salesforce OAuth client secret | Yes |
| `QUICKBOOKS_CLIENT_ID` | QuickBooks OAuth client ID | Yes |
| `QUICKBOOKS_CLIENT_SECRET` | QuickBooks OAuth client secret | Yes |
| `GOOGLE_SHEETS_API_KEY` | Google Sheets API key | Yes |
| `AIRTABLE_API_KEY` | Airtable personal access token | Yes |
| `ZAPIER_WEBHOOK_SECRET` | Zapier webhook verification secret | Yes |
| `NOTION_API_KEY` | Notion integration token | Yes |
| `BIGQUERY_PROJECT_ID` | BigQuery project identifier | Yes |
| `BIGQUERY_PRIVATE_KEY` | BigQuery service account private key | Yes |
| `NEXTAUTH_SECRET` | NextAuth.js secret for session encryption | Yes |
| `NEXTAUTH_URL` | Application base URL | Yes |

## Database Setup

The database schema includes 12 tables for comprehensive deal management:

bash
# Apply migrations
supabase db reset

# Or for production
supabase db push


**Core tables**: users, companies, deals, financial_data, financial_ratios, comparable_analyses, deal_scoring_criteria, deal_scores, historical_transactions, financial_models, integration_configs, sync_logs

## Deploy to Vercel

1. **Connect repository** to Vercel
2. **Configure environment variables** in Vercel dashboard
3. **Deploy** — automatic deployments on push to main

## Project Structure


├── app/                    # Next.js 15 app directory
│   ├── (auth)/            # Authentication pages
│   ├── (dashboard)/       # Protected dashboard pages
│   ├── api/               # API routes
│   └── globals.css        # Global styles
├── components/            # Reusable UI components
├── lib/                   # Business logic and utilities
├── db/                    # Database access layer
├── actions/               # Server actions
├── types/                 # TypeScript type definitions
├── supabase/              # Supabase configuration
└── public/                # Static assets


## Getting Help

- Check CLAUDE.md for AI coding session guidelines
- Review TECHNICAL_DEBT.md for known limitations
- See ROADMAP.md for planned features