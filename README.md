# DOCKER LEMP 🚀
- Nginx
- PHP 7.2-fpm or 7.3-fpm
- MySQL5.7.33 or MariaDB or MySQL8
- PHPMyAdmin
- Maildev

## :rocket: Quickstart 
- Install and launch Docker  
- `cp .env.dist .env`  
- `docker-compose up`

| Service      | Path                      |
| ------------ | ------------------------- |
| Website      | `http://localhost:80`     | 
| PhpMyAdmin   | `http://localhost:8081`   |
| Mail catcher | `http://localhost:8082`   |

| Folder       | Note                      |
| ------------ | ------------------------- |
| bin          | Contain all Dockerfile    | 
| docker       | Contain all settings      |
| log (post up)| Contain log               |
| public       | Root folder               |

## :tent: Use a virtual host
- On your machine, run `$ sudo nano /etc/hosts` and add `127.0.0.1   myhost.local`
- Change the server name in `docker/nginx/nginx.conf#L3` to `myhost.local`
- Modify `.env` and set `SERVER_PORT=80`
- Run `$ docker-compose up`
- If it fails make sure no service like Apache is running on port 80 

## About MySQL credentials
If you change mysql credentials in .env you have to re-create mysql container:
- Database will be deleted, make a dump with PhpMyAdmin
- Remove db folder : `$ rm -rf docker/db`
- Run : `docker-compose up` 
- Re-import your database on PhpMyAdmin
