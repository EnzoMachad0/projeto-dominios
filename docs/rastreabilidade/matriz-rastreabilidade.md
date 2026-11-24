# Matriz de rastreabilidade

| Campo | Informação |
| --- | --- |
| Autoria | Danilo Sucupira Galvão |
| Versão | 0.8 — 23 de novembro de 2026 |
| Base inicial | `main` em 10/11/2026 (commit `0bd8dc9`), com os artefatos dos PRs #27 a #37 |
| Atualização | CU-03 de Heitor Barbosa Souza em 15/11/2026; CU-01 de Brenner Rodrigues Sardinha e CU-04 de Enzo de Oliveira Machado em 17/11/2026; situação das entrevistas e correção das inconsistências I01 a I05 em 17/11/2026, sobre a `main` no commit `f7250bc`; consolidação da síntese das entrevistas e do sistema análogo (#40) por Luiz Augusto Vaz em 17/11/2026, sobre a `main` no commit `a6aabfa`; processo de negócio (BPMN), visão arquitetural C4 e modelo de projeto por Luiz Augusto Vaz em 21/11/2026, sobre a `main` no commit `93c8446` |
| Situação | Proposta para revisão |

Relaciona as fontes, as necessidades e os requisitos aos artefatos que os detalham, modelam e verificam (rastreabilidade vertical), e os requisitos entre si (rastreabilidade horizontal). Atende à issue #24 e à seção 3 do [processo de requisitos](../PROCESSO_REQUISITOS.md).

## 1. Convenção

### 1.1. Rastreabilidade vertical e horizontal

- **Vertical:** liga itens de níveis diferentes, na cadeia fonte → dor do processo → necessidade → requisito → caso de uso → entidade → elemento de arquitetura → elemento de projeto → tela → verificação. Cada linha das tabelas da seção 3 é lida nos dois sentidos: para trás, do requisito até a fonte que o originou; para frente, do requisito até os artefatos que o detalham e o verificam.
- **Horizontal:** liga itens do mesmo nível, ou seja, um requisito com outro: dependência, restrição por regra de negócio, complemento por requisito não funcional, consolidação, atendimento e conflito (seção 4).

### 1.2. Códigos de fonte

São os mesmos da [lista geral](../requisitos/lista-geral.md) (seção 1) e da [especificação de requisitos](../requisitos/especificacao-requisitos.md) (seção 1.4): E01, E02, Q01, Q02, SA, DOC e ENU.

A [pesquisa documental](../levantamento/pesquisa-documental.md) (seção 2) usa F01 a F14 para identificar cada documento consultado dentro da fonte DOC (F01 é a LGPD). Nas linhas de origem DOC, esta matriz cita o documento pelo nome (LGPD, resoluções da ANPD).

### 1.3. Legenda

| Valor | Significado |
| --- | --- |
| `A conferir` | O [protótipo no Figma](https://www.figma.com/design/pD7rcKYlK7cQ0M5KidV1kL/PulsarRH?node-id=1-3) foi produzido (#22), mas a tela correspondente ainda não foi identificada nesta matriz (lacuna L03). |
| `—` | Não há vínculo. A justificativa está na seção 6. |
| `N/A` | O vínculo não se aplica: requisito de infraestrutura ou de armazenamento, sem caso de uso nem tela própria, ou sem tela prevista na interface do usuário (RI01 da especificação). |
| `Transversal` | O requisito apoia todas as necessidades N01 a N05. |

### 1.4. Onde cada item está detalhado

| Item | Documento |
| --- | --- |
| Fontes E01, E02, Q01, Q02, SA, DOC e ENU | [Lista geral](../requisitos/lista-geral.md), seção 1 |
| Necessidades N01 a N08 | [Documento de visão](../visao.md), seção 3.3 (os códigos foram atribuídos nesta matriz) |
| RF01 a RF22, RN01 a RN16, CA01 a CA18 | [Especificação de requisitos](../requisitos/especificacao-requisitos.md), seções 3.2, 3.3 e 3.6 |
| Correspondência com a síntese (`SIN-*`) e o sistema análogo | [Lista geral](../requisitos/lista-geral.md), seção 9 |
| RF-DOC, RN-DOC e RNF-DOC | [Pesquisa documental](../levantamento/pesquisa-documental.md), seção 5 |
| RNF01 a RNF16 | [Especificação suplementar](../requisitos/especificacao-suplementar.md), seção 3 |
| Casos de uso | [Índice e diagrama](../casos-de-uso/README.md), [CU-01](../casos-de-uso/CU-01-configurar-e-abrir-coleta.md), [CU-02](../casos-de-uso/CU-02-responder-e-enviar-avaliacao.md), [CU-03](../casos-de-uso/CU-03-encerrar-ou-cancelar-coleta.md), [CU-04](../casos-de-uso/CU-04-consultar-analise-de-resultados.md) e [CU-05](../casos-de-uso/CU-05-manter-catalogo-de-parametros.md) |
| Entidades | [MER](../modelos/dominio/modelo-entidade-relacionamento.md) e [dicionário de dados](../dicionario-dados.md) |
| Dores D1 a D6 e etapas do processo | [Processo de negócio (BPMN)](../modelos/processo/README.md) |
| Containers, componentes, decisões AD01 a AD05 e lacunas A01 a A05 (C4) | [Visão arquitetural](../modelos/arquitetura/README.md), seções 4 a 7 |
| Diagramas de estado, contratos CO01 a CO04, diagramas de sequência e de classes de projeto | [Modelo de projeto](../modelos/projeto/README.md) |
| Padrões de projeto PP01 a PP22 | [Padrões de projeto](../modelos/projeto/padroes-de-projeto.md) |
| Achados AC01 a AC25 da auditoria de normas ISO | [Auditoria de conformidade](../auditoria/auditoria-conformidade-iso.md), seção 12: cada achado lista os requisitos afetados |

## 2. Fontes e necessidades

### 2.1. Fontes

| Código | Fonte | Situação | Registro no repositório |
| --- | --- | --- | --- |
| E01 | Entrevista com o stakeholder e esclarecimentos posteriores | Realizada | [Resumo anotado](../levantamento/entrevistas/E01-perguntas-e-resumo-das-respostas.md) (oral, sem gravação; L01); [síntese](../levantamento/sintese-entrevistas.md) |
| E02 | Entrevista com a professora da disciplina (20/10/2026) | Realizada | [Identificação e resultado](../levantamento/entrevistas/E02-entrevista-professora.md) (oral, sem gravação e sem anotação das respostas; L01); confirmou, com a E01, os requisitos da lista geral v0.3 |
| Q01, Q02 | Questionários de levantamento | Pendentes | — (lacuna L02) |
| SA | Análise do sistema análogo Culture Amp | Realizada | [analise-sistema-analogo-culture-amp.md](../levantamento/analise-sistema-analogo-culture-amp.md); correspondência na lista geral, seção 9.2 |
| DOC | Pesquisa documental sobre LGPD e ISO/IEC 25010 | Realizada | [pesquisa-documental.md](../levantamento/pesquisa-documental.md) |
| ENU | Enunciado da disciplina | Consultado | PDF da disciplina, fora do repositório |

### 2.2. Necessidades

| Código | Necessidade (visão, seção 3.3) | Prioridade | Fontes |
| --- | --- | --- | --- |
| N01 | Padronizar critérios de avaliação | Alta | E01 |
| N02 | Organizar ciclos de avaliação mútua | Alta | E01, ENU |
| N03 | Responder de forma independente e segura | Alta | E01 |
| N04 | Acompanhar a evolução individual | Alta | E01, ENU |
| N05 | Proteger dados pessoais | Alta | E01, DOC |
| N06 | Orientar o desenvolvimento | Alta | E01, ENU, SA |
| N07 | Contemplar diferentes perspectivas | Alta | E01, ENU |
| N08 | Documentar o desempenho com contexto | Alta | E01 |

## 3. Matriz vertical

### 3.1. Requisitos funcionais

| ID | Resumo | Fonte | Necessidade | Caso de uso | Entidades | Arquitetura (C4) | Protótipo | Verificação | Situação |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| RF01 | Autenticar e autorizar em cada operação | E01, DOC | N05 | CU-08; pré-condição de CU-01 a CU-05 | USUARIO | Autenticação e acesso; Política de visibilidade | A conferir | CA02 | Validado (E01, E02) |
| RF02 | Manter usuários | E01 | N02 | CU-06 | USUARIO, TIME | Organização | A conferir | CA01 | Validado (E01, E02) |
| RF03 | Manter times | E01 | N02 | CU-06 | TIME, USUARIO | Organização | A conferir | CA01 | Validado (E01, E02) |
| RF04 | Manter relações de trabalho | E01 | N02 | CU-07 | RELACAO_TRABALHO | Organização | A conferir | CA01, CA03 | Validado (E01, E02) |
| RF05 | Manter parâmetros | E01 | N01 | CU-05 | PARAM, GRUPO_PARAM | Catálogo | A conferir | CA01, CA05, CA11 | Validado (E01, E02) |
| RF06 | Manter grupos de parâmetros | E01 | N01 | CU-05 | GRUPO_PARAM | Catálogo | A conferir | CA01, CA05 | Validado (E01, E02) |
| RF07 | Remanejar parâmetros entre grupos | E01 | N01 | CU-05 | PARAM, GRUPO_PARAM, COLETA_GRUPO, COLETA_PARAM | Catálogo | A conferir | CA04, CA11 | Validado (E01, E02) |
| RF08 | Configurar coletas | E01 | N02 | CU-01, CU-09 | COLETA, COLETA_PAR, COLETA_TIME, COLETA_PARTICIPANTE, COLETA_GRUPO, COLETA_PARAM | Coletas | A conferir | CA01, CA05 | Validado (E01, E02) |
| RF09 | Publicar o questionário da coleta | E01 | N02 | CU-01 | COLETA, COLETA_GRUPO, COLETA_PARAM, AVALIACAO | Coletas | A conferir | CA05, CA06, CA06C | Validado (E01, E02) |
| RF10 | Atribuir avaliações mútuas por pares ou times | E01 | N02 | CU-01 | AVALIACAO, COLETA_PAR, COLETA_TIME, RELACAO_TRABALHO | Coletas | A conferir | CA06, CA06A, CA06B | Validado (E01, E02) |
| RF11 | Manter respostas em rascunho | E01 | N03 | CU-02 | FEEDBACK, AVALIACAO | Respostas | A conferir | CA01, CA07 | Validado (E01, E02) |
| RF12 | Enviar avaliação | E01 | N03 | CU-02 | AVALIACAO, FEEDBACK | Respostas | A conferir | CA08 | Validado (E01, E02) |
| RF13 | Acompanhar, encerrar e cancelar coletas | E01 | N02 | CU-03 | COLETA, AVALIACAO | Coletas | A conferir | CA12 | Validado (E01, E02) |
| RF14 | Consultar histórico individual | E01, ENU | N04 | CU-04 | AVALIACAO, FEEDBACK, COLETA_PARAM | Análise e histórico; Política de visibilidade | A conferir | CA09, CA11 | Validado (E01, E02) |
| RF15 | Analisar resultados por usuário | E01, ENU | N04 | CU-04 | AVALIACAO, FEEDBACK, COLETA_PARAM | Análise e histórico; Política de visibilidade | A conferir | CA10, CA11 | Validado (E01, E02) |
| RF16 | Registrar eventos de auditoria | E01, DOC, SA | N05 | CU-01, CU-02, CU-03, CU-05 | EVENTO_AUDITORIA | Auditoria | N/A | CA11, CA13 | Validado (E01, E02) |
| RF17 | Avaliação 360° | E01, ENU, SA | N07 | CU-09 | COLETA, COLETA_PARTICIPANTE, AVALIACAO | Coletas | A conferir | CA14 | Validado (E01, E02) |
| RF18 | Planos de ação com metas e acompanhamento | E01, ENU, SA | N06 | CU-11 | PLANO_ACAO, ACAO_PLANO, ACOMPANHAMENTO_ACAO, REGISTRO_FEEDBACK | Feedback e desenvolvimento | A conferir | CA18 | Validado (E01, E02) |
| RF19 | Classificar feedbacks (formal ou informal, positivo ou construtivo) | E01, ENU | N07 | CU-02, CU-10 | REGISTRO_FEEDBACK | Feedback e desenvolvimento; Respostas | A conferir | CA17 | Validado (E01, E02) |
| RF20 | Registrar feedback informal, fora de uma coleta | E01, ENU | N07 | CU-10 | REGISTRO_FEEDBACK | Feedback e desenvolvimento | A conferir | CA16 | Validado (E01, E02) |
| RF21 | Registrar o contexto do feedback | E01 | N08 | CU-02, CU-10 | REGISTRO_FEEDBACK | Feedback e desenvolvimento | A conferir | CA16 | Validado (E01, E02) |
| RF22 | Autoavaliação | E01 | N07 | CU-02, CU-09 | AVALIACAO, COLETA_PARTICIPANTE | Coletas; Respostas | A conferir | CA15 | Validado (E01, E02) |
| RF-DOC-01 | Aviso de privacidade | DOC (LGPD, arts. 6º, VI, e 9º) | N05 | — | — | Aplicação web | A conferir | — | Validado (E01, E02) |
| RF-DOC-02 | Contato do encarregado em destaque | DOC (LGPD, art. 41, §1º; Res. CD/ANPD nº 18/2024) | N05 | — | — | Aplicação web | A conferir | — | Validado (E01, E02) |
| RF-DOC-03 | Titular consulta os próprios dados | DOC (LGPD, arts. 18 e 19) | N05 | — | — | — | A conferir | — | Validado (E01, E02) |
| RF-DOC-04 | Registrar requisições de titulares e alertar sobre o prazo | DOC (LGPD, arts. 18 e 19) | N05 | — | — | — | A conferir | — | Validado (E01, E02) |
| RF-DOC-05 | Corrigir dados cadastrais | DOC (LGPD, art. 18, III) | N05 | CU-06, via RF02 | USUARIO | Organização, via RF02 | A conferir | CA01, via RF02 | Validado (E01, E02) |
| RF-DOC-06 | Titular contesta feedback recebido | DOC (LGPD, arts. 6º, V, e 18, III) | N05 | — | — | — | A conferir | — | Validado (E01, E02) |
| RF-DOC-07 | Anonimizar ou bloquear dados ao fim da retenção | DOC (LGPD, arts. 16 e 18) | N05 | — | — | — | A conferir | — | Validado (E01, E02) |
| RF-DOC-08 | Configurar prazo de retenção | DOC (LGPD, arts. 15 e 16) | N05 | — | — | — | A conferir | — | Validado (E01, E02) |
| RF-DOC-09 | Exportar dados do titular | DOC (LGPD, arts. 18, V, e 19) | N05 | — | — | — | A conferir | — | Validado (E01, E02) |
| RF-DOC-10 | Registrar e revogar consentimento | DOC (LGPD, arts. 8º e 18, IX) | N05 | — | — | — | A conferir | — | Validado (E01, E02) |
| RF-DOC-11 | Informar compartilhamentos com terceiros | DOC (LGPD, art. 18, VII) | N05 | — | — | — | A conferir | — | Validado (E01, E02) |
| RF-DOC-12 | Relatório das operações de tratamento | DOC (LGPD, art. 37) | N05 | — | — | — | A conferir | — | Validado (E01, E02) |
| RF-DOC-13 | Listar titulares afetados em incidente | DOC (LGPD, art. 48; Res. CD/ANPD nº 15/2024) | N05 | — | — | — | A conferir | — | Validado (E01, E02) |
| RF-DOC-14 | Orientar o avaliador a não incluir dados sensíveis no comentário | DOC (LGPD, arts. 6º, III, 11 e 12) | N05 | CU-02 (requisitos especiais) | FEEDBACK (`comentario`) | Aplicação web; Respostas | A conferir | — | Validado (E01, E02) |

### 3.2. Regras de negócio

Regras de negócio não têm tela própria. Elas aparecem nas telas dos requisitos funcionais que restringem (grade da seção 4.1).

| ID | Resumo | Fonte | Necessidade | Caso de uso | Entidades | Arquitetura (C4) | Verificação | Situação |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| RN01 | Reciprocidade | E01 | N02 | CU-01, CU-02, CU-03 | AVALIACAO | Coletas | CA06, CA06C, CA12 | Validado (E01, E02) |
| RN02 | Unicidade de avaliação e de resposta | E01 | N02 | CU-01, CU-02 | AVALIACAO, FEEDBACK | Coletas; Respostas | CA06, CA06A, CA06B, CA07 | Validado (E01, E02) |
| RN03 | Elegibilidade | E01 | N02 | CU-01 | USUARIO, TIME, RELACAO_TRABALHO, COLETA_PAR, COLETA_TIME | Coletas; Organização | CA06A, CA06B | Validado (E01, E02) |
| RN04 | Composição do catálogo e da coleta | E01 | N01 | CU-01, CU-05 | PARAM, COLETA_PARAM | Catálogo; Coletas | CA04, CA05 | Validado (E01, E02) |
| RN05 | Preservação do que foi publicado | E01 | N04 | CU-01, CU-04, CU-05 | COLETA, COLETA_TIME, COLETA_GRUPO, COLETA_PARAM, AVALIACAO | Coletas | CA04, CA06C, CA11 | Validado (E01, E02) |
| RN06 | Tipo de avaliação (`score`) | E01 | N01 | CU-02, CU-05 | PARAM, COLETA_PARAM, FEEDBACK | Catálogo; Respostas | CA07 | Validado (E01, E02) |
| RN07 | Estados da coleta | E01 | N02 | CU-01, CU-02, CU-03 | COLETA | Coletas | CA12 | Validado (E01, E02) |
| RN08 | Estados da avaliação e do feedback | E01 | N03 | CU-02, CU-03 | AVALIACAO, FEEDBACK | Respostas; Coletas | CA08, CA12 | Validado (E01, E02) |
| RN09 | Independência e liberação | E01 | N03 | CU-02, CU-03, CU-04 | AVALIACAO, FEEDBACK | Política de visibilidade | CA09 | Validado (E01, E02) |
| RN10 | Cálculo dos indicadores | E01, DOC | N04 | CU-04 | FEEDBACK, COLETA_PARAM (indicadores derivados do dicionário) | Análise e histórico | CA10 | Validado (E01, E02) |
| RN11 | Comparabilidade entre coletas | E01 | N04 | CU-04, CU-05 | COLETA_PARAM | Análise e histórico | CA11 | Validado (E01, E02) |
| RN12 | Sem exclusão física | E01 | N04 | CU-01, CU-03, CU-04, CU-05, CU-06 | Todas | Banco de dados (todos os componentes) | CA01 | Validado (E01, E02) |
| RN13 | Ciclo de desenvolvimento | E01 | N06 | CU-11 | PLANO_ACAO, REGISTRO_FEEDBACK | Feedback e desenvolvimento | CA18 | Validado (E01, E02) |
| RN14 | Escopo de atuação do gestor e do RH | E01 | N02, N06 | CU-01, CU-03, CU-09, CU-11 | TIME, COLETA, PLANO_ACAO | Política de visibilidade | CA02, CA14 | Validado (E01, E02) |
| RN15 | Regras por modalidade | E01 | N07 | CU-01, CU-02, CU-09, CU-10 | COLETA, COLETA_PARTICIPANTE, AVALIACAO, REGISTRO_FEEDBACK | Coletas; Política de visibilidade | CA14, CA15, CA16 | Validado (E01, E02) |
| RN16 | Feedback baseado em fatos | E01 | N08 | CU-10 | REGISTRO_FEEDBACK | Feedback e desenvolvimento | CA16 | Validado (E01, E02) |
| RN-DOC-01 | Finalidade definida para cada dado | DOC (LGPD, art. 6º, I a III) | N05 | — | — | — | — | Validado (E01, E02) |
| RN-DOC-02 | Regime de identificação do avaliador | DOC (LGPD, arts. 5º, III, 6º, VI, e 12) | N05 | — | — | Política de visibilidade | — | Validado (E01, E02) |
| RN-DOC-03 | Mínimo de respondentes em resultados anônimos | DOC (LGPD, arts. 5º, III, e 12) | N05 | — | — | Política de visibilidade; Análise e histórico | — | Validado (E01, E02) |
| RN-DOC-04 | Uso apenas para as finalidades informadas | DOC (LGPD, arts. 6º, I, e 9º) | N05 | — | — | — | — | Validado (E01, E02) |
| RN-DOC-05 | Questionários sem dados sensíveis | DOC (LGPD, arts. 5º, II, 6º e 11) | N05 | CU-05 | PARAM (`pergunta`) | Catálogo | — | Validado (E01, E02) |
| RN-DOC-06 | Decisões não unicamente automatizadas | DOC (LGPD, art. 20) | N05 | — | — | — | — | Validado (E01, E02) |

### 3.3. Requisitos não funcionais

Os RNF03 e RNF13 tratam das telas e serão verificados também nos protótipos (#22). No CU-03, a aplicação do RNF03 e a extensão transacional do RNF02 são propostas explícitas, ainda sujeitas a validação. As escolhas de encerramento antecipado e cancelamento dos rascunhos estão registradas nas questões em aberto do caso de uso.

| ID | Característica (ISO/IEC 25010:2023) | Fonte | Necessidade | Caso de uso | Especificação suplementar | Entidades | Arquitetura (C4) | Verificação | Situação |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| RNF01 | *Security* (*confidentiality*) | E01, DOC, SA | N05 | CU-01 a CU-05 | 3.1 | N/A | API da aplicação; Política de visibilidade; Autenticação e acesso | CA02, CA13; testes de autorização | Validado (E01, E02) |
| RNF02 | *Reliability* (*faultlessness*); *Security* (*integrity*) | E01, DOC | N02, N03 | CU-01, CU-02, CU-03, CU-05 | 3.3 | N/A | Coletas; Respostas; Banco de dados (transação) | CA06, CA08, CA13; teste de concorrência | Validado (E01, E02) |
| RNF03 | *Interaction capability* (*inclusivity*, *operability*); *Flexibility* (*adaptability*) | E01, DOC | N03 | CU-01 a CU-05 | 3.5 (a 3.6 remete a ele) | N/A | Aplicação web | CA13; uso por teclado e teste nas larguras-limite | Validado (E01, E02) |
| RNF04 | *Performance efficiency* | E01, DOC | N04 | CU-04, CU-05 | 3.4 | N/A | Análise e histórico; Banco de dados | CA13; ensaio de carga | Validado (E01, E02) |
| RNF05 | *Reliability* (*recoverability*) | E01, DOC | Transversal | N/A | 3.3 | N/A | Backup | CA13; simulação de restauração | Validado (E01, E02) |
| RNF06 | *Security* (*accountability*) | E01, DOC | N05 | CU-01, CU-03, CU-05 | 3.1 | EVENTO_AUDITORIA | Auditoria; Banco de dados | CA13; inspeção dos eventos | Validado (E01, E02) |
| RNF07 | *Security* (*confidentiality*) | E01, DOC, SA | N05 | CU-02, CU-03, CU-04 | 3.1 | N/A | Logs técnicos | CA13; inspeção de logs | Validado (E01, E02) |
| RNF08 | *Security* (*confidentiality*) | E01, DOC, SA | N05 | N/A | 3.1 | N/A | Conexões Aplicação web ↔ API (HTTPS) | Varredura da configuração TLS | Validado (E01, E02) |
| RNF09 | *Security* (*authenticity*) | DOC | N05 | CU-08 | 3.1 | USUARIO | Autenticação e acesso; Provedor de identidade (opcional) | Testes de senha fraca e de MFA | Validado (E01, E02) |
| RNF10 | *Security* (*confidentiality*) | DOC | N05 | N/A | 3.1 | USUARIO, FEEDBACK | Banco de dados; Autenticação e acesso | Inspeção do banco de homologação | Validado (E01, E02) |
| RNF11 | *Security* (*resistance*) | DOC | N05 | CU-08 | 3.1 | N/A | Autenticação e acesso | Teste de força bruta e análise de dependências | Validado (E01, E02) |
| RNF12 | *Functional suitability* (*correctness*) | DOC | N04 | CU-04 | 3.2 | N/A | Análise e histórico | CA10; casos de referência | Validado (E01, E02) |
| RNF13 | *Interaction capability* (*self-descriptiveness*, *user error protection*) | DOC | N03 | CU-02 | 3.5 | N/A | Aplicação web | Teste de usabilidade com roteiro | Validado (E01, E02) |
| RNF14 | *Maintainability* (*testability*) | DOC | N05 | CU-04 | 3.7 | N/A | Política de visibilidade | Relatório de testes | Validado (E01, E02) |
| RNF15 | *Compatibility* (*interoperability*) | DOC | N02 | N/A | 3.8 | N/A | Sistemas de RH (fora da 1ª versão) | Revisão do contrato de integração | Validado (E01, E02) |
| RNF16 | *Security* (*confidentiality*) | DOC, ENU | N05 | — | 3.1 | N/A | Política de visibilidade; Auditoria | Revisão das saídas com dados de teste | Validado (E01, E02) |

### 3.4. Processo de negócio (BPMN)

Liga as dores do [processo atual](../modelos/processo/processo-atual.bpmn) às necessidades e as etapas do [processo proposto](../modelos/processo/processo-proposto.bpmn) aos requisitos, casos de uso e componentes. As dores e etapas ainda dependem da validação com o stakeholder (#10, #25).

| Dor | Descrição resumida | Necessidade | Etapas do processo proposto que a tratam |
| --- | --- | --- | --- |
| D1 | Critérios não padronizados | N01 | Configurar coleta; Publicar questionário e gerar avaliações |
| D2 | Feedback só nos ciclos formais | N07, N08 | Registrar feedback informal com fato e impacto |
| D3 | Histórico perdido; resultados não comparáveis | N04 | Liberar resultados e calcular indicadores; Consultar resultados e histórico |
| D4 | Ações de melhoria sem registro nem acompanhamento | N06 | Criar plano de ação; Executar ações; Registrar verificações e novo feedback |
| D5 | Dados pessoais sem controle de acesso | N05 | Transversal: controle de acesso e auditoria em todas as etapas |
| D6 | Só o gestor avalia | N07 | Configurar coleta (360°); Responder e enviar avaliações, inclusive autoavaliação |

| Etapa do processo proposto | Raia | Caso de uso | Requisitos | Arquitetura (C4) | Dor |
| --- | --- | --- | --- | --- | --- |
| Configurar coleta: modalidade, questionário e participantes | RH ou gestor | CU-01, CU-09 | RF08, RF17; RN14 | Coletas | D1, D6 |
| Publicar questionário e gerar avaliações | Sistema | CU-01 | RF09, RF10, RF17; RN05 | Coletas | D1 |
| Responder e enviar avaliações, inclusive autoavaliação | Avaliadores | CU-02 | RF11, RF12, RF22 | Respostas | D6 |
| Acompanhar e encerrar a coleta | RH ou gestor | CU-03 | RF13 | Coletas | — |
| Liberar resultados e calcular indicadores | Sistema | CU-03, CU-04 | RF15; RN09, RN10, RN15 | Política de visibilidade; Análise e histórico | D3 |
| Consultar resultados e histórico | Colaborador avaliado | CU-04 | RF14, RF15 | Análise e histórico | D3 |
| Criar plano de ação com o colaborador | RH ou gestor | CU-11 | RF18; RN13 | Feedback e desenvolvimento | D4 |
| Executar ações e registrar progresso | Colaborador avaliado | CU-11 | RF18 | Feedback e desenvolvimento | D4 |
| Registrar verificações e novo feedback | RH ou gestor | CU-11 | RN13 | Feedback e desenvolvimento | D4 |
| Registrar feedback informal com fato e impacto | Qualquer participante | CU-10 | RF19, RF20, RF21; RN16 | Feedback e desenvolvimento | D2 |
| Todas as etapas (transversal) | — | CU-08 | RF01, RF16; RN14; RNF01, RNF07 | Autenticação e acesso; Política de visibilidade; Auditoria | D5 |

### 3.5. Arquitetura (C4)

Sentido inverso das colunas "Arquitetura (C4)" das seções 3.1 a 3.3: de cada elemento da [visão arquitetural](../modelos/arquitetura/README.md) para o que ele atende.

| Elemento | Nível C4 | Casos de uso | Requisitos | Entidades | Situação |
| --- | --- | --- | --- | --- | --- |
| RH, Gestor, Profissional | 1 — Pessoas | Todos | Visão, seção 3.2 | USUARIO | Proposto |
| Serviço de e-mail | 1 — Externo | — | Nenhum (lacuna L08) | — | A confirmar |
| Provedor de identidade | 1 — Externo | CU-08 | RNF09 | — | Opcional |
| Sistemas de RH | 1 — Externo | — | RNF15; RF-DOC-11 | — | Fora da 1ª versão (D-01) |
| Aplicação web | 2 — Container | Todos | RNF03, RNF08, RNF13; RF-DOC-01, RF-DOC-02, RF-DOC-14 | — | Proposto |
| API da aplicação | 2 — Container | Todos | RF01 a RF22; RN01 a RN16; RNF01, RNF02 | — | Proposto |
| Banco de dados | 2 — Container | Todos | RN12; RNF02, RNF04, RNF06, RNF10 | Todas | Proposto |
| Logs técnicos | 2 — Container | — | RNF07 | — | Proposto |
| Backup | 2 — Infraestrutura | — | RNF05 | Todas (cópia) | Proposto |
| Autenticação e acesso | 3 — Componente | CU-08 | RF01; RNF01, RNF09, RNF10, RNF11 | USUARIO | Proposto |
| Organização | 3 — Componente | CU-06, CU-07 | RF02, RF03, RF04; RN03; RF-DOC-05 | USUARIO, TIME, RELACAO_TRABALHO | Proposto |
| Catálogo | 3 — Componente | CU-05 | RF05, RF06, RF07; RN04, RN06; RN-DOC-05 | GRUPO_PARAM, PARAM | Proposto |
| Coletas | 3 — Componente | CU-01, CU-03, CU-09 | RF08, RF09, RF10, RF13, RF17, RF22; RN01 a RN05, RN07, RN08, RN15; RNF02 | COLETA, COLETA_TIME, COLETA_PAR, COLETA_PARTICIPANTE, COLETA_GRUPO, COLETA_PARAM, AVALIACAO | Proposto |
| Respostas | 3 — Componente | CU-02 | RF11, RF12, RF19, RF22; RN02, RN06, RN08; RNF02; RF-DOC-14 | AVALIACAO, FEEDBACK | Proposto |
| Feedback e desenvolvimento | 3 — Componente | CU-10, CU-11 | RF18 a RF21; RN13, RN16 | REGISTRO_FEEDBACK, PLANO_ACAO, ACAO_PLANO, ACOMPANHAMENTO_ACAO | Proposto |
| Análise e histórico | 3 — Componente | CU-04 | RF14, RF15; RN10, RN11; RNF04, RNF12 | AVALIACAO, FEEDBACK, COLETA_PARAM (leitura) | Proposto |
| Política de visibilidade | 3 — Componente transversal | CU-02, CU-04, CU-10, CU-11 | RF01, RF14, RF15; RN09, RN14, RN15; RNF01, RNF14, RNF16 | — | Proposto |
| Auditoria | 3 — Componente transversal | Todos os que alteram dados | RF16; RNF06, RNF16 | EVENTO_AUDITORIA | Proposto |

### 3.6. Projeto (design)

Liga os artefatos do [modelo de projeto](../modelos/projeto/README.md) e os [padrões de projeto](../modelos/projeto/padroes-de-projeto.md) aos requisitos, casos de uso e componentes C4.

| Artefato | Tipo | Casos de uso | Requisitos | Componente (C4) | Padrões |
| --- | --- | --- | --- | --- | --- |
| Estados da coleta | Diagrama de estado | CU-01, CU-03 | RF09, RF13; RN07 | Coletas | PP10 |
| Estados da avaliação | Diagrama de estado | CU-02, CU-03 | RF11, RF12; RN08 | Respostas | PP01 |
| Estados do plano e da ação | Diagrama de estado | CU-11 | RF18; RN13 | Feedback e desenvolvimento | — |
| CO01 `abrir` | Contrato de operação | CU-01, CU-09 | RF09, RF10, RF17, RF22; RN03, RN05, RN14, RN15; RNF02 | Coletas | PP02, PP12, PP17 |
| CO02 `enviar` | Contrato de operação | CU-02 | RF12; RN06, RN08; RNF02 | Respostas | PP01, PP11, PP18 |
| CO03 `encerrar` | Contrato de operação | CU-03 | RF13; RN07, RN08, RN09, RN12; RNF02 | Coletas | PP10, PP17, PP18 |
| CO04 `criarPlano` | Contrato de operação | CU-11 | RF18; RN13, RN14; CA18 | Feedback e desenvolvimento | PP02, PP17 |
| Abrir coleta | Diagrama de sequência | CU-01 | RF09, RF10, RF16, RF17; RN05, RN14; RNF02 | Coletas; Política de visibilidade; Auditoria | PP03, PP12, PP13, PP17 |
| Enviar avaliação | Diagrama de sequência | CU-02 | RF12, RF16; RN06, RN08; RNF02, RNF13 | Respostas; Auditoria | PP01, PP11, PP18 |
| Encerrar coleta | Diagrama de sequência | CU-03 | RF13, RF16; RN07, RN08, RN09, RN12; RNF02 | Coletas; Auditoria | PP10, PP17, PP18 |
| Consultar resultados | Diagrama de sequência | CU-04 | RF14, RF15; RN09, RN10, RN11, RN14; RNF01, RNF12 | Análise e histórico; Política de visibilidade | PP07, PP11, PP19 |
| Criar plano de ação | Diagrama de sequência | CU-11 | RF16, RF18; RN13, RN14 | Feedback e desenvolvimento; Auditoria | PP02, PP17 |
| Classes de domínio | Diagrama de classes | CU-01 a CU-04, CU-09 a CU-11 | RF08 a RF22; RN01 a RN16 | Coletas; Respostas; Feedback e desenvolvimento | PP01, PP02, PP06, PP10 a PP12, PP14, PP21 |
| Classes de aplicação | Diagrama de classes | CU-01 a CU-04, CU-10, CU-11 | RF01, RF14 a RF16; RN09, RN12, RN14; RNF01, RNF02, RNF06 | Todos os componentes | PP03, PP04, PP07, PP08, PP15 a PP20 |
| Padrões GRASP | PP01 a PP09 | Todos | Ver a coluna "Motivo" de cada padrão | Todos | — |
| Padrões GoF | PP10 a PP14 | CU-01 a CU-04, CU-09 | RN02, RN03, RN06, RN07, RN10, RN15; RF10, RF16, RF17, RF22 | Coletas; Respostas; Análise; Auditoria | — |
| Padrões arquiteturais | PP15 a PP22 | Todos | RN05, RN09, RN12, RN14; RF07, RF09; RNF01, RNF02, RNF07, RNF14, RNF16 | Todos | — |

## 4. Matriz horizontal

### 4.1. Requisitos funcionais × regras de negócio

Um "X" indica que a regra restringe o requisito. A grade foi derivada do texto dos RF e das RN na [especificação de requisitos](../requisitos/especificacao-requisitos.md) (seções 3.2 e 3.3).

| RF \ RN | RN01 | RN02 | RN03 | RN04 | RN05 | RN06 | RN07 | RN08 | RN09 | RN10 | RN11 | RN12 |
| --- | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| RF01 | | | | | | | | | | | | |
| RF02 | | | X | | | | | | | | | X |
| RF03 | | | X | | X | | | | | | | X |
| RF04 | | | X | | | | | | | | | X |
| RF05 | | | | X | X | X | | | | | X | X |
| RF06 | | | | | X | | | | | | | X |
| RF07 | | | | X | X | | | | | | X | |
| RF08 | | | X | X | | | X | | | | | X |
| RF09 | X | | X | X | X | | X | | | | | |
| RF10 | X | X | X | | | | | | | | | |
| RF11 | | X | | | | X | X | X | | | | X |
| RF12 | | | | | | X | X | X | | | | |
| RF13 | X | | | | | | X | X | | | | X |
| RF14 | | | | | X | | | | X | | | X |
| RF15 | | | | | | | | | X | X | X | |
| RF16 | | | | | X | | | | | | | X |
| RF17 | | X | | | X | | X | X | | | | X |
| RF18 | | | | | | | | | | | | X |
| RF19 | | | | | | | | | | | | |
| RF20 | | | | | | | | | | | | X |
| RF21 | | | | | | | | | | | | X |
| RF22 | | X | | | X | | X | X | | | | X |

As regras RN13 a RN16, criadas na consolidação da #40, estão na seção 4.2. O RF01 não é restringido por regras de negócio. Seus vínculos horizontais são com o RNF01, o RNF09 e o RNF11 (seção 4.2).

### 4.2. Outras relações entre requisitos

| Origem | Relação | Destino | Registro |
| --- | --- | --- | --- |
| RF02 a RF16 | Dependem de | RF01 | Especificação, RF01 ("em cada operação") |
| RF03 | Depende de | RF02 | Especificação, RF03 (o gestor é um usuário com perfil `GESTOR`) |
| RF04 | Depende de | RF02 | Especificação, RF04 |
| RF05 | Depende de | RF06 | Especificação, RF05 (o parâmetro informa o grupo); CU-05, extensão 2a |
| RF07 | Depende de | RF05, RF06 | Especificação, RF07 |
| RF08 | Depende de | RF03, RF04, RF05, RF06 | Especificação, RF08 (modos TIMES e PARES, grupos e parâmetros) |
| RF09 | Depende de | RF08 | Especificação, RF09 |
| RF10 | Ocorre na mesma transação que | RF09 | Especificação, RF09 ("publicação e geração de todas as avaliações devem ser atômicas") |
| RF11 | Depende de | RF10 | Especificação, RF11 ("avaliação atribuída") |
| RF12 | Depende de | RF11 | Especificação, RF12 |
| RF13 (encerramento ou cancelamento de coleta aberta) | Depende de | RF09 | Especificação, RF13; CU-03. Cancelar uma coleta em preparação não exige publicação prévia. |
| RF14, RF15 | Dependem de | RF12, RF13 | Especificação, RN09 (liberação ao avaliado pelo gestor ou pelo RH) |
| RF16 | Registra eventos de | RF02 a RF13 | Especificação, RF16 |
| RF01 | Complementado por | RNF01, RNF09, RNF11 | Especificação suplementar, 3.1 |
| RF09, RF10, RF12 | Complementados por | RNF02 | Especificação suplementar, 3.3 |
| RF13 | Complementado por | RNF02 | Extensão do CU-03: finalização atômica e coordenada com envios concorrentes; validada (E01, E02) |
| RF11, RF12 | Complementados por | RNF13 | Especificação suplementar, 3.5; CU-02 |
| RF16 | Complementado por | RNF06 | Especificação suplementar, 3.1 |
| RN09 | Complementada por | RNF14 | Especificação suplementar, 3.7 |
| RN10 | Complementada por | RNF12 | Especificação suplementar, 3.2 |
| RN-DOC-05 | Complementada por | RF-DOC-14 | Identificada nesta matriz: a regra trata das perguntas, e o requisito, dos comentários |
| RF-DOC-05 | Atendido por | RF02 | Lista geral, seção 6 |
| RNF01 | Consolida | RNF-DOC-01 | Lista geral, seção 5; especificação suplementar |
| RNF02 | Consolida | RNF-DOC-07 | Idem |
| RNF03 | Consolida | RNF-DOC-13, RNF-DOC-14 | Idem |
| RNF04 | Consolida | RNF-DOC-15 | Idem |
| RNF05 | Consolida | RNF-DOC-09 | Idem |
| RNF06 | Consolida | RNF-DOC-06 | Idem |
| RNF08 | Consolida | RNF-DOC-04, RI03 | Idem |
| RNF09 | Consolida | RNF-DOC-03 | Idem |
| RNF10 | Consolida | RNF-DOC-05 | Idem |
| RNF11 | Consolida | RNF-DOC-08 | Idem |
| RNF12 | Consolida | RNF-DOC-10 | Idem |
| RNF13 | Consolida | RNF-DOC-11, RNF-DOC-12 | Idem |
| RNF14 | Consolida | RNF-DOC-16 | Idem |
| RNF15 | Consolida | RNF-DOC-17 | Idem |
| RNF16 | Consolida | RNF-DOC-02 | Idem |
| RN12 | Restringe | RF-DOC-07, RF-DOC-08 | Lista geral, seção 7 (C01 resolvido: anonimização ao fim da retenção) |
| RN09 | Complementada por | RN-DOC-02, RN-DOC-03, RNF16 | Lista geral, seção 7 (C02 resolvido: identificação por modalidade) |
| RF10 | Delimitado por | RF22 | Lacuna L07 resolvida na #40: a coleta recíproca rejeita a autoavaliação, que passou a ser modalidade própria (RN15) |
| RF17, RF22 | Restringidos por | RN15 | Especificação, RN15 |
| RF08, RF13, RF17, RF18 | Restringidos por | RN14 | Especificação, RN14 |
| RF18 | Restringido por | RN13 | Especificação, RN13 |
| RF18 | Depende de | RF21 | Especificação, RF18 (o plano nasce de um feedback registrado) |
| RF20, RF21 | Restringidos por | RN16 | Especificação, RN16 |
| RF19 | Complementa | RF20, RF21 | Especificação, RF19 |
| CU-02 | Depende de | CU-01 | Índice de casos de uso |
| CU-04 | Depende de | CU-03 | Índice de casos de uso |
| CU-02 | Depende de | CU-09 | Índice de casos de uso (respostas do 360°) |
| CU-11 | Depende de | CU-02, CU-10 | Índice de casos de uso |

### 4.3. Decisões arquiteturais × requisitos

As decisões AD01 a AD05 estão na [visão arquitetural](../modelos/arquitetura/README.md), seção 6. Todas são propostas.

| Decisão | Resumo | Motivada por | Afeta |
| --- | --- | --- | --- |
| AD01 | Um único servidor de aplicação dividido em componentes | RNF02, RNF04; RN01 | API da aplicação; todos os componentes |
| AD02 | Decisões de acesso só na API, no componente Política de visibilidade | RNF01, RNF14; RN09, RN14, RN15 | Política de visibilidade; Aplicação web |
| AD03 | Auditoria no mesmo banco e na mesma transação da operação | RF16; RNF06 | Auditoria; Banco de dados |
| AD04 | Logs técnicos separados e sem conteúdo de respostas | RNF07 | Logs técnicos |
| AD05 | Diagramas sem tecnologia definida | Especificação suplementar, seção 5 | Todos os containers |

## 5. Cobertura

| Tipo | Total | Com caso de uso descrito | Só com caso de uso a elaborar | Sem caso de uso ou N/A | Com entidade | Com arquitetura (C4) | Com verificação | Com protótipo |
| --- | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| RF01 a RF22 | 22 | 22 | 0 | 0 | 22 | 22 | 22 | A conferir |
| RF-DOC | 14 | 2 | 0 | 12 | 2 | 4 | 1 | 0 |
| RN01 a RN16 | 16 | 16 | 0 | 0 | 16 | 16 | 16 | N/A |
| RN-DOC | 6 | 1 | 0 | 5 | 1 | 3 | 0 | N/A |
| RNF01 a RNF16 | 16 | 11 | 0 | 5 | 3 | 16 | 16 | 0 |

"Caso de uso descrito" inclui os casos completos (CU-01 a CU-05) e os resumidos no índice (CU-06 a CU-11). No RNF, "com verificação" considera os métodos da especificação suplementar. Em RN-DOC, dois dos três vínculos com a arquitetura (RN-DOC-02 e RN-DOC-03) seguem a decisão do conflito C02 (identificação por modalidade).

Processo de negócio: as 6 dores (D1 a D6) estão ligadas a necessidades, e as 10 etapas do processo proposto a casos de uso, requisitos e componentes (seção 3.4). Arquitetura: os 9 componentes e os 5 containers estão ligados a requisitos (seção 3.5); o serviço de e-mail é o único elemento sem requisito (L08). Projeto: os 4 contratos, 5 diagramas de sequência, 3 diagramas de estado, 2 diagramas de classes e 22 padrões estão ligados a requisitos e componentes (seção 3.6); CU-05 a CU-08 não têm diagrama de sequência próprio (L10).

## 6. Lacunas e inconsistências

### 6.1. Lacunas

| ID | Lacuna | Justificativa ou encaminhamento |
| --- | --- | --- |
| L01 | Resolvida: as duas entrevistas foram orais e não foram gravadas, por isso não há transcrição. A E01 está registrada como resumo anotado das respostas, e a E02, com a professora, sem anotação das respostas ([README das entrevistas](../levantamento/entrevistas/README.md)). Os requisitos com origem nas entrevistas citam a E01 e a [síntese](../levantamento/sintese-entrevistas.md). | Registros adotados (#41). As duas entrevistas confirmaram os requisitos (lista geral v0.3). |
| L02 | Parcialmente resolvida: a síntese das entrevistas e o sistema análogo foram incorporados à lista geral na #40 (seção 9). Nenhum requisito tem origem em Q01 ou Q02. | Questionários ainda pendentes (#7, #8); os requisitos que vierem deles devem seguir a regra de identificadores da lista geral. |
| L03 | O protótipo foi produzido no Figma (#22), mas as telas ainda não foram relacionadas aos requisitos. | Identificar a tela de cada requisito e substituir "A conferir" pelo nome da tela. |
| L04 | Resolvida: RF08 a RF10, RF14, RF15, RN03 e RN10 têm casos de uso completos. | CU-01 descrito na issue #14 e CU-04 na issue #16; CU-03 já havia sido descrito na issue #17. |
| L05 | Resolvida na #40: RF17 a RF22 têm caso de uso resumido (CU-09 a CU-11), entidades, critérios CA14 a CA18 e necessidades N06 a N08. | Descrever CU-09 a CU-11 de forma completa, se a disciplina exigir. |
| L06 | 12 dos 14 RF-DOC e 5 dos 6 RN-DOC não têm caso de uso, e quase todos não têm critério de aceitação. | Os critérios CA01 a CA13 cobrem os requisitos de E01. Vários itens DOC dependem das dúvidas D-01 a D-13 da pesquisa documental. |
| L07 | Resolvida na #40: a autoavaliação passou a ser modalidade própria (RF22, RN15), e o RF10 a rejeita apenas na coleta recíproca. Registro original: o RF10 rejeita a autoavaliação, e o RF17 (360°) a inclui. A síntese das entrevistas (SIN-RF04 e SIN-RN04) põe o 360° e a autoavaliação na primeira versão, mas a lista geral e a especificação (seção 2.6: "Não há autoavaliação no núcleo") ainda a excluem. | A síntese foi seguida: a coleta recíproca mantém a restrição, e a autoavaliação segue a RN15. |
| L08 | O serviço de e-mail aparece na visão arquitetural (convites, lembretes e recuperação de senha), mas nenhum requisito o exige (lacuna A01 da arquitetura). | Perguntar ao stakeholder na validação (#25). Se confirmado, criar o RF e ligá-lo aqui; se não, retirar o elemento dos diagramas C4. |
| L09 | 10 dos 14 RF-DOC e 3 dos 6 RN-DOC não têm componente de arquitetura. | Os requisitos foram validados e os conflitos C01 e C02, resolvidos; falta atribuir o componente responsável a cada item. |
| L10 | O modelo de projeto detalha só os fluxos principais de CU-01 a CU-04 e CU-11. CU-05 a CU-10 e os fluxos alternativos não têm diagrama de sequência. | CU-05 a CU-08 são cadastros que seguem o mesmo formato de controlador e repositório. Modelar os demais se a disciplina exigir. |
| L11 | A auditoria de normas ISO encontrou cinco achados maiores. Três foram tratados na validação (E01, E02): metas de RNF (AC03), validação dos requisitos (AC04) e retenção (AC14, conflito C01). Seguem abertos a disponibilidade sem requisito (AC06) e a avaliação de impacto à privacidade (AC19). | Seguir a ordem da seção 12.1 da [auditoria](../auditoria/auditoria-conformidade-iso.md). Ao criar um requisito por causa de um achado, citar o AC de origem na coluna "Fonte". |

### 6.2. Inconsistências entre artefatos

Todas as inconsistências abaixo foram corrigidas em 17/11/2026. As linhas ficam como registro do que mudou.

| ID | Inconsistência | Onde | Correção |
| --- | --- | --- | --- |
| I01 | Três esquemas de código para as fontes: a especificação usava F01, F02 e F04 para E01, ENU e DOC, e o F01 coincidia com o código da LGPD na pesquisa documental. | Lista geral, especificação de requisitos e pesquisa documental | A especificação passou a usar os códigos da lista geral. Os F01 a F14 da pesquisa documental continuam identificando documentos dentro da fonte DOC (seção 1.2). |
| I02 | O RNF03 aparecia duas vezes, com conteúdos diferentes. | Especificação suplementar, 3.5 e 3.6 | O RNF03 aparece uma vez, na seção 3.5, com teclado, rótulos e larguras de 360 a 1.440 px, como na lista geral e na especificação. A seção 3.6 remete a ele. |
| I03 | O CA13 e a seção 1.5 da especificação citavam só o RNF01 a RNF07. | Especificação de requisitos, 1.5, 3.6 e 5 | Os dois trechos e a cadeia "Segurança e preservação" da seção 5 passaram a abranger os RNF01 a RNF16, com os métodos de verificação da especificação suplementar. |
| I04 | O RF07 e o RF16 eram Importantes na lista geral e essenciais na especificação. | Lista geral, seção 3; especificação, RF07 e RF16 | A especificação passou a seguir a lista geral, onde a priorização foi feita (#11). |
| I05 | EVENTO_AUDITORIA estava no texto do MER e no dicionário, mas não nos diagramas. | `mer-organizacao-catalogo.mmd` e MER, seção "Estrutura organizacional e catálogo" | A entidade entrou no diagrama de organização e catálogo, com os atributos do dicionário e a associação opcional com o usuário que executa a operação. |

## 7. Manutenção

- Ao criar ou alterar um requisito, caso de uso, entidade, tela ou critério de aceitação, atualizar a linha correspondente da seção 3 e as relações da seção 4.
- Ao alterar o BPMN, a visão arquitetural C4 ou o modelo de projeto, atualizar as seções 3.4, 3.5, 3.6 e 4.3 e a coluna "Arquitetura (C4)" das seções 3.1 a 3.3.
- Identificadores removidos não são reutilizados (lista geral, seção 2).
- Quando um caso de uso "a elaborar" for descrito, retirar a marcação e conferir os requisitos listados no arquivo do caso de uso.
