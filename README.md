# Laravel 9

# install composer.json
composer install || composer update

# copy file environment
cp .env.example .env

# generate key
php artisan key:generate

# connect link storage
php artisan storage:link

# migrate db
php artisan migrate

# run tests
php artisan serve  #localhost:8000

# Clear cache 
php artisan config:cache 
php artisan cache:clear 

# install swagger
1. composer require "darkaonline/l5-swagger"
2. file l5-swagger: edit title, edit generate_always -> true
3. php artisan vendor:publish --provider "L5Swagger\L5SwaggerServiceProvider"
4. Open your AppServiceProvider (located in app/Providers) and add this line in register function

$this->app->register(\L5Swagger\L5SwaggerServiceProvider::class);

or open your config/app.php and add this line in providers section

L5Swagger\L5SwaggerServiceProvider::class,

5. add config Controller (open Controller.php example)

6.  php artisan l5-swagger:generate # optional

7. if system requires Open API flow step 

composer require vyuldashev/laravel-openapi

'providers' => [
    // ...
    Vyuldashev\LaravelOpenApi\OpenApiServiceProvider::class,
];

php artisan vendor:publish --provider="Vyuldashev\LaravelOpenApi\OpenApiServiceProvider" --tag="openapi-config"

php artisan openapi:generate