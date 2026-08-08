# FinAI Advisor

> Um assistente financeiro inteligente que transforma dados de gastos em clareza, relatórios e decisões mais conscientes.
Assistente financeiro com IA para ajudar usuários a registrar, analisar e compreender suas finanças pessoais.

O **FinAI Advisor** é um projeto de assistente pessoal de finanças apoiado por inteligência artificial. Seu objetivo é ajudar pessoas a entender sua vida financeira por meio da organização de despesas, análise de hábitos de consumo, respostas contextualizadas e recomendações práticas de melhoria.
O FinAI Advisor é um projeto de portfólio que reúne desenvolvimento full stack, inteligência artificial, RAG, APIs, banco de dados, segurança, testes, conteinerização e CI/CD. O projeto encontra-se em sua fase inicial; as funcionalidades descritas neste documento representam o escopo planejado, salvo indicação contrária.

> **Aviso:** o FinAI Advisor oferece apoio educacional e informativo. Ele não substitui orientação de profissionais certificados nem constitui recomendação de investimento, crédito ou produto financeiro.
> **Aviso:** o FinAI Advisor terá finalidade informativa e educacional. Não oferecerá recomendação profissional de investimento, crédito ou produtos financeiros.

## Problema

Controlar finanças pessoais costuma exigir tempo, conhecimento e consistência. Mesmo quando os dados estão disponíveis, pode ser difícil responder perguntas simples, como:
Dados financeiros pessoais frequentemente ficam dispersos e são difíceis de interpretar. Registrar receitas e despesas, identificar padrões de consumo, acompanhar metas e transformar números em decisões práticas exige tempo e conhecimento.

- Para onde meu dinheiro está indo?
- Quais despesas mais cresceram neste mês?
- Estou dentro do orçamento?
- O que posso ajustar para atingir uma meta financeira?
Além disso, uma interface de IA aplicada a finanças precisa ser confiável: ela não pode preencher lacunas inventando transações, saldos ou conclusões sem respaldo nos dados do usuário e em fontes verificáveis.

O FinAI Advisor busca tornar essas respostas mais acessíveis, usando linguagem natural e análises baseadas nos dados que o próprio usuário disponibiliza.
## Solução proposta

O FinAI Advisor centralizará informações financeiras do usuário e oferecerá análises, relatórios e um chat em linguagem natural. As respostas do assistente combinarão os dados financeiros autorizados pelo usuário com uma base de conhecimento confiável, usando RAG (*Retrieval-Augmented Generation*), e passarão por validações antes da entrega.

## Funcionalidades previstas
## Funcionalidades planejadas

- Registro e categorização de receitas e despesas;
- Visualização da situação financeira por período e categoria;
- Relatórios e resumos financeiros personalizados;
- Perguntas em linguagem natural sobre gastos, orçamento e metas;
- Base de conhecimento financeiro para respostas educativas;
- Identificação de padrões, variações e possíveis excessos de gastos;
- Sugestões de ações para melhorar a organização financeira;
- Definição e acompanhamento de metas, como reserva de emergência, quitação de dívidas ou economia mensal.
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

## Como o assistente deve funcionar
O fluxo planejado para perguntas ao assistente será:

