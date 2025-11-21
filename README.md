# slqmesh_dbt_snowflake

### SQLMesh installation on MacOS
Let's start by creating a folder which whill hold all of our SQLMesh data projects
I have created the following one:
> % mkdir data_pipeline_sqlmesh
Then issue the following commands to install SQLMesh with Snowflake as a target datawarehouse, meaning the datawarehouse which will contain the data we will be working with
> % python3 -m venv .env

> % source .env/bin/activate

> pip install "sqlmesh[web]"

> pip install "sqlmesh[snowflake]"

