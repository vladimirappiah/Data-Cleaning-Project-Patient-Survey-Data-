# Data-Cleaning-Project-Patient-Survey-Data-

# Creating Tables for HCAHPS

## Overview
This document provides instructions for creating database tables necessary for storing hospital data and HCAHPS (Hospital Consumer Assessment of Healthcare Providers and Systems) survey results. By the end of this guide, you will know how to:

1. Create a schema for organizing data.
2. Define and create tables for hospital beds and HCAHPS data.

## Prerequisites
- A PostgreSQL database environment is set up and accessible.
- Basic understanding of SQL commands like `CREATE TABLE` and `SCHEMA`.

## Steps

### 1. Create the Schema
Before creating tables, ensure you have a schema named `Hospital_Data` to organize your tables.

```sql
-- Create schema to organize hospital data
CREATE SCHEMA IF NOT EXISTS "Hospital_Data";
```

### 2. Create the `hospital_beds` Table
The `hospital_beds` table stores information about hospital bed availability, including provider identifiers, hospital names, fiscal years, and the number of beds.

```sql
CREATE TABLE IF NOT EXISTS "postgres"."Hospital_Data".hospital_beds
(
     provider_ccn integer,
     hospital_name character varying(255),
     fiscal_year_begin_date character varying(10),
     fiscal_year_end_date character varying(10),
     number_of_beds integer
);
```

### 3. Create the `HCAHPS_data` Table
The `HCAHPS_data` table captures patient survey responses, facility details, and response metrics.

```sql
CREATE TABLE IF NOT EXISTS "postgres"."Hospital_Data".HCAHPS_data
(
    facility_id character varying(10),
    facility_name character varying(255),
    address character varying(255),
    city character varying(50),
    state character varying(2),
    zip_code character varying(10),
    county_or_parish character varying(50),
    telephone_number character varying(20),
    hcahps_measure_id character varying(255),
    hcahps_question character varying(255),
    hcahps_answer_description character varying(255),
    hcahps_answer_percent integer,
    num_completed_surveys integer,
    survey_response_rate_percent integer,
    start_date character varying(10),
    end_date character varying(10)
);
```

## Notes
- **Schema Requirement:** Ensure the schema `Hospital_Data` is created before running these `CREATE TABLE` statements.
- **Data Types:** The `character varying` data type is used for fields with variable text length, while `integer` is used for numerical values.
- **Safety:** The `IF NOT EXISTS` clause prevents errors if the table already exists.

## Example Usage
After creating the tables, you can populate them with data using `INSERT` statements or by importing CSV files.

```sql
-- Example Insert into hospital_beds table
INSERT INTO "postgres"."Hospital_Data".hospital_beds 
(provider_ccn, hospital_name, fiscal_year_begin_date, fiscal_year_end_date, number_of_beds)
VALUES 
(123456, 'Example Hospital', '2023-01-01', '2023-12-31', 150);
```

## Resources
- [PostgreSQL Documentation](https://www.postgresql.org/docs/)
- [HCAHPS Information](https://www.hcahpsonline.org/)

## Author
Created by me for managing hospital data efficiently.
