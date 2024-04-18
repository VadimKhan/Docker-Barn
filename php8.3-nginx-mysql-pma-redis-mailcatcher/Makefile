up:
	docker-compose up -d

down:
	docker-compose down

build:
	docker-compose build

clean: 
	composer fresh npm-i npm-dev optimize

composer:
	docker-compose exec phpapp sh -c "composer install && composer update"

optimize:
	docker-compose exec phpapp sh -c "php artisan cache:clear && php artisan view:clear && php artisan config:clear"

fresh:
	docker-compose exec phpapp sh -c "php artisan migrate:fresh --seed"

larastan:
	docker-compose exec phpapp sh -c "./vendor/bin/phpstan analyse --memory-limit=2G"

npm-i:
	docker-compose exec phpapp sh -c "npm i"

npm-dev:
	docker-compose exec phpapp sh -c "npm run dev"
