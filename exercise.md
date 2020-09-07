# Interview as DevOps Engineer

The aim of this exercise is to create the infrastructure and execute a sample data pipeline to transfer the contents of a CSV file to a relational DB.

The suggested technology stack is:
- Docker Engine 18.06
- Kubernetes Minikube 1.13
- Alpine Linux 3.7
- Python 3
- pipenv
- MySQL 8.0

## Step 1. Create the infrastructure

Create a cluster of containers with 3 images.

1. Container 1: Must inclue the MySQL database tables definition from `templates/msql/init_db.sql`
2. Container 2: Must include a Linux system with the file `data/sample/sample.csv` at the path `/var/data`
3. Container 3: Must include a Linux system with Task management solution capable to run Python jobs (Jenkins, Cron, Airflow, etc.)

**Considerations**
Consider you are the owner of container 2 and Container 3, but not of Container 1.

## Step 2. Create a job to load the data into User Actions database

1. Create a job that loads the data from the file `data/sample/sample.csv` into the DB *useractions* 
    1. The full contents must be loaded into table `all`
    2. The contents of any log/sign in must be loaded into table `login_attempts` following below map:
        1. user -> user_id
        2. logged -> `true` if `action` includes text "logging in" and `result` is equal to  "success", `false` otherwise
        3. timestamp -> action_date

**Considerations**
Consider that each record within the DB must have a unique `id` with an auto incremented number.
Use SQL and Python as execution language for the jobs as much as possible
