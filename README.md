# Como criar um Script para instalação do Apache2 + Subir Página Html ( Ubuntu )


# Preview
(https://files.tecnoblog.net/wp-content/uploads/2022/04/ubuntu-22-04-lts.jpg)

Para subir uma página em html através do Ubuntu, é necessário primeiramente criar um diretório em que ele contenha os arquivos a serem configurados, neste caso utilizaremos este repositório como exemplo, com o mesmo sendo incluso no diretório criado. 

Primeiro iremos criar um arquivo que será chamado de " instalar_apache.sh", em seguida iremos utilizar os seguintes comandos:

bash
sudo nano instalar_apache.sh
bash
#!/bin/bash
sudo apt update ( atualizar a lista de pacotes )
sudo apt install -y apache2 ( instalar o apache )
sudo mkdir -p /var/www/homepage ( criar uma pasta para ser utilizada como diretório )
sudo git clone + link do repositório ( clonar repositório )

Em seguida iremos configurar o Apache2 para usar o diretório criado.

<VirtualHost *:80>
  ServerAdmin amind@homepage
  ServerName homepage
  ServerAlias www.homepage
  DocumentRoot /var/www/homepage/public_html
  <Directory /var/www/homepage>
  ErrorLog /error.log
  CustomLog /access.log combined
</VirtualHost>

Em seguida, configurar o ip de domínio, no caso iremos utilizar 127.0.0.1

sudo a2ensite homepage.conf ( ativar o site )
sudo service apache2 restar ( reiniciar o serviço Apache2 )
sudo chmod +x install apache.sh ( Dar permissão ao script )
sudo ./install apache.sh


