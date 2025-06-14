# Pagila OLTP to OLAP Transformation Project

## Project Overview
This project demonstrates the transformation of the Pagila database (a sample DVD rental database) from an OLTP (Online Transaction Processing) model to an OLAP (Online Analytical Processing) model. The project focuses on dimensional modeling techniques, including star schemas and snowflake schemas, to facilitate data analysis and business intelligence.

## Project Structure
- `source_database/`: Contains the original OLTP database schema and data
  - `normalized.drawio`: Database schema diagram in draw.io format
  - `normalized-pagila.jpg`: Visual representation of the OLTP schema
  - `pagila-schema.sql`: SQL script to create the database schema
  - `pagila-data.sql`: SQL script to populate the database with sample data

- `star_schemas_OLAP/`: Contains star schema designs for data marts
  - `1_sales_olap/`: Sales data mart with star schema design
    - `sales.drawio`: Star schema diagram for sales in draw.io format
    - `sales.jpg`: Visual representation of the sales star schema
  - `2_inventory_factless/`: Planned inventory data mart with factless fact table (in development)

- `flake_schemas_OLAP/`: Planned snowflake schema designs (in development)

- `docker-compose.yaml`: Configuration for running PostgreSQL and pgAdmin in Docker

## Getting Started

### Prerequisites
- Docker and Docker Compose installed on your system
- Basic understanding of SQL and database concepts

### Setting Up the Database
1. Clone this repository to your local machine
2. Navigate to the project root directory
3. Run the following command to start the PostgreSQL database and pgAdmin:
   ```
   docker-compose up -d
   ```
4. The database will be automatically initialized with the Pagila schema and data

### Accessing the Database
- **PostgreSQL Database**:
  - Host: localhost
  - Port: 5432
  - Database: pagila
  - Username: postgres
  - Password: admin

- **pgAdmin**:
  - URL: http://localhost:5050
  - Email: admin@admin.com
  - Password: root

## Dimensional Modeling
This project demonstrates the transformation from a normalized OLTP database to dimensional models for analytical processing:

### OLTP Model
The source Pagila database is a normalized OLTP database designed for efficient transaction processing. It contains tables for customers, films, rentals, payments, etc., with relationships designed to minimize data redundancy.

### Star Schema Model
The star schema model in `star_schemas_OLAP/1_sales_olap/` demonstrates a dimensional model with:
- A central fact table containing business metrics (e.g., sales amounts)
- Dimension tables connected directly to the fact table (e.g., time, customer, film)

### Snowflake Schema Model
The planned snowflake schema model in `flake_schemas_OLAP/` will demonstrate a dimensional model where dimension tables are normalized into multiple related tables.

## Learning Objectives
- Understand the differences between OLTP and OLAP database designs
- Practice dimensional modeling techniques
- Learn how to transform a normalized database into star and snowflake schemas
- Gain experience with PostgreSQL and Docker

## Contributing
Feel free to contribute to this project by implementing additional data marts, creating snowflake schemas, or adding analytical queries.

## License
This project uses the Pagila database, which is available under the PostgreSQL License.
