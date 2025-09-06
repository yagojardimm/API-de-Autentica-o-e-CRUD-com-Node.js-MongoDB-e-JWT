![image](https://github.com/yagojardimm/Trab-estrutura-de-dados/assets/134665777/0e4c999d-15b7-4b8a-ac69-aab319ffca37)
# Curso: Engenharia de Software 
# Disciplina: Laboratório de Desenvolvimento de Aplicativos Nativos

API de Autenticação e CRUD com Node.jsEsta é uma API RESTful completa, construída com Node.js, Express e MongoDB, que implementa um sistema de autenticação de usuários baseado em JWT (Access e Refresh Tokens) e expõe um CRUD protegido de tarefas (To-dos).Funcionalidades PrincipaisAutenticação Segura:Registro de usuários com senhas criptografadas (usando bcrypt).Login de usuários com sistema de accessToken (curta duração) e refreshToken (longa duração).Rota para renovar o accessToken de forma segura utilizando o refreshToken.CRUD de Tarefas Protegido:Operações completas de Criar, Ler, Atualizar e Deletar tarefas.Cada usuário só pode acessar e manipular suas próprias tarefas, garantindo o isolamento dos dados.Validação de Dados:Validação robusta na entrada de dados para todas as rotas críticas, utilizando Zod.Rotas Adicionais:Endpoint protegido (/me) para que o usuário autenticado possa consultar seus próprios dados.Tecnologias UtilizadasBackend: Node.js, Express.jsBanco de Dados: MongoDB com Mongoose (ODM)Autenticação: JSON Web Tokens (jsonwebtoken)Segurança de Senhas: bcryptjsValidação: ZodVariáveis de Ambiente: dotenvCORS: Habilitado com o pacote corsDesenvolvimento: nodemon para reinicialização automática do servidorComo Executar o ProjetoPré-requisitosNode.js (versão 18 ou superior)MongoDB (uma instância local ou uma conta no MongoDB Atlas)Um cliente de API, como Insomnia ou PostmanPassos para InstalaçãoClone o repositório:git clone <URL_DO_SEU_REPOSITORIO>
cd <NOME_DA_PASTA>
Instale as dependências do projeto:npm install
Configure as variáveis de ambiente:Crie um arquivo chamado .env na raiz do projeto.Copie o conteúdo do arquivo .env.example para o seu novo arquivo .env.Preencha as variáveis com suas informações:MONGO_URI: Sua string de conexão com o MongoDB.ACCESS_TOKEN_SECRET e REFRESH_TOKEN_SECRET: Crie chaves secretas longas e aleatórias (um gerador de senhas online é ótimo para isso).Inicie o servidor em modo de desenvolvimento:npm run dev
O servidor estará disponível em http://localhost:3000 (ou na porta que você definiu no .env).Guia de Endpoints da APIA URL base para todas as requisições é http://localhost:3000.Módulo de Autenticação (/auth)POST /auth/registerCria um novo usuário.Body (JSON):{
    "name": "Seu Nome",
    "email": "seu@email.com",
    "password": "sua_senha_segura"
}
POST /auth/loginAutentica um usuário e retorna os tokens e os dados do usuário.Body (JSON):{
    "email": "seu@email.com",
    "password": "sua_senha_segura"
}
POST /auth/refreshGera um novo accessToken e refreshToken a partir de um refreshToken válido.Body (JSON):{
    "refreshToken": "seu_refresh_token_aqui"
}
GET /meRetorna os dados do usuário autenticado.Headers:Authorization: Bearer <seu_access_token>Módulo de Tarefas (/todos) - Requer AutenticaçãoPara todas as rotas abaixo, é necessário enviar o accessToken no header de autorização.Header: Authorization: Bearer <seu_access_token>POST /todosCria uma nova tarefa.Body (JSON):{
    "title": "Minha nova tarefa"
}
GET /todosLista todas as tarefas pertencentes ao usuário autenticado.GET /todos/:idBusca uma única tarefa pelo seu ID.PUT /todos/:idAtualiza uma tarefa existente.Body (JSON):{
    "title": "Título da tarefa atualizado",
    "done": true
}
DELETE /todos/:idDeleta uma tarefa.
