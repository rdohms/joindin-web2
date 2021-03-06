# Joind.in

This is the source code for the next generation of the Joind.in website - a resource set up to allow
events to get real-time feedback from those attending. It also gives speakers a 
way to claim and track their presentations over time.

This version is the next generation version, providing a responsive cross-device site for screens of all devices

You can either install joind.in on an existing PHP platform, or use our vagrant setup.

## Quick start with Vagrant

The virtual machine has been moved to a different repo. To use it [fork the joindin-vm](https://github.com/joindin/joindin-vm) repository and follow the instructions in there. 

This VM will load all three Joind.in projects (joind.in, joindin-vm and joindin-web2). 

## Quick Start for existing platforms

1. Clone repository to any location

        git clone https://github.com/joindin/responsive
        cd responsive
        
1. Create a vhost entry for the site. The docroot should be `/web`.

        <VirtualHost *:80>
            ServerName joindin.local
    
            DocumentRoot "/home/exampleuser/www/responsive/web"
    
            <Directory "/home/exampleuser/www/responsive">
                Options FollowSymLinks
                AllowOverride All
            </Directory>
        </VirtualHost>

1. Add hostname to /etc/hosts.

        echo "127.0.0.1 joindin.local" | sudo tee -a /etc/hosts

1. Enjoy the site!

1. Set up Redis: instructions can be found at http://redis.io/topics/quickstart but to be honest, your favourite package manager should do a good enough job

1. Enjoy the site!

## Configuration

1. Copy the file config/config.php.dist to config/config.php

        cp config/config.php.dist config/config.php

1. Change the value of `apiUrl` to the URL of your development API if you don't want to use the production API.

       Note that if you are connecting to the production API, you will find that you won't be able to log in as you don't have the correct oauth client_id.

       **Create a local copy of the API from the [GitHub project](https://github.com/joindin/joindin-api) and then you can log in to it from your web2 installation**
 

## Minification

To use minified JS and CSS files, you need gulp:

1. Install node and npm.
2. In the root of web2, run `npm install`.
3. Run `npm run gulp` to create web/js/site.js and web/css/site.css.
4. Update config.php to set `$config['slim']['custom']['useMinifiedFiles']` to true.

## Other Resources

* The main website http://joind.in
* Issues list: http://joindin.jira.com/ (good bug reports ALWAYS welcome!)
* CI Environment: lots of output and information about tests, deploys etc: http://jenkins.joind.in
* Community: We hang out on IRC, pop in with questions or comments! #joind.in on Freenode
