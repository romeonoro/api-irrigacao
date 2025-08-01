https://getcomposer.org/download/
https://www.postman.com/downloads/

php 8.3.0

composer global require laravel/installer



- MYSQL -> CREATE DATABASE Gerenciamento;
- .env -> DB_DATABASE=Gerenciamento
DB_USERNAME=root
DB_PASSWORD=**
- JWT_SECRET="senha"
- Criar pasta do projeto (fora do OneDrive), subpasta backend, cmd como adm -> laravel new Gerenciamento[none, 0] (estrutura do projeto);
- IDE Intellij (extensoes)
- routes -> api.php -> Route::post('/auth/register', [AuthController::class, 'register']);
Route::post('/auth/login', [AuthController::class, 'login']);
Route::post('/auth/logout', [AuthController::class, 'logout']);
- app -> Http.Controllers -> AuthController.php -> registro, login e logout de usuário com token JWT
