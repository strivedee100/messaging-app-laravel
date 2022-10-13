## Messaging Application

This application is implemented by using pusher API.

## Installation

### Step 1: Clone the repository
Find a location on your computer where you want to store the project. A directory made for projects is generally a good choice.

Launch a bash console there and clone the project.

```bash
git clone https://github.com/strivedee100/messaging_demo_laravel.git
```
### Step 2: cd into the project
You will need to be inside the project directory that was just created, so cd into it.
```bash
cd messaging_demo_laravel
```

### Step 3: Install composer dependencies
Whenever you clone a new Laravel project you must now install all of the project dependencies. This is what actually installs Laravel itself, among other necessary packages to get started.

```bash
$ composer install
```

### Step 4: Copy the .env file
.env files are not generally committed to source control for security reasons. But there is a .env.example which is a template of the .env file that the project requires.

So you should make a copy of the .env.example file and name it .env so that you can setup your local deployment configuration in the next few steps.

```bash
make a copy of .env.example and rename to .env

put database credentials in .env file
```
### Step 5: Generate an app encryption key
Laravel requires you to have an app encryption key which is generally randomly generated and stored in your .env file. The app will use this encryption key to encode various elements of your application from cookies to password hashes and more.

Laravel’s command line tools thankfully make it easy to generate this. Run this command in the terminal to generate that key.

```bash
$ php artisan key:generate
```

### Step 6: Create an empty database for the application
Create an empty database for your project using the database tools you prefer (phpmyadmin, datagrip, or any other mysql client).

### Step 7: In the .env file, add database information to allow Laravel to connect to the database
You will want to allow Laravel to connect to the database that you just created in the previous step. To do this, you must add the connection credentials in the .env file and Laravel will handle the connection from there.

In the .env file fill in the **DB_HOST**, **DB_PORT**, **DB_DATABASE**, **DB_USERNAME**, and **DB_PASSWORD** options to match the credentials of the database you just created. This will allow you to run migrations in the next step.

### Step 8: Branding & Name
In the .env file feel free to customize the values for **APP_NAME**.

### Step 9: Migrate the database
Once your credentials are in the .env file, now you can migrate your database. This will create all the necessary tables in your database.

`php artisan migrate`

### Step 10: Create and setup pusher account
- Create an account to [pusher](https://pusher.com/)
- Now create a Channels app. Go to the “Keys” page for that app, and make a note of your app_id, key, secret and cluster.
- Put pusher credentials to .env file
```bash
PUSHER_APP_ID=YOUR_PUSHER_APP_ID
PUSHER_APP_KEY=YOUR_PUSHER_APP_KEY
PUSHER_APP_SECRET=YOUR_PUSHER_APP_SECRET
PUSHER_APP_CLUSTER=YOUR_PUSHER_APP_CLUSTER
```
- replace PUSHER_APP_KEY in your app.blade.php
```bash
var pusher = new Pusher('xyz.....', {
                 cluster: 'cb1',
                 forceTLS: true
});
```
### Step 11: Local development server
To run a local development server you may run the following command. This will start a development server at **http://localhost:8000**.

`php artisan serve`
