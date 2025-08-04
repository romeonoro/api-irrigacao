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
   
5. Gere a chave da aplicação:
   ```bash
   php artisan key:generate
   ```
   
6. Rode as migrations:
   ```bash
   php artisan migrate
   ```
   
7. Gere a chave JWT:
   ```bash
   php artisan jwt:secret
   ```

8. Inicie o servidor local:
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
