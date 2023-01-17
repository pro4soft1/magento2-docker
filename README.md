# Setup  Magento Docker with ShopFinder Module

### Steps :



1. clone this repository by running the following command

``   `git clone https://github.com/pro4soft1/magento2-docker.git
``
2. please make sure Dokcer is installed and running

3. Add an entry to your local hosts file with your custom domain. like `"magento2.local"` run this command line in your terminal .
  - `echo "127.0.0.1 magento2.local" | sudo tee -a /etc/hosts`

4. Please Make sure you stoped the other processes for web services like port 80 and 9200

5. To Start the project there are 2 ways to start the project
6. first one is run this command line in your magento2 folder `sh run` this sometimes  doesn't work if your computer not faster
7. Here is the another way to start the project
7. go to magento 2 folder and execute the following command make sure you in magento2 folder
  - `bin/download 2.4.3 community`
  - `bin/setup`
  - `bin/fixowns`
  - `bin/clinotty bin/magento module:disable Magento_TwoFactorAuth`
  - `bin/composer require sf/module-shopfinder`
  - `bin/magento s:up`
  - `bin/magento s:d:c`
  - `bin/magento c:f`


    to access magneto2 admin you need to go 
    
    https://magento2.local/admin

    username:admin

    password:admin123



## GraphQL Api  


To Test GraphQL Api  you need to install any GraphQl Client You Can use this one : https://chrome.google.com/webstore/detail/altair-graphql-client/flnheeellpciglgpaodhkhmapeljopja 
in Chrome browser 


#### by adding this Url to your client configuration `https://magento.test/graphql`

### to get shopFinder list Api you need to call below Api payload
    {

        getshops(filter: {}, pageSize: 5, currentPage: 1) {

            items {
            address
            address_2
            can_collect
            city
            country
            created_at
            description
            email
            entity_id
            identifier
            image
            latitude
            longitude
            name
            open_info
            phone
            state
            status
            store_id
            updated_at
            zip
        }
        total_count
        }
    }


### to get shopFinder By ID below Api payload
    {
        
            getshop(id: 1) {
            address
            address_2
            can_collect
            city
            country
            created_at
            description
            email
            entity_id
            identifier
            image
            latitude
            longitude
            name
            open_info
            phone
            state
            status
            store_id
            updated_at
            zip
        }   
    }
## Custom CLI Commands May Help you

