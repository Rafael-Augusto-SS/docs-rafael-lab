# Configuração do Servidor Apache para MkDocs

Eu configurei um servidor Apache para servir um site MkDocs com um domínio personalizado. Segui os seguintes passos:

## 1. Configurar o Apache

1. *Copiei e editei o arquivo de configuração*

    Fui para o diretório de configuração do Apache e copiei o arquivo padrão para um novo arquivo de configuração:

    ```
    bash
    cd /etc/apache2/sites-available
    cp 000-default.conf docs.rafael.lab.conf
    ```
    
    Então, editei o novo arquivo de configuração:

    ```
    bash
    sudo vim docs.rafael.lab.conf
    ```

    No editor, adicionei o ServerName e alterei o DocumentRoot da seguinte forma:
        
        <VirtualHost *:80>
            ServerAdmin webmaster@rafael.lab
            ServerName docs.rafael.lab

            ProxyPass / http://127.0.0.1:8000/
            ProxyPassReverse / http://127.0.0.1:8000/

            ErrorLog ${APACHE_LOG_DIR}/docs.rafael.lab_error.log
            CustomLog ${APACHE_LOG_DIR}/docs.rafael.lab_access.log combined
        </VirtualHost>
    
    Salvei e saí do editor    
2. *Habilitei o novo site e módulos necessários*

    
        a2ensite docs.rafael.lab.conf
        a2enmod rewrite
    

    Reiniciei o Apache para aplicar as mudanças:
    ```
    bash
    systemctl restart apache2
    ```
    
## 2. Configurar o Arquivo /etc/hosts

1. *Editei o arquivo /etc/hosts*


    Abri o arquivo /etc/hosts:

    ```
    bash
    nano /etc/hosts
    ```

    Adicionei a linha para mapear o domínio para o IP local:

    ```
    bash
    127.3.1.1 docs.rafael.lab
    ```

    Salvei e saí do editor

## 3. Acessar o site:
   O site está acessível em: http://docs.rafael.lab no navegador