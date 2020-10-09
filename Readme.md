## Symfony Docker
- symfony 3.4
- php 7.4 (我不會 7.3)
- mysql 8.0 (我不會 5.7 應該都行)

#### Reference
來源 : https://medium.com/@ger86/how-to-integrate-docker-into-a-symfony-based-project-f06164dc7944

#### Step 
1. docker-compose.yml
2. nginx
3. php
4. db (等等需更改密碼為 env)

#### Run
1. 
重新建置 (無cache)
sudo docker-compose build --no-cache

啟動
sudo docker-compose up -d 

關閉
sudo docker-compose down

2. 
docker-compose exec db bash 
(或著 docker exec -it symfony-3-docker_db_1 bash)

3. 
docker-compose exec php bash
(或著 docker exec -it symfony-3-docker_php_1 bash)

curl -sS https://get.symfony.com/cli/installer | bash
mv /root/.symfony/bin/symfony /usr/local/bin/symfony

使用 symfony new --help 檢查指令
symfony new symfony --dir=/var/www/symfony --version=3.4

建議"不要"使用 (因為外層已經有 git, 內層不用 git, 直接安裝沒問題的)
git config --global user.email tkt9k2562@gmail.com
git config --global user.name tkt9k2562

