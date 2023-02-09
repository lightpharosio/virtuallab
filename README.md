### Les captures 1 à 4 représentent : 

- Création d'une Machine virtuelle
- Création d'une machine virtuelle Linux de la Distribution Ubuntu 22.04 server 64 (1vCPU, 1GBRAM) 
- Création d'une machine virtuelle avec un disque fixe de 30GB
- Création d'une machine virtuelle Linux de la Distribution Ubuntu 22.04 server 64 (1vCPU, 1GBRAM) 
- Création d'une machine virtuelle avec un disque dynamique 

### Les capture 5 et 6 représentent : 

- Ouverture de la console virtualbox.
- Récupération de l'addresse IP de la machine allouée par virtualBox à la VM (Virtual Machine) avec la commande 'ifconfig'

### La capture 7 représente : 
sudo apt update
sudo apt install apache2 \
                 ghostscript \
                 libapache2-mod-php \
                 mysql-server \
                 php \
                 php-bcmath \
                 php-curl \
                 php-imagick \
                 php-intl \
                 php-json \
                 php-mbstring \
                 php-mysql \
                 php-xml \
                 php-zip

### La capture 9 représente :
- Les commandes : 'sudo mkdir -p /srv/www'
                  'sudo chown www-data: /srv/www'

- Ces deux commandes créent le répertoire /srv/www et changent son propriétaire en tant que l'utilisateur www-data. Cela permet de configurer un répertoire sécurisé pour installer l'installation de WordPress.

- La commande 'curl https://wordpress.org/latest.tar.gz | sudo -u www-data tar zx -C /srv/www' 

- Consiste à la décompression du fichier .tar dans le répertoire /srv/www.
