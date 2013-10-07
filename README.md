# Data Manager

A tool to view normalization state of a database and help modify tables / columns to attain a desired Normal Form.

Developers can:
* Run this on your DB to find any inconsistencies (detect mode)
* Parse flattened data through it's API (REST) and get normalized arrays returned (act mode)
Administrators can:
* Run this to find compliance with 3rd normalization requirements 
* Use the tool to clone a DB into a new normalized or intentional de-normalized version of itself
* Store configuration from such a conversion job
* Use the tool as ETL to routinely transfer data (Incremental is not handled in current release.)

### Technical Objectives ###

- [ ] Full JavaScript Stack
- [ ] TDD with agile approach
- [ ] Rules based approach
- [ ] Convention over configuration with over-ride
- [ ] Restful API
- [ ] Command line interface

## Detailed Scope (Product Backlog)

### Use Cases
1. Read DB and get all structure (meta-data) information including
	1. Table and column names and types
	1. Foreign Key relationships
	1. Primary Key relationships
	1. Unique constraints (indexes)
1. Show tables with sample data in grid
1. Show relationships with in grid
1. Show relationships in an ER diagram
1. Allow user to modify relationships
1. Allow user to modify table names
1. Allow user to modify column names
1. Tell user the current Normal Form of database from the following options:
	1. 1 NF
	1. 2 NF
	1. 3 NF
	1. BCNF (3.5 NF)
	1. 4 NF, 5 NF, DKNF and 6 NF are left out for a future release
1. Allow user to clone the DB to a new form, the user can also goto a lower Normal Form
1. Allow user to save transformation configuration
1. Allow user to save connection configuration
1. Allow user to pass in configuration on CLI call

### Assumptions (Convention)
1. id (int 11), primary_id, unid (char 32 or char 36) named columns are considered PK for the table
1. For non transactional databases, FK columns are structured with double underscore like subjects__id
1. Underscore is the naming convention followed in database for eg. first_name
1. All columns with double underscore are considered dependent on a foreign table
1. Columns starting with underscore are considered for caching purposes and are not processed by the system. For eg. a subjects__id might be followed by a _subjects__name
1. Foreign key prefix is exactly the same spelling as it's associated table name without any singularization or pluralization

### Out of scope
1. does not handle composite primary keys
1. incremental data loading in ETL mode

## Releases (Sprint Backlog)
1. Express.js with CLI in detect mode
1. Express.js with CLI in act mode
1. Rest API
1. Basic responsive UI using Backbone.js
1. Drag-drop on grids and advanced UI features
1. ER diagrams (view mode)
1. Drag-drop on ER diagrams
