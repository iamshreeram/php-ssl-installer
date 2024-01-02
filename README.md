# php-ssl-installer
This is fork of [this gist](https://gist.github.com/iamshreeram/a67abbbd23d56d058786c5530834086b/forks). Steps to install SSL certificate in hostinger.  

### Enable SSH :
```
ssh x123011738@31.170.164.22 -p 65002
```

### Download acme-client
```
git clone https://github.com/kelunik/acme-client
```

### Install composer
```
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"; 
php composer-setup.php;
php -r "unlink('composer-setup.php');";
php composer.phar install --no-dev
```

### Generating SSL
```
php bin/acme setup --server letsencrypt --email admin@email.com --agree-terms
php bin/acme issue --domains yourdomain.com:www.youdomain.com --path /home/x123011738/public_html:/home/x123011738/public_html --server letsencrypt
```

Certificate : `/home/x123011738/acme-client/data/certs/acme-v01.api.letsencrypt.org.directory/yourdomain.com/fullchain.pem`
private key : `/home/x123011738/acme-client/data/certs/acme-v01.api.letsencrypt.org.directory/yourdomain.com/key.pem`

## Add CRT and privatekey in hostinger

### Checking expiration date and renewing SSL certificate
```
php acme-client/bin/acme check --name yourdomain.com --server letsencrypt
```
### Automatically renew Let’s Encrypt SSL certificate with cron job
```
php acme/acme-client/bin/acme issue --domains yourdomain.com:www.yourdomain.com --path /home/x123011738/public_html:/home/x123011738/public_html --server letsencrypt
```
