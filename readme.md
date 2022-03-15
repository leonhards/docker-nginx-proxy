First, create docker network for proxy container:
<br><code>docker network create nginx-proxy</code>

Run the docker-compose file:
<br><code>docker-compose up -d</code>

<br>
<b><u># Issue:</u></b><br>
After finishing the Wordpress installation, there will be an error when uploading a new theme: <b>"413 request entity too large"</b>.
<br>It happens because the file is bigger than default maximum upload size (2 MB).

<br>To solve this issue:
1. Run the docker CLI for nginx-proxy or run this command:<br>
<code>docker exec -it &lt;container&gt; bash</code>
2. Run the following command to install vim:<br>
<code>apt-get update</code><br>
<code>apt-get install vim</code>
3. Edit the nginx.conf file using this command:<br>
<code>vim /etc/nginx/nginx.conf</code>
4. Add the following parameter in nginx.conf file:
<code>client_max_body_size 20M;</code>
5. Press Esc button on your keyboard and type <code>:wq</code> and hit Enter.
