# Matriz de rastreabilidade

| Campo | Informação |
| --- | --- |
| Autoria | Danilo Sucupira Galvão |
| Versão | 0.1 — 10 de novembro de 2026 |
| Base | `main` em 10/11/2026 (commit `0bd8dc9`), com os artefatos dos PRs #27 a #37 |
| Situação | Proposta para revisão |

Relaciona as fontes, as necessidades e os requisitos aos artefatos que os detalham, modelam e verificam (rastreabilidade vertical), e os requisitos entre si (rastreabilidade horizontal). Atende à issue #24 e à seção 3 do [processo de requisitos](../PROCESSO_REQUISITOS.md).

## 1. Convenção

### 1.1. Rastreabilidade vertical e horizontal

- **Vertical:** liga itens de níveis diferentes, na cadeia fonte → necessidade → requisito → caso de uso → entidade → tela → verificação. Cada linha das tabelas da seção 3 é lida nos dois sentidos: para trás, do requisito até a fonte que o originou; para frente, do requisito até os artefatos que o detalham e o verificam.
- **Horizontal:** liga itens do mesmo nível, ou seja, um requisito com outro: dependência, restrição por regra de negócio, complemento por requisito não funcional, consolidação, atendimento e conflito (seção 4).

### 1.2. Códigos de fonte

São os mesmos da [lista geral](../requisitos/lista-geral.md) (seção 1). Outros documentos usam códigos diferentes para as mesmas fontes:

| Lista geral e esta matriz | Especificação de requisitos (seção 1.4) | Pesquisa documental (seção 2) |
| --- | --- | --- |
| E01 | F01 | — |
| ENU | F02 | — |
| DOC | F04 | F01 a F14 identificam cada documento consultado (F01 é a LGPD) |

Nas linhas de origem DOC, esta matriz cita o documento pelo nome (LGPD, resoluções da ANPD), e não pelo código da pesquisa documental, para evitar confusão com o F01 da especificação.

### 1.3. Legenda

| Valor | Significado |
| --- | --- |
| `CU-01 (a elaborar)` | O caso de uso está no [índice](../casos-de-uso/README.md), mas a descrição ainda não existe. |
| `Pendente (#22)` | O artefato está planejado e ainda não foi produzido. |
| `—` | Não há vínculo. A justificativa está na seção 6. |
| `N/A` | O vínculo não se aplica: requisito de infraestrutura ou de armazenamento, sem caso de uso nem tela própria, ou sem tela prevista na interface do usuário (RI01 da especificação). |
| `Transversal` | O requisito apoia todas as necessidades N01 a N05. |

### 1.4. Onde cada item está detalhado

| Item | Documento |
| --- | --- |
| Fontes E01, E02, Q01, Q02, SA, DOC e ENU | [Lista geral](../requisitos/lista-geral.md), seção 1 |
| Necessidades N01 a N06 | [Documento de visão](../visao.md), seção 3.3 (os códigos foram atribuídos nesta matriz) |
| RF01 a RF16, RN01 a RN12, CA01 a CA13 | [Especificação de requisitos](../requisitos/especificacao-requisitos.md), seções 3.2, 3.3 e 3.6 |
| RF17 a RF20 | [Lista geral](../requisitos/lista-geral.md), seção 3 |
| RF-DOC, RN-DOC e RNF-DOC | [Pesquisa documental](../levantamento/pesquisa-documental.md), seção 5 |
| RNF01 a RNF16 | [Especificação suplementar](../requisitos/especificacao-suplementar.md), seção 3 |
| Casos de uso | [Índice e diagrama](../casos-de-uso/README.md), [CU-02](../casos-de-uso/CU-02-responder-e-enviar-avaliacao.md) e [CU-05](../casos-de-uso/CU-05-manter-catalogo-de-parametros.md) |
| Entidades | [MER](../modelos/dominio/modelo-entidade-relacionamento.md) e [dicionário de dados](../dicionario-dados.md) |

## 2. Fontes e necessidades

### 2.1. Fontes

| Código | Fonte | Situação | Registro no repositório |
| --- | --- | --- | --- |
| E01 | Entrevista com o stakeholder e esclarecimentos posteriores | Realizada | Transcrição ausente (lacuna L01) |
| E02 | Segunda entrevista | Pendente | — (lacuna L02) |
| Q01, Q02 | Questionários de levantamento | Pendentes | — (lacuna L02) |
| SA | Análise de sistema análogo | Pendente | — (lacuna L02) |
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
| N06 | Desenvolver competências | Média | ENU |

## 3. Matriz vertical

### 3.1. Requisitos funcionais

