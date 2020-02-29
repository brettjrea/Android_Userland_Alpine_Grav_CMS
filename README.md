# Android_Userland_Alpine_Grav_CMS

 A set up script and breakdown to install GravCMS on Android using Alpine Linux on Userland. Haven't tested it on Alpine for WSL or VM but probably will work. Docker definitely needs docker specific commands.
 
 ## Installing quickly with a script.
 
`su -`

`wget https://raw.githubusercontent.com/brettjrea/Android_Userland_Alpine_Grav_CMS/master/setup.sh`

`bash setup.sh`

## Install by doing what the script does snip by snip.

`su -`

`apk update`

`apk add git php7 php7-curl php7-ctype php7-dom php7-gd php7-json php7-mbstring php7-openssl php7-session php7-simplexml php7-xml php7-zip php7-iconv php7-phar`

`git config --global http.sslverify "false"`

`php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"`

`php -r "if (hash_file('sha384', 'composer-setup.php') === 'e0012edf3e80b6978849f5eff0d4b4e4c79ff1609dd1e613307e16318854d24ae64f26d17af3ef0bf7cfb710ca74755a') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"`

`php composer-setup.php`

`php -r "unlink('composer-setup.php');"`

`mv composer.phar /usr/local/bin/composer`

`git clone -b master https://github.com/getgrav/grav.git`

`cd ~/grav`

`composer install --no-dev -o`

`bin/grav install`

`bin/gpm install admin -y`

`bin/gpm install git-sync`

`bin/gpm selfupgrade -f`

`bin/gpm update -f`

`php -S localhost:8000 system/router.php`