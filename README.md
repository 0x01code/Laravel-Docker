# Laravel-Docker
Laravel in Dcoker Compose

# Setup

Copy File Env  
`
cp .env-example .env
`  
`
cp src/.env-example .env
`

Setup env  
`
vim .env
`  
`
vim src/.env
`  

# Run Docker  
RUN Mode Develop  
`
docker-compose -f docker-compose-dev.yml up -d
`  

RUN Mode Production  
`
docker-compose up -d
`

# Exec Docker
`
docker exec -it php bash
`  

# Dependencies Install
`
composer install
`  
`
npm install
`  

# Setup Laravel
Generate Key  
`
php artisan key:generate
`

# Phpmyadmin For Dev Mode
http://localhost:81