- `bin/analyse`: Run `phpstan analyse` within the container to statically analyse code, passing in directory to analyse. Ex. `bin/analyse app/code`
- `bin/bash`: Drop into the bash prompt of your Docker container. The `phpfpm` container should be mainly used to access the filesystem within Docker.
- `bin/cache-clean`: Access the [cache-clean](https://github.com/mage2tv/magento-cache-clean) CLI. Note the watcher is automatically started at startup in `bin/start`. Ex. `bin/cache-clean config full_page`
- `bin/cli`: Run any CLI command without going into the bash prompt. Ex. `bin/cli ls`
- `bin/clinotty`: Run any CLI command with no TTY. Ex. `bin/clinotty chmod u+x bin/magento`
- `bin/cliq`: The same as `bin/cli`, but pipes all output to `/dev/null`. Useful for a quiet CLI, or implementing long-running processes.
- `bin/composer`: Run the composer binary. Ex. `bin/composer install`
- `bin/copyfromcontainer`: Copy folders or files from container to host. Ex. `bin/copyfromcontainer vendor`
- `bin/copytocontainer`: Copy folders or files from host to container. Ex. `bin/copytocontainer --all`
- `bin/cron`: Start or stop the cron service. Ex. `bin/cron start`
- `bin/dev-urn-catalog-generate`: Generate URN's for PhpStorm and remap paths to local host. Restart PhpStorm after running this command.
- `bin/devconsole`: Alias for `bin/n98-magerun2 dev:console`
- `bin/docker-compose`: Support V1 (`docker-compose`) and V2 (`docker compose`) docker compose command, and use custom configuration files, such as `compose.yml` and `compose.dev.yml`
- `bin/download`: Download specific Magento version from Composer to the container, with optional arguments of the version (2.4.5-p1 [default]) and type ("community" [default], "enterprise", or "mageos"). Ex. `bin/download 2.4.5-p1 enterprise`
- `bin/fixowns`: This will fix filesystem ownerships within the container.
- `bin/fixperms`: This will fix filesystem permissions within the container.
- `bin/grunt`: Run the grunt binary. Ex. `bin/grunt exec`
- `bin/install-php-extensions`: Install PHP extension in the container. Ex. `bin/install-php-extensions sourceguardian`
- `bin/magento`: Run the Magento CLI. Ex: `bin/magento cache:flush`
- `bin/mftf`: Run the Magento MFTF. Ex: `bin/mftf build:project`
- `bin/mysql`: Run the MySQL CLI with database config from `env/db.env`. Ex. `bin/mysql -e "EXPLAIN core_config_data"` or`bin/mysql < magento.sql`
- `bin/mysqldump`: Backup the Magento database. Ex. `bin/mysqldump > magento.sql`
- `bin/n98-magerun2`: Access the [n98-magerun2](https://github.com/netz98/n98-magerun2) CLI. Ex: `bin/n98-magerun2 dev:console`
- `bin/node`: Run the node binary. Ex. `bin/node --version`
- `bin/npm`: Run the npm binary. Ex. `bin/npm install`
- `bin/phpcbf`: Auto-fix PHP_CodeSniffer errors with Magento2 options. Ex. `bin/phpcbf <path-to-extension>`
- `bin/phpcs`: Run PHP_CodeSniffer with Magento2 options. Ex. `bin/phpcs <path-to-extension>`
- `bin/phpcs-json-report`: Run PHP_CodeSniffer with Magento2 options and save to `report.json` file. Ex. `bin/phpcs-json-report <path-to-extension>`
- `bin/pwa-studio`: (BETA) Start the PWA Studio server. Note that Chrome will throw SSL cert errors and not allow you to view the site, but Firefox will.
- `bin/redis`: Run a command from the redis container. Ex. `bin/redis redis-cli monitor`
- `bin/remove`: Remove all containers.
- `bin/removeall`: Remove all containers, networks, volumes, and images, calling `bin/stopall` before doing so.
- `bin/removevolumes`: Remove all volumes.
- `bin/restart`: Stop and then start all containers.
- `bin/root`: Run any CLI command as root without going into the bash prompt. Ex `bin/root apt-get install nano`
- `bin/rootnotty`: Run any CLI command as root with no TTY. Ex `bin/rootnotty chown -R app:app /var/www/html`
- `bin/setup`: Run the Magento setup process to install Magento from the source code, with optional domain name. Defaults to `magento.test`. Ex. `bin/setup magento.test`
- `bin/setup-composer-auth`: Setup authentication credentials for Composer.
- `bin/setup-domain`: Setup Magento domain name. Ex: `bin/setup-domain magento.test`
- `bin/setup-grunt`: Install and configure Grunt JavaScript task runner to compile .less files
- `bin/setup-pwa-studio`: (BETA) Install PWA Studio (requires NodeJS and Yarn to be installed on the host machine). Pass in your base site domain, otherwise the default `master-7rqtwti-mfwmkrjfqvbjk.us-4.magentosite.cloud` will be used. Ex: `bin/setup-pwa-studio magento.test`
- `bin/setup-ssl`: Generate an SSL certificate for one or more domains. Ex. `bin/setup-ssl magento.test foo.test`
- `bin/setup-ssl-ca`: Generate a certificate authority and copy it to the host.
- `bin/start`: Start all containers, good practice to use this instead of `docker-compose up -d`, as it may contain additional helpers.
- `bin/status`: Check the container status.
- `bin/stop`: Stop all project containers.
- `bin/stopall`: Stop all docker running containers
- `bin/update`: Update your project to the most recent version of `docker-magento`.
- `bin/xdebug`: Disable or enable Xdebug. Accepts params `disable` (default) or `enable`. Ex. `bin/xdebug enable`
