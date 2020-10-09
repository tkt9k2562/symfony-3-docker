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
