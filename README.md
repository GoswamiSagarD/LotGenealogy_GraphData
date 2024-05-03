# Lot Genealogy using Neo4j and Graph Datasets
---
Author: [Sagar Goswami](https://github.com/GoswamiSagarD)

```
This project is to perform Lot Genealogy Analytics on Mock Manufacturing Data using Neo4j and Graph Datasets.
```

The project is divided into 4 parts:
1. Data Generation (Mock Manufacturing Data)
2. Data Ingestion (Neo4j)
3. Data Analysis (Cypher Queries)
4. Data Visualization (Neo4j Browser)


### Terminology
---
1. **Item**: A raw material or a product that is used in the manufacturing process. Items can either be raw materials, sub-assemblies, or finished goods (among many other which are not considered in this project).
2. **Job/Work Order**: A job/work order is a task that is assigned to a manufacturing process. It is a set of instructions that are to be followed to produce a product. A job will consume certain items (Component Items) and produce a item (Assembly Item).
3. **Lot**: A lot is a collection of items that are produced together. A lot is assigned a unique identifier and is used to track the items in the lot for inventory management, quality control and traceability.
4. **BOM (Bill of Materials)**: A BOM is a list of items that are required to produce a product. It is a hierarchical structure that lists the items required to produce a product. The BOM is exploded to show the consumption of items in a job/work order.



## 1. Data Generation (Mock Manufacturing Data)
---
The mock data is generated using simple and humble tools like Excel, and some creative help from the internet ([Mockaroo](https://mockaroo.com/)).

The data resembles material consumption for a Job/Work Order, projected on a exploded BOM-like structure. The data is generated in CSV format and is stored in the `data` directory.

This data is then converted into separate CSV files to ingest into Neo4j database using humble Python and pandas magic. The data is stored in the `data/neo4j` directory. The list of CSV files are:
1. items.csv `(:item)`
2. lots.csv `(:lot)`
3. jobs.csv `(:job)`
4. item_belongs_to_lot.csv `(:item)-[:BELONGS_TO]->(:lot)`
5. lot_consumed_by_job.csv `(:lot)-[:CONSUMED_BY]->(:job)`
6. job_produces_lot.csv `(:job)-[:PRODUCES]->(:lot)`

The data generation process is explained in the [Data Generation](src/01_data_generation.ipynb) notebook.