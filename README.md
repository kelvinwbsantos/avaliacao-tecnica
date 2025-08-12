# Ambiente de Desenvolvimento da Avaliação Técnica

Este repositório contém a configuração do Docker Compose e os arquivos necessários para orquestrar e executar todo o ambiente de desenvolvimento, que consiste em um backend em NestJS e um frontend em Angular.

## 🚀 Começando

Siga estas instruções para configurar e executar o ambiente de desenvolvimento completo em sua máquina local.

### Pré-requisitos

Antes de começar, garanta que você tenha as seguintes ferramentas instaladas:
* [Git](https://git-scm.com/)
* [Docker](https://www.docker.com/products/docker-desktop/)
* [Docker Compose](https://docs.docker.com/compose/install/) (geralmente já vem com o Docker Desktop)

### Instalação (Passo a Passo)

1.  **Crie uma pasta de trabalho e clone os repositórios:**

    ```bash
    # Crie uma pasta para o projeto
    mkdir workspace
    cd workspace

    # 1. Clone este repositório de orquestração
    git clone [https://github.com/kelvinwbsantos/avaliacao-tecnica.git](https://github.com/kelvinwbsantos/avaliacao-tecnica.git)

    # 2. Clone o repositório do backend
    git clone [https://github.com/kelvinwbsantos/back-nest-avaliacao-tecnica-1.git](https://github.com/kelvinwbsantos/back-nest-avaliacao-tecnica-1.git)

    # 3. Clone o repositório do frontend
    git clone [https://github.com/kelvinwbsantos/front-angular-avaliacao-tecnica-1.git](https://github.com/kelvinwbsantos/front-angular-avaliacao-tecnica-1.git)
    ```

2.  **Navegue para a pasta do orquestrador:**

    ```bash
    cd avaliacao-tecnica
    ```

3.  **Configure as Variáveis de Ambiente:**

    Crie o arquivo `.env` na raiz desta pasta. Você pode copiar o arquivo de exemplo `env.example` (se você criar um).

    ```bash
    # Comando para criar o .env (opcional, se tiver o .env.example)
    # cp .env.example .env

    # Abra o arquivo .env e preencha com suas configurações.
    # Exemplo de conteúdo para o .env:
    ```
    ```env
    # Configurações do Banco de Dados PostgreSQL
    POSTGRES_DB=mydb
    POSTGRES_USER=postgres
    POSTGRES_PASSWORD=root

    # Segredos da Aplicação
    JWT_SECRET=chavesupersecreta
    JWT_EXPIRES_IN=1d
    ```

4.  **Suba os contêineres:**

    Execute o seguinte comando para construir as imagens e iniciar todos os serviços em segundo plano.

    ```bash
    docker-compose up --build -d
    ```

### Verificação

Após a execução, o ambiente estará disponível nos seguintes endereços:

* **Frontend (Angular):** [http://localhost:4200](http://localhost:4200)
* **Backend (NestJS):** [http://localhost:3000](http://localhost:3000)
* **Documentação da API (Swagger):** [http://localhost:3000/api](http://localhost:3000/api)

### Comandos Úteis do Docker

* **Ver os logs de um serviço específico (ex: backend):**
    `docker-compose logs -f backend`
* **Parar todos os serviços:**
    `docker-compose down`
* **Parar e remover os volumes (apaga o banco de dados):**
    `docker-compose down -v`
* **Acessar o terminal de um contêiner (ex: backend):**
    `docker-compose exec backend /bin/sh`

### Estrutura de Pastas Esperada

Para que o `docker-compose.yml` funcione, sua estrutura de pastas local deve ser a seguinte:
```
/workspace/
|-- avaliacao-tecnica/  (Você está aqui)
|-- back-nest-avaliacao-tecnica-1/
|-- front-angular-avaliacao-tecnica-1/
```