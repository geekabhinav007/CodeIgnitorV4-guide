[Static Page](./docs/static.md){: .btn .mr-4 .fs-10 .fw-500}   [News Section](./docs/news.md){: .btn  .mr-4 .fs-10 .fw-500}

# Installation 

- Install lampp using Following commands:

```console
sudo apt-get install lamp-server^
```

- Installation of some dependencies (Server Requirement):

```console
sudo apt-get -y install php-intl\
                     php-mbstring\
                     php-json\
                     php-mysqlnd\
                     php-xml\
                     php-curl
```

- Now download CodeIgnitor 4 from its [website](https://www.codeigniter.com/download) and extract the file at same directory or folder.

- After that you can their is big name of folder and also their are two folder of same name for convience rename the inner folder to `ci` or `CI`.

- Move the renamed folder at /var/www/html/, now switch to the directory where `ci` or `CI` is present and run following command from that directory.

```console
sudo mv ci /var/www/html/
```
- Now to check all the step run following command and see:

```console
cd /var/www/html/
ls
```
- If ci/CI folder is present then you have done with Installation and enviroment setup.

- Now you can see you have following file and folder under ci folder.


[https://github.com/geekabhinav007/CodeIgnitorV4-guide/blob/main/img/intialDirectory.png](https://github.com/geekabhinav007/CodeIgnitorV4-guide/blob/main/img/intialDirectory.png)

## Intial Configuration

- Open the app/Config/App.php comment out baseURL at line 27 and add new base url as following:

```php
public $baseURL = 'http://localhost/ci/public/';
```

```
Note : If you will be running your site using a web server (e.g., Apache or Nginx), you will need to modify the permissions for the writable folder inside your project, so that it is writable by the user or account used by your web server.
```
- use following command to give executable permission to writable directory under ci directory:

```console
sudo chmod -R 777 writable/
```
- if you are not able to see Welcome page like below at `http://localhost/ci/public`
then restart your server by using following command:

[https://github.com/geekabhinav007/CodeIgnitorV4-guide/blob/main/img/Welcomepage.png](https://github.com/geekabhinav007/CodeIgnitorV4-guide/blob/main/img/Welcomepage.png)


```console
sudo systemctl restart apache2.service
```
### Thanks for following tutorial. 
