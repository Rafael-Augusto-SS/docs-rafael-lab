# Instalação para um servidor MkDocs

Bem-vindo ao Guia de instalação de um servidor web estatico com MkDocs

1. Instalar o Módulo venv
```
sudo apt-get update
sudo apt-get install python3-venv
sudo apt install python3 python3-pip -y
```

2. Criar e navegar para o diretório do projeto
```
mkdir var/www/docs.rafael.lab
cd var/www/docs.rafael.lab
python3 -m venv .myenv
```

3. Fazer o restante das instalações necessarias
```
source .venv/bin/active
pip install mkdocs
```

4.criar um arquivo requirements e executa-lo
```
mkdocs
mkdocs-material
mkdocs-mermaid2-plugin

pip install -r requirements.txt

```