<<<<<<< HEAD
# Static Pages Tutorial

This tutorial assumes you’ve downloaded CodeIgniter and installed the framework in your development environment.

## Make our First Controller

- Create a file at `app/Controllers/Pages.php` with following code:

- Make a file name Pages.php and copy paste below code in your Pages.php file:

- Run one command at a time.

- if you folder name is different from ci rename it as ci to use furthure commands:

```console
cd
cd /var/www/html/ 
sudo mv your-file-name ci

- now check your folder is renamed or not by navigating /var/www/html/.

```console
cd
cd /var/www/html/ci/app/Controllers/
touch Pages.php
```

```php
<?php

namespace App\Controllers;

class Pages extends BaseController
{
    public function index()
    {
        return view('welcome_message');
    }

    public function view($page = 'home')
    {
        // ...
    }
}
```
Note : if you are using vim editor(or wants to use vim : `sudo apt-get install vim` ) use press `esc` and then `:wq` to save and quit simlarly `:q` to quit without saving. Open file in vim use `vim file_name`. use arrow to nagigate.  

- Create the header at `app/Views/templates/header.php` and add the following code:

```console
cd
cd /var/www/html/ci/app/Views/
mkdir templates
cd templates/
touch header.php
```
- Now open the file header.php and add following code:

```html
<!doctype html>
<html>
<head>
    <title>CodeIgniter Tutorial</title>
</head>
<body>

    <h1><?= esc($title) ?></h1>
```
- Now make file name footer.php

```console
cd
cd /var/www/html/ci/app/Views/
mkdir templates
cd templates/
touch footer.php
```
- Now add the following code to footer.php.

```php
    <em>&copy;Kumar Abhinav 2021</em>
</body>
</html>
```
- now navigate to app/Views/pages.

```console
cd
cd /var/www/html/ci/app/Views/
mkdir pages
cd pages
touch home.php
touch about.php
```

- Add following code to home.php:

```php
<?php
echo "Hello World"
?>
```

- Add following code to about.php:

```php
<?php
echo" Hello World I am about page ";
?>
```



=======
[Home](./index.html){: .btn .fs-10 .mr-4}

# static page
>>>>>>> origin
