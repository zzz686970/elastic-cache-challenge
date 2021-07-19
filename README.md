- **Load Database Stored Procedure**

  The application calls a stored procedure on the database which must be created before running the application.  You will need the RDS instance hostname, the database name and the username used to connect to the database.
  You can install the procedure from the install.sql file with the following command:
  ``` psql -h <RDS_HOSTNAME> -U <DB_USER> -f install.sql <DB_NAME> ``` 
- **Configure Database Connection**

  You will also need to configure the application to connect to the database by editing the [`config/database.ini`](https://raw.githubusercontent.com/ACloudGuru/elastic-cache-challenge/master/config/database.ini) file.  Use the database name, username and password you created when deploying the database.
- **Configure HTTP Server**

  If you are running the application on your workstation, you can access it at http://127.0.0.1:5000.  Alternately, you can configure an HTTP server listening on the public interface as a proxy.  I've provided such a configuration for the nginx http server in [`config/nginx-app.conf`](https://raw.githubusercontent.com/ACloudGuru/elastic-cache-challenge/master/config/nginx-app.conf).


```
## connect to instance
ssh -i "key.pem" ec2-user@ec2-3-135-64-237.us-east-2.compute.amazonaws.com

yum -y update
yum -y install python-pip
yum install git

## install psycopg2
First make sure you have postgresql-devel installed:
yum install postgresql-devel
To make sure you have the correct version do a search like following:
yum search devel  | grep python
Choose the write python version devel package and install it. For python3 it was
yum install python3-devel.x86_64
Finally you can install psycopg2 using pip:
pip install psycopg2

pip install redis
## test local connection
sudo amazon-linux-extras install redis6

redis-cli -c -h host_name -p 6379

```