# Troubleshoot

### Issue 1: Accessing localhost (xampp) from another computer over LAN network 

You may solve the problem like bellow:

1. Go to Your [XAMPP](https://www.apachefriends.org/) Control panel using [remote desktop connection](https://support.microsoft.com/en-us/windows/how-to-use-remote-desktop-5fe128d5-8fb1-7a23-3b8a-41e636865e8c).
2. Click on apache > config > Apache (httpd-xampp.conf).
3. Search for `Require local` and then replace with `Require all granted`

```
Alias /phpMyAdmin "C:/xampp/phpMyAdmin/"
<Directory "C:/xampp/phpMyAdmin">
    AllowOverride AuthConfig
    Require local 
    ErrorDocument 403 /error/XAMPP_FORBIDDEN.html.var
</Directory>
``` 
4. Save configuration and restart xampp

link solved: [stackoverflow.com](https://stackoverflow.com/questions/5524116/accessing-localhost-xampp-from-another-computer-over-lan-network-how-to)

### Issue 2: host localhost is not allowed to connect to this MySQL server

You may solve the problem like bellow:

1. Open **my.ini** file
2. add **skip-grant-tables** under the **[mysqld]**
3. [mysqld] is look like

```
The MySQL server
[mysqld]
skip-grant-tables
port= 3306
socket = "C:/xampp/mysql/mysql.sock"
basedir = "C:/xampp/mysql" 
tmpdir = "C:/xampp/tmp" 
datadir = "C:/xampp/mysql/data"
pid_file = "mysql.pid"
```

link solved: [stackoverflow.com](https://stackoverflow.com/questions/15087492/host-localhost-is-not-allowed-to-connect-to-this-mysql-server-1130)

### Issue 3: Hall Effect Sensor Debouncing

The Hall Effect sensor produces unreliable readings due to noise or bouncing. solution:

* **Adjust Debounce Parameter:** In the Arduino code, modify the debounce parameter. Experiment with values; in this case, changing the debounce value from `500` to `10` successfully fixed the issue.

```
...
meteran.setDebounceTime(10);
meteran2.setDebounceTime(10);
meteran3.setDebounceTime(10);
...
```

* **Adjust Sensor Sensitivity:** The sensitivity of a Hall Effect sensor determines how small a change in the magnetic field it can detect. Adjusting the sensitivity can help optimize the sensor's performance for your application.

### Issue 4: MySql error "Pool is closed" in node-red

The error `Pool is closed` in Node-RED can occur when the number of connections exceeds the maximum number of allowed consecutive connections. To fix this, you can try `restarting` Node-RED. The node tries to connect to the MySQL server every five seconds, so if the server is coming back, the error should go away automatically.