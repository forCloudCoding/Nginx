## Basic NGINX Installation :

1. Update packages :

    ```
    sudo apt update
    ```


2. Install NGINX service:

    ```
    sudo apt install nginx -y
    ```


3. Start the service:

    ```
    sudo systemctl start nginx
    ```


    To verify that the service has started, you can click the NGINX UI button and you should see the NGINX default welcome page.

4. Alternatively, you can run the following command to view the service status:

    ```
    systemctl status nginx
    ```



