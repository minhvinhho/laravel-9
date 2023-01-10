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
5. add config Controller
/**
 * @OA\Info(
 *      version="1.0.0",
 *      title="L5 OpenApi",
 *      description="L5 Swagger OpenApi description",
 *      @OA\Contact(
 *          email=""
 *      ),
 *     @OA\License(
 *         name="Apache 2.0",
 *         url="https://www.apache.org/licenses/LICENSE-2.0.html"
 *     )
 * )
 * 
 * @OA\Get(
 *     path="/",
 *     description="Home page",
 *     @OA\Response(response="default", description="Welcome page")
 * )
 */
6.  php artisan l5-swagger:generate # optional

7. if system requires Open API flow step 

composer require vyuldashev/laravel-openapi

'providers' => [
    // ...
    Vyuldashev\LaravelOpenApi\OpenApiServiceProvider::class,
];

php artisan vendor:publish --provider="Vyuldashev\LaravelOpenApi\OpenApiServiceProvider" --tag="openapi-config"

php artisan openapi:generate