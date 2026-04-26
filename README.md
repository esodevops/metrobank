# MetroBank SQL Project

A PostgreSQL practice project containing schema definition, data loading scripts, and CSV source data for a core banking domain.

## Project Structure

- `DDL.sql` - Data Definition Language script for creating and modifying tables.
- `DML.sql` - Data Manipulation Language script with sample inserts.
- `DQL.sql` - Data Query Language script (currently empty, ready for analysis queries).
- `metrobank_csvs/` - CSV datasets:
  - `accounts.csv`
  - `branches.csv`
  - `customers.csv`
  - `employees.csv`
  - `loans.csv`
  - `transactions.csv`

## Data Model (Current)

Main entities in the schema:

- Branches
- Customers
- Employees
- Accounts
- Transactions
- Loans

Key relationships:

- employees.branch_id -> branches.branch_id
- accounts.customer_id -> customers.customer_id
- accounts.branch_id -> branches.branch_id
- transactions.account_no -> accounts.account_no
- loans.customer_id -> customers.customer_id
- loans.account_no -> accounts.account_no

## Prerequisites

- PostgreSQL 13+ (or compatible)
- psql CLI

## Quick Start

1. Create a database:

```sql
CREATE DATABASE metrobank;
```

2. Connect to the database:

```bash
psql -d metrobank
```

3. Run schema script:

```bash
\i DDL.sql
```

4. Run sample data script:

```bash
\i DML.sql
```

5. (Optional) Add query scripts in `DQL.sql` and run:

```bash
\i DQL.sql
```

## Notes

- `DDL.sql` currently includes create, alter, truncate, and drop examples.
- If you run full `DDL.sql` repeatedly, be aware of constraint and drop/truncate sections near the end.
- `DML.sql` contains manual insert statements for sample records.

## Suggested Next Improvements

- Add an ERD image and table-level documentation.
- Split DDL into idempotent setup and teardown scripts.
- Add staging-table CSV import pipeline using `COPY`.
- Add indexes and audit triggers for production-style workflows.
