# ADR 001 — Escolha da Stack

## Status

Aprovado

## Contexto

O FinAI Advisor precisa de uma arquitetura full stack adequada para uma aplicação financeira com API, persistência de dados, interface web e futura integração com IA e RAG.

## Decisão

Será utilizada a seguinte stack principal:

- Backend: Python com FastAPI;
- Frontend: React;
- Banco de dados: PostgreSQL.

## Consequências

- FastAPI oferece uma base moderna e tipada para construir a API e integrar serviços de IA.
- React permite criar uma interface web componentizada para dashboard, relatórios e chat.
- PostgreSQL fornece persistência relacional para usuários, transações, categorias, metas e relatórios.
- O projeto exigirá integração e manutenção separadas entre frontend, backend e banco de dados.