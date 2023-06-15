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
    - your_user, your_pass, your_db, your_table. And import some data into your_db
    - These infomation need to be declared in pyspark_notebook.ipynb


2. Grant privileges for mysql user:
   - Access to mysql as root user and exec query
    ```
    GRANT ALL PRIVILEGES ON your_db.*  TO 'your_user'@'%';
    ```
  
## Apache Sqoop site

## Pyspark notebook site