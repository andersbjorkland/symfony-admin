# Symfony Admin Interface
This project is a scaffold for quickly setting up an admin with an API interface. Included with this project is:

* Symfony maker-bundle
* Symfony Security
* Symfony Mailer
* Doctrine
* API Platform
* Easy Admin
* symfonycasts/verify-email-bundle 
* symfonycasts/reset-password-bundle

## Get started
**Clone repository**  
``git clone https://github.com/andersbjorkland/symfony-admin.git``

**Install dependencies**  
``composer install``

**Basic configuration**  
In dev-environment, default db is a mysql database called 'symfony-admin'. This can be changed in the *.env*-file.

This project uses an email to verify user and reset password. It uses SMTP which you should configure in a .env.local (as this file is gitignored by default). Configure it like this:  
``MAILER_DSN=smtp://mailer@example.com:password@smtp.example.com:465``

Once the mailer credentials are configured, you are to configure the mailer parameter in *config/services* with the same email:  
``mailer: 'mailer@example.com'``


## Create Database
Provided you have configured the database that you want, otherwise fallbacks to default: symfony-admin, you can create the database. Launch your database engine, for example XAMPP and activate MySQL. You are now ready to initiate it:  
``php bin/console doctrine:database:create``

Next you can prepare the database to accept User entities. These are included by default. Run the following:
``php bin/console doctrine:migrations:migrate``

A basic migration file has been included. Running the command above will insert the correct schema for the user into the database.

## Install public assets
Easy Admin comes with assets that should be installed. It should install API Platform assets as well, if they haven't been installed already. Run the following:  
``php bin\console assets:install``

## Adding entities
Having maker-bundle and API Platform means that creation of entities and exposing them for the API is easy. You should configure the entities afterwards to only expose fields you want to have exposed. Run the following command to create entities (you will be asked if you want to add them for the API too):  
``php bin\console make:entity``

After creating entites you should run the following commands:  
``php bin\console make:migration``  
``php bin\console doctrine:migrations:migrate``



