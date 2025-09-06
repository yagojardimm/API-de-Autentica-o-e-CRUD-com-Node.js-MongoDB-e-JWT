![image](https://github.com/yagojardimm/Trab-estrutura-de-dados/assets/134665777/0e4c999d-15b7-4b8a-ac69-aab319ffca37)
# Curso: Engenharia de Software 
# Disciplina: Laboratório de Desenvolvimento de Aplicativos Nativos

API de Autenticação e CRUD com Node.js
Esta é uma API RESTful completa, construída com Node.js, Express e MongoDB, que implementa um sistema de autenticação de usuários baseado em JWT (Access e Refresh Tokens) e expõe um CRUD protegido de tarefas (To-dos).

Funcionalidades Principais
Autenticação Segura:

Registro de usuários com senhas criptografadas (usando bcrypt).

Login de usuários com sistema de accessToken (curta duração) e refreshToken (longa duração).

Rota para renovar o accessToken de forma segura utilizando o refreshToken.

CRUD de Tarefas Protegido:

Operações completas de Criar, Ler, Atualizar e Deletar tarefas.

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
