# CLAUDE.md — Deal Sorter and Analyzer

## Project Overview
A secure M&A deal analysis platform for private equity teams that integrates with Salesforce, QuickBooks, and other data sources to provide comparable company analysis, financial modeling, and deal scoring capabilities. Built with Next.js 15, Supabase, and enterprise-grade security for handling sensitive financial data.

## Tech Stack
- Next.js 15 (App Router, Server Components)
- TypeScript (strict mode)
- Supabase (PostgreSQL, Auth, RLS)
- Tailwind CSS
- Integrations: Salesforce, QuickBooks, Google Sheets, Airtable, Zapier, Notion, BigQuery

## Folder Structure

/app                    # Next.js App Router
  /(auth)              # Public auth pages: login, signup, forgot-password
  /(dashboard)         # Protected pages: dashboard, deals, analysis, scoring, export, reports
  /api                 # API routes for integrations and data
  /globals.css         # Global Tailwind imports
/components            # Reusable UI components organized by feature
  /ui                  # Base UI components (buttons, forms, charts)
  /auth               # Authentication components
  /dashboard          # Dashboard-specific components
  /deals              # Deal management components
  /analysis           # Analysis and comparison components
/lib                   # Business logic, utilities, API clients
  /integrations       # External API clients (Salesforce, QuickBooks, etc.)
  /utils              # Helper functions
  /validations        # Zod schemas
/db                    # Database access layer ONLY
  /queries            # Database queries
  /mutations          # Database mutations
/actions              # Server actions for forms and mutations
/types                # TypeScript type definitions
/supabase             # Supabase config, migrations, types


## Coding Conventions
- TypeScript strict mode enabled — no `any` types
- Server Components by default, Client Components only when needed
- All database access goes in /db directory
- Business logic goes in /lib and /actions
- No API keys or secrets in client components
- Use Zod for all data validation
- Tailwind for styling, no custom CSS unless absolutely necessary
- Follow Next.js 15 conventions: Server Actions for mutations, parallel routes for complex layouts

## Current State
Project scaffold is generated with:
- Complete data model (12 tables) set up in Supabase
- Authentication system with role-based access (Analyst, Partner, Associate)
- 23 route stubs matching the site map
- Integration stubs for all 7 external services
- Basic UI components and layout structure
- TypeScript types generated from database schema

## What to Build Next - v1 Features
1. **Salesforce deal data import** - Automatic field mapping for company financials, revenue, EBITDA, transaction details
2. **Comparable company analysis generator** - Industry peers based on SIC codes, revenue size, geography with side-by-side metrics
3. **Financial ratio calculator dashboard** - PE metrics like EV/Revenue, EV/EBITDA, P/E ratios with visual charts
4. **Deal scoring matrix** - Customizable weighting for market size, competitive position, management quality, financial performance
5. **Financial model export to QuickBooks** - Pre-built templates for DCF analysis, LBO modeling, portfolio tracking
6. **Historical M&A transaction database** - Filter by industry, deal size, transaction type, time period for precedent analysis

## Never Touch Rules
- Never modify .env files without explicit instruction
- Never alter migration files without explicit instruction
- Never modify RLS policies without security review
- Never commit API keys or secrets
- Never bypass TypeScript strict mode

## How to Work on This Project
1. **Always read this file first** before starting any work session
2. **Run `npm run build`** before committing to catch TypeScript errors
3. **Commit small and often** with conventional commit messages (feat:, fix:, docs:, etc.)
4. **Document technical debt explicitly** in TECHNICAL_DEBT.md
5. **Test integrations carefully** — this handles sensitive financial data
6. **Verify RLS policies** before deploying — data security is critical
7. **Use Server Actions** for all form submissions and mutations
8. **Keep client components minimal** — most logic should be server-side

## Security Notes
- This application handles sensitive M&A data — security is paramount
- All database access is protected by Row Level Security (RLS)
- Role-based access control is enforced at database level
- Integration credentials are server-side only
- Data export features require additional audit logging