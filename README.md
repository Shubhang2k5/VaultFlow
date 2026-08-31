# VaultFlow, A Fintech Banking Platform

A full-stack financial management application built with Next.js and TypeScript. The application provides a unified interface for connecting bank accounts, viewing balances and transactions, analyzing spending, and initiating transfers.

## Overview

The platform integrates banking and payment services to provide a centralized financial dashboard. Users can authenticate securely, connect multiple bank accounts, view account information and transaction history, and transfer funds between supported accounts.

## Technology Stack

- Next.js
- TypeScript
- Appwrite
- Plaid
- Dwolla
- React Hook Form
- Zod
- Tailwind CSS
- Chart.js
- ShadCN

## Features

- Secure server-side authentication with validation and authorization
- Multiple bank account integration through Plaid
- Consolidated account balances and financial overview
- Recent transaction history with pagination and filtering
- Spending breakdown by category
- Detailed information for connected bank accounts
- Synchronization of account and transaction data
- Fund transfers through Dwolla
- Responsive interface for desktop, tablet, and mobile devices

## Project Setup

### Prerequisites

Install the following before running the application:

- Git
- Node.js
- npm

### Installation

Clone the repository and install dependencies:

```bash
git clone <repository-url>
cd <project-directory>
npm install
```

### Environment Variables

Create a `.env` file in the project root and configure the following variables:

```env
# Next.js
NEXT_PUBLIC_SITE_URL=

# Appwrite
NEXT_PUBLIC_APPWRITE_ENDPOINT=https://cloud.appwrite.io/v1
NEXT_PUBLIC_APPWRITE_PROJECT=
APPWRITE_DATABASE_ID=
APPWRITE_USER_COLLECTION_ID=
APPWRITE_BANK_COLLECTION_ID=
APPWRITE_TRANSACTION_COLLECTION_ID=
APPWRITE_SECRET=

# Plaid
PLAID_CLIENT_ID=
PLAID_SECRET=
PLAID_ENV=sandbox
PLAID_PRODUCTS=auth,transactions,identity
PLAID_COUNTRY_CODES=US,CA

# Dwolla
DWOLLA_KEY=
DWOLLA_SECRET=
DWOLLA_BASE_URL=https://api-sandbox.dwolla.com
DWOLLA_ENV=sandbox
```

Use valid credentials for the configured Appwrite, Plaid, and Dwolla environments. Keep all secrets in environment variables and do not commit the `.env` file to version control.

### Run Locally

Start the development server:

```bash
npm run dev
```

The application will be available at:

```text
http://localhost:3000
```

## Integrations

### Appwrite

Appwrite is used for authentication and application data storage. User profiles and connected bank information are persisted in the configured database collections.

### Plaid

Plaid provides bank-account connectivity and financial data. It is used to create Link sessions, exchange public tokens, retrieve account information, and synchronize transactions.

### Dwolla

Dwolla handles customer creation, funding-source configuration, and account-to-account transfers. The application is configured to use Dwolla's sandbox environment by default.

## Data Flow

1. A user creates an account and signs in through Appwrite.
2. A Plaid Link session is created for connecting a bank account.
3. The Plaid public token is exchanged for an access token.
4. Account information is retrieved and associated with the authenticated user.
5. Plaid account and transaction data is synchronized with the application.
6. Dwolla funding sources are configured using the relevant Plaid processor information.
7. Transfer requests are submitted through Dwolla and recorded as application transactions.

## Core Application Components

The project contains server actions and reusable components responsible for:

- Authentication and user management
- Bank account retrieval and management
- Plaid token exchange and transaction synchronization
- Dwolla customer and funding-source management
- Fund transfers
- Transaction creation and retrieval
- Bank selection and account display
- Transaction pagination
- Spending-category visualization
- Form validation and submission

## Security Considerations

- Sensitive credentials are supplied through environment variables.
- Authentication sessions use secure, HTTP-only cookies.
- Server-side actions handle operations involving external financial services.
- Account identifiers used for sharing are protected through application-level encryption utilities.
- Production deployments should use production credentials and secure configuration appropriate for the selected financial-service providers.
