# ERROR-a-client-request-body-is-buffered-to-a-temporary-file-var-cache-nginx-client_temp

Increase Client Body Buffer Size: If the warning is occurring because the request body size exceeds the default buffer size configured in NGINX, you can increase the buffer size. You can adjust the client_body_buffer_size directive in your NGINX configuration file (nginx.conf). Set it to a value large enough to accommodate your expected request body sizes. For example:

````
client_body_buffer_size 10M;
````
This sets the buffer size to 10 megabytes.

Adjust Client Body Temp Path: If the warning persists despite increasing the buffer size, you may need to adjust the temporary file storage location or permissions. Ensure that the directory specified in the client_body_temp_path directive in your NGINX configuration exists and has appropriate permissions for NGINX to write temporary files.

bash
````
client_body_temp_path /var/cache/nginx/client_temp;
````
Ensure that the directory /var/cache/nginx/client_temp exists and is writable by the NGINX process.
````
sudo chown -R nginx:nginx /var/cache/nginx/client_temp
sudo nginx -s reload
````
