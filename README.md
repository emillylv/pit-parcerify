# Marketplace de conexão entre pequenos criadores de conteúdo e micro e pequenos negócios

> Aplicativo Android que conecta micro e pequenos negócios a nano influenciadores (até 10 mil seguidores) e criadores UGC por afinidade de **nicho, público e localização**, em um formato de **deslize (swipe)**.

**Status:** em planejamento e prototipação (desenvolvimento previsto de janeiro a junho de 2027)

---

## Sobre o projeto

O projeto propõe um marketplace de parcerias em que:

- o **criador de conteúdo** navega por um feed de campanhas publicadas por empresas e demonstra interesse deslizando o card;
- a **empresa** navega por um feed de criadores compatíveis e também demonstra interesse;
- o criador "curte" uma campanha (candidatura) e a empresa "curte" um criador para essa campanha (convite); quando há **interesse dos dois lados**, a API registra o match, libera o chat e envia uma notificação push;
- as condições da parceria (entregáveis, prazo, remuneração ou permuta) são combinadas no chat, e a parceria só é concluída com a **confirmação explícita do criador**.

## Problema abordado

Pequenos negócios têm dificuldade em encontrar criadores compatíveis com sua marca, público e localização, e a seleção de influenciadores é apontada como um dos principais desafios do marketing de influência para anunciantes brasileiros (Santos; Bernardo; Ramos, 2022). Do outro lado, pequenos criadores, que ainda constroem sua audiência, têm dificuldade em identificar empresas abertas a parcerias. As plataformas existentes costumam priorizar perfis com maior engajamento ou marcas de maior porte.

**Pergunta de pesquisa:** como um marketplace digital poderá facilitar a conexão entre pequenos negócios e pequenos criadores de conteúdo, considerando afinidade de marca, público, localização, estilo de conteúdo e orçamento, de modo a ampliar o acesso a oportunidades de parceria para ambos?

## Objetivos

### Objetivo geral

Investigar e propor o desenvolvimento de um marketplace digital que facilite a conexão entre pequenos negócios e pequenos criadores de conteúdo, permitindo a identificação de parceiros compatíveis com características da marca, do público, da localização, do estilo de conteúdo e do orçamento disponível.

### Objetivos específicos

- Identificar as dificuldades de pequenos negócios na busca por criadores de conteúdo.
- Identificar as dificuldades de pequenos criadores para encontrar oportunidades de parceria.
- Levantar critérios de compatibilidade entre negócios e criadores (segmento, público, localização, estilo de conteúdo, alcance e orçamento).
- Analisar marketplaces e plataformas de marketing de influência para definir os requisitos do software.
- Propor as principais funcionalidades e fluxos de interação do marketplace.
- Avaliar a viabilidade da proposta como solução tecnológica.

## Funcionalidades principais (MVP)

- Cadastro, login e recuperação de senha para empresas e criadores
- Perfil de empresa e perfil de criador (com métricas informadas manualmente)
- Publicação de campanhas pela empresa
- Feed de swipe de campanhas (criador) e de criadores (empresa), com filtros
- Match por interesse mútuo
- Chat entre empresa e criador
- Confirmação explícita da parceria pelo criador

A priorização completa (MoSCoW) está no Product Backlog: _[link do Trello]_

## Tecnologias previstas

| Camada | Tecnologia |
| --- | --- |
| Aplicativo (front-end) | Flutter e Dart (Android), padrão MVVM |
| Estado, navegação e comunicação | provider, go_router e dio |
| API (back-end) | Python e FastAPI, hospedada no Railway |
| Recomendação | Pontuação linear com pesos (v1); scikit-learn e XGBoost (futuro) |
| Banco de dados | PostgreSQL com PostGIS (Supabase, região São Paulo) |
| Autenticação, arquivos e chat | Supabase Auth, Storage e Realtime |
| Notificações | Firebase Cloud Messaging |
| Integração (etapa 2) | API do Instagram (métricas verificadas dos criadores) |
| Versionamento | Git e GitHub |
| Design e gestão | Figma e Trello |

**Arquitetura:** cliente-servidor em três camadas, com API própria: aplicativo Flutter (apresentação), API REST em FastAPI (serviços: regras de negócio, matching, recomendação e notificações) e PostgreSQL gerenciado pelo Supabase (dados). O aplicativo envia toda regra de negócio à API e usa o Supabase diretamente apenas para login, envio de fotos e recebimento do chat. O banco fica na região São Paulo; a API, na região US East, pois o Railway não possui região na América do Sul. O diagrama está em [`docs/`](docs/).

## Estrutura do repositório

```
docs/        → introdução, requisitos, histórias de usuário, arquitetura, backlog, PMC
app/         → aplicativo Flutter
api/         → API FastAPI (Python)
database/    → migrations SQL, políticas de acesso (RLS) e scripts
README.md
```

## Como executar

_Será preenchido na etapa de implementação (pré-requisitos, instalação do Flutter, configuração do projeto Supabase e comandos de execução)._

## Equipe

| Nome | Papel |
| --- | --- |
| Amanda Pimentel Gonçalves | Integrante da equipe |
| Emilly Luiza Vermeulen Cordeiro | Integrante da equipe |
| Humberto Fernandes Villela | Orientador |

Faculdade Cotemig · Projeto de Inovação Tecnológica I · Belo Horizonte, 2026

## Documentação

- [Introdução e referencial](docs/)
- [Requisitos e análise de concorrentes](docs/)
- [Personas e histórias de usuário](docs/)
- [Arquitetura e protótipo](docs/)
- Product Backlog: _[link do Trello]_

## Licença

_Definir com o orientador (ex.: MIT, ou "todos os direitos reservados" enquanto o projeto for acadêmico)._
