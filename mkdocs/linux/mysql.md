# Create user for MySQL

## Prerequisites

- Install MySQL in your server.
- Root access to your MySQL.

### Create a New User in MySQL

To create a new user you need to login to your MySQL shell using the following command.

```bash
sudo mysql -u root -p
```

You will be prompted to enter your root password. Once you have logged in you can execute the following command yo create a new user.

```mysql
CREATE USER 'username'@'localhost' IDENTIFIED BY 'password';
```

!!! note info
    password is the real password for the new user

Now a new user will get created, but that user wont have any permissions to perform any operations in MySQL.

### Grant Permissions to User in MySQL

Here are a list of some common permissions that can be provided to the users in MySQL.

#### Types of Permissions

|  parameter  |  value    |
|  ---------  |  -------  |
| **ALL PRIVILEGES** | this would allow a MySQL user full access to a database or if no database is selected, global access across the system |
| **CREATE** | allows user to create new tables or databases |
| **DROP** | allows user to delete tables or databases |
| **DELETE** | allows user to delete rows from tables |
| **INSERT** | allows user to insert rows into tables |
| **SELECT** | allows user to use the SELECT command to read through databases |
| **UPDATE** | allow user to update table rows |
| **GRANT OPTION** | allows user to grant or remove other users’ privileges |

You can use one of the above privileges to assign to the user. The common permission provided to a user is:

```mysql
GRANT ALL PRIVILEGES ON database_name.* TO 'username'@'localhost';
```

This command will provide all permissions for the user over the specific database.

Now you need to reload the privileges for the changes to take effect.

```mysql
FLUSH PRIVILEGES;
```

### Grant specific permissions

If you wish to provide specific permissions you can use the following syntax.

#### Assign permissions

```mysql
GRANT type_of_permission ON database_name.table_name TO 'username'@'localhost';
```

Once you update or change permissions you need to flush privileges for the changes to take effect.

#### Remove permissions

```mysql
REVOKE type_of_permission ON database_name.table_name FROM 'username'@'localhost';
```

This command will remove the specific permission type of user from the specific database or table.

#### Review User Permissions

You can view the permissions assigned to the user using the following command.

```mysql
SHOW GRANTS FOR 'username'@'localhost';
```
