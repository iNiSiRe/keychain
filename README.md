
Keychain

---------------------------------------

Description:

Application for store and comfort access to keys and other usefull text data.

---------------------------------------

Nginx config:

server {
	listen 80;
	server_name local.keychain.com;
	root /home/inisire/projects/keychain;

	index index.php index.html;

	location / {
		try_files $uri $uri/ =404;
	}

	location ~ \.php$ {
		fastcgi_pass unix:/var/run/php5-fpm.sock;
		fastcgi_split_path_info ^(.+\.php)(/.*)$;
		include fastcgi_params;
		fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
		fastcgi_param HTTPS off;
	}

	error_log /home/inisire/projects/keychain/error.log;
	access_log /home/inisire/projects/keychain/access.log;
}

-------------------------------------
