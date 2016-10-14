Далее настраиваем ссылки, по-умолчанию маршрутизация имеет вид /index.php?r=site%2Fabout, переведём ее в такой 
вид /site/about. Для этого создадим файл web/.htaccess с содержимым как рекомендуют в оф. гайде:

Options +FollowSymLinks

IndexIgnore */*
------ Folder web --------

RewriteEngine on

# if a directory or a file exists, use it directly

RewriteCond %{REQUEST_FILENAME} !-f

RewriteCond %{REQUEST_FILENAME} !-d

# otherwise forward it to index.php

RewriteRule . index.php

------- Folder site -------

Options +FollowSymLinks

IndexIgnore */*

RewriteEngine on

RewriteCond %{REQUEST_URI} !^/(web)

RewriteRule ^assets/(.*)$ /web/assets/$1 [L]

RewriteRule ^css/(.*)$ web/css/$1 [L]

RewriteRule ^js/(.*)$ web/js/$1 [L]

RewriteRule ^images/(.*)$ web/images/$1 [L]

RewriteRule (.*) /web/$1

RewriteCond %{REQUEST_FILENAME} !-f

RewriteCond %{REQUEST_FILENAME} !-d

RewriteRule . /web/index.php

-------   web.php  ------

 'urlManager' => [
            'enablePrettyUrl' => true,
            'showScriptName' => false,
            'rules' => [
            ],
        ],
