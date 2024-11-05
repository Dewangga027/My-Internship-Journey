# Issue 1: Accessing localhost (XAMPP) from another computer over LAN network

If you're having trouble accessing your XAMPP server from another computer on the same local area network (LAN), you can follow the steps below to resolve the issue.

## Steps to Solve the Problem

1. **Open XAMPP Control Panel**:
   - Launch the XAMPP Control Panel on the computer where XAMPP is installed. You can access the Control Panel using a [Remote Desktop Connection](https://support.microsoft.com/en-us/windows/how-to-use-remote-desktop-5fe128d5-8fb1-7a23-3b8a-41e636865e8c) if you're connecting remotely.

2. **Edit Apache Configuration**:
   - In the XAMPP Control Panel, locate the **Apache** module.
   - Click on the **Config** button next to Apache.
   - Select **Apache (httpd-xampp.conf)** from the dropdown menu. This will open the configuration file in a text editor.

3. **Modify the Directory Settings**:
   - Search for the line that says `Require local`. This line restricts access to the server to only the local machine.
   - Replace `Require local` with `Require all granted` to allow access from any IP address on the local network.

   Your configuration should look like this:
   ```apache
   Alias /phpMyAdmin "C:/xampp/phpMyAdmin/"
   <Directory "C:/xampp/phpMyAdmin">
       AllowOverride AuthConfig
       Require all granted
       ErrorDocument 403 /error/XAMPP_FORBIDDEN.html.var
   </Directory>

4. **Save the Configuration**:
   - After making the changes, save the file and close the text editor.

5. **Restart XAMPP**:
   - Go back to the XAMPP Control Panel and restart the Apache module. This is necessary for the changes to take effect.

## Verify Access

To verify that the setup is correct:
   - On the computer trying to access the XAMPP server, open a web browser.
   - Enter the IP address of the XAMPP server machine followed by the port (default is `80`). For example: `http://192.168.1.100` (replace with your XAMPP server's IP address).

You should be able to access the XAMPP dashboard or any hosted applications without any issues.

## Helpful Links

> [!IMPORTANT]  
> For more detailed troubleshooting, refer to this [Stack Overflow thread](https://stackoverflow.com/questions/5524116/accessing-localhost-xampp-from-another-computer-over-lan-network-how-to).
