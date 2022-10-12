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

- Move the renamed folder at /var/www/html/, now change directory where `ci` or `CI` is present and run following command from that directory.

```console
sudo mv ci /var/www/html/
```
- Now to check all the step run following command and see:

```console
cd /var/www/html/
ls
```
- If ci/CI folder is present then you have done with Installation and enviroment setup.

