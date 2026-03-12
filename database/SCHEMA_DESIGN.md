# Database Schema Design

## Table of Contents
1. [Entity Relationship Diagram (ERD)](#entity-relationship-diagram-erd)
2. [Table Structures](#table-structures)
3. [Relationships](#relationships)

## Entity Relationship Diagram (ERD)
![ERD for PostGIS integration](link_to_your_erd_image)

## Table Structures
### Land Parcels
| Field Name      | Data Type | Description                  |
|------------------|-----------|------------------------------|
| id               | serial    | Unique ID for the parcel     |
| geometry         | geometry  | Geospatial data (PostGIS)   |
| owner_id         | integer   | ID of the owner              |
| created_at       | timestamp | Creation timestamp            |
| updated_at       | timestamp | Last updated timestamp        |

### Easements
| Field Name      | Data Type | Description                  |
|------------------|-----------|------------------------------|
| id               | serial    | Unique ID for the easement   |
| parcel_id        | integer   | Associated land parcel ID     |
| geometry         | geometry  | Geospatial data (PostGIS)    |
| created_at       | timestamp | Creation timestamp            |
| updated_at       | timestamp | Last updated timestamp        |

### PAPs (Project Affected Persons)
| Field Name      | Data Type | Description                  |
|------------------|-----------|------------------------------|
| id               | serial    | Unique ID for PAP            |
| name             | varchar   | Name of the affected person   |
| parcel_id        | integer   | Associated land parcel ID     |
| impact_description| text      | Description of the impact     |
| created_at       | timestamp | Creation timestamp            |
| updated_at       | timestamp | Last updated timestamp        |

### RAP (Resettlement Action Plan Status)
| Field Name      | Data Type | Description                  |
|------------------|-----------|------------------------------|
| id               | serial    | Unique ID for RAP record      |
| pap_id           | integer   | Associated PAP ID            |
| status           | varchar   | Current status of RAP        |
| created_at       | timestamp | Creation timestamp            |
| updated_at       | timestamp | Last updated timestamp        |

## Relationships
- **Land Parcels** have many **Easements**.
- **Land Parcels** can have many **PAPs**.
- Each **PAP** is associated with one **RAP** entry.