# FinAI Advisor

Assistente financeiro com IA para ajudar usuários a registrar, analisar e compreender suas finanças pessoais.

O FinAI Advisor é um projeto de portfólio que reúne desenvolvimento full stack, inteligência artificial, RAG, APIs, banco de dados, segurança, testes, conteinerização e CI/CD. O projeto encontra-se em sua fase inicial; as funcionalidades descritas neste documento representam o escopo planejado, salvo indicação contrária.

> **Aviso:** o FinAI Advisor terá finalidade informativa e educacional. Não oferecerá recomendação profissional de investimento, crédito ou produtos financeiros.

## Problema

Dados financeiros pessoais frequentemente ficam dispersos e são difíceis de interpretar. Registrar receitas e despesas, identificar padrões de consumo, acompanhar metas e transformar números em decisões práticas exige tempo e conhecimento.

Além disso, uma interface de IA aplicada a finanças precisa ser confiável: ela não pode preencher lacunas inventando transações, saldos ou conclusões sem respaldo nos dados do usuário e em fontes verificáveis.

## Solução proposta

O FinAI Advisor centralizará informações financeiras do usuário e oferecerá análises, relatórios e um chat em linguagem natural. As respostas do assistente combinarão os dados financeiros autorizados pelo usuário com uma base de conhecimento confiável, usando RAG (*Retrieval-Augmented Generation*), e passarão por validações antes da entrega.

## Funcionalidades planejadas

- Cadastro de receitas, despesas e categorias financeiras;
- Dashboard financeiro e análise de gastos;
- Gestão de metas financeiras;
- Relatórios financeiros;
- Autenticação de usuários;
- Chat com IA fundamentado nos dados financeiros do usuário;
- RAG com base de conhecimento financeiro confiável;
- Respostas da IA com validação e fontes quando aplicável.

## Arquitetura proposta

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

## IA e RAG

O fluxo planejado para perguntas ao assistente será:

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

O RAG permitirá consultar uma base de conhecimento selecionada. Dados financeiros do usuário e conteúdos recuperados deverão compor o contexto da resposta; na ausência de dados ou contexto suficiente, o sistema deverá informar essa limitação em vez de inventar informações.

## Segurança e confiabilidade

Para reduzir alucinações e proteger informações sensíveis, o projeto prevê:

- RAG baseado em fontes confiáveis;
- validação de contexto e *similarity threshold* para recuperação de conteúdo;
- validador de respostas da IA;
- *fallback* quando não houver dados suficientes;
- proteção de *secrets* e variáveis de ambiente;
- testes automatizados, incluindo cenários de *prompt injection*;
- autenticação e controle de acesso aos dados financeiros.

Princípio central: **a IA nunca deve inventar dados financeiros do usuário.**

## Stack planejada

| Camada | Tecnologias |
| --- | --- |
| Frontend | React |
| Backend | Python e FastAPI |
| Dados | PostgreSQL |
| IA | LLMs e embeddings |
| RAG | ChromaDB ou FAISS |
| Qualidade | Pytest |
| Conteinerização | Docker |
| Automação | GitHub Actions |

## Metodologia

O desenvolvimento seguirá Scrum e XP adaptados para uma pessoa desenvolvedora. O planejamento será organizado em sprints, com entregas incrementais, priorização de backlog, testes automatizados e revisão contínua da qualidade.

| Sprint | Período |
| --- | --- |
| Sprint 0 | 07/08 → 13/08 |
| Sprint 1 | 14/08 → 18/08 |
| Sprint 2 | 19/08 → 23/08 |
| Sprint 3 | 24/08 → 30/08 |
| Sprint 4 | 31/08 → 09/09 |
| Sprint 5 | 10/09 → 18/09 |
| Sprint 6 | 19/09 → 27/09 |

## CI/CD planejado

```text
Push / Pull Request
  ↓
Lint
  ↓
Tests
  ↓
Build
  ↓
Docker
  ↓
Deploy
```

O pipeline será automatizado com GitHub Actions quando a estrutura do projeto estiver disponível.

## Roadmap

| Milestone | Escopo |
| --- | --- |
| M1 — Foundation | EPIC-01: Fundação e Arquitetura |
| M2 — Core Backend | EPIC-02: Gestão Financeira; EPIC-03: Análise Financeira; EPIC-07: Autenticação |
| M3 — AI Engine | EPIC-04: Inteligência Artificial; EPIC-05: RAG / Knowledge Base |
| M4 — Product Ready | EPIC-06, 08, 09, 10, 11, 12, 13 e 14 |

Épicos planejados:

1. Fundação e Arquitetura
2. Gestão Financeira
3. Análise Financeira
4. Inteligência Artificial
5. RAG / Knowledge Base
6. Segurança e Confiabilidade
7. Autenticação
8. Metas Financeiras
9. Relatórios
10. DevOps / CI-CD
11. Qualidade / XP
12. Documentação
13. Observabilidade
14. Inteligência Avançada *(stretch goal)*

O EPIC-14 será tratado como objetivo adicional e só será priorizado se o cronograma principal estiver seguro.

## Instalação

> **Ainda não disponível.** O repositório está na fase de fundação e ainda não contém a aplicação nem arquivos de configuração para instalação.

Quando a estrutura inicial estiver implementada, esta seção documentará os pré-requisitos, as variáveis de ambiente, os comandos de execução local, os serviços Docker e a estratégia de testes.

## Status

**Em planejamento / fundação.** Nenhuma funcionalidade de produto deve ser considerada implementada neste momento.

## Licença

Distribuído sob a licença [MIT](LICENSE).
