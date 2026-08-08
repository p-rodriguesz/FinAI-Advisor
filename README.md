# FinAI Advisor

Assistente financeiro com IA para ajudar usuários a registrar, analisar e compreender suas finanças pessoais.

O FinAI Advisor é um projeto de portfólio que reúne desenvolvimento full stack, inteligência artificial, RAG, APIs, banco de dados, segurança, testes, conteinerização e CI/CD.

> **Aviso:** o FinAI Advisor tem finalidade informativa e educacional. Não oferece recomendação profissional de investimento, crédito ou produtos financeiros.

## Problema

Dados financeiros pessoais podem ficar dispersos e ser difíceis de interpretar. Registrar receitas e despesas, identificar padrões de consumo, acompanhar metas e transformar números em decisões práticas exige tempo e conhecimento.

Uma interface de IA aplicada a finanças também precisa ser confiável: ela não pode preencher lacunas inventando transações, saldos ou conclusões sem respaldo nos dados do usuário e em fontes verificáveis.

## Solução proposta

O FinAI Advisor centralizará informações financeiras do usuário e oferecerá análises, relatórios e um chat em linguagem natural. As respostas do assistente combinarão dados financeiros autorizados pelo usuário com uma base de conhecimento confiável, utilizando RAG (*Retrieval-Augmented Generation*), e passarão por validação antes da entrega.

## Funcionalidades planejadas

- Cadastro de receitas, despesas e categorias financeiras;
- Dashboard financeiro e análise de gastos;
- Gestão de metas financeiras;
- Relatórios financeiros;
- Autenticação de usuários;
- Chat com IA fundamentado nos dados financeiros do usuário;
- RAG com base de conhecimento financeiro confiável;
- Respostas da IA com validação e fontes quando aplicável.

## Arquitetura

```text
React
  ↓
FastAPI
  ↓
Services
  ├── Auth
  ├── Finance
  ├── AI
  ├── RAG
  └── Reports
  ↓
PostgreSQL
```

Consulte também a [documentação de arquitetura](docs/architecture/README.md) e a [ADR 001](docs/decisions/README.md).

## IA e RAG

```text
Pergunta do usuário
  ↓
Dados financeiros autorizados + contexto recuperado pelo RAG
  ↓
LLM
  ↓
Validação da resposta
  ↓
Resposta ao usuário + fontes, quando aplicável
```

Na ausência de dados ou contexto suficiente, o sistema deverá informar essa limitação em vez de inventar informações.

## Segurança e confiabilidade

- RAG baseado em fontes confiáveis;
- validação de contexto e *similarity threshold*;
- validador de respostas da IA;
- *fallback* quando não houver dados suficientes;
- proteção de *secrets* e variáveis de ambiente;
- testes automatizados, incluindo cenários de *prompt injection*;
- autenticação e controle de acesso aos dados financeiros.

Princípio central: **a IA nunca deve inventar dados financeiros do usuário.**

## Stack

| Camada | Tecnologias |
| --- | --- |
| Frontend | React e Vite |
| Backend | Python e FastAPI |
| Dados | PostgreSQL |
| IA | LLMs e embeddings |
| RAG | ChromaDB ou FAISS |
| Qualidade | Pytest, Flake8 e Black |
| Conteinerização | Docker e Docker Compose |
| Automação | GitHub Actions |

## Metodologia

O desenvolvimento seguirá Scrum e XP adaptados para uma pessoa desenvolvedora, com sprints, entregas incrementais, priorização de backlog, testes automatizados e revisão contínua.

| Sprint | Período |
| --- | --- |
| Sprint 0 | 07/08 → 13/08 |
| Sprint 1 | 14/08 → 18/08 |
| Sprint 2 | 19/08 → 23/08 |
| Sprint 3 | 24/08 → 30/08 |
| Sprint 4 | 31/08 → 09/09 |
| Sprint 5 | 10/09 → 18/09 |
| Sprint 6 | 19/09 → 27/09 |

## CI

Em `push` e `pull_request` para a branch `main`, o workflow executa:

```text
Setup do Python → Flake8 → Black → Pytest
```

## Roadmap

| Milestone | Escopo |
| --- | --- |
| M1 — Foundation | EPIC-01: Fundação e Arquitetura |
| M2 — Core Backend | EPIC-02, EPIC-03 e EPIC-07 |
| M3 — AI Engine | EPIC-04 e EPIC-05 |
| M4 — Product Ready | EPIC-06, EPIC-08 a EPIC-14 |

O EPIC-14, Inteligência Avançada, é um *stretch goal* e será priorizado somente se o cronograma principal estiver seguro.

## Instalação

### Com Docker

1. Crie o arquivo local de variáveis de ambiente:

   ```powershell
   Copy-Item .env.example .env
   ```

2. Inicie os serviços:

   ```powershell
   docker compose up --build
   ```

A API estará disponível em `http://localhost:8000`, com verificação de saúde em `http://localhost:8000/health`. A interface estará disponível em `http://localhost:5173`.

## Status

**Fundação em andamento.** A estrutura de execução local, o endpoint de saúde da API, a interface inicial e o workflow de CI estão disponíveis. As funcionalidades de produto ainda não foram implementadas.

## Licença

Distribuído sob a licença [MIT](LICENSE).
