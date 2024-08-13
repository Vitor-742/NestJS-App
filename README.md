# Aplicação NestJs para teste técnico da starsoft com Redis, PostgreSQL e Kafka

Essa aplicação é uma API(express) usando NestJs como framework, Redis para cache de autenticação, PostgreSQL como banco de dados padrão da aplicação e Kafka para
envio e recebimento de mensagens de log

## Índice

- [Recursos](#recursos)
- [Instalação](#instalação)
- [Variáveis de Ambiente](#variáveis-de-ambiente)
- [Executando a Aplicação](#executando-a-aplicação)
- [Endpoints da API](#endpoints-da-api)
  - [Autenticação](#autenticação)
  - [Gerenciamento de Usuários](#gerenciamento-de-usuários)
- [Integração com Kafka](#integração-com-kafka)
- [Migrações de Banco de Dados](#migrações-de-banco-de-dados)
- [Licença](#licença)

## Recursos

- **Autenticação de Usuários**: Cadastro, login e proteção de endpoints com JWT.
- **Gerenciamento de Usuários**: Operações CRUD (Criar, Ler, Atualizar, Excluir) completas para usuários.
- **PostgreSQL**: Usado como banco de dados principal para armazenar dados de usuários.
- **Redis**: Usado como banco de dados para cache do token de autorização
- **Kafka**: Integrado para mensagens e arquitetura orientada a eventos.
- **Swagger**: Documentação automatica de endpoints

## Instalação

1. **Clone o repositório**:

   ```bash
   git clone https://github.com/Vitor-742/starsoft-test.git
   cd starsoft-test
   ```

2. **Instale as dependências**:

   ```bash
   npm install
   ```

3. **Inicie os containers docker**:
   ```bash
   docker-compose up -d
   ```

## Executando a Aplicação

1. **Inicie a aplicação**:

   ```bash
   npm start
   ```

   A aplicação será iniciada na porta especificada no seu arquivo \`.env\` (padrão: \`3000\`).

## Endpoints da API
- Para ver todos os endpoints da API visite o Swagger

## Swagger

- [Swagger Local](http://localhost:3000/api/)
- Para autenticar as requisições usando um Bearer Token na interface do Swagger, siga os seguintes passos:
    - Obtenha o Token: Primeiro, faça login através do endpoint /auth/login para obter o token JWT. Esse token será retornado no campo accessToken da resposta.
    - Configure a Autenticação no Swagger: No topo direito da interface do Swagger, clique no botão Authorize. Uma janela modal será aberta.
    - Informe o Token: No campo de autenticação, insira o token JWT precedido da palavra Bearer, por exemplo: Bearer seu_token_aqui. Clique em Authorize para aplicar o token.
    - Faça as Requisições: Agora, você pode fazer requisições autenticadas aos endpoints protegidos da API. O token será automaticamente incluído no cabeçalho Authorization de cada requisição.

## Integração com Kafka

A aplicação está integrada com o Kafka para mensagens. O Kafka é usado para publicar e consumir eventos relacionados às operações de usuário, como criação e atualização de usuários.

- **Tópicos Kafka**:
  - \`user_created\`: Publicado quando um novo usuário é criado.
  - \`user_updated\`: Publicado quando um usuário é atualizado.

## Deploy

Acesse a API através da url: [Swagger](starsoft-test-production.up.railway.app)
