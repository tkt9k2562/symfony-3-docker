## Symfony Docker
- symfony 3.4
- php 7.4
- mysql 8.0

#### Reference
來源 : https://medium.com/@ger86/how-to-integrate-docker-into-a-symfony-based-project-f06164dc7944

#### Step 
1. docker-compose.yml
2. nginx
3. php
4. db (等等需更改密碼為 env)
5. 最後 , phpmyadmin localhost:8000 , symfony localhost:8001

#### Run
1. 
重新建置 (無cache)
sudo docker-compose build --no-cache

啟動
sudo docker-compose up -d 

關閉
sudo docker-compose down

單純重啟 php (例如更改 php environment APP_ENV 或 DATABASE_URL)
docker-compose up -d php

2. 
docker-compose exec db bash 
(或著 docker exec -it symfony-3-docker_db_1 bash)

3. 
docker-compose exec php bash
(或著 docker exec -it symfony-3-docker_php_1 bash)

"""
請"不要"使用以下 , 可能安裝不完整
curl -sS https://get.symfony.com/cli/installer | bash
mv /root/.symfony/bin/symfony /usr/local/bin/symfony

使用 symfony new --help 檢查指令
symfony new symfony --dir=/var/www/symfony --version=3.4

建議"不要"使用 (因為外層已經有 git, 內層不用 git, 直接安裝沒問題的)
git config --global user.email tkt9k2562@gmail.com
git config --global user.name tkt9k2562
"""

我使用 composer create-project symfony/framework-standard-edition symfony "3.4.*" 來安裝 
(而我的路徑在 /var/www/ , 也就是建立 /var/www/symfony , 而非 /var/www/html)

注意 parameters.yml 要更改: 
    database_host: db:3306 # 正常是 127.0.0.1 , 但 docker 是 db:3306
    database_port: 3306
    database_name: symfony_user
    database_user: root
    database_password: symfony_db
    
然後 
php bin/console doctrine:database:drop --force
php bin/console doctrine:database:create
因為一開始就建立好 database 了

可使用 localhost:8000 開啟 phpmyadmin
帳號 root 
密碼 symfony_db
(可見 symfony/app/config/parameters.yml)

#### Composer
1. 
composer require doctrine/doctrine-migrations-bundle "^1.3"
