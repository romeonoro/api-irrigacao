# 🌿 Guia de Testes da API de Irrigação com Postman

Este documento orienta como configurar e testar os endpoints da API RESTful de Irrigação utilizando o Postman.

## ✅ Pré-requisitos

- Ter o Postman instalado.
- Servidor da API rodando localmente (ex: http://localhost:8000/api).

## 📦 Importar a Coleção

1. Abra o Postman.
2. Clique em **Import** no canto superior esquerdo.
3. Vá até a aba **Upload Files**.
4. Selecione o arquivo `irrigacao_api_postman_collection.json`.
5. Clique em **Import**.

## 🛠️ Variáveis de Ambiente

1. No Postman, clique no ícone de engrenagem (⚙️) no canto superior direito.
2. Vá em **Environments** > **Add**.
3. Nomeie como: `API Irrigação`.
4. Adicione as seguintes variáveis:

| Nome      | Valor                     |
|-----------|---------------------------|
| base_url  | http://localhost:8000/api |
| token     | (Deixe em branco por enquanto) |

5. Clique em **Save** e selecione esse ambiente no canto superior direito.

## 🔐 1. Registro de Usuário

- **Método:** POST  
- **Rota:** `/auth/register`  
- **Body (raw / JSON):**
\`\`\`json
{
  "username": "usuario1",
  "password": "senha123"
}
\`\`\`

## 🔑 2. Login e Obtenção do Token JWT

- **Método:** POST  
- **Rota:** `/auth/login`  
- **Body (raw / JSON):**
\`\`\`json
{
  "username": "usuario1",
  "password": "senha123"
}
\`\`\`

- Após enviar, copie o token do campo \`"token"\` da resposta.
- Vá até a aba de variáveis (⚙️ Environment), cole o token na variável \`token\` e salve.

## 🚜 3. Criar Pivô de Irrigação

- **Método:** POST  
- **Rota:** \`/pivots\`  
- **Header:**  
  - \`Authorization: Bearer {{token}}\`
  - \`Content-Type: application/json\`

- **Body (raw / JSON):**
\`\`\`json
{
  "description": "Pivô Fazenda A",
  "flowRate": 150.5,
  "minApplicationDepth": 6.0
}
\`\`\`

## 💧 4. Criar Registro de Irrigação

- **Método:** POST  
- **Rota:** \`/irrigations\`  
- **Header:**  
  - \`Authorization: Bearer {{token}}\`
  - \`Content-Type: application/json\`

- **Body (raw / JSON):**
\`\`\`json
{
  "pivotId": "UUID_DO_PIVÔ",
  "applicationAmount": 20.0,
  "irrigationDate": "2025-07-01T10:00:00Z"
}
\`\`\`

> 📌 Substitua \`UUID_DO_PIVÔ\` pelo ID retornado na criação do pivô.

## 📋 Outros Endpoints (GET, PUT, DELETE)

Use as rotas a seguir com o mesmo cabeçalho \`Authorization\`:

- \`GET /pivots\`
- \`GET /pivots/:id\`
- \`PUT /pivots/:id\`
- \`DELETE /pivots/:id\`
- \`GET /irrigations\`
- \`GET /irrigations/:id\`
- \`DELETE /irrigations/:id\`

## 🧪 Dica Extra: Testes Automáticos

Na aba **Tests** de cada requisição, você pode adicionar:
\`\`\`js
pm.test("Status 200 OK", function () {
  pm.response.to.have.status(200);
});
\`\`\`

## 📌 Observações

- Todos os endpoints, exceto \`/auth/register\` e \`/auth/login\`, requerem JWT no cabeçalho \`Authorization\`.
- Use o formato \`Bearer {{token}}\`.
