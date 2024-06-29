# Descrição
Esta API RESTful foi desenvolvida para gerenciar informações sobre alimentos em um sistema de estoque. Utilizando o framework Express, MongoDB para armazenamento de dados e Mongoose como ODM, a API oferece funcionalidades completas para CRUD (Create, Read, Update, Delete) de alimentos.

## Funcionalidades
#### Listar todos os alimentos (GET /api/foods)
Retorna uma lista de todos os alimentos no banco de dados.

#### Buscar um alimento específico (GET /api/foods/)
Retorna os detalhes de um alimento com base no ID fornecido.

#### Criar um novo alimento (POST /api/foods)
Cria um novo alimento com base nos dados fornecidos.

#### Atualizar um alimento existente (PUT /api/foods/)
Atualiza os dados de um alimento existente com base no ID fornecido.

#### Excluir um alimento (DELETE /api/foods/)
Remove um alimento com base no ID fornecido.

## Estrutura
O projeto utiliza uma estrutura em camadas para melhor organização e manutenção do código.

## Modelo
O esquema define a estrutura dos documentos de alimentos, incluindo campos como name, category, quantity, expirationDate e price.

## Conexão com MongoDB
A conexão com o banco de dados MongoDB é estabelecida utilizando mongoose.connect.

## Middleware de Tratamento de Erros
Utilizamos um middleware de tratamento de erros para capturar e lidar com exceções de forma centralizada.
