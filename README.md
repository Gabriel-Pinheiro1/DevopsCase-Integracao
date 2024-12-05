# DevopsCase - Integração

Este repositório contém a configuração de integração do projeto **DevopsCase**, que envolve um sistema dividido em três partes principais: **Frontend**, **Backend** e **Banco de Dados**. Este projeto utiliza **Docker** para orquestrar os containers e configurar a comunicação entre o frontend, backend e o banco de dados.

## Requisitos do Projeto

Para rodar este projeto, é necessário ter o Docker e o Docker Compose instalados na sua máquina. 

- **Docker**: [Instalar Docker](https://docs.docker.com/get-docker/)
- **Docker Compose**: [Instalar Docker Compose](https://docs.docker.com/compose/install/)

## Como Rodar?

### Passo 1: Clonar o Repositório

Primeiro, você deve clonar este repositório:

```bash
git clone https://github.com/Gabriel-Pinheiro1/DevopsCase-Integracao.git
```
### Passo 2: Navegar até a Pasta do Repositório
Após clonar o repositório, navegue até a pasta do repositório:

```bash
cd DevopsCase-Integracao
```
### Passo 3: Clonar os Repositórios de Frontend e Backend
Na raiz do projeto **DevopsCase-Integracao**, clone os outros dois repositórios: **Frontend** e **Backend**.

**Frontend:**
```bash
git clone https://github.com/Gabriel-Pinheiro1/devopscasefront.git
```
**Backend:**
```bash
git clone https://github.com/Gabriel-Pinheiro1/devopscaseback.git
```

### Passo 4: Verificar a Estrutura do Projeto
Após clonar os repositórios, a estrutura do projeto deverá parecer com a seguinte:

```bash
DevopsCase-Integracao/
├── devopscasefront/
├── devopscaseback/
└── docker-compose.yml
```

### Passo 5: Inicializar o Container
Agora, para inicializar o ambiente, basta rodar o comando abaixo, que vai configurar e rodar os containers definidos no docker-compose.yml:

```bash
docker-compose up --build
```
Você pode acessar os conteiners localmente em:

Frontend: http://localhost:80


Backend: http://localhost:3000


Para parar o projeto, aperte `Ctrl + C` ou use o comando:

```bash
docker-compose down
```

## Como funciona?

O projeto é composto por três partes principais: o **Frontend**, o **Backend** e a **Integração via Docker**. A seguir, explicamos como essas partes interagem para formar o sistema.

### Frontend

O **Frontend** é responsável pela interface do usuário. Ele comunica-se com o **Backend** via requisições HTTP. O código do Frontend está hospedado no repositório `devopscasefront`, que, quando inicializado, pode ser acessado na porta **80**. Essa interface permite que o usuário interaja com o sistema, visualizando e enviando dados para o backend.

### Backend

O **Backend** é a camada lógica do sistema, onde as operações de processamento de dados são realizadas. O código do Backend está hospedado no repositório `devopscaseback`. Ele executa as requisições feitas pelo Frontend, processa as informações e interage com o banco de dados ou outras fontes de dados. O Backend está acessível através da porta **3000**.

### Integração via Docker

A integração entre o **Frontend**, **Backend** e quaisquer outras dependências externas (como bancos de dados) é realizada utilizando o Docker. O arquivo `docker-compose.yml` define todos os containers necessários para o funcionamento do sistema, orquestrando tanto o Frontend quanto o Backend, além de outras dependências, permitindo que todos os serviços sejam executados simultaneamente em containers isolados.

Cada serviço possui um **Dockerfile** específico:

- **Frontend**: O `Dockerfile` do Frontend define como a aplicação será construída e executada dentro do container. Ele especifica a imagem base, instala as dependências necessárias e copia o código-fonte da aplicação para o container.

- **Backend**: O `Dockerfile` do Backend segue um processo semelhante, com a especificação de uma imagem base, instalação das dependências, configuração do ambiente e execução do código da API.

Através do `docker-compose.yml`, o Docker pode construir e iniciar os containers definidos nos respectivos `Dockerfiles` de forma coordenada, com comunicação entre os containers feita por meio de portas específicas.

### Comunicação entre Frontend e Backend

Quando o usuário interage com o **Frontend**, ele faz chamadas para o **Backend** por meio de APIs. Essas APIs são expostas pelo Backend e respondem com os dados necessários para que a interface de usuário seja atualizada. O uso do Docker permite que o Frontend e Backend sejam facilmente configurados e gerenciados em containers separados, sem a necessidade de configuração manual para o ambiente de desenvolvimento.







