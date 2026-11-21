# Matriz de rastreabilidade

| Campo | Informação |
| --- | --- |
| Autoria | Danilo Sucupira Galvão |
| Versão | 0.6 — 17 de novembro de 2026 |
| Base inicial | `main` em 10/11/2026 (commit `0bd8dc9`), com os artefatos dos PRs #27 a #37 |
| Atualização | CU-03 de Heitor Barbosa Souza em 15/11/2026; CU-01 de Brenner Rodrigues Sardinha e CU-04 de Enzo de Oliveira Machado em 17/11/2026; situação das entrevistas e correção das inconsistências I01 a I05 em 17/11/2026, sobre a `main` no commit `f7250bc`; consolidação da síntese das entrevistas e do sistema análogo (#40) por Luiz Augusto Vaz em 17/11/2026, sobre a `main` no commit `a6aabfa` |
| Situação | Proposta para revisão |

Relaciona as fontes, as necessidades e os requisitos aos artefatos que os detalham, modelam e verificam (rastreabilidade vertical), e os requisitos entre si (rastreabilidade horizontal). Atende à issue #24 e à seção 3 do [processo de requisitos](../PROCESSO_REQUISITOS.md).

## 1. Convenção

### 1.1. Rastreabilidade vertical e horizontal

- **Vertical:** liga itens de níveis diferentes, na cadeia fonte → necessidade → requisito → caso de uso → entidade → tela → verificação. Cada linha das tabelas da seção 3 é lida nos dois sentidos: para trás, do requisito até a fonte que o originou; para frente, do requisito até os artefatos que o detalham e o verificam.
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
| Containers e componentes (C4) | [Visão arquitetural](../modelos/arquitetura/README.md), seções 4 e 5: cada componente da API lista os casos de uso, requisitos e entidades que atende |

## 2. Fontes e necessidades

### 2.1. Fontes

| Código | Fonte | Situação | Registro no repositório |
| --- | --- | --- | --- |
| E01 | Entrevista com o stakeholder e esclarecimentos posteriores | Realizada | Transcrição pendente (#41, lacuna L01); [síntese preliminar](../levantamento/sintese-entrevistas.md) |
| E02 | Segunda entrevista | Realizada | Transcrição pendente (#41, lacuna L01); síntese junto com a E01, incorporada à lista geral (seção 9.1) |
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
| N07 | Contemplar diferentes perspectivas | Alta | E01, E02, ENU |
| N08 | Documentar o desempenho com contexto | Alta | E01 |

## 3. Matriz vertical

### 3.1. Requisitos funcionais

| ID | Resumo | Fonte | Necessidade | Caso de uso | Entidades | Protótipo | Verificação | Situação |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| RF01 | Autenticar e autorizar em cada operação | E01, DOC | N05 | CU-08; pré-condição de CU-01 a CU-05 | USUARIO | A conferir | CA02 | Proposto |
| RF02 | Manter usuários | E01 | N02 | CU-06 | USUARIO, TIME | A conferir | CA01 | Proposto |
| RF03 | Manter times | E01 | N02 | CU-06 | TIME, USUARIO | A conferir | CA01 | Proposto |
| RF04 | Manter relações de trabalho | E01 | N02 | CU-07 | RELACAO_TRABALHO | A conferir | CA01, CA03 | Proposto |
| RF05 | Manter parâmetros | E01 | N01 | CU-05 | PARAM, GRUPO_PARAM | A conferir | CA01, CA05, CA11 | Validado |
| RF06 | Manter grupos de parâmetros | E01 | N01 | CU-05 | GRUPO_PARAM | A conferir | CA01, CA05 | Proposto |
| RF07 | Remanejar parâmetros entre grupos | E01 | N01 | CU-05 | PARAM, GRUPO_PARAM, COLETA_GRUPO, COLETA_PARAM | A conferir | CA04, CA11 | Proposto |
| RF08 | Configurar coletas | E01 | N02 | CU-01, CU-09 | COLETA, COLETA_PAR, COLETA_TIME, COLETA_PARTICIPANTE, COLETA_GRUPO, COLETA_PARAM | A conferir | CA01, CA05 | Proposto |
| RF09 | Publicar o questionário da coleta | E01 | N02 | CU-01 | COLETA, COLETA_GRUPO, COLETA_PARAM, AVALIACAO | A conferir | CA05, CA06, CA06C | Proposto |
| RF10 | Atribuir avaliações mútuas por pares ou times | E01 | N02 | CU-01 | AVALIACAO, COLETA_PAR, COLETA_TIME, RELACAO_TRABALHO | A conferir | CA06, CA06A, CA06B | Proposto |
| RF11 | Manter respostas em rascunho | E01 | N03 | CU-02 | FEEDBACK, AVALIACAO | A conferir | CA01, CA07 | Proposto |
| RF12 | Enviar avaliação | E01 | N03 | CU-02 | AVALIACAO, FEEDBACK | A conferir | CA08 | Proposto |
| RF13 | Acompanhar, encerrar e cancelar coletas | E01 | N02 | CU-03 | COLETA, AVALIACAO | A conferir | CA12 | Proposto |
| RF14 | Consultar histórico individual | E01, ENU | N04 | CU-04 | AVALIACAO, FEEDBACK, COLETA_PARAM | A conferir | CA09, CA11 | Proposto |
| RF15 | Analisar resultados por usuário | E01, ENU | N04 | CU-04 | AVALIACAO, FEEDBACK, COLETA_PARAM | A conferir | CA10, CA11 | Proposto |
| RF16 | Registrar eventos de auditoria | E01, DOC, SA | N05 | CU-01, CU-02, CU-03, CU-05 | EVENTO_AUDITORIA | N/A | CA11, CA13 | Proposto |
| RF17 | Avaliação 360° | E01, E02, ENU, SA | N07 | CU-09 | COLETA, COLETA_PARTICIPANTE, AVALIACAO | A conferir | CA14 | Proposto |
| RF18 | Planos de ação com metas e acompanhamento | E01, ENU, SA | N06 | CU-11 | PLANO_ACAO, ACAO_PLANO, ACOMPANHAMENTO_ACAO, REGISTRO_FEEDBACK | A conferir | CA18 | Proposto |
| RF19 | Classificar feedbacks (formal ou informal, positivo ou construtivo) | E01, ENU | N07 | CU-02, CU-10 | REGISTRO_FEEDBACK | A conferir | CA17 | Proposto |
| RF20 | Registrar feedback informal, fora de uma coleta | E01, ENU | N07 | CU-10 | REGISTRO_FEEDBACK | A conferir | CA16 | Proposto |
| RF21 | Registrar o contexto do feedback | E01 | N08 | CU-02, CU-10 | REGISTRO_FEEDBACK | A conferir | CA16 | Proposto |
| RF22 | Autoavaliação | E01, E02 | N07 | CU-02, CU-09 | AVALIACAO, COLETA_PARTICIPANTE | A conferir | CA15 | Proposto |
| RF-DOC-01 | Aviso de privacidade | DOC (LGPD, arts. 6º, VI, e 9º) | N05 | — | — | A conferir | — | Proposto |
| RF-DOC-02 | Contato do encarregado em destaque | DOC (LGPD, art. 41, §1º; Res. CD/ANPD nº 18/2024) | N05 | — | — | A conferir | — | Proposto |
| RF-DOC-03 | Titular consulta os próprios dados | DOC (LGPD, arts. 18 e 19) | N05 | — | — | A conferir | — | Pendente (D-04) |
| RF-DOC-04 | Registrar requisições de titulares e alertar sobre o prazo | DOC (LGPD, arts. 18 e 19) | N05 | — | — | A conferir | — | Proposto |
| RF-DOC-05 | Corrigir dados cadastrais | DOC (LGPD, art. 18, III) | N05 | CU-06, via RF02 | USUARIO | A conferir | CA01, via RF02 | Proposto — atendido por RF02 |
| RF-DOC-06 | Titular contesta feedback recebido | DOC (LGPD, arts. 6º, V, e 18, III) | N05 | — | — | A conferir | — | Pendente (D-05) |
| RF-DOC-07 | Anonimizar, bloquear ou eliminar dados | DOC (LGPD, arts. 16 e 18) | N05 | — | — | A conferir | — | Pendente — conflito C01 |
| RF-DOC-08 | Configurar prazo de retenção | DOC (LGPD, arts. 15 e 16) | N05 | — | — | A conferir | — | Pendente — conflito C01 |
| RF-DOC-09 | Exportar dados do titular | DOC (LGPD, arts. 18, V, e 19) | N05 | — | — | A conferir | — | Pendente (D-02, D-13) |
| RF-DOC-10 | Registrar e revogar consentimento | DOC (LGPD, arts. 8º e 18, IX) | N05 | — | — | A conferir | — | Pendente (D-02) |
| RF-DOC-11 | Informar compartilhamentos com terceiros | DOC (LGPD, art. 18, VII) | N05 | — | — | A conferir | — | Pendente (D-01) |
| RF-DOC-12 | Relatório das operações de tratamento | DOC (LGPD, art. 37) | N05 | — | — | A conferir | — | Proposto |
| RF-DOC-13 | Listar titulares afetados em incidente | DOC (LGPD, art. 48; Res. CD/ANPD nº 15/2024) | N05 | — | — | A conferir | — | Proposto |
| RF-DOC-14 | Orientar o avaliador a não incluir dados sensíveis no comentário | DOC (LGPD, arts. 6º, III, 11 e 12) | N05 | CU-02 (requisitos especiais) | FEEDBACK (`comentario`) | A conferir | — | Proposto |

### 3.2. Regras de negócio

Regras de negócio não têm tela própria. Elas aparecem nas telas dos requisitos funcionais que restringem (grade da seção 4.1).

| ID | Resumo | Fonte | Necessidade | Caso de uso | Entidades | Verificação | Situação |
| --- | --- | --- | --- | --- | --- | --- | --- |
| RN01 | Reciprocidade | E01 | N02 | CU-01, CU-02, CU-03 | AVALIACAO | CA06, CA06C, CA12 | Proposto |
| RN02 | Unicidade de avaliação e de resposta | E01, E02 | N02 | CU-01, CU-02 | AVALIACAO, FEEDBACK | CA06, CA06A, CA06B, CA07 | Proposto |
| RN03 | Elegibilidade | E01 | N02 | CU-01 | USUARIO, TIME, RELACAO_TRABALHO, COLETA_PAR, COLETA_TIME | CA06A, CA06B | Proposto |
| RN04 | Composição do catálogo e da coleta | E01 | N01 | CU-01, CU-05 | PARAM, COLETA_PARAM | CA04, CA05 | Proposto |
| RN05 | Preservação do que foi publicado | E01 | N04 | CU-01, CU-04, CU-05 | COLETA, COLETA_TIME, COLETA_GRUPO, COLETA_PARAM, AVALIACAO | CA04, CA06C, CA11 | Proposto |
| RN06 | Tipo de avaliação (`score`) | E01 | N01 | CU-02, CU-05 | PARAM, COLETA_PARAM, FEEDBACK | CA07 | Validado |
| RN07 | Estados da coleta | E01 | N02 | CU-01, CU-02, CU-03 | COLETA | CA12 | Proposto |
| RN08 | Estados da avaliação e do feedback | E01 | N03 | CU-02, CU-03 | AVALIACAO, FEEDBACK | CA08, CA12 | Proposto |
| RN09 | Independência e liberação | E01 | N03 | CU-02, CU-03, CU-04 | AVALIACAO, FEEDBACK | CA09 | Pendente (PV03, PV04) |
| RN10 | Cálculo dos indicadores | E01, DOC | N04 | CU-04 | FEEDBACK, COLETA_PARAM (indicadores derivados do dicionário) | CA10 | Proposto |
| RN11 | Comparabilidade entre coletas | E01 | N04 | CU-04, CU-05 | COLETA_PARAM | CA11 | Proposto |
| RN12 | Sem exclusão física | E01 | N04 | CU-01, CU-03, CU-04, CU-05, CU-06 | Todas | CA01 | Validado — conflito C01 |
| RN13 | Ciclo de desenvolvimento | E01 | N06 | CU-11 | PLANO_ACAO, REGISTRO_FEEDBACK | CA18 | Proposto |
| RN14 | Escopo de atuação do gestor e do RH | E01 | N02, N06 | CU-01, CU-03, CU-09, CU-11 | TIME, COLETA, PLANO_ACAO | CA02, CA14 | Proposto |
| RN15 | Regras por modalidade | E01, E02 | N07 | CU-01, CU-02, CU-09, CU-10 | COLETA, COLETA_PARTICIPANTE, AVALIACAO, REGISTRO_FEEDBACK | CA14, CA15, CA16 | Proposto — liberação pendente (PV04) |
| RN16 | Feedback baseado em fatos | E01 | N08 | CU-10 | REGISTRO_FEEDBACK | CA16 | Proposto |
| RN-DOC-01 | Finalidade definida para cada dado | DOC (LGPD, art. 6º, I a III) | N05 | — | — | — | Proposto |
| RN-DOC-02 | Regime de identificação do avaliador | DOC (LGPD, arts. 5º, III, 6º, VI, e 12) | N05 | — | — | — | Pendente — conflito C02 |
| RN-DOC-03 | Mínimo de respondentes em resultados anônimos | DOC (LGPD, arts. 5º, III, e 12) | N05 | — | — | — | Pendente — conflito C02 |
| RN-DOC-04 | Uso apenas para as finalidades informadas | DOC (LGPD, arts. 6º, I, e 9º) | N05 | — | — | — | Proposto |
| RN-DOC-05 | Questionários sem dados sensíveis | DOC (LGPD, arts. 5º, II, 6º e 11) | N05 | CU-05 | PARAM (`pergunta`) | — | Proposto |
| RN-DOC-06 | Decisões não unicamente automatizadas | DOC (LGPD, art. 20) | N05 | — | — | — | Pendente (D-09) |

### 3.3. Requisitos não funcionais

Os RNF03 e RNF13 tratam das telas e serão verificados também nos protótipos (#22). No CU-03, a aplicação do RNF03 e a extensão transacional do RNF02 são propostas explícitas, ainda sujeitas a validação. As escolhas de encerramento antecipado e cancelamento dos rascunhos estão registradas nas questões em aberto do caso de uso.

| ID | Característica (ISO/IEC 25010:2023) | Fonte | Necessidade | Caso de uso | Especificação suplementar | Entidades | Verificação | Situação |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| RNF01 | *Security* (*confidentiality*) | E01, DOC, SA | N05 | CU-01 a CU-05 | 3.1 | N/A | CA02, CA13; testes de autorização | Proposto |
| RNF02 | *Reliability* (*faultlessness*); *Security* (*integrity*) | E01, DOC | N02, N03 | CU-01, CU-02, CU-03, CU-05 | 3.3 | N/A | CA06, CA08, CA13; teste de concorrência | Proposto |
| RNF03 | *Interaction capability* (*inclusivity*, *operability*); *Flexibility* (*adaptability*) | E01, DOC | N03 | CU-01 a CU-05 | 3.5 (a 3.6 remete a ele) | N/A | CA13; uso por teclado e teste nas larguras-limite | Proposto |
| RNF04 | *Performance efficiency* | E01, DOC | N04 | CU-04, CU-05 | 3.4 | N/A | CA13; ensaio de carga | Pendente (PV07) |
| RNF05 | *Reliability* (*recoverability*) | E01, DOC | Transversal | N/A | 3.3 | N/A | CA13; simulação de restauração | Pendente (PV07) |
| RNF06 | *Security* (*accountability*) | E01, DOC | N05 | CU-01, CU-03, CU-05 | 3.1 | EVENTO_AUDITORIA | CA13; inspeção dos eventos | Proposto |
| RNF07 | *Security* (*confidentiality*) | E01, DOC, SA | N05 | CU-02, CU-03, CU-04 | 3.1 | N/A | CA13; inspeção de logs | Pendente (PV05) |
| RNF08 | *Security* (*confidentiality*) | E01, DOC, SA | N05 | N/A | 3.1 | N/A | Varredura da configuração TLS | Proposto |
| RNF09 | *Security* (*authenticity*) | DOC | N05 | CU-08 | 3.1 | USUARIO | Testes de senha fraca e de MFA | Proposto |
| RNF10 | *Security* (*confidentiality*) | DOC | N05 | N/A | 3.1 | USUARIO, FEEDBACK | Inspeção do banco de homologação | Proposto |
| RNF11 | *Security* (*resistance*) | DOC | N05 | CU-08 | 3.1 | N/A | Teste de força bruta e análise de dependências | Pendente (D-12) |
| RNF12 | *Functional suitability* (*correctness*) | DOC | N04 | CU-04 | 3.2 | N/A | CA10; casos de referência | Proposto |
| RNF13 | *Interaction capability* (*self-descriptiveness*, *user error protection*) | DOC | N03 | CU-02 | 3.5 | N/A | Teste de usabilidade com roteiro | Proposto |
| RNF14 | *Maintainability* (*testability*) | DOC | N05 | CU-04 | 3.7 | N/A | Relatório de testes | Proposto |
| RNF15 | *Compatibility* (*interoperability*) | DOC | N02 | N/A | 3.8 | N/A | Revisão do contrato de integração | Pendente (D-01) |
| RNF16 | *Security* (*confidentiality*) | DOC, ENU | N05 | — | 3.1 | N/A | Revisão das saídas com dados de teste | Pendente — conflito C02 |

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
| RF14, RF15 | Dependem de | RF12, RF13 | Especificação, RN09 (liberação após o envio dos dois sentidos e o encerramento) |
| RF16 | Registra eventos de | RF02 a RF13 | Especificação, RF16 |
| RF01 | Complementado por | RNF01, RNF09, RNF11 | Especificação suplementar, 3.1 |
| RF09, RF10, RF12 | Complementados por | RNF02 | Especificação suplementar, 3.3 |
| RF13 | Complementado por | RNF02 | Extensão proposta no CU-03: finalização atômica e coordenada com envios concorrentes; pendente de validação |
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
| RN12 | Conflita com | RF-DOC-07, RF-DOC-08 | Lista geral, seção 7 (C01) |
| RN09 | Conflita com | RN-DOC-02, RN-DOC-03, RNF16 | Lista geral, seção 7 (C02) |
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

## 5. Cobertura

| Tipo | Total | Com caso de uso descrito | Só com caso de uso a elaborar | Sem caso de uso ou N/A | Com entidade | Com verificação | Com protótipo |
| --- | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| RF01 a RF22 | 22 | 22 | 0 | 0 | 22 | 22 | A conferir |
| RF-DOC | 14 | 2 | 0 | 12 | 2 | 1 | 0 |
| RN01 a RN16 | 16 | 16 | 0 | 0 | 16 | 16 | N/A |
| RN-DOC | 6 | 1 | 0 | 5 | 1 | 0 | N/A |
| RNF01 a RNF16 | 16 | 11 | 0 | 5 | 3 | 16 | 0 |

"Caso de uso descrito" inclui os casos completos (CU-01 a CU-05) e os resumidos no índice (CU-06 a CU-11). No RNF, "com verificação" considera os métodos da especificação suplementar.

## 6. Lacunas e inconsistências

### 6.1. Lacunas

| ID | Lacuna | Justificativa ou encaminhamento |
| --- | --- | --- |
| L01 | As duas entrevistas foram realizadas, mas as transcrições ainda não estão no repositório: `E01-transcricao.md` e `E02-transcricao.md` são registros temporários ([README das entrevistas](../levantamento/entrevistas/README.md)). Por isso, os requisitos com fonte E01 e a [síntese das entrevistas](../levantamento/sintese-entrevistas.md) não citam trechos das respostas (`E0X-Rxx`). | Receber e revisar as transcrições (#41) e conferir a síntese com elas (#6). |
| L02 | Parcialmente resolvida: a síntese das entrevistas (E01 e E02) e o sistema análogo foram incorporados à lista geral na #40 (seção 9). Nenhum requisito tem origem em Q01 ou Q02. | Questionários ainda pendentes (#7, #8); os requisitos que vierem deles devem seguir a regra de identificadores da lista geral. |
| L03 | O protótipo foi produzido no Figma (#22), mas as telas ainda não foram relacionadas aos requisitos. | Identificar a tela de cada requisito e substituir "A conferir" pelo nome da tela. |
| L04 | Resolvida: RF08 a RF10, RF14, RF15, RN03 e RN10 têm casos de uso completos. | CU-01 descrito na issue #14 e CU-04 na issue #16; CU-03 já havia sido descrito na issue #17. |
| L05 | Resolvida na #40: RF17 a RF22 têm caso de uso resumido (CU-09 a CU-11), entidades, critérios CA14 a CA18 e necessidades N06 a N08. | Descrever CU-09 a CU-11 de forma completa, se a disciplina exigir. |
| L06 | 12 dos 14 RF-DOC e 5 dos 6 RN-DOC não têm caso de uso, e quase todos não têm critério de aceitação. | Os critérios CA01 a CA13 cobrem os requisitos de E01. Vários itens DOC dependem das dúvidas D-01 a D-13 da pesquisa documental. |
| L07 | Resolvida na #40: a autoavaliação passou a ser modalidade própria (RF22, RN15), e o RF10 a rejeita apenas na coleta recíproca. Registro original: o RF10 rejeita a autoavaliação, e o RF17 (360°) a inclui. A síntese das entrevistas (SIN-RF04 e SIN-RN04) põe o 360° e a autoavaliação na primeira versão, mas a lista geral e a especificação (seção 2.6: "Não há autoavaliação no núcleo") ainda a excluem. | A síntese foi seguida: a coleta recíproca mantém a restrição, e a autoavaliação segue a RN15. |

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
- Identificadores removidos não são reutilizados (lista geral, seção 2).
- Quando um caso de uso "a elaborar" for descrito, retirar a marcação e conferir os requisitos listados no arquivo do caso de uso.
