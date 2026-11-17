# Documento de visão

Sistema de gestão de competências e feedback — versão 0.2, 17 de novembro de 2026. Situação: proposta para validação.

Estrutura baseada no modelo de documento de visão de Larman (*Utilizando UML e padrões*, cap. 7): problema, stakeholders, necessidades, visão geral do produto, funcionalidades e restrições.

## 1. Introdução

Este documento apresenta o problema, os envolvidos e o escopo da primeira versão de um sistema web para avaliação de desempenho por meio de feedbacks estruturados. Os requisitos detalhados estão na [especificação de requisitos](requisitos/especificacao-requisitos.md) e na [lista geral](requisitos/lista-geral.md).

## 2. Posicionamento

### 2.1. Declaração do problema

| | |
| --- | --- |
| **O problema** | Avaliações e feedbacks feitos de forma informal, em planilhas ou conversas, sem critérios padronizados nem histórico. |
| **Afeta** | Profissionais, gestores e a área de RH. |
| **Cujo impacto é** | Avaliações pouco comparáveis, perda de histórico, dificuldade de acompanhar a evolução das pessoas e risco de exposição indevida de dados pessoais. |
| **Uma solução bem-sucedida** | Padronizaria questionários, organizaria campanhas de avaliação mútua, preservaria o histórico e apresentaria indicadores confiáveis, com acesso controlado conforme a LGPD. |

### 2.2. Declaração de posição do produto

| | |
| --- | --- |
| **Para** | Organizações que querem estruturar a avaliação entre pessoas que trabalham juntas. |
| **Quem** | Precisa aplicar avaliações periódicas e acompanhar a evolução de cada profissional. |
| **O sistema** | É uma aplicação web de gestão de competências e feedback. |
| **Que** | Cria coletas com questionários padronizados, gera avaliações recíprocas por pares ou por times e analisa os resultados ao longo do tempo. |
| **Diferentemente de** | Planilhas e formulários genéricos. |
| **Nosso produto** | Preserva o questionário de cada coleta, garante reciprocidade e independência das respostas e calcula indicadores comparáveis entre ciclos. |

## 3. Stakeholders e usuários

### 3.1. Stakeholders que não são usuários

| Stakeholder | Interesse |
| --- | --- |
| Responsável pelo negócio (stakeholder entrevistado) | Definir o processo de avaliação e validar o escopo e as prioridades. |
| Organização usuária (controladora dos dados) | Cumprir a LGPD e usar os resultados de forma adequada. |
| Professor da disciplina | Avaliar a qualidade dos artefatos de requisitos. |

### 3.2. Perfis de usuário

| Perfil | Descrição | Responsabilidades |
| --- | --- | --- |
| RH | Administra o processo de avaliação. | Mantém usuários, times, catálogo de perguntas e coletas; acompanha coletas e planos de ação em toda a organização. |
| GESTOR | Responsável por um ou mais times. | Cria e acompanha coletas, avaliações 360°, planos de ação e resultados dos times sob sua responsabilidade. |
| PROF (profissional) | Participante comum. | Responde às avaliações atribuídas, faz autoavaliação, registra feedbacks informais, executa as ações dos seus planos e consulta seus resultados liberados. |

Qualquer perfil pode avaliar e ser avaliado. *Avaliador* e *receptor* são papéis circunstanciais em cada avaliação, não perfis de acesso.

### 3.3. Principais necessidades

| Necessidade | Prioridade | Solução proposta |
| --- | --- | --- |
| Padronizar critérios de avaliação | Alta | Catálogo de grupos e parâmetros com tipos de avaliação (RF05 a RF07). |
| Organizar ciclos de avaliação mútua | Alta | Coletas por pares ou por times, com avaliações nos dois sentidos (RF08 a RF10). |
| Responder de forma independente e segura | Alta | Rascunho, envio imutável e liberação após o par completo (RF11, RF12, RN09). |
| Acompanhar a evolução individual | Alta | Histórico e análise com indicadores comparáveis (RF14, RF15, RN10, RN11). |
| Proteger dados pessoais | Alta | Controle de acesso, auditoria e requisitos da LGPD (RF16, RNF01, RF-DOC). |
| Contemplar diferentes perspectivas | Alta | Avaliação 360°, autoavaliação, feedback informal e classificação dos feedbacks (RF17, RF19, RF20, RF22). |
| Documentar o desempenho com contexto | Alta | Registro dos fatos e impactos de cada feedback (RF21, RN16). |
| Orientar o desenvolvimento | Alta | Planos de ação ligados ao feedback, com metas, prazos e acompanhamento (RF18, RN13). |

## 4. Visão geral do produto

Aplicação web, em português, acessada por navegador e preparada para telas de celular. O RH monta o questionário a partir do catálogo, escolhe os participantes e abre a coleta. Cada participante responde sobre os colegas indicados, e os resultados são liberados quando a coleta é encerrada. Além das coletas recíprocas, o sistema oferece avaliação 360°, autoavaliação e feedback informal, e permite ligar um feedback a um plano de ação acompanhado até o feedback seguinte.

### 4.1. Premissas e dependências

- Cada usuário tem um perfil e pertence a um time ativo para participar de novas coletas.
- Uma coleta usa um único questionário para todos os pares.
- Autenticação por identificador único de conta (e-mail proposto).
- Linguagem, framework e hospedagem ainda não foram definidos.

## 5. Funcionalidades

### 5.1. Escopo da primeira versão

1. Cadastro de usuários, times e relações de trabalho.
2. Catálogo de grupos de parâmetros e perguntas, com remanejamento.
3. Configuração, abertura, acompanhamento e encerramento de coletas.
4. Geração de avaliações recíprocas por pares ou por times.
5. Preenchimento em rascunho e envio das avaliações.
6. Histórico individual e análise de resultados.
7. Auditoria das operações administrativas.
8. Avaliação 360° e autoavaliação.
9. Registro de feedback informal, com contexto e classificação formal ou informal e positivo ou construtivo.
10. Planos de ação com metas, ações, prazos e acompanhamento.

### 5.2. Fora do escopo ou pendente de confirmação

- Anonimato das respostas (conflito C02).
- Regras de liberação dos resultados do 360°, da autoavaliação e do feedback informal (PV04).
- Aplicativo móvel nativo e integrações com sistemas de RH.
- Calibração, reuniões individuais, reconhecimento e pesquisas de engajamento, observados no sistema análogo.

A avaliação 360°, a autoavaliação, o feedback informal, a classificação e os planos de ação passaram a integrar o escopo com a síntese das entrevistas e permanecem como propostas até a validação com o stakeholder.

## 6. Restrições

- Não há exclusão física de dados (RN12), sujeita à compatibilização com a LGPD (conflito C01).
- Questionários publicados e resultados históricos não podem ser alterados retroativamente.
- Requisitos de qualidade: ver a [especificação suplementar](requisitos/especificacao-suplementar.md).

## 7. Pontos pendentes de confirmação

| Pendência | Descrição |
| --- | --- |
| PV03, PV04 | Obrigatoriedade da reciprocidade e matriz de acesso aos resultados. |
| PV05 | Política de privacidade e retenção. |
| PV08 | Resolvida pela síntese das entrevistas: as modalidades e os planos do enunciado integram a primeira versão, ainda como proposta. |
| Fontes | Transcrições das entrevistas (#41) ainda não recebidas e questionários (#7, #8) ainda não aplicados. |
