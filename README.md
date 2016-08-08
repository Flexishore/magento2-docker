# Magento 2 : Docker configuration
Magento 2 stack based on Docker : Magento 2, PHP 7, Nginx, Mariadb 10.1, Redis 3.2

## Start working with Magento 2
1. Install [Docker](https://www.docker.com/)
2. Copy your dump of database (any sql file) to directory `data`
3. Place Magento 2 project source code in directory `src`
4. Change your `HOME_DIR` in `.env` file. If you are working on Windows please check this [link](https://blog.pavelsklenar.com/5-useful-docker-tip-and-tricks-on-windows/)
5. Run _docker-compose up -d_

That's all! Your application should be working on `yourapp.com`. PhpMyAdmin can be accessed by `yourapp.com:8080` (you can
make there changes in your _core_config_data_ table.

!! Do not forget to add `yourapp.com` to your _hosts_ file with this line :
`DOCKER_MACHINE_IP yourapp.com`
 
 To check IP run this command : _docker-machine ip_
 
 ## Redis as session storage
 To store sessions in redis use this sample configuration :
 ```
 'session' =>
   array (
       'save' => 'redis',
       'redis' =>
           array (
               'host' => 'redis',
               'port' => '6379',
               'password' => '',
               'timeout' => '10',
               'persistent_identifier' => 'sess-db0',
               'database' => '0',
               'compression_threshold' => '0',
               'compression_library' => 'gzip',
               'log_level' => '7',
               'max_concurrency' => '6',
               'break_after_frontend' => '5',
               'break_after_adminhtml' => '30',
               'first_lifetime' => '600',
               'bot_first_lifetime' => '60',
               'bot_lifetime' => '7200',
               'disable_locking' => '0',
               'min_lifetime' => '60',
               'max_lifetime' => '2592000'
           )
)
 ```