```text
Dados financeiros do usuário
          ↓
Organização e categorização
          ↓
Análise de padrões e indicadores
          ↓
IA + base de conhecimento financeiro
          ↓
Respostas, relatórios e sugestões acionáveis
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

O foco é converter números em explicações claras: apresentar o que aconteceu, por que pode ter acontecido e quais próximos passos o usuário pode considerar.
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

## Exemplos de perguntas
O desenvolvimento seguirá Scrum e XP adaptados para uma pessoa desenvolvedora. O planejamento será organizado em sprints, com entregas incrementais, priorização de backlog, testes automatizados e revisão contínua da qualidade.

- “Quanto gastei com alimentação este mês?”
- “Compare meus gastos de transporte dos últimos três meses.”
- “Quais categorias ultrapassaram meu orçamento?”
- “Como posso reduzir meus gastos sem comprometer despesas essenciais?”
- “Monte um resumo financeiro do mês.”
- “Quanto preciso guardar por mês para alcançar minha meta?”
| Sprint | Período |
| --- | --- |
| Sprint 0 | 07/08 → 13/08 |
| Sprint 1 | 14/08 → 18/08 |
| Sprint 2 | 19/08 → 23/08 |
| Sprint 3 | 24/08 → 30/08 |
| Sprint 4 | 31/08 → 09/09 |
| Sprint 5 | 10/09 → 18/09 |
| Sprint 6 | 19/09 → 27/09 |

## Princípios do projeto
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

- **Clareza:** informações financeiras devem ser compreensíveis, não apenas tecnicamente corretas.
- **Personalização:** análises e sugestões devem considerar o contexto e os objetivos do usuário.
- **Privacidade:** dados financeiros exigem proteção, transparência e controle pelo usuário.
- **Responsabilidade:** sugestões devem evitar promessas de resultado e explicitar suas limitações.
- **Ação:** cada análise deve ajudar o usuário a tomar uma próxima decisão prática.
O pipeline será automatizado com GitHub Actions quando a estrutura do projeto estiver disponível.

## Roadmap

## Privacidade e segurança
| Milestone | Escopo |
| --- | --- |
| M1 — Foundation | EPIC-01: Fundação e Arquitetura |
| M2 — Core Backend | EPIC-02: Gestão Financeira; EPIC-03: Análise Financeira; EPIC-07: Autenticação |
| M3 — AI Engine | EPIC-04: Inteligência Artificial; EPIC-05: RAG / Knowledge Base |
| M4 — Product Ready | EPIC-06, 08, 09, 10, 11, 12, 13 e 14 |

Como o projeto lida com informações financeiras potencialmente sensíveis, sua implementação deve priorizar:
Épicos planejados:

- coleta apenas dos dados necessários;
- autenticação e controle de acesso adequados;
- proteção de dados em trânsito e em armazenamento;
- não exposição de chaves, tokens ou dados pessoais em commits;
- transparência sobre o uso de IA e o tratamento dos dados;
- opção de o usuário revisar, exportar ou excluir suas informações, conforme aplicável.
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

## Status
O EPIC-14 será tratado como objetivo adicional e só será priorizado se o cronograma principal estiver seguro.

O FinAI Advisor está em fase inicial de concepção. A estrutura técnica, as instruções de instalação e os fluxos de execução serão documentados aqui à medida que forem implementados.
## Instalação

## Roadmap inicial
> **Ainda não disponível.** O repositório está na fase de fundação e ainda não contém a aplicação nem arquivos de configuração para instalação.

- [ ] Definir requisitos e jornadas principais do usuário;
- [ ] Modelar receitas, despesas, categorias, orçamentos e metas;
- [ ] Implementar cadastro e autenticação;
- [ ] Criar registro e consulta de transações;
- [ ] Implementar painel e relatórios básicos;
- [ ] Integrar o assistente de IA e a base de conhecimento;
- [ ] Adicionar recomendações, validações e avisos de segurança;
- [ ] Criar testes, documentação de API e guia de contribuição.
Quando a estrutura inicial estiver implementada, esta seção documentará os pré-requisitos, as variáveis de ambiente, os comandos de execução local, os serviços Docker e a estratégia de testes.

## Contribuições
## Status

Contribuições, sugestões e relatos de problemas são bem-vindos. Antes de abrir uma alteração, descreva claramente o objetivo, mantenha o escopo focado e nunca inclua dados pessoais, financeiros ou credenciais no repositório.
**Em planejamento / fundação.** Nenhuma funcionalidade de produto deve ser considerada implementada neste momento.

## Licença

Este projeto é disponibilizado sob a licença [MIT](LICENSE).
Distribuído sob a licença [MIT](LICENSE).