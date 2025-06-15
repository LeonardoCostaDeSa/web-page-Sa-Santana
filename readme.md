1. Inicie o MySQL pelo XAMPP

Abra o XAMPP Control Panel.

Clique em Start na linha MySQL.

(Opcional) Clique em Admin para abrir o phpMyAdmin.

2. Crie o banco de dados

No phpMyAdmin ou terminal MySQL execute:

CREATE DATABASE petshop CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;

Você pode usar outro nome, mas anote para o próximo passo.

3. Configure o arquivo .env

Copie o exemplo:

cp .env.example .env

Edite as linhas de banco de dados (ajuste se necessário):

DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=petshop      # mesmo nome criado no passo 3
DB_USERNAME=root         # ou crie um usuário próprio
DB_PASSWORD=             # coloque a senha, se houver

Gere a chave da aplicação:

php artisan key:generate

4. Instale as dependências do Composer

composer install

4.1 Limite de requisições GitHub (Opcional)

Se o Composer pedir um Personal Access Token:

Acesse GitHub → Settings → Developer settings → Personal access tokens → Tokens (classic).

Crie um token com o escopo read:packages (e repo, se o repositório for privado).

Configure no Composer (global ou no projeto):

composer config --global github-oauth.github.com SEU_TOKEN_AQUI

5. Rode as migrações

php artisan migrate

Isso criará todas as tabelas necessárias no banco.

Erro 1045 (Access denied): verifique usuário/senha no .env e execute php artisan config:clear antes de tentar novamente.

6. (Opcional) Popular dados de teste

php artisan db:seed         # se existirem Seeders

7. Suba o servidor de desenvolvimento

php artisan serve

A API estará acessível em http://127.0.0.1:8000.