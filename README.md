
## Sobre Laradock

Laradock é um ambiente de desenvolvimento PHP completo para Docker.
Ele suporta uma variedade de serviços comuns, todos pré-configurados para fornecer um ambiente de desenvolvimento PHP pronto.

## Como Utilizar

1 - Clonar um projeto inicial do Laravel no Github para o wsl

```bash
git clone https://github.com/laravel/laravel.git nome_do_projeto
```

2 - Clonar para dentro da pasta do projeto o laradock

```bash
git clone https://github.com/Laradock/laradock.git
```

3 - Na pasta laradock copiar o .env.example para .env

```env
cp .env.example .env
```

4 - Editar o .env da pasta laradock com os recursos que pretende usar

* Seleciona a versão dp PHP
```env
PHP_VERSION=8.2
```

* Define o prefixo dos containers
```env
COMPOSE_PROJECT_NAME=laradock
```

* Definindo as variáveis do MySQL
```env
MYSQL_VERSION=latest
MYSQL_DATABASE=default
MYSQL_USER=default
MYSQL_PASSWORD=secret
MYSQL_PORT=3306
MYSQL_ROOT_PASSWORD=root
MYSQL_ENTRYPOINT_INITDB=./mysql/docker-entrypoint-initdb.d
```

5 - Na pasta do projeto copiar o .env.example para .env

```env
cp .env.example .env
```

6 - Editar o .env do projeto

```env
APP_NAME=laradock
```

```env
DB_CONNECTION=mysql
DB_HOST=mysql
DB_PORT=3306
DB_DATABASE=default
DB_USERNAME=default
DB_PASSWORD=secret
```

7 - Executar os contêniners que irá utilizar (na pasta laradock)

```bash
docker-compose up -d nginx mysql workspace 
```

8 - Acessar o bash do contêiner workspace (através da pasta laradock)

```bash
docker-compose exec workspace bash
```

9 - No bash do contêiner workspace, instalar as bibliotecas com o composer

```bash
composer install
```

10 - Gerar a APP_KEY

```bash
php artisan key:generate
```

11 - Para conectar com o Banco de Dados MySQL utilizar os seguintes parâmetros:

* Name: laradock
* Host: 127.0.0.1
* Port: 3306
* Username: default
* Password: secret
