# elasticache-memcached-php-demo

This is a simple demo, showing how to do session caching with Amazon ElastiCache using PHP.

## Step 1: Install php, apache, memcache client on the server.
e.g. yum install php httpd php-pecl-memcache

## Step 2: Update /etc/php.ini file params:

session.save_handler = memcache

session.save_path = "tcp://elasticache-memcache-node1-endpoint:11211,tcp://elasticache-memcache-node2-endpoint:11211, etc."

## Step 3: Configure php.d/memcache.ini param values:

memcache.hash_strategy = consistent

memcache.allow_failover = 1

memcache.session_redundancy = 3

## Step 4: Restart httpd 
e.g. etc/init.d/httpd restart

## Step 5: Run sample code in var/www/html

- index.php (basic login page that will capture un/pw and redirect to login.php)
- login.php (stores session variables. Note: Its not authenticating the user, this is just a demo to show how to use the session
- home.php (if session variables are set, home.php will load. Otherwise will redirect user back to index.php



