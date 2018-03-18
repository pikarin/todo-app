# Todo App

Simple todo app with laravel, vue.js and tailwindcss.

### Prerequisites

+ PHP >= 7.1.3
+ Composer
+ Node.js

### Installing

Clone repository and cd into folder

```sh
git clone 
cd todo-app
```

install composer dependency

```sh
composer install
```

create `.env` file from `.env.example`

```sh
cp .env.example .env
```

generate application key

```sh
php artisan tinker key:generate
```

insert your database credential to .env file

```
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=your_db_name
DB_USERNAME=your_db_user
DB_PASSWORD=your_db_password
```

migrate database
```sh
php artisan migrate
```

install node dependency

```sh
npm install
```

compile js and css

```sh
npm run dev
```

access the app `127.0.0.1:8000`
```sh
php artisan serve
```

## Running the tests

TODO

### And coding style tests

TODO

## Built With

* [Laravel](https://laravel.com/docs/5.6) - The web framework used
* [Vuejs](https://vuejs.org/) - The javascript framework used
* [Tailwindcss](https://tailwindcss.com/) - The css framework used
* [Composer](https://getcomposer.org/) - PHP Dependency Management
* [Node.js](https://nodejs.org/en/)
