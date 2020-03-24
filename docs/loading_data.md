# Loading Sample Data into your Cluster

In this section, we will use the MYSQL client to load data into your newly created Aurora instance.  Ensure your primary Aurora database is in available state.

To load data into Aurora MySQL, perform the following:

1. Connect to your primary database instance
    ```
    $ mysql -h aurora-{YOUR_NAME}-cluster.{XXXXXXXXXX}.{REGION}.rds.amazonaws.com -u {USERNAME} -p
    Welcome to the MySQL monitor.
    ```
2. Create a landsat database
    ```
    mysql> CREATE DATABASE landsat;
    Query OK, 1 row affected (0.09 sec)
    mysql> USE landsat;
    Database changed
    ```

3. Create the scene_list table
    ```
    CREATE TABLE `scene_list` (
    `entityId` varchar(64) DEFAULT NULL,
    `min_lat` decimal(8,5) DEFAULT NULL,
    `min_lon` decimal(8,5) DEFAULT NULL);

    Query OK, 0 rows affected (0.12 sec)
    ```
          
4.	Load sample data into scene_list table
    ```
    mysql> INSERT INTO scene_list (entityId, min_lat, min_lon) VALUES (1,10.4,50), (2,22.5,60.4),(3,56,32.4),(4,22.5,60.4),(5,54.3,50.6),(6,40.5,50.4),(7,34.2,22),(8,2.5,10.4),(9,22,45.3),(10,2.5,23.2);
    ```

5.	Run SQL query against scene_list table:
    - `mysql> select count(*) from scene_list;`

        Result should look like the following
        ```
        +----------+
        | count(*) |
        +----------+
        |       10 |
        +----------+
        1 row in set (0.08 sec)
        ```

    - `mysql> select * from scene_list limit 5;`

        Result should look like the following
        ```
        +----------+----------+----------+
        | entityId | min_lat  | min_lon  |
        +----------+----------+----------+
        | 1        | 10.40000 | 50.00000 |
        | 2        | 22.50000 | 60.40000 |
        | 3        | 56.00000 | 32.40000 |
        | 4        | 22.50000 | 60.40000 |
        | 5        | 54.30000 | 50.60000 |
        +----------+----------+----------+
        5 rows in set (0.08 sec)
        ```

