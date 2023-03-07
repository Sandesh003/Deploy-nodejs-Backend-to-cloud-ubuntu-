https://haydenjames.io/linux-securely-copy-files-using-scp/ (for upload local file to remote directory) 
// ~ Go to your file location in your local machine and open cmd there
enter this command :- scp file.txt username(droplet or ec2 username)@to_host(public IP):/remote/directory/ (/root)

// install node and npm:-

~ sudo apt update
~ sudo apt install nodejs
~ node -v
~ sudo apt install npm

// install process manager (pm2)
~ npm install pm2 -g
~ pm2 start //your entry file path

//install nginx (https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-ubuntu-20-04)
~ sudo apt update
~ sudo apt install nginx
~ sudo ufw app list
~ sudo ufw allow 'Nginx Full' (or any options you needed)
~ sudo ufw status (if it shows inactive then use " sudo ufw enable " command ) (https://linuxconfig.org/firewall-ufw-status-inactive-on-ubuntu-22-04-jammy-jellyfish-linux) 

// Checking your Web Server
~ systemctl status nginx (it will show active(running))
~ curl http://localhost ( to check weather your app is running )

// To stop your web server
~ sudo systemctl stop nginx

// To start the web server when it is stopped
~ sudo systemctl start nginx

// To stop and then start the service again
~ sudo systemctl restart nginx

// For Reverse Proxy (https://www.digitalocean.com/community/tutorials/how-to-configure-nginx-as-a-reverse-proxy-on-ubuntu-22-04)
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

