Далее настраиваем ссылки, по-умолчанию маршрутизация имеет вид /index.php?r=site%2Fabout, переведём ее в такой 
вид /site/about. Для этого создадим файл web/.htaccess с содержимым как рекомендуют в оф. гайде:

Options +FollowSymLinks
IndexIgnore */*

RewriteEngine on

# if a directory or a file exists, use it directly
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d

# otherwise forward it to index.php
RewriteRule . index.php



-------   web.php  ------

 'urlManager' => [
            'enablePrettyUrl' => true,
            'showScriptName' => false,
            'rules' => [
            ],
        ],
