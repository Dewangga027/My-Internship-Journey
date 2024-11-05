# Issue 2: Host localhost is not allowed to connect to this MySQL server

If you encounter the error "Host 'localhost' is not allowed to connect to this MySQL server," it typically indicates that MySQL is not configured to allow connections from the localhost or that the necessary permissions have not been set. Below are the steps to resolve this issue.

## Steps to Solve the Problem

1. **Open the MySQL Configuration File (`my.ini`)**:
   - Locate the MySQL configuration file, which is usually named `my.ini`. For XAMPP users, you can find it in the directory:
     ```
     C:\xampp\mysql\bin\my.ini
     ```
   - Open this file using a text editor (e.g., Notepad or Visual Studio Code).

2. **Add `skip-grant-tables` Under `[mysqld]`**:
   - In the `my.ini` file, find the section labeled `[mysqld]`. This section contains configuration options for the MySQL server.
   - Below the `[mysqld]` header, add the line `skip-grant-tables`. This option allows MySQL to start without checking user permissions, which can help you regain access to the server.

    The modified `[mysqld]` section should look like this:
   ```ini
   [mysqld]
   skip-grant-tables
   port=3306
   socket="C:/xampp/mysql/mysql.sock"
   basedir="C:/xampp/mysql"
   tmpdir="C:/xampp/tmp"
   datadir="C:/xampp/mysql/data"
   pid_file="mysql.pid"
   ```
    This configuration bypasses the user privilege system, enabling access without authentication.

3. **Save the Changes**:
    - After adding the `skip-grant-tables` line, save the changes to the `my.ini` file and close the text editor.

4. **Restart MySQL Server**:
    - To apply the changes, you must restart the MySQL server. Go to the XAMPP Control Panel, and stop the MySQL module if it is running. Then start it again.

5. **Connect to MySQL**:
    - After restarting MySQL, you should be able to connect to the MySQL server without encountering the permission error.

6. **Reset User Privileges (Optional but Recommended)**:
    - Once you have successfully connected to the MySQL server, it’s advisable to reset the user privileges to ensure security. You can do this by running the following SQL commands in the MySQL command line or phpMyAdmin:

        ```sql
        FLUSH PRIVILEGES;
        ```
    - Then, you can remove the `skip-grant-tables` line from the `my.ini` file to restore the normal permission checks.

7. **Save and Restart MySQL Again**:
    - After making changes to user privileges, save the `my.ini` file again and restart the MySQL server to apply the normal privilege checks.

## Verify Connection

After performing the above steps:

- Attempt to connect to your MySQL server again, either through a database management tool like phpMyAdmin or through the command line.

## Helpful Links

> [!TIP]  
> For more detailed troubleshooting, refer to this [Stack Overflow thread](https://stackoverflow.com/questions/15087492/host-localhost-is-not-allowed-to-connect-to-this-mysql-server-1130).
