# DOCKER PRESTASHOP

Este docker utiliza como base o docker oficial do Prestashop, apenas separando a pasta do plugin do Mercado Pago para mapeamento local do volume.

## Uso

> 1 - Crie um arquivo chamado .env usando de base o arquivo .env.sample

> 2 - Defina o path dos arquivos de SSL neste arquivo

> 3 - No arquivo docker-compose, comente o bloco do mysql caso não precise do banco de dados rodando local

> 4 - `docker-compose up -d --build` para executar os containers

> 5 - Em caso de erro de permissões nos arquivos, executar na pasta do docker: `chown -R ubuntu: mercadopago`

> 6 - Depois da instalação, remova a pasta "install" do servidor: `docker exec prestashop_app rm -rf install`

## Local with self signed certificates
[Help](https://deliciousbrains.com/ssl-certificate-authority-for-local-https-development/)\
In the "certs" folder there's a self-signed key pair.\
To add these certs to be accepted by the browser enter the certs folder:\
`sudo security add-trusted-cert -d -r trustRoot -k "/Library/Keychains/System.keychain" myCA.pem`

## Configuring XDebug local
To run XDebug you need to set the path mappings.\
### PHPSTORM:
> 1 - Go to `Preferences` > `PHP` > `Servers`
>
> 2 - Add a server clicking +
>
> 3 - Put the following options:
> - Name: localhost
> - Host: localhost
> - Port: 443
> - Check "Use Path mappings"
>   - Expand the project folder.
>   - Where there's `index.php` on the left column, put `/var/www/html/index.php` on the right one
>   - Where there's `mercadopago` on the left column, put `/var/www/html/modules/mercadopago` on the right one
>
> 4 - Click `Apply` then `OK`

### VSCODE
> 1 - Install de official Xdebug extension. Serach for: `xdebug.php-debug`\
> 2 - On the top menu click on `Run` then `Add configuration` then select `PHP`\
> 3 - Put the following config on the list:
> ```
> {
>   "name": "Listen for Prestashop Docker XDebug",
>   "type": "php",
>   "request": "launch",
>   "port": 9003,
>   "pathMappings": {
>       "/var/www/html/index.php": "${workspaceRoot}/index.php",
>       "/var/www/html/modules/mercadopago": "${workspaceRoot}/mercadopago",
>   },
>   "log": true
> },
> 4 - Then on the run tab click `Run`
> ```
