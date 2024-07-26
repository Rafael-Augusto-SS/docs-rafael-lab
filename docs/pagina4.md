# Configuração do Servidor Apache com WordPress

Eu configurei um servidor Apache para servir um site WordPress com um domínio personalizado. Segui os seguintes passos:

## 1. Configurar o Apache

1. *Copiei e editei o arquivo de configuração*

    Fui para o diretório de configuração do Apache e copiei o arquivo padrão para um novo arquivo de configuração:

        cd /etc/apache2/sites-available
        nano /etc/apache2/sites-available/www.rafael.lab.conf
    
    Então, editei o novo arquivo de configuração:

        sudo vim www.rafael.lab.conf
    

    No editor, adicionei o ServerName e alterei o DocumentRoot da seguinte forma:

        <<VirtualHost *:80>
            ServerAdmin webmaster@rafael.lab
            ServerName www.rafael.lab
            DocumentRoot /var/www/html/wordpress

            <Directory /var/www/html/wordpress>
                Options Indexes FollowSymLinks
                AllowOverride All
                Require all granted
            </Directory>

            ErrorLog ${APACHE_LOG_DIR}/www.rafael.lab_error.log
            CustomLog ${APACHE_LOG_DIR}/www.rafael.lab_access.log combined
        </VirtualHost>

    

    Salvei e saí do editor
2. *Habilitei o novo site e módulos necessários*

        a2ensite www.rafael.lab.conf
        a2enmod rewrite

    Reiniciei o Apache para aplicar as mudanças:

        systemctl restart apache2
    
## 2. Configurar o Arquivo /etc/hosts

1. *Editei o arquivo /etc/hosts*


    Abri o arquivo /etc/hosts:

        nano /etc/hosts
    
    Adicionei a linha para mapear o domínio para o IP local:

        10.0.2.15 www.rafael.lab
    
    Salvei e saí do editor

## 3. Acessar o site:
   O site está acessível em: http://www.rafael.lab no navegador