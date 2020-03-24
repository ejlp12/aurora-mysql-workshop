## Cloning Aurora Database

Create a clone copy of your aurora database by performing the following steps:

1.	Go to the **RDS** Aurora Console
2.	Click on **Instances** 
3.	Select your DB instance `auroa-{yourname}`
4.	Choose instance **Actions**
5.	Select **Create clone**
 
6.	Enter the following values
    - **DB Engine**: **Aurora MYSQL**
    - **DB instance class**: **db.t2.small**
    - Under **Settings**, for **DB Instance identifier** enter `aurora-{yourname}-clone`
    - Under **Network & Security****, Public accessibility**: Yes (should be ok for this lab)
    - Leave all other fields to their default value
    
7.	Click **Create Clone**

    !!! Note ""
        It may take a few minutes for the clone to become available.  

## Compare Primary and Cloned database

In this section, we will delete records from the primary database and validate that the delete operation does not affect the cloned database.

Perform the following tasks on your Primary Database. 

1. Connect to primary endpoint
    ```
    mysql –h <primary endpoint name> -u <db user name> -p
    ```
    Example: 
    ```
    mysql -h aurora-{yourname}.xxxxxxxxx.{region}.rds.amazonaws.com -u root -p
    Enter password: 
    mysql> 
    ```

2. Get the existing record count
    ```
    mysql> use landsat;
    mysql> select count(*) from scene_list;
    ```
    Result should look similar to the following
    ```
    +----------+
    | count(*) |
    +----------+
    |       10 |
    +----------+
    1 row in set (0.07 sec)
    ```

3. Run DELETE query on primary DB instance to delete 5 records
   ```
   mysql> delete from scene_list limit 5;
   Query OK, 5 rows affected (0.08 sec)
   ```
4. Get the updated count 
    ```
    select count(*) from scene_list;
    ```
    Result should look similar to the following
    ```
    +----------+
    | count(*) |
    +----------+
    |        5 |
    +----------+
    1 row in set (0.08 sec)
    ```
5. Exit from your primary endpoint
    ```
    mysql> exit;
    ```
Perform the following tasks on your Cloned Database. 


1. Connect to cloned endpoint
    ```
    $ mysql -h <{yourname}-aurora-clone.xxxxx.us-xxxx.rds.amazonaws.com> –u <username> -p
    ```

2. Get the existing record count
    ```
    mysql> use landsat;
    mysql> select count(*) from scene_list;
    ```
    Result should look similar to the following
    ```
    +----------+
    | count(*) |
    +----------+
    |       10 |
    +----------+
    1 row in set (0.09 sec)
    ```

3. Exit from cloned endpoint
    ```
    mysql> exit;
    ```

!!! Recap 
    Notice that the cloned records match the primary count prior to deletion. 
