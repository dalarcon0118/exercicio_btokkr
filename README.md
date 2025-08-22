**Exercício Técnico: Catálogo de Produtos Simples**

Este exercício busca avaliar a capacidade do candidato para projetar, implementar e integrar componentes de **frontend**, **backend** e **base de dados**, além de sua habilidade para documentar e preparar um projeto para a execução e deploy.

---

### **Objetivo do Exercício**

Desenvolver uma aplicação web simples que funcione como um **Catálogo de Produtos**. A aplicação deverá permitir a visualização de produtos, a busca por nome e a visualização dos detalhes de um produto específico.

---

### **Requisitos Técnicos**

As tecnologias específicas a serem utilizadas neste desafio são:

* **Frontend:** **Angular or react or vue** (com TypeScript)  
* **Backend:** **Node.js** (com Nest.js)  
* **Base de Dados:** **MySQL or Mongo**

#### **1\. Base de Dados (MySQL)**

* **Schema:** Projetar um schema de base de dados para armazenar as informações dos produtos. No mínimo, cada produto deve ter os seguintes atributos:  
  * `id` (identificador único, UUID)  
  * `nome`  
  * `descricao`  
  * `preco` (numérico, com precisão para moeda)  
  * `url_imagem`  
  * `quantidade_em_stock` (inteiro)  
* **Dados de Exemplo:** Incluir um script SQL (`.sql`) ou um seeder no backend que popule a base de dados com pelo menos **5 produtos de exemplo** ao iniciar a aplicação pela primeira vez ou via comando específico.

#### **2\. Backend (Node.js com Express.js)**

* **Linguagem:** **JavaScript** (ES6+ ou TypeScript).  
* **Endpoints:** Implementar uma API RESTful com os seguintes endpoints:  
  * `GET /api/products`: Retorna uma lista de todos os produtos. Deve aceitar paginação (ex: `?page=1&limit=10`) e um parâmetro de ordenação (ex: `?sort=price,asc`).  
  * `GET /api/products?search={term}`: Filtra a lista de produtos por `nome` que contenha o `term` de busca (case-insensitive).  
  * `GET /api/products/:id`: Retorna os detalhes de um produto específico pelo seu `id`.  
* **Conexão com DB:** Utilizar um ORM/ODM como **Sequelize** ou **TypeORM** para interagir com o MySQL.  
* **Manejo de Erros:** Implementar um manejo robusto de erros (erros `404 Not Found`, `400 Bad Request`, `500 Internal Server Error`, etc.), retornando mensagens descritivas em formato JSON.  
* **Validação:** Implementar validação de entrada para os parâmetros da requisição e corpo (ex: garantir que `id` é um UUID válido).

#### **3\. Frontend (Angular)**

* **Linguagem:** **TypeScript**.  
* **Componentes:**  
  * **Lista de Produtos:** Uma página que exiba todos os produtos em um formato de lista ou grid, mostrando o nome, preço e imagem.  
  * **Barra de Pesquisa:** Um campo de input que, ao digitar, filtre os produtos dinamicamente na tela (realizando chamadas à API do backend).  
  * **Detalhes do Produto:** Uma página separada que mostre todos os atributos de um produto (nome, descrição, preço, imagem, quantidade em estoque) quando o usuário clicar em um item da lista.  
* **Comunicação com API:** Utilizar o módulo `HttpClient` do Angular para consumir os endpoints do backend.  
* **Roteamento:** Configurar o roteamento do Angular para navegar entre a lista e os detalhes do produto.  
* **Estado:** Gerenciamento de estado básico para a lista de produtos e o termo de busca.

#### **4\. Containerização e Orquestração**

* **Docker:** Fornecer **Dockerfiles** para as aplicações de frontend e backend.  
* **Docker Compose:** Incluir um arquivo `docker-compose.yml` que permita levantar o ambiente completo (serviço de backend, serviço de frontend e banco de dados MySQL) com um único comando.

#### **5\. Infraestrutura como Código (IaC) para Deploy**

* **Arquivos IaC:** Incluir no repositório arquivos para deploy em um ambiente de orquestração de contêineres.  
* **Opções (Escolha uma):**  
  * **Pulumi** (com JavaScript/TypeScript) ou **Terraform**: Arquivos para provisionar os recursos necessários para deployar a aplicação (ex: um cluster Kubernetes ou instâncias de VM, balanceadores de carga, banco de dados).  
  * **Manifestos Kubernetes (`.yaml`):** Arquivos de manifesto para deployar as aplicações de frontend e backend no Kubernetes (Deployments, Services, Ingress).

---

### **Entregáveis**

O candidato deverá fornecer:

1. **Repositório Git Público:** Um link para um repositório no GitHub, GitLab ou Bitbucket que contenha todo o código fonte do projeto.  
2. **`README.md` Completo:** Um arquivo `README.md` na raiz do repositório com as seguintes seções:  
   * **Descrição do Projeto:** Breve explicação do catálogo de produtos.  
   * **Tecnologias Utilizadas:** Listagem explícita das tecnologias usadas para cada camada (Angular, Node.js, MySQL, Docker, Pulumi/Terraform/Kubernetes Manifestos).  
   * **Instruções de Setup e Execução Local:** Passos claros e concisos para clonar o repositório, instalar dependências, configurar o banco de dados e levantar a aplicação completa localmente usando **Docker Compose**.  
   * **Endpoints da API:** Documentação detalhada dos endpoints do backend (URL, método, parâmetros de query/path/body, exemplos de requisição e resposta).  
   * **Instruções de Deploy (Opcional, mas valorizado):** Breves instruções sobre como os arquivos de IaC podem ser usados para deployar a aplicação.  
   * **Decisões de Design (Opcional, mas valorizado):** Uma breve explicação de quaisquer decisões de design importantes (ex: estrutura de pastas, gerenciamento de estado no Angular, por que um determinado ORM foi escolhido, abordagens de segurança).

---

### **Critérios de Avaliação**

O exercício será avaliado com base nos seguintes pontos-chave:

* **Funcionalidade (20%):** Todas as funcionalidades solicitadas implementadas e operacionais.  
* **Qualidade do Código (20%):**  
  * Organização e estrutura do projeto (separação de responsabilidades, padrões de projeto).  
  * Legibilidade, modularidade, reusabilidade e clareza do código (comentários relevantes).  
  * Manejo de erros e validações em ambas as camadas (frontend e backend).  
  * Uso de boas práticas e convenções das tecnologias escolhidas (Angular, Node.js).  
* **Design da Solução (20%):**  
  * Design lógico e eficiente do schema do banco de dados.  
  * Aderência a princípios RESTful no design da API.  
  * Uso apropriado de componentes, serviços e gerenciamento de estado no Angular.  
* **Containerização e Automação (20%):**  
  * Correta configuração dos Dockerfiles e `docker-compose.yml`.  
  * Apresentação de arquivos de IaC relevantes para deploy (Pulumi/Terraform/Kubernetes).  
* **Documentação e Comunicação (10%):** Clareza, completude e precisão do `README.md` e outras explicações.  
* **Conhecimento Full-Cycle (10%):** Capacidade de integrar as diferentes camadas, demonstrar compreensão das interações entre elas e do ciclo de vida completo de uma aplicação (desenvolvimento, containerização, deploy).

