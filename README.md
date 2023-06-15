# Sqoop MySQL HDFS by Docker
ETL the MySQL to HDFS by Apache Spoop and use PySpark notebook to transform data

## Follow my steps to build:

## Docker site
   Execute docker file (.yml) at root directory by command:
   ```bash
   docker-compose up -d
   ```

   Check three docker containers is running (mysql, jupyter-upgrad, sqoop-server)?
   ```bash
   docker-compose ps
   ```

## MySQL site
1. Build and setup your MySQL DB:
    - Create `your_user, your_pass, your_db, your_table`.
    - This information need to be used in pyspark
    - To import data into MySQL table. You can follow my pyspark code that's defined in pyspark_notebook.ipynb (focus at `spark.write`)


2. Grant privileges for mysql user:
   - Access to mysql as root user and exec query
    ```
    GRANT ALL PRIVILEGES ON your_db.*  TO 'your_user'@'%';
    ```
  
## Apache Sqoop site
   Setup HDFS in sqoop server:
   ```bash
   # create new HDFS folder (sqoop_dictory)
   hdfs dfs -mkdir -p /user/root/data/sqoop_dictory
   
   # check folder sqoop_dictory is created
   hdfs dfs -ls /user/root/data/
   ```

   ETL MySQL table to HDFS by command:
   ```bash
   sqoop import --connect jdbc:mysql://mysql:3306/your_db --table your_table --username your_user --password your_pass -m 1 --target-dir /user/root/data/sqoop_dictory
   ```

## Pyspark notebook site
   Execute code in `pyspark_notebook.ipynb` file to visualize the result
