# Demo deployment Azure Data Factory

This repository will deploy an Azure Data Factory and associated resources to your Azure subscription. You will need to have an active Azure subscription to run this sample. 

## What's contained

After deployment, your resource group will contain: 

* an Azure data factory 
* a Cosmos DB account
* a synapse analytics workspace with a dedicated SQL pool
* a storage account

The data factory contains 

* A pipeline that copies parquet data from an open data source to Synapse 
* 2 pipelines that copy data from a Dynamics 365 demo account to Cosmos DB and Synapse
* A mapping dataflow that transforms data from these two data sources and loads it to a CDM data structure
* A pipeline that runs the mapping dataflow

## Before you start

You will need a (free demo) Dynamics 365 account and the credentials to that account. Furthermore you will need to grant your data factory permisssion to access your Synapse dedicated SQL pool. 

You can do this by running the following SQL command after logging into your dedicated SQL pool via the Azure Synapse workspace:

```sql
create user [<your_ADF_name_here>] from external provider;
exec sp_addrolemember 'db_owner' add member '<your_ADF_name_here>';
```