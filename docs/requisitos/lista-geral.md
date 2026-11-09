# Lista geral de requisitos

Versão 0.1 — 8 de novembro de 2026. Lista única de requisitos funcionais (RF), não funcionais (RNF) e regras de negócio (RN), conforme a etapa 3.3 do [processo de requisitos](../PROCESSO_REQUISITOS.md). O detalhamento está na [especificação de requisitos](especificacao-requisitos.md) e na [especificação suplementar](especificacao-suplementar.md).

## 1. Fontes

| Código | Fonte | Situação |
| --- | --- | --- |
| E01 | Entrevista com o stakeholder e esclarecimentos posteriores. | Realizada |
| E02 | Segunda entrevista. | **Pendente** |
| Q01, Q02 | Questionários de levantamento. | **Pendentes** |
| SA | Análise de sistema análogo. | **Pendente** |
| DOC | [Pesquisa documental sobre LGPD e ISO/IEC 25010](../levantamento/pesquisa-documental.md). | Realizada |
| ENU | Enunciado da disciplina (`trabalho_da_disciplina_de_domnio.pdf`). | Consultado |

Quando E02, Q01, Q02 e SA forem concluídas, seus requisitos devem ser incorporados com os mesmos identificadores, quando confirmarem um item existente, ou com novos identificadores na sequência.

## 2. Convenções

- **Identificadores:** estáveis; um identificador removido não é reutilizado. Requisitos da pesquisa documental mantêm o sufixo `DOC` de sua origem.
- **Prioridade:** **Essencial** (sem ele a primeira versão não atende ao objetivo), **Importante** (agrega valor relevante, mas admite solução provisória) e **Desejável** (pode ficar para versão futura). A prioridade é uma proposta da equipe e precisa ser discutida com o stakeholder.
- **Situação:** **Validado** (confirmado explicitamente pelo stakeholder), **Proposto** (levantado, aguardando validação) e **Pendente** (depende de decisão registrada).

## 3. Requisitos funcionais

| ID | Descrição resumida | Fonte | Prioridade | Situação |
| --- | --- | --- | --- | --- |
| RF01 | Autenticar contas ativas e verificar perfil e escopo em cada operação. | E01, DOC | Essencial | Proposto |
| RF02 | RH mantém usuários (nome, cargo, time, perfil, e-mail), sem exclusão física. | E01 | Essencial | Proposto |
| RF03 | RH mantém times (nome, setor, gestor), sem exclusão física. | E01 | Essencial | Proposto |
| RF04 | RH mantém relações de trabalho simétricas, sem autorrelação nem duplicatas. | E01 | Essencial | Proposto |
| RF05 | RH mantém parâmetros com pergunta, grupo e tipo de avaliação (`score`). | E01 | Essencial | Validado |
| RF06 | RH mantém grupos de parâmetros com título e descrição. | E01 | Essencial | Proposto |
| RF07 | RH remaneja parâmetros entre grupos sem alterar coletas publicadas. | E01 | Importante | Proposto |
| RF08 | RH configura coletas: período, questionário e modo de seleção PARES ou TIMES. | E01 | Essencial | Proposto |
| RF09 | Abrir a coleta publica cópia imutável do questionário e congela os participantes. | E01 | Essencial | Proposto |
| RF10 | Gerar as avaliações nos dois sentidos para cada par, sem duplicatas nem autoavaliação. | E01 | Essencial | Proposto |
| RF11 | Avaliador mantém respostas em rascunho dentro do período da coleta. | E01 | Essencial | Proposto |
| RF12 | Avaliador envia o questionário completo; depois do envio, as respostas ficam imutáveis. | E01 | Essencial | Proposto |
| RF13 | RH acompanha, encerra e cancela coletas, cancelando pendências no encerramento. | E01 | Essencial | Proposto |
| RF14 | Consultar histórico individual com filtros, respeitando permissões. | E01, ENU | Essencial | Proposto |
| RF15 | Analisar resultados por usuário: médias normalizadas, proporções de Sim/Não e evolução. | E01, ENU | Essencial | Proposto |
| RF16 | Registrar eventos de auditoria das mudanças administrativas e transições de estado. | E01, DOC | Importante | Proposto |
| RF17 | Avaliação 360° (gestor, colegas, subordinados e autoavaliação). | ENU | Desejável | Pendente (PV08) |
| RF18 | Planos de desenvolvimento individual com metas e acompanhamento. | ENU | Desejável | Pendente (PV08) |
| RF19 | Classificar feedbacks como formal/informal e positivo/construtivo. | ENU | Desejável | Pendente (PV08) |
| RF20 | Feedback espontâneo, fora de uma coleta formal. | ENU, roteiro (pergunta 9) | Desejável | Pendente (PV08) |
| RF-DOC-01 | Aviso de privacidade antes do primeiro uso e sempre acessível. | DOC | Essencial | Proposto |
| RF-DOC-02 | Contato do encarregado ou canal do titular em local de destaque. | DOC | Importante | Proposto |
| RF-DOC-03 | Titular consulta os dados mantidos sobre ele. | DOC | Importante | Pendente (D-04) |
| RF-DOC-04 | Registrar requisições de titulares e alertar sobre o prazo de 15 dias. | DOC | Desejável | Proposto |
| RF-DOC-05 | Corrigir dados cadastrais inexatos. | DOC | Essencial | Proposto — atendido por RF02 |
| RF-DOC-06 | Titular registra contestação de feedback recebido, sem alterar o original. | DOC | Desejável | Pendente (D-05) |
| RF-DOC-07 | Anonimizar, bloquear ou eliminar dados pessoais. | DOC | Importante | Pendente — conflito C01 |
| RF-DOC-08 | Configurar prazo de retenção e sinalizar registros vencidos. | DOC | Importante | Pendente — conflito C01 |
| RF-DOC-09 | Exportar dados do titular em formato estruturado. | DOC | Desejável | Pendente (D-02, D-13) |
| RF-DOC-10 | Registrar e revogar consentimento, quando for a base legal. | DOC | Desejável | Pendente (D-02) |
| RF-DOC-11 | Informar compartilhamentos com terceiros. | DOC | Desejável | Pendente (D-01) |
| RF-DOC-12 | Relatório das operações de tratamento. | DOC | Desejável | Proposto |
| RF-DOC-13 | Listar titulares afetados em incidente. | DOC | Desejável | Proposto |
| RF-DOC-14 | Orientar o avaliador a não incluir dados sensíveis em comentários. | DOC | Importante | Proposto |

## 4. Regras de negócio

| ID | Descrição resumida | Fonte | Prioridade | Situação |
| --- | --- | --- | --- | --- |
| RN01 | Reciprocidade: cada par gera dois sentidos, criados e cancelados na mesma transação. | E01 | Essencial | Proposto |
| RN02 | Unicidade de avaliação por coleta, avaliador e receptor, e de resposta por pergunta. | E01 | Essencial | Proposto |
| RN03 | Elegibilidade: usuários e times ativos; relação de trabalho no modo PARES. | E01 | Essencial | Proposto |
| RN04 | Composição: parâmetro com um grupo atual; sem repetição na mesma coleta. | E01 | Essencial | Proposto |
| RN05 | Preservação: a abertura congela questionário, modo e pares. | E01 | Essencial | Proposto |
| RN06 | Tipo de avaliação: valores aceitos conforme `ESCALA_0_10`, `ESCALA_0_5` ou `BOOLEANO`. | E01 | Essencial | Validado |
| RN07 | Estados da coleta e transições permitidas. | E01 | Essencial | Proposto |
| RN08 | Estados da avaliação; feedback herda o estado. | E01 | Essencial | Proposto |
| RN09 | Independência e liberação: resultado visível só com o par completo e a coleta encerrada. | E01 | Essencial | Pendente (PV03, PV04) |
| RN10 | Fórmulas de cálculo dos indicadores. | E01, DOC | Essencial | Proposto |
| RN11 | Comparabilidade entre coletas. | E01 | Importante | Proposto |
| RN12 | Não há exclusão física de dados. | E01 | Essencial | Validado — conflito C01 |
| RN-DOC-01 | Cada dado coletado deve ter finalidade definida. | DOC | Essencial | Proposto |
| RN-DOC-02 | Regime de identificação do avaliador definido por modalidade. | DOC | Importante | Pendente — conflito C02 |
| RN-DOC-03 | Número mínimo de respondentes para exibir resultados anônimos. | DOC | Importante | Pendente — conflito C02 |
| RN-DOC-04 | Dados usados apenas para as finalidades informadas. | DOC | Essencial | Proposto |
| RN-DOC-05 | Questionários não solicitam dados sensíveis. | DOC | Essencial | Proposto |
| RN-DOC-06 | Decisões sobre o colaborador não podem ser unicamente automatizadas. | DOC | Importante | Pendente (D-09) |

## 5. Requisitos não funcionais

O detalhamento, com condição e critério de verificação, está na [especificação suplementar](especificacao-suplementar.md).

| ID | Característica ISO/IEC 25010:2023 | Descrição resumida | Fonte | Prioridade | Situação |
| --- | --- | --- | --- | --- | --- |
| RNF01 | *Security* | Autenticação e autorização validadas no servidor, negando por padrão. Consolida RNF-DOC-01. | E01, DOC | Essencial | Proposto |
| RNF02 | *Reliability* / *Security* (*integrity*) | Operações críticas transacionais, sem duplicatas sob concorrência. Consolida RNF-DOC-07. | E01, DOC | Essencial | Proposto |
| RNF03 | *Interaction capability* / *Flexibility* | Uso por teclado, rótulos e telas de 360 a 1.440 px. Consolida RNF-DOC-13 e RNF-DOC-14. | E01, DOC | Importante | Proposto |
| RNF04 | *Performance efficiency* | 95% das consultas em até 2 s com 50 usuários simultâneos. Consolida RNF-DOC-15. | E01, DOC | Importante | Pendente (PV07) |
| RNF05 | *Reliability* (*recoverability*) | Backup diário e restauração em até 4 h. Consolida RNF-DOC-09. | E01, DOC | Importante | Pendente (PV07) |
| RNF06 | *Security* (*accountability*) | Auditoria protegida contra alteração. Consolida RNF-DOC-06. | E01, DOC | Essencial | Proposto |
| RNF07 | *Security* (*confidentiality*) | Restringir dados ao escopo autorizado e não registrar respostas em logs. | E01, DOC | Essencial | Pendente (PV05) |
| RNF08 | *Security* (*confidentiality*) | Comunicação cifrada com TLS/HTTPS. Consolida RI03 e RNF-DOC-04. | E01, DOC | Essencial | Proposto |
| RNF09 | *Security* (*authenticity*) | Política de senha e MFA para perfis administrativos. Consolida RNF-DOC-03. | DOC | Importante | Proposto |
| RNF10 | *Security* (*confidentiality*) | Armazenamento protegido de credenciais e comentários. Consolida RNF-DOC-05. | DOC | Importante | Proposto |
| RNF11 | *Security* (*resistance*) | Limitar tentativas de login e não liberar com vulnerabilidade crítica conhecida. Consolida RNF-DOC-08. | DOC | Importante | Pendente (D-12) |
| RNF12 | *Functional suitability* (*correctness*) | Indicadores com fórmula documentada e casos de referência. Consolida RNF-DOC-10. | DOC | Essencial | Proposto |
| RNF13 | *Interaction capability* (*self-descriptiveness*, *user error protection*) | Informar quem verá a resposta; preservar rascunho e confirmar o envio. Consolida RNF-DOC-11 e RNF-DOC-12. | DOC | Importante | Proposto |
| RNF14 | *Maintainability* (*testability*) | Regras de visibilidade cobertas por testes automatizados. Consolida RNF-DOC-16. | DOC | Importante | Proposto |
| RNF15 | *Compatibility* (*interoperability*) | Integração com sistemas de RH em formato documentado, se houver. Consolida RNF-DOC-17. | DOC | Desejável | Pendente (D-01) |
| RNF16 | *Security* (*confidentiality*) | Em avaliações anônimas, nenhuma saída do sistema revela o autor. Consolida RNF-DOC-02. | DOC, ENU | Desejável | Pendente — conflito C02 |

## 6. Duplicidades tratadas

Requisitos não funcionais equivalentes foram unidos sob um único identificador (`RNFxx`), mantendo o identificador documental de origem na descrição para não perder a rastreabilidade. RF-DOC-05 é atendido pela alteração de cadastro do RF02 e não gera funcionalidade nova.

## 7. Conflitos registrados

| ID | Conflito | Itens | Encaminhamento |
| --- | --- | --- | --- |
| C01 | A E01 definiu que nenhum dado é excluído fisicamente, mas a LGPD (arts. 15, 16 e 18) prevê eliminação ou anonimização ao fim do tratamento ou a pedido do titular. | RN12 × RF-DOC-07, RF-DOC-08 | Discutir com o stakeholder (PV05). Alternativa proposta: manter a regra no uso operacional e permitir anonimização irreversível ao término do prazo de retenção. |
| C02 | A E01 propôs avaliação identificada, enquanto o README e o enunciado citam anonimato. | RN09, PV04 × RN-DOC-02, RN-DOC-03, RNF16 | Confirmar com o stakeholder e o professor (PV04, D-03). |

## 8. Cobertura do escopo do enunciado

| Tema do enunciado | Requisitos | Situação |
| --- | --- | --- |
| Modalidades de feedback (gestor, pares, 360°) | RF08, RF10, RF17 | Pares e times cobertos; 360° pendente |
| Questionários de competências | RF05 a RF09 | Coberto |
| Relatórios e indicadores | RF15, RN10, RNF12 | Coberto |
| Histórico e evolução | RF14, RF15, RN11 | Coberto |
| Planos de desenvolvimento | RF18 | Pendente |
| Confidencialidade, anonimato e LGPD | RN09, RNF07, RNF16, RF-DOC-01 a 14 | Parcial; conflitos C01 e C02 |
| Plataforma web e uso em dispositivos móveis | RI01, RNF03 | Coberto |

## 9. Próximos passos

1. Incorporar os requisitos de E02, Q01, Q02 e SA.
2. Discutir as prioridades e os conflitos C01 e C02 com o stakeholder.
3. Atualizar a situação dos itens validados e refletir as mudanças na especificação e na matriz de rastreabilidade.
