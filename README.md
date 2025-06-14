# Pagila OLTP to OLAP data project

This project demonstrates the end-to-end process of transforming a classic transactional database (OLTP) into an analytical data warehouse (OLAP). Starting with the standard Pagila DVD rental database, this repository contains the dimensional models (Star Schema), the SQL scripts, and a fully containerized environment to reproduce the entire setup.

## Project Structure
```
.
├── README.md
├── docker-compose.yaml                    
├── source_database              
│   ├── normalized-pagila.jpg    
│   ├── normalized.drawio        
│   ├── pagila-data.sql          
│   └── pagila-schema.sql        
└── star_schemas_OLAP            
    └── 1_sales_olap             
        ├── sales.drawio         
        └── sales.jpg            
     
```


## Key Concepts & Skills Demonstrated

* **Dimensional Modeling**: Designing and implementing data models optimized for business intelligence and analytics.
* **Star Schema**: Building a simple, high-performance schema with a central fact table and denormalized dimensions.
* **OLTP vs. OLAP**: Understanding and articulating the architectural differences between transactional and analytical systems.
* **Data Warehouse Design**: Creating the foundational structures for a data warehouse.
* **Slowly Changing Dimensions (SCD Type 2)**: Implementing a strategy to track the historical changes of dimension attributes, preserving a full history.
* **Database Containerization**: Using Docker and Docker Compose to create a reproducible and isolated database environment.
* **Advanced Modeling Concepts**: Planning for future extensions like Factless Fact Tables and Snowflake Schemas.

## Data Models

### 1. Source: Normalized OLTP Schema
The project starts with the original Pagila database, which is highly normalized (3NF) to ensure data integrity and reduce redundancy for transactional operations.

<img src="https://github.com/NebylytsiaKyrylo/pagila_oltp_to_olap/blob/75dc20e5d294f26495aedeba291bfae8f818e7b3/source_database/normalized-pagila.jpg" alt="Normalized OLTP Schema"/>

### 2. Target: Denormalized Star Schema (Sales Data Mart)
For analytics, the data is remodeled into a Star Schema. This design denormalizes dimensions to reduce complex joins and drastically improve query performance for analytical workloads. This model also incorporates SCD Type 2 principles to track the history of changes in dimensions like customers or stores.

<img src="https://github.com/NebylytsiaKyrylo/pagila_oltp_to_olap/blob/75dc20e5d294f26495aedeba291bfae8f818e7b3/star_schemas_OLAP/1_sales_olap/sales.jpg" alt="Denormalized Star Schema (Sales Data Mart)"/>

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
 
## Future Work
- [ ] Implement the SQL `CREATE TABLE` scripts for the schemas.
- [ ] Design and implement the "Inventory Factless Fact Table", Flake Schema.
- [ ] Develop SQL scripts to populate schemas from the source database.
