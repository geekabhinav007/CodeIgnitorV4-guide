[Home](./index.html){: .btn .fs-10 .mr-4}
# News Section Tutorial

- Check that the database connectivity is done or not.
- check for phpmyadmin else on terminal 
 ```shell
 sudo mysql
 ```
 - Create a user name "Let say" `ci` with password `abc`.
 
 ```sql
 sudo mysql
 
 CREATE USER 'ci'@'localhost' IDENTIFIED BY 'abc';
 
 GRANT ALL PRIVILEGES ON *.* TO 'ci'@'localhost';

 FLUSH PRIVILEGES;
 ```
 - Create database and create table by following query:
 
 ```sql
 
 CREATE DATABASE ci;
 
 USE ci;
 
 CREATE TABLE news (
    id INT UNSIGNED NOT NULL AUTO_INCREMENT,
    title VARCHAR(128) NOT NULL,
    slug VARCHAR(128) NOT NULL,
    body TEXT NOT NULL,
    PRIMARY KEY (id),
    KEY slug (slug)
);

INSERT INTO news VALUES
(1,'Elvis sighted','elvis-sighted','Elvis was sighted at the Podunk internet cafe. It looked like he was writing a CodeIgniter app.'),
(2,'Say it isn\'t so!','say-it-isnt-so','Scientists conclude that some programmers have a sense of humor.'),
(3,'Caffeination, Yes!','caffeination-yes','World\'s largest coffee shop open onsite nested coffee shop for staff only.');
 
```

- Now add following data in `.env` file under ci folder.
```shell
database.default.hostname = localhost
database.default.database = ci
database.default.username = ci
database.default.password = abc
database.default.DBDriver = MySQLi
```
- Open up the `app/Models/` directory and create a new file called NewsModel.php

```shell
cd
cd /var/www/html/ci/app/Models/
touch NewsModel.php
```
- Add following code to `NewsModel.php` File:

```php
<?php

namespace App\Models;

use CodeIgniter\Model;

class NewsModel extends Model
{
    protected $table = 'news';
}
```
- Edit `NewsModel.php` file under `/apps/Models/`

```php
public function getNews($slug = false)
    {
        if ($slug === false) {
            return $this->findAll();
        }

        return $this->where(['slug' => $slug])->first();
    }
```
- Now create a file under `app/Controllers/` with name `News.php`.
- Add following code to `News.php`.

```php
<?php

namespace App\Controllers;

use App\Models\NewsModel;

class News extends BaseController
{
    public function index()
    {
        $model = model(NewsModel::class);

        $data['news'] = $model->getNews();
    }

    public function view($slug = null)
    {
        $model = model(NewsModel::class);

        $data['news'] = $model->getNews($slug);
    }
}
```
- Change the index function in the file News.php at location `app/Controllers/News.php`.
```php
public function index()
    {
        $model = model(NewsModel::class);

        $data = [
            'news'  => $model->getNews(),
            'title' => 'News archive',
        ];

        return view('templates/header', $data)
            . view('news/overview')
            . view('templates/footer');
    }
```
- Also chanage the view function in the file News.php at location
```php
public function view($slug = null)
    {
        $model = model(NewsModel::class);

        $data['news'] = $model->getNews($slug);

        if (empty($data['news'])) {
            throw new \CodeIgniter\Exceptions\PageNotFoundException('Cannot find the news item: ' . $slug);
        }

        $data['title'] = $data['news']['title'];

        return view('templates/header', $data)
            . view('news/view')
            . view('templates/footer');
    }
```
- Create a file name `overview.php` at location `app/Views/news/` and add following code to overview.php file:

```php

<h2><?= esc($title) ?></h2>

<?php if (! empty($news) && is_array($news)): ?>

    <?php foreach ($news as $news_item): ?>

        <h3><?= esc($news_item['title']) ?></h3>

        <div class="main">
            <?= esc($news_item['body']) ?>
        </div>
        <p><a href="/news/<?= esc($news_item['slug'], 'url') ?>">View article</a></p>

    <?php endforeach ?>

<?php else: ?>

    <h3>No News</h3>

    <p>Unable to find any news for you.</p>

<?php endif ?>
```

- Create a file `view.php` under `app/Views/news/` and add following code in the file `view.php`.

```php
<h2><?= esc($news['title']) ?></h2>
<p><?= esc($news['body']) ?></p>
```

- Now change the Routing file under Config folder.
- Navigate to `app/Config/` and open `Routes.php` file using following command:

```shell
gedit Routes.php
```
- Comment out all the routing and add these routing at 38 line 

```php
/*
 * --------------------------------------------------------------------
 * Route Definitions
 * --------------------------------------------------------------------
 */

// We get a performance increase by specifying the default
// route since we don't have to scan directories.

$routes->get('/', 'Home::index');
$routes->get('news/(:segment)', 'News::view/$1');
$routes->get('news', 'News::index');
$routes->get('pages', 'Pages::index');
$routes->get('(:any)', 'Pages::view/$1');
```
- Start your php server by follwing command:
```php
php spark serve
```
- You can see your desire result at `localhost:8080/news`.

### Happy Learning
