# How to get client ip when using nginx

When use nginx as web server, without configuration, the ip get from service behind nginx will be localhost or 127.0.0.1, we can forward the client ip to request on nginx's configuration file.

The sample configuration is like below:

	server {
		client_max_body_size 50M;
		listen 80;
		server_name test.swanwish.com;
		location / {
			proxy_pass http://127.0.0.1:8098;
			proxy_set_header Host $host;
			proxy_set_header X-Real-IP $remote_addr;
			proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
		}
	}

