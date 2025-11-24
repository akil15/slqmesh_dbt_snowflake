# slqmesh_dbt_snowflake

### SQLMesh Installation on MacOS
Let's start by creating a folder which whill hold all of our SQLMesh data projects.

I have created the following one:
```bash
% mkdir data_pipeline_sqlmesh
```

Then issue the following commands to install SQLMesh with Snowflake as a target datawarehouse, meaning the datawarehouse which will contain the data we will be working with:
```bash
% python3 -m venv .env
% source .env/bin/activate
% pip install "sqlmesh[web]"
% pip install "sqlmesh[snowflake]"
```

Issue the following SQL commands in your Snowflake worksheet.

This will create the required variables like warehouse, database, role, user to be used during the execution of our models.
```sql
USE ROLE accountadmin;
CREATE WAREHOUSE demo_ask_wh WITH warehouse_size='xsmall';
CREATE DATABASE IF NOT EXISTS demo_ask_db;
CREATE ROLE IF NOT EXISTS demo_ask_role;
GRANT USAGE ON WAREHOUSE demo_ask_wh TO ROLE demo_ask_role;
GRANT OWNERSHIP ON DATABASE demo_ask_db TO ROLE demo_ask_role;
GRANT ROLE demo_ask_role TO USER akilsalhab;
```

Update the config.yaml file with the appropriate connection parameters - note that upon issuing the latest config, you would have noticed that some elements have appeared in data_pipeline_mesh repository
```bash
nano config.yaml
```
You simply need to fill in the following parameters:
{
...
  account: <<YOUR_SNOWFLAKE_ACCOUNT>>
  user: <<I_HAVE_MY_SNOWFLAKE_DEFAULT_USERNAME>>
  password: <<YOUR_USER_PASSWORD>>
  database: demo_ask_db
  warehouse: demo_ask_wh
...
}

After saving that file, you can enter the following command to ensure the connectivity is working:
```bash
% sqlmesh info
```




