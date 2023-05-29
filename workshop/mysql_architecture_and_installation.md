[Summary](./index.md)

[Previous](./test_connectivity.md)

# MySQL Architecture and Installation

## Introduction
**Objective:** Installation of MySQL 8 (Community) on Oracle Linux 8. Because by default RedHat install MariaDB so, we update the repository to install the original MySQL.

**We are working on server:** mysql1

**•	References:**
- [https://dev.mysql.com/doc/mysql-yum-repo-quick-guide/en/](https://dev.mysql.com/doc/mysql-yum-repo-quick-guide/en/)
- [https://dev.mysql.com/doc/refman/8.0/en/validate-password.html](https://dev.mysql.com/doc/refman/8.0/en/validate-password.html)


## Task 1 - Installation of MySQL Community
1.	Open an SSH client to app-srv

    ```shell
    ssh -i id_rsa_app-srv opc@your_public_ip
    ```

2.	Connect to mysql1 from app-srv

    ```shell
    ssh -i $HOME/sshkeys/id_rsa_mysql1 opc@mysql1
    ```

3.	**We work from now on server  mysql1.**
    Which MySQL packages are installed on your Linux?

    ```shell
    sudo rpm -qa | grep mysql
    ```

4.	What happens when you try to install the mysql binaries with RedHat repositories? 
    Run this command but don’t confirm

    ```shell
    sudo yum install mysql 
    ```

5.	As you have seen, above command try to install MariaDB sw. Each distribution has its own repositories and different choices for the packages to install.

6.	Oracle Linux 8 already have the official MySQL repository, but we want here to practice how to import it in a generic/education perspective. 
    First add the repository PGPkey

    ```shell
    sudo rpm --import https://repo.mysql.com/RPM-GPG-KEY-mysql-2022 
    ```

7.	Now download the package from https://dev.mysql.com/downloads/ and install it

    ```shell
    wget https://dev.mysql.com/get/mysql80-community-release-el8-1.noarch.rpm

    sudo yum -y install mysql80-community-release-el8-1.noarch.rpm
    ```

8.	Update repository database with the new references
shell-mysql1> sudo yum repolist all

9.	Repeat the command above to install mysql-client (without using the mysql module id default repositories, to force the usage of MySQL ones) and note the different packages

    ```shell
    sudo yum module disable mysql

    sudo yum install mysql
    ```

10.	If only mysql packages are shown, confirm the installation.

11.	Install mysql-server

    ```shell
    sudo yum install mysql-server
    ```

12.	Because MySQL is automatically installed you can use OS command for service management, for example to check if it’s already started

    ```shell
    sudo systemctl status mysqld
    ```

13.	Start MySQL if not started

    ```shell
    sudo systemctl start mysqld

    sudo systemctl status mysqld
    ```

14.	Check the content of my.cnf, that is in default folder for linux OS and note some info (lines that stat with “#” are just comments)

    1. Display the content of the file

        ```shell
        cat /etc/my.cnf 
        ```

    2.	Where is the database and the error log (mysqld.log) stored?
        Write down the answer.

    3.	check if there are error for the instance looking in the error log file

        ```shell
        sudo grep -i error /var/log/mysqld.log
        ```

 
15.	Starting from MySQL 5.7 the default installation of MySQL Server generates a one-time password. You find it in error log notes above

    ```shell
    sudo grep 'temporary' /var/log/mysqld.log
    ```

16.	Login to MySQL using password retrieved in previous step

    ```shell
    mysql -uroot -p -h localhost
    ```

17.	Try to run a command and write down the error message.

    ERROR MESSAGE: _______________________________________________________________

    ```sql
    status;
    ```

18.	Change root password

    ```sql
    ALTER USER 'root'@'localhost' IDENTIFIED BY 'Welcome1!';
    ```


19.	Retry command above, now it works

    ```sql
    status;
    ```

20.	Which databases are installed by default?

    ```sql
    show databases;
    ```

    ``+--------------------+``    
    ``| Database           |``  
    ``+--------------------+``  
    ``| information_schema |``  
    ``| mysql              |``  
    ``| performance_schema |``  
    ``| sys                |``  
    ``+--------------------+``  
    ``4 rows in set (0.01 sec)``

    <pre>
    +--------------------+    
    | Database           |  
    +--------------------+  
    | information_schema |  
    | mysql              |  
    | performance_schema |  
    | sys                |  
    +--------------------+  
    4 rows in set (0.01 sec)
    </pre>
    
21.	To see which version of MySQL you are using submit the command

    ```sql
    show variables like "%version%";
    ```

22.	Check default users in standard installation

    ```sql
    select user, host from mysql.user where user='root';
    ```

23.	Logout as ‘root’ and connect as admin

    ```sql
    exit
    ```

## Task 2 - Detailed Installation of MySQL on Linux

## Task 3 - Verify the new MySQL Installation on Linux and import test databases


[Next](./mysql__database_design.md)

[Summary](./index.md)
