# How to build

First, create docker network for proxy container:
<br><code>$ docker network create nginx-proxy</code>

Run the docker-compose file:
<br><code>$ docker-compose up -d</code>


## Fixing '413 request entity too large' Error:

Step-by-step to solve the issue:

1. Run the docker CLI for 'nginx-proxy' or run this command:
<br><code>$ docker exec -it &lt;container&gt; bash</code>
2. Install text editor before editing the nginx.conf file:
<br><code># apt-get update</code>
<br><code># apt-get install vim</code>
3. Edit the nginx.conf file using this command:<br>
<code># vim /etc/nginx/nginx.conf</code>
4. Add the following parameter in nginx.conf file:
<br><code>client_max_body_size 64M;</code>
5. Press Esc button on your keyboard and type <code>:wq</code> to save changes and hit Enter.
6. Restart 'nginx-proxy' container.

## Fixing ‘The link you followed has expired’ Error:

Step-step to solve the issue:

1. Edit .htaccess file.
2. Add following code at the bottom of .htaccess file:
```php
php_value upload_max_filesize 64M
php_value post_max_size 64M
php_value max_execution_time 300
php_value max_input_time 300
```
3. Save changes.

