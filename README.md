# Trilha QA - Projeto NaSalinha

Este repositório contém a documentação e os testes realizados no sistema NaSalinha durante a trilha de QA. O foco inicial foi o setup do ambiente e a organização do fluxo de trabalho.

## Tecnologias Utilizadas

- **Sistema Operacional:** Linux Ubuntu
- **Containerização:** Docker e Docker Compose
- **Testes de API:** Postman
- **Gestão:** GitHub Projects (Kanban)

## Como Rodar o Projeto

Para subir o ambiente de teste localmente, utilizei os seguintes comandos no terminal:

1. Clone do repositório:
   `git clone https://github.com/Gustavohmmagalhaes/nasalinha-qa-challenge.git`

2. Build e execução dos containers:
   `docker compose up --build`

3. Inicialização das tabelas do Banco de Dados:
   `docker exec -it nasalinha-backend npx prisma migrate dev`

O Front-End pode ser acessado em `localhost:3000` e o Back-End em `localhost:5001`.

## Estratégia e Tipos de Testes

Para garantir a qualidade do sistema NaSalinha, a estratégia de testes foi estruturada seguindo os fundamentos de QA:

### 1. Níveis de Teste (Quando testar?)

- **Teste de Sistema:** Validação das funcionalidades core (Autenticação, Check-in e Pontos) para garantir que o sistema atenda aos requisitos de ponta a ponta.
- **Teste de Regressão:** Execução de cenários críticos após a correção de falhas para garantir que as novas alterações não impactaram funcionalidades já estabilizadas.

### 2. Técnicas de Teste (Como testar?)

- **Caixa Preta:** Testes baseados em cenários de uso e análise de valores limite, focando nas entradas e saídas do sistema sem necessidade de validar o código-fonte diretamente.

### 3. Tipos de Teste (O que testar?)

- **Teste de Funcionalidade:** Foco em validar se o comportamento do sistema (ex: cadastro, login) corresponde às regras de negócio definidas.
- **Teste de Interface:** Validação visual e de navegação para garantir que a experiência do usuário (UX) esteja correta.
- **Validação de API:** Testes de integração focados em endpoints, payloads e Status Codes (200, 201, 400, etc.).

## Organização dos testes (Kanban)

Para cumprir o requisito de gestão dos testes, estou utilizando o GitHub Projects com as seguintes colunas para acompanhar a evolução de cada funcionalidade:

- **Ready for Test:** Funcionalidades planejadas e prontas para validação.
- **In test:** Funcionalidades em processo de teste manual ou via API.
- **Test done:** Testes finalizados e bugs devidamente documentados.

## Atividades Concluídas (Semanas 1 e 2)

- Configuração e subida do ambiente utilizando Docker e Docker Compose.
- Estruturação do repositório de QA e documentação inicial.
- Criação e configuração do quadro Kanban para gestão dos requisitos.
- Início do mapeamento dos testes exploratórios no sistema local.
