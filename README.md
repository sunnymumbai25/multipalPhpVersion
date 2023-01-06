# multipalPhpVersion
D:\xampp_8.2\php7.2
  php.ini
    extension_dir = "ext" #uncomment following line in php.ini file

D:\xampp_8.2\apache\conf\extra
  httpd-vhosts.conf
    #add below command to config folder
    <VirtualHost *:80>
      ServerName oldversionnrai
      DocumentRoot "D:/xampp_8.2/htdocs/php7"
      <Directory  "D:/xampp_8.2/htdocs/php7">
        Options +Indexes +Includes +FollowSymLinks +MultiViews
        AllowOverride All
        Require local
      </Directory>

        UnsetEnv PHPRC
      <FilesMatch "\.php$">
        php_flag engine off
        SetHandler application/x-httpd-php7.2
        Action application/x-httpd-php7.2 "/php7.2/php-cgi.exe"
      </FilesMatch>
    </VirtualHost>

    <VirtualHost *:80>
      ServerName oldversionnrais
      DocumentRoot "D:/xampp_8.2/htdocs/php8"
      <Directory  "D:/xampp_8.2/htdocs/php8">
        Options +Indexes +Includes +FollowSymLinks +MultiViews
        AllowOverride All
        Require local
      </Directory>
    </VirtualHost>

#made change on host file
C:\Windows\System32\drivers\etc
  hosts
    127.0.0.1 oldversionnrai 
    127.0.0.1 oldversionnrais

#add below command to file
D:\xampp_8.2\apache\conf\extra
  httpd-xampp.conf
    <IfModule mime_module>
        AddType text/html .php .phps
    </IfModule>

    ScriptAlias /php-cgi/ "D:/xampp_8.2/php/"
    <Directory "D:/xampp_8.2/php"> #add
        AllowOverride None
        Options None
        Require all denied
        <Files "php-cgi.exe">
              Require all granted
        </Files>
    </Directory>

    ScriptAlias /php7.2/ "D:/xampp_8.2/php7.2/" #add 
    <Directory "D:/xampp_8.2/php7.2">
        AllowOverride None
        Options None
        Require all denied
        <Files "php-cgi.exe">
              Require all granted
        </Files>
    </Directory>

    <Directory "D:/xampp_8.2/cgi-bin">
        <FilesMatch "\.php$">
            SetHandler cgi-script
        </FilesMatch>
        <FilesMatch "\.phps$">
            SetHandler None
        </FilesMatch>
    </Directory>

    <Directory "D:/xampp_8.2/htdocs/xampp">
        <IfModule php_module>
          <Files "status.php">
            php_admin_flag safe_mode off
          </Files>
        </IfModule>
        AllowOverride AuthConfig
    </Directory>

    <IfModule alias_module>
        Alias /licenses "D:/xampp_8.2/licenses/"
        <Directory "D:/xampp_8.2/licenses">
            Options +Indexes
            <IfModule autoindex_color_module>
                DirectoryIndexTextColor  "#000000"
                DirectoryIndexBGColor "#f8e8a0"
                DirectoryIndexLinkColor "#bb3902"
                DirectoryIndexVLinkColor "#bb3902"
                DirectoryIndexALinkColor "#bb3902"
            </IfModule>
            Require local
            ErrorDocument 403 /error/XAMPP_FORBIDDEN.html.var
       </Directory>

        Alias /phpmyadmin "D:/xampp_8.2/phpMyAdmin/"
        <Directory "D:/xampp_8.2/phpMyAdmin">
            AllowOverride AuthConfig
            Require local
            ErrorDocument 403 /error/XAMPP_FORBIDDEN.html.var
        </Directory>

        Alias /webalizer "D:/xampp_8.2/webalizer/"
        <Directory "D:/xampp_8.2/webalizer">
            <IfModule php_module>
            <Files "webalizer.php">
              php_admin_flag safe_mode off
            </Files>
            </IfModule>
            AllowOverride AuthConfig
            Require local
            ErrorDocument 403 /error/XAMPP_FORBIDDEN.html.var
        </Directory>
    </IfModule>

D:\xampp_8.2\htdocs\php8\index.php
  <?php    echo  phpversion();?>

D:\xampp_8.2\htdocs\php7\index.php
  <?php    echo  phpversion();?>

    
#Below url run project on browser
http://oldversionnrai/
http://oldversionnrais/