| ID | Resumo | Fonte | Necessidade | Caso de uso | Entidades | Protótipo | Verificação | Situação |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| RF01 | Autenticar e autorizar em cada operação | E01, DOC | N05 | CU-08; pré-condição de CU-02 e CU-05 | USUARIO | Pendente (#22) | CA02 | Proposto |
| RF02 | Manter usuários | E01 | N02 | CU-06 | USUARIO, TIME | Pendente (#22) | CA01 | Proposto |
| RF03 | Manter times | E01 | N02 | CU-06 | TIME, USUARIO | Pendente (#22) | CA01 | Proposto |
| RF04 | Manter relações de trabalho | E01 | N02 | CU-07 | RELACAO_TRABALHO | Pendente (#22) | CA01, CA03 | Proposto |
| RF05 | Manter parâmetros | E01 | N01 | CU-05 | PARAM, GRUPO_PARAM | Pendente (#22) | CA01, CA05, CA11 | Validado |
| RF06 | Manter grupos de parâmetros | E01 | N01 | CU-05 | GRUPO_PARAM | Pendente (#22) | CA01, CA05 | Proposto |
| RF07 | Remanejar parâmetros entre grupos | E01 | N01 | CU-05 | PARAM, GRUPO_PARAM, COLETA_GRUPO, COLETA_PARAM | Pendente (#22) | CA04, CA11 | Proposto |
| RF08 | Configurar coletas | E01 | N02 | CU-01 (a elaborar) | COLETA, COLETA_PAR, COLETA_TIME, COLETA_GRUPO, COLETA_PARAM | Pendente (#22) | CA01, CA05 | Proposto |
| RF09 | Publicar o questionário da coleta | E01 | N02 | CU-01 (a elaborar) | COLETA, COLETA_GRUPO, COLETA_PARAM, AVALIACAO | Pendente (#22) | CA05, CA06, CA06C | Proposto |
| RF10 | Atribuir avaliações mútuas por pares ou times | E01 | N02 | CU-01 (a elaborar) | AVALIACAO, COLETA_PAR, COLETA_TIME, RELACAO_TRABALHO | Pendente (#22) | CA06, CA06A, CA06B | Proposto |
| RF11 | Manter respostas em rascunho | E01 | N03 | CU-02 | FEEDBACK, AVALIACAO | Pendente (#22) | CA01, CA07 | Proposto |
| RF12 | Enviar avaliação | E01 | N03 | CU-02 | AVALIACAO, FEEDBACK | Pendente (#22) | CA08 | Proposto |
| RF13 | Acompanhar, encerrar e cancelar coletas | E01 | N02 | CU-03 (a elaborar) | COLETA, AVALIACAO | Pendente (#22) | CA12 | Proposto |
| RF14 | Consultar histórico individual | E01, ENU | N04 | CU-04 (a elaborar) | AVALIACAO, FEEDBACK, COLETA_PARAM | Pendente (#22) | CA09, CA11 | Proposto |
| RF15 | Analisar resultados por usuário | E01, ENU | N04 | CU-04 (a elaborar) | AVALIACAO, FEEDBACK, COLETA_PARAM | Pendente (#22) | CA10, CA11 | Proposto |
| RF16 | Registrar eventos de auditoria | E01, DOC | N05 | CU-02, CU-05 | EVENTO_AUDITORIA | N/A | CA11, CA13 | Proposto |
| RF17 | Avaliação 360° | ENU | N02 | — | — | — | — | Pendente (PV08) |
| RF18 | Plano de desenvolvimento individual com metas | ENU | N06 | — | — | — | — | Pendente (PV08) |
| RF19 | Classificar feedbacks (formal ou informal, positivo ou construtivo) | ENU | — | — | — | — | — | Pendente (PV08) |
| RF20 | Feedback espontâneo, fora de uma coleta | ENU, roteiro (pergunta 9) | — | — | — | — | — | Pendente (PV08) |
| RF-DOC-01 | Aviso de privacidade | DOC (LGPD, arts. 6º, VI, e 9º) | N05 | — | — | Pendente (#22) | — | Proposto |
| RF-DOC-02 | Contato do encarregado em destaque | DOC (LGPD, art. 41, §1º; Res. CD/ANPD nº 18/2024) | N05 | — | — | Pendente (#22) | — | Proposto |
| RF-DOC-03 | Titular consulta os próprios dados | DOC (LGPD, arts. 18 e 19) | N05 | — | — | Pendente (#22) | — | Pendente (D-04) |
| RF-DOC-04 | Registrar requisições de titulares e alertar sobre o prazo | DOC (LGPD, arts. 18 e 19) | N05 | — | — | Pendente (#22) | — | Proposto |
| RF-DOC-05 | Corrigir dados cadastrais | DOC (LGPD, art. 18, III) | N05 | CU-06, via RF02 | USUARIO | Pendente (#22) | CA01, via RF02 | Proposto — atendido por RF02 |
| RF-DOC-06 | Titular contesta feedback recebido | DOC (LGPD, arts. 6º, V, e 18, III) | N05 | — | — | Pendente (#22) | — | Pendente (D-05) |
| RF-DOC-07 | Anonimizar, bloquear ou eliminar dados | DOC (LGPD, arts. 16 e 18) | N05 | — | — | Pendente (#22) | — | Pendente — conflito C01 |
| RF-DOC-08 | Configurar prazo de retenção | DOC (LGPD, arts. 15 e 16) | N05 | — | — | Pendente (#22) | — | Pendente — conflito C01 |
| RF-DOC-09 | Exportar dados do titular | DOC (LGPD, arts. 18, V, e 19) | N05 | — | — | Pendente (#22) | — | Pendente (D-02, D-13) |
| RF-DOC-10 | Registrar e revogar consentimento | DOC (LGPD, arts. 8º e 18, IX) | N05 | — | — | Pendente (#22) | — | Pendente (D-02) |
| RF-DOC-11 | Informar compartilhamentos com terceiros | DOC (LGPD, art. 18, VII) | N05 | — | — | Pendente (#22) | — | Pendente (D-01) |
| RF-DOC-12 | Relatório das operações de tratamento | DOC (LGPD, art. 37) | N05 | — | — | Pendente (#22) | — | Proposto |
| RF-DOC-13 | Listar titulares afetados em incidente | DOC (LGPD, art. 48; Res. CD/ANPD nº 15/2024) | N05 | — | — | Pendente (#22) | — | Proposto |
| RF-DOC-14 | Orientar o avaliador a não incluir dados sensíveis no comentário | DOC (LGPD, arts. 6º, III, 11 e 12) | N05 | CU-02 (requisitos especiais) | FEEDBACK (`comentario`) | Pendente (#22) | — | Proposto |

### 3.2. Regras de negócio

Regras de negócio não têm tela própria. Elas aparecem nas telas dos requisitos funcionais que restringem (grade da seção 4.1).

| ID | Resumo | Fonte | Necessidade | Caso de uso | Entidades | Verificação | Situação |
| --- | --- | --- | --- | --- | --- | --- | --- |
| RN01 | Reciprocidade | E01 | N02 | CU-02, CU-03 (a elaborar) | AVALIACAO | CA06, CA06C, CA12 | Proposto |
| RN02 | Unicidade de avaliação e de resposta | E01 | N02 | CU-02 | AVALIACAO, FEEDBACK | CA06, CA06A, CA06B, CA07 | Proposto |
| RN03 | Elegibilidade | E01 | N02 | CU-01 (a elaborar) | USUARIO, TIME, RELACAO_TRABALHO, COLETA_PAR, COLETA_TIME | CA06A, CA06B | Proposto |
| RN04 | Composição do catálogo e da coleta | E01 | N01 | CU-01 (a elaborar), CU-05 | PARAM, COLETA_PARAM | CA04, CA05 | Proposto |
| RN05 | Preservação do que foi publicado | E01 | N04 | CU-01 (a elaborar), CU-05 | COLETA, COLETA_TIME, COLETA_GRUPO, COLETA_PARAM, AVALIACAO | CA04, CA06C, CA11 | Proposto |
| RN06 | Tipo de avaliação (`score`) | E01 | N01 | CU-02, CU-05 | PARAM, COLETA_PARAM, FEEDBACK | CA07 | Validado |
| RN07 | Estados da coleta | E01 | N02 | CU-02, CU-03 (a elaborar) | COLETA | CA12 | Proposto |
| RN08 | Estados da avaliação e do feedback | E01 | N03 | CU-02 | AVALIACAO, FEEDBACK | CA08 | Proposto |
| RN09 | Independência e liberação | E01 | N03 | CU-02, CU-04 (a elaborar) | AVALIACAO, FEEDBACK | CA09 | Pendente (PV03, PV04) |
| RN10 | Cálculo dos indicadores | E01, DOC | N04 | CU-04 (a elaborar) | FEEDBACK, COLETA_PARAM (indicadores derivados do dicionário) | CA10 | Proposto |
| RN11 | Comparabilidade entre coletas | E01 | N04 | CU-04 (a elaborar), CU-05 | COLETA_PARAM | CA11 | Proposto |
| RN12 | Sem exclusão física | E01 | N04 | CU-05, CU-06 | Todas | CA01 | Validado — conflito C01 |
| RN-DOC-01 | Finalidade definida para cada dado | DOC (LGPD, art. 6º, I a III) | N05 | — | — | — | Proposto |
| RN-DOC-02 | Regime de identificação do avaliador | DOC (LGPD, arts. 5º, III, 6º, VI, e 12) | N05 | — | — | — | Pendente — conflito C02 |
| RN-DOC-03 | Mínimo de respondentes em resultados anônimos | DOC (LGPD, arts. 5º, III, e 12) | N05 | — | — | — | Pendente — conflito C02 |
| RN-DOC-04 | Uso apenas para as finalidades informadas | DOC (LGPD, arts. 6º, I, e 9º) | N05 | — | — | — | Proposto |
| RN-DOC-05 | Questionários sem dados sensíveis | DOC (LGPD, arts. 5º, II, 6º e 11) | N05 | CU-05 | PARAM (`pergunta`) | — | Proposto |
| RN-DOC-06 | Decisões não unicamente automatizadas | DOC (LGPD, art. 20) | N05 | — | — | — | Pendente (D-09) |

### 3.3. Requisitos não funcionais

Os RNF03 e RNF13 tratam das telas e serão verificados também nos protótipos (#22).

| ID | Característica (ISO/IEC 25010:2023) | Fonte | Necessidade | Caso de uso | Especificação suplementar | Entidades | Verificação | Situação |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| RNF01 | *Security* (*confidentiality*) | E01, DOC | N05 | CU-02, CU-05 | 3.1 | N/A | CA02, CA13; testes de autorização | Proposto |
| RNF02 | *Reliability* (*faultlessness*); *Security* (*integrity*) | E01, DOC | N02, N03 | CU-02, CU-05 | 3.3 | N/A | CA06, CA08, CA13; teste de concorrência | Proposto |
| RNF03 | *Interaction capability* (*inclusivity*, *operability*); *Flexibility* (*adaptability*) | E01, DOC | N03 | CU-02, CU-05 | 3.5 e 3.6 (ID duplicado, ver I02) | N/A | CA13; uso por teclado e teste nas larguras-limite | Proposto |
| RNF04 | *Performance efficiency* | E01, DOC | N04 | CU-05 | 3.4 | N/A | CA13; ensaio de carga | Pendente (PV07) |
| RNF05 | *Reliability* (*recoverability*) | E01, DOC | Transversal | N/A | 3.3 | N/A | CA13; simulação de restauração | Pendente (PV07) |
| RNF06 | *Security* (*accountability*) | E01, DOC | N05 | CU-05 | 3.1 | EVENTO_AUDITORIA | CA13; inspeção dos eventos | Proposto |
| RNF07 | *Security* (*confidentiality*) | E01, DOC | N05 | CU-02 | 3.1 | N/A | CA13; inspeção de logs | Pendente (PV05) |
| RNF08 | *Security* (*confidentiality*) | E01, DOC | N05 | N/A | 3.1 | N/A | Varredura da configuração TLS | Proposto |
| RNF09 | *Security* (*authenticity*) | DOC | N05 | CU-08 | 3.1 | USUARIO | Testes de senha fraca e de MFA | Proposto |
| RNF10 | *Security* (*confidentiality*) | DOC | N05 | N/A | 3.1 | USUARIO, FEEDBACK | Inspeção do banco de homologação | Proposto |
| RNF11 | *Security* (*resistance*) | DOC | N05 | CU-08 | 3.1 | N/A | Teste de força bruta e análise de dependências | Pendente (D-12) |
| RNF12 | *Functional suitability* (*correctness*) | DOC | N04 | CU-04 (a elaborar) | 3.2 | N/A | CA10; casos de referência | Proposto |
| RNF13 | *Interaction capability* (*self-descriptiveness*, *user error protection*) | DOC | N03 | CU-02 | 3.5 | N/A | Teste de usabilidade com roteiro | Proposto |
| RNF14 | *Maintainability* (*testability*) | DOC | N05 | N/A | 3.7 | N/A | Relatório de testes | Proposto |
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

O RF01 não é restringido por regras de negócio. Seus vínculos horizontais são com o RNF01, o RNF09 e o RNF11 (seção 4.2).

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
| RF13 | Depende de | RF09 | Especificação, RF13 ("encerrar coleta aberta") |
| RF14, RF15 | Dependem de | RF12, RF13 | Especificação, RN09 (liberação após o envio dos dois sentidos e o encerramento) |
| RF16 | Registra eventos de | RF02 a RF13 | Especificação, RF16 |
| RF01 | Complementado por | RNF01, RNF09, RNF11 | Especificação suplementar, 3.1 |
| RF09, RF10, RF12 | Complementados por | RNF02 | Especificação suplementar, 3.3 |
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
| RF10 | Conflita com | RF17 | Identificada nesta matriz (lacuna L07): o RF10 rejeita a autoavaliação, e o RF17 a inclui |
| CU-02 | Depende de | CU-01 | Índice de casos de uso |
| CU-04 | Depende de | CU-03 | Índice de casos de uso |

## 5. Cobertura

| Tipo | Total | Com caso de uso descrito | Só com caso de uso a elaborar | Sem caso de uso ou N/A | Com entidade | Com verificação | Com protótipo |
| --- | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| RF01 a RF20 | 20 | 10 | 6 | 4 | 16 | 16 | 0 |
| RF-DOC | 14 | 2 | 0 | 12 | 2 | 1 | 0 |
| RN01 a RN12 | 12 | 10 | 2 | 0 | 12 | 12 | N/A |
| RN-DOC | 6 | 1 | 0 | 5 | 1 | 0 | N/A |
| RNF01 a RNF16 | 16 | 9 | 1 | 6 | 3 | 16 | 0 |

"Caso de uso descrito" inclui os casos completos (CU-02 e CU-05) e os resumidos no índice (CU-06, CU-07 e CU-08). No RNF, "com verificação" considera os métodos da especificação suplementar.

## 6. Lacunas e inconsistências

### 6.1. Lacunas

| ID | Lacuna | Justificativa ou encaminhamento |
| --- | --- | --- |
| L01 | Os requisitos com fonte E01 apontam para uma entrevista cuja transcrição não está no repositório. O [README das entrevistas](../levantamento/entrevistas/README.md) ainda marca a E01 como "Não realizada". | Registrar a transcrição e atualizar o README (#5, #6). |
| L02 | Nenhum requisito tem origem em E02, Q01, Q02 ou SA. | Fontes ainda não realizadas (#7, #8, #9). Os requisitos que vierem delas devem seguir a regra de identificadores da lista geral. |
| L03 | Nenhum requisito tem protótipo. | Protótipos ainda não produzidos (#22). Ao concluí-los, substituir "Pendente (#22)" pelo nome da tela. |
| L04 | RF08 a RF10, RF13 a RF15, RN03 e RN10 só se ligam a casos de uso ainda não descritos (CU-01, CU-03 e CU-04). | Descrições pendentes nas issues #14, #16 e #17. |
| L05 | RF17 a RF20 não têm caso de uso, entidade nem verificação. RF19 e RF20 também não têm necessidade correspondente na visão. | Dependem da PV08. Se forem confirmados, a visão precisa de uma necessidade para tipos de feedback e feedback espontâneo. |
| L06 | 12 dos 14 RF-DOC e 5 dos 6 RN-DOC não têm caso de uso, e quase todos não têm critério de aceitação. | Os critérios CA01 a CA13 cobrem os requisitos de E01. Vários itens DOC dependem das dúvidas D-01 a D-13 da pesquisa documental. |
| L07 | O RF10 rejeita a autoavaliação, e o RF17 (360°) a inclui. O conflito não está na seção 7 da lista geral. | Registrar como C03 na lista geral e decidir junto com a PV08. |

### 6.2. Inconsistências entre artefatos

| ID | Inconsistência | Onde |
| --- | --- | --- |
| I01 | Três esquemas de código para as fontes (seção 1.2 desta matriz). | Lista geral, especificação de requisitos e pesquisa documental |
| I02 | O RNF03 aparece duas vezes, com conteúdos diferentes. | Especificação suplementar, 3.5 e 3.6 |
| I03 | O CA13 e a seção 1.5 da especificação citam só o RNF01 a RNF07. A verificação do RNF08 ao RNF16 está apenas na especificação suplementar. | Especificação de requisitos, 1.5 e 3.6 |
| I04 | O RF07 é Importante na lista geral e essencial na especificação. | Lista geral, seção 3; especificação, RF07 |
| I05 | EVENTO_AUDITORIA está no texto do MER e no dicionário, mas não nos diagramas Mermaid do MER. | `mer-organizacao-catalogo.mmd` e `mer-coletas-respostas.mmd` |

## 7. Manutenção

- Ao criar ou alterar um requisito, caso de uso, entidade, tela ou critério de aceitação, atualizar a linha correspondente da seção 3 e as relações da seção 4.
- Identificadores removidos não são reutilizados (lista geral, seção 2).
- Quando um caso de uso "a elaborar" for descrito, retirar a marcação e conferir os requisitos listados no arquivo do caso de uso.
