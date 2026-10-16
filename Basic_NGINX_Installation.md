## Basic NGINX Installation :

1. Update packages :

    ```
    sudo apt update
    ```


2. Install NGINX service :

    ```
    sudo apt install nginx -y
    ```


3. Start the service :

    ```
    sudo systemctl start nginx
    ```


    To verify that the service has started, you can click the NGINX UI button and you should see the NGINX default welcome page.

4. Alternatively, you can run the following command to view the service status :

    ```
    systemctl status nginx
    ```

5. Install UFW (Uncomplicated Firewall) :

    ```
    sudo apt update
    sudo apt install ufw -y
    ```

6. Enable and start the service :

    ```
    sudo systemctl enable ufw
    sudo systemctl start ufw
    ```

7. Check status :

    ```
    systemctl status ufw
    ```

8. Verify installation :

    ```
    ufw --version
    ```
9. In the NGINX system directory located at ```/etc/nginx/sites-available```.
    Create a new configuration file named ```helloworld``` with below contents.

    ```
    server {
            listen 80;
            server_name helloworldcom;
            root /var/www/helloworld;

            # Add index.php to the list if PHP is used
            index index.html index.htm index.nginx-debian.html;

            location / {
                    # First attempt to serve request as file, then
                    # as directory, then fall back to displaying a 404.
                    try_files $uri $uri/ =404;
            }
    }
    ```
10. Create the folder and index file for "helloworld.com".

    In the directory ```/var/www``` and create a new directory called ```helloworld```.

    ```
        cd /var/www
        sudo mkdir helloworld
        cd helloworld
        sudo touch index.html
        echo '<h1> Hello World! </h1>' | sudo tee -a index.html
    ```
11. Remove the default NGINX welcome page.

    ```
    sudo rm /etc/nginx/sites-enabled/default
    ```

12. Create a symbolic link for the new Hello World configuration file & reload the Server Configuration.

    ```
    sudo ln -s /etc/nginx/sites-available/helloworld /etc/nginx/sites-enabled/
    ```

    Test the configuration :

    ```
    sudo nginx -t
    ```
    Expected Output :
    ```
    nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
    nginx: configuration file /etc/nginx/nginx.conf test is successful
    ```

    Reload the NGINX Server Configuration :

    ```
    sudo nginx -s reload
    ```

13. Enable UFW, add two firewall rules to allow ports 22 and 80 over TCP protocol

    ```
    sudo ufw status

    sudo ufw enable

    sudo ufw allow 22/tcp
    sudo ufw allow 80/tcp
    ```


