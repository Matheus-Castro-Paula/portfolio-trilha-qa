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

### 3. Tipos de Testes Obrigatórios Executados

Para garantir a cobertura exigida no desafio, os 18 Casos de Teste foram distribuídos entre as 3 áreas core utilizando as seguintes abordagens:

- **Foco Funcional:** Validação das regras de negócio e comportamento esperado pelo usuário (ex: cálculo de pontos, validação de inputs e obrigatoriedade de campos).
- **Validação de API:** Testes focados no servidor utilizando Postman para validar Status Codes (`200`, `201`, `400`, `403`), formatos de resposta e segurança de endpoints (RBAC).
- **Teste de Regressão:** Cenários desenhados para simular o fluxo principal do sistema e garantir que futuras correções de bugs não gerem efeitos colaterais em funcionalidades já estabilizadas (ex: garantir integridade do ranking após deleção de check-ins).

## Organização dos testes (Kanban)

Para cumprir o requisito de gestão dos testes, estou utilizando o GitHub Projects com as seguintes colunas para acompanhar a evolução de cada funcionalidade:

- **Ready for Test:** Funcionalidades planejadas e prontas para validação.
- **In test:** Funcionalidades em processo de teste manual ou via API.
- **Bugs Back-End:** Registro dos Bugs descobertos através do Back-End.
- **Bugs Front-End:** Registro dos Bugs descobertos através do Front-End.
- **Test done Back-End:** Testes do Back-End finalizados e resultados devidamente documentados.
- **Test done Front-End:** Testes do Front-End finalizados e resultados devidamente documentados.
- **Blocked:** Testes que não puderam ser concluídos devido a impedimentos técnicos ou bugs impeditivos.

## Evolução do Projeto

O ciclo de QA foi dividido em etapas estratégicas para garantir a cobertura total da aplicação.

### Etapa 1: Infraestrutura e Governança (Semanas 1 e 2)

O foco inicial foi o estabelecimento de uma base técnica sólida. Isso incluiu a containerização de todo o ecossistema (Back-end, Front-end e Banco de Dados) via Docker para garantir a paridade entre ambientes de desenvolvimento e teste. Paralelamente, foi estruturada a governança do projeto através do GitHub Projects, permitindo a rastreabilidade dos requisitos desde o dia zero e a organização de um fluxo de trabalho ágil.

### Etapa 2: Planejamento e Design de Testes (Semana 3)

Com o ambiente estabilizado, a estratégia evoluiu para o design detalhado dos cenários. Nesta fase, as regras de negócio foram transformadas em **36 Casos de Teste (CTs) técnicos** — sendo 18 focados na validação da interface (Front-end) e 18 focados na validação da API (Back-end) —, utilizando o GitHub Issues como repositório de documentação integrado ao GitHub Projects.

- **Foco em Regras Críticas e Segurança:** O planejamento cobriu testes de escalação de privilégio (RBAC), restrição de frequência de check-ins, isolamento de temporadas e bloqueio de mídias inválidas em ambas as camadas.
- **Preparação Técnica Integrada:** Para o Back-end, utilizou-se a coleção do Postman (pasta `/docs`) para mapeamento de rotas e Status Codes. Para o Front-end, o design focou em validação visual e responsividade.

### Etapa 3: Execução de Testes de Interface (Semana 4)

O foco desta etapa foi auditar a aplicação através da interface (Front-end), garantindo que as regras de negócio fossem respeitadas visualmente.

- **Execução dos Casos de Teste:** Foram executados os 18 cenários de Front-end, com foco em usabilidade e responsividade mobile.
- **Bugs Críticos Identificados:** Descoberta de falhas como o vazamento de dados no histórico (CT-12) e a ausência de bloqueios para envios duplicados (CT-10).
- **Gestão Visual:** Foi utilizado o sistema de labels (`test-case`, `bug`, `pass`, `fail`) para indicar o resultado de cada teste diretamente no board e as labels (`severity: critical`, `severity: major` e `severity: minor`) para definir a severidade de cada bug.

### Etapa 4: Testes de API e Integração (Semana 5)

Validação profunda do Back-end utilizando Postman para garantir a integridade dos endpoints e regras de servidor.

- **Consolidação de Falhas (404):** Múltiplas rotas inexistentes foram unificadas na Issue #25 para facilitar a correção.
- **Testes Bloqueados:** Cenários como o CT-Back-02 (Issue #3) e CT-Back-03 (Issue #4) foram movidos para a coluna **Blocked** devido a falhas críticas nas rotas que impediram a validação completa da funcionalidade.
- **Gestão Visual:** A gestão visual foi a mesma da semana anterior, utilizando o sistema de labels (`test-case`, `bug`, `pass`, `fail`) para indicar o resultado de cada teste diretamente no board e as labels (`severity: critical`, `severity: major` e `severity: minor`) para definir a severidade de cada bug.

**O Quadro de Testes** está presente na aba "Projects" dentro deste mesmo repositório.
