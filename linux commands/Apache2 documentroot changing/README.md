We assume Apache is already installed on your system. If not, you can install it with the following command:
```bash
sudo apt install apache2
```

Step 1: Create your website folder where your website's files will be stored. For this example, we'll create a folder named 'example-site':
```bash
mkdir ~/example-site
```

Step 2: Place all the files for your website in the 'example-site' folder.

Step 3: Allow execute permission to your home directory; add the www-data user to your user group:
```bash
sudo adduser www-data username
```
Replace username with your actual user.

Step 4.1: Configure Apache to use your new folder. Change to the 'sites-available' directory:
```bash
cd /etc/apache2/sites-available
```

Step 4.2: Create a new configuration file for your site:
```bash
sudo nano example-site.conf
```

Step 4.3: In the configuration file, add the following:
```bash
<VirtualHost *:80>
<Directory /home/username/example-site/>
    Options Indexes FollowSymLinks
    AllowOverride None
    Require all granted
</Directory>
DocumentRoot /home/username/example-site 
</VirtualHost>
```
Replace username with your actual username.

Step 5.1: Disable the default site configuration with:
```bash
sudo a2dissite 000-default.conf
```

Step 5.2: Enable your new site configuration with:
```bash
sudo a2ensite example-site.conf
```

Step 6: Reload Apache to apply the changes:
```bash
sudo systemctl restart apache2
```
`
