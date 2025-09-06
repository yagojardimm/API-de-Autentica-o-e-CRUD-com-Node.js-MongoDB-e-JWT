![image](https://github.com/yagojardimm/Trab-estrutura-de-dados/assets/134665777/0e4c999d-15b7-4b8a-ac69-aab319ffca37)
# Curso: Engenharia de Software 
# Disciplina: Laboratório de Desenvolvimento de Aplicativos Nativos
curso: Engenharia de Software
disciplina: Laboratório de Desenvolvimento de Aplicativos Nativos
API de Autenticação e CRUD com Node.js
Esta é uma API RESTful completa, construída com Node.js, Express e MongoDB, que implementa um sistema de autenticação de usuários baseado em JWT (Access e Refresh Tokens) e expõe um CRUD protegido de tarefas (To-dos).

Funcionalidades Principais

Autenticação Segura:
Registro de usuários com senhas criptografadas (usando bcrypt).
Login de usuários com sistema de accessToken (curta duração) e refreshToken (longa duração).
Rota para renovar o accessToken de forma segura utilizando o refreshToken.

CRUD de Tarefas Protegido:
Operações completas de criar, ler, atualizar e deletar tarefas.
Cada usuário só pode acessar e manipular suas próprias tarefas, garantindo o isolamento dos dados.

Validação de Dados:
Validação robusta na entrada de dados para todas as rotas críticas, utilizando Zod.

Rotas Adicionais:
Endpoint protegido (/me) para que o usuário autenticado possa consultar seus próprios dados.

Tecnologias Utilizadas
Backend: Node.js, Express.js
Banco de Dados: MongoDB com Mongoose (ODM)
Autenticação: JSON Web Tokens (jsonwebtoken)
Segurança de Senhas: bcryptjs
Validação: Zod
Variáveis de Ambiente: dotenv
CORS: Habilitado com o pacote cors
Desenvolvimento: nodemon para reinicialização automática do servidor

Como Executar o Projeto

Pré-requisitos
Node.js (versão 18 ou superior)
MongoDB (uma instância local ou uma conta no MongoDB Atlas)
Um cliente de API, como Insomnia ou Postman

Passos para Instalação

Clone o repositório:
git clone <URL_DO_SEU_REPOSITORIO>
cd <NOME_DA_PASTA>

Instale as dependências do projeto:
npm install

Configure as variáveis de ambiente:
Crie um arquivo chamado .env na raiz do projeto.
Copie o conteúdo do arquivo .env.example para o seu novo arquivo .env.
Preencha as variáveis com suas informações:
MONGO_URI: Sua string de conexão com o MongoDB.
ACCESS_TOKEN_SECRET e REFRESH_TOKEN_SECRET: Crie chaves secretas longas e aleatórias.

Inicie o servidor em modo de desenvolvimento:
npm run dev
O servidor estará disponível em http://localhost:3000

Guia de Endpoints da API

A URL base para todas as requisições é http://localhost:3000.

Módulo de Autenticação (/auth)

POST /auth/register
Cria um novo usuário.
Body (JSON):
{
"name": "Seu Nome",
"email": "seu@email.com",
"password": "sua_senha_segura"
}

POST /auth/login
Autentica um usuário.
Body (JSON):
{
"email": "seu@email.com",
"password": "sua_senha_segura"
}

POST /auth/refresh
Gera um novo accessToken.
Body (JSON):
{
"refreshToken": "seu_refresh_token_aqui"
}

GET /me
Retorna os dados do usuário autenticado.
Headers:
Authorization: Bearer <seu_access_token>

Módulo de Tarefas (/todos) - Requer Autenticação

Header: Authorization: Bearer <seu_access_token>

POST /todos
Cria uma nova tarefa.
Body (JSON):
{
"title": "Minha nova tarefa"
}

GET /todos
Lista todas as tarefas do usuário.

GET /todos/:id
Busca uma tarefa pelo ID.

PUT /todos/:id
Atualiza uma tarefa.
Body (JSON):
{
"title": "Título da tarefa atualizado",
"done": true
}

DELETE /todos/:id
Deleta uma tarefa.
