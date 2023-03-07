// install node and npm:-

~ sudo apt update
~ sudo apt install nodejs
~ node -v
~ sudo apt install npm

// install process manager (pm2)
~ npm install pm2 -g
~ pm2 start //your entry file path

//install nginx
~ sudo apt update
~ sudo apt install nginx
~ sudo ufw app list
~ sudo ufw allow 'Nginx Full' (or any options you needed)
~ sudo ufw status (if it shows inactive then use " sudo ufw enable " command ) 

// Checking your Web Server
~ systemctl status nginx (it will show active(running))
~ curl http://localhost ( to check weather your app is running )

// To stop your web server
~ sudo systemctl stop nginx

// To start the web server when it is stopped
~ sudo systemctl start nginx

// To stop and then start the service again
~ sudo systemctl restart nginx

// For Reverse Proxy
~ Go to " /etc/nginx/sites-enabled/ " and edit the default file with nano command...
~ add following into default file IN server --> location / 
	 proxy_pass http://localhost:8000; # your app's port
         proxy_http_version 1.1;
         proxy_set_header Upgrade $http_upgrade;
         proxy_set_header Connection 'upgrade';
         proxy_set_header Host $host;
         proxy_cache_bypass $http_upgrade;

// Check your file
~ sudo nginx -t

if everything is perfect than restart your nginx server
~ sudo systemctl restart nginx

// Check your site with your curl
~ curl http://localhost (it will now show your home route content)

