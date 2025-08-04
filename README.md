# 💧 API de Gerenciamento de Irrigação

Esta API RESTful foi desenvolvida como desafio técnico, utilizando **Laravel** e autenticação **JWT**. Ela permite o gerenciamento de pivôs de irrigação e o registro de irrigações aplicadas.

---

## 🚀 Funcionalidades

- Cadastro e login de usuários com autenticação via JWT.
- CRUD de **Pivôs de Irrigação**.
- CRUD de **Registros de Irrigação** (com verificação de propriedade do pivô).
- Proteção de rotas com token JWT.
- Base de dados SQLite simples para testes rápidos.

---

## ⚙️ Tecnologias Utilizadas

- PHP 8+
- Laravel 10+
- [tymon/jwt-auth](https://github.com/tymondesigns/jwt-auth) (JWT)
- SQLite (persistência simples e portátil)

---

## ✅ Pré-requisitos
### 🧑‍💻 Sistema Operacional Recomendado

- Windows 10 ou superior
- Evite rodar o projeto em diretórios sincronizados com nuvem (como OneDrive)

### ✅ PHP 8.1 ou superior (recomendado: 8.3)

- Verifique se o PHP está instalado:
```bash
  php -v
```
- Site oficial: https://www.php.net/downloads.php

### ✅ Composer
- Gerenciador de dependências do PHP:
```bash
composer -V
```
- Site oficial: https://getcomposer.org/download/
  
### ✅ Laravel Installer
- Instale globalmente com:
```bash
composer global require laravel/installer
```
### ✅ Banco de Dados: SQLite
1. Criar o arquivo SQLite
- No diretório database, crie o arquivo de banco:
```bash
touch database/database.sqlite
```
- No Windows, crie manualmente o arquivo vazio database.sqlite na pasta database/.

2. Configurar o .env
- No seu arquivo .env, altere as configurações do banco para:
```env
DB_CONNECTION=sqlite
DB_DATABASE=/caminho/absoluto/para/database/database.sqlite
```
- Exemplo no Windows:
```env
DB_CONNECTION=sqlite
DB_DATABASE=C:\projetos\Gerenciamento\database\database.sqlite
```
- Importante: Use o caminho absoluto. Laravel não entende caminhos relativos no .env para SQLite.

### 🔐 JWT (Json Web Token)
- Instalar e configurar:
``` bash
composer require tymon/jwt-auth
php artisan vendor:publish --provider="Tymon\JWTAuth\Providers\LaravelServiceProvider"
php artisan jwt:secret
```
### ▶️ Rodar o Projeto
- Após configurar o .env, rode os comandos:
```bash
php artisan migrate
php artisan serve
```

### 🧪 Ferramentas para Testes
Postman
- Baixe em: https://www.postman.com/downloads/

### 🧰 IDEs 
IntelliJ IDEA (com plugins PHP e Laravel)

## 📦 Instalação

1. **Clone o projeto:**
   ```bash
   git clone https://github.com/romeonoro/api-irrigacao.git
   cd api-irrigacao
2. **Instale as dependências:**
   ```bash
   composer install
   ```

3. **Crie o arquivo .env:**
   Copie o arquivo .env.example ou use este exemplo:
   ```env
   DB_CONNECTION=sqlite
   DB_DATABASE=${PWD}/database/database.sqlite
   ```

4. **Crie o banco de dados SQLite:**
   ```bash
   touch database/database.sqlite
   ```
   
5. **Gere a chave da aplicação:**
   ```bash
   php artisan key:generate
   ```
   
6. **Rode as migrations:**
   ```bash
   php artisan migrate
   ```
   
7. **Gere a chave JWT:**
   ```bash
   php artisan jwt:secret
   ```

8. **Inicie o servidor local:**
   ```bash
   php artisan serve
   ```

## 🧪 Testes com Postman

1. **Importe o arquivo:**
   - `irrigacao_api_postman_collection.json`

2. **Configure o ambiente no Postman:**

   **Variáveis:**
   - `base_url`: `http://localhost:8000/api`
   - `token`: (preencha após o login)

3. **Siga o passo a passo em:**
[  `POSTMAN.md`](https://github.com/romeonoro/API-Gerenciamento-Irrigacao/blob/main/POSTMAN.md)

## 📬 Endpoints Principais

### 🔐 Autenticação

| Método | Rota           | Descrição              |
|--------|----------------|------------------------|
| POST   | /auth/register | Registrar novo usuário |
| POST   | /auth/login    | Gerar token JWT        |

## 🚜 Pivôs de Irrigação

| Método | Rota           | Descrição               |
|--------|----------------|-------------------------|
| GET    | /pivots        | Listar pivôs do usuário |
| GET    | /pivots/{id}   | Detalhes de um pivô     |
| POST   | /pivots        | Criar novo pivô         |
| PUT    | /pivots/{id}   | Atualizar pivô          |
| DELETE | /pivots/{id}   | Remover pivô            |

## 💦 Registros de Irrigação

| Método | Rota               | Descrição                         |
|--------|--------------------|-----------------------------------|
| GET    | /irrigations       | Listar irrigações do usuário      |
| GET    | /irrigations/{id}  | Detalhes de uma irrigação         |
| POST   | /irrigations       | Criar novo registro de irrigação  |
| DELETE | /irrigations/{id}  | Remover registro                  |

> ⚠️ Todos os endpoints (exceto login e registro) exigem um token JWT válido no header:

```makefile
Authorization: Bearer SEU_TOKEN
```

## 📁 Estrutura de Pastas
```pgsql
├── app/
│ └── Http/
│ └── Controllers/
│ ├── AuthController.php
│ ├── PivotController.php
│ └── IrrigationController.php
├── app/
│ └── Models/
│ ├── User.php
│ ├── Pivot.php
│ └── Irrigation.php
├── routes/
│ └── api.php
├── database/
│ └── migrations/
├── .env
├── irrigacao_api_postman_collection.json
```
