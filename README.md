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
- **Test done:** Testes finalizados e bugs devidamente documentados.

## Evolução do Projeto

O ciclo de QA foi dividido em etapas estratégicas para garantir a cobertura total da aplicação.

### Etapa 1: Infraestrutura e Governança (Semanas 1 e 2)

O foco inicial foi o estabelecimento de uma base técnica sólida. Isso incluiu a containerização de todo o ecossistema (Back-end, Front-end e Banco de Dados) via Docker para garantir a paridade entre ambientes de desenvolvimento e teste. Paralelamente, foi estruturada a governança do projeto através do GitHub Projects, permitindo a rastreabilidade dos requisitos desde o dia zero e a organização de um fluxo de trabalho ágil.

### Etapa 2: Planejamento e Design de Testes (Semana 3)

Com o ambiente estabilizado, a estratégia evoluiu para o design detalhado dos cenários. Nesta fase, as regras de negócio foram transformadas em 18 Casos de Teste (CTs) técnicos, utilizando o GitHub Issues como repositório de documentação integrado ao GitHub Projects.

- **Foco em Regras Críticas e Segurança:** O planejamento foi expandido além do "caminho feliz", cobrindo testes de escalação de privilégio (RBAC), restrição de frequência de check-ins (janela de 24h), isolamento de temporadas e bloqueio de mídias inválidas.
- **Preparação Técnica:** Integração com a coleção do Postman (disponível na pasta `/docs` do Back-End) para mapeamento exato das rotas, payloads e definição de Status Codes esperados antes da execução.

**O Quadro de Testes** está presente na aba "Projects" dentro deste mesmo repositório.
