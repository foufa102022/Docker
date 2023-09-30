# Docker
# Les commandes à suivre pour lancer le container
## docker build -t my-image . 
## docker volume create my_database 
## docker run -dit --name chetoui_cont1 -v /home/chfoufa/docker-exam/Ex1/application:/var/www/html -v my_database:/var/lib/mysql -p 8888:80 my-image
> vous pouver acceder à l'application dans le brawser via : localhost:8888
