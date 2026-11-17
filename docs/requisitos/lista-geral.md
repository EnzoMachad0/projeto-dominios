# Lista geral de requisitos

Versão 0.2 — 17 de novembro de 2026. Lista única de requisitos funcionais (RF), não funcionais (RNF) e regras de negócio (RN), conforme a etapa 3.3 do [processo de requisitos](../PROCESSO_REQUISITOS.md). O detalhamento está na [especificação de requisitos](especificacao-requisitos.md) e na [especificação suplementar](especificacao-suplementar.md).

## 1. Fontes

| Código | Fonte | Situação |
| --- | --- | --- |
| E01 | Entrevista com o stakeholder e esclarecimentos posteriores. | Realizada |
| E02 | Segunda entrevista, reunida com a E01 na [síntese das entrevistas](../levantamento/sintese-entrevistas.md). | Realizada — transcrição pendente (#41) |
| Q01, Q02 | Questionários de levantamento. | **Pendentes** |
| SA | [Análise do sistema análogo Culture Amp](../levantamento/analise-sistema-analogo-culture-amp.md). | Realizada |
| DOC | [Pesquisa documental sobre LGPD e ISO/IEC 25010](../levantamento/pesquisa-documental.md). | Realizada |
| ENU | Enunciado da disciplina (`trabalho_da_disciplina_de_domnio.pdf`). | Consultado |

A versão 0.2 incorpora a [síntese das entrevistas](../levantamento/sintese-entrevistas.md) (identificadores locais `SIN-*`) e a análise do sistema análogo (SA). Como as transcrições ainda não foram recebidas (#41), os itens com origem nas entrevistas citam a síntese e permanecem **Propostos** até a conferência com as transcrições (#6) e a validação com o stakeholder (#25). A seção 9 registra a correspondência entre os identificadores locais e os desta lista. Quando Q01 e Q02 forem concluídos, seus requisitos devem ser incorporados com os mesmos identificadores, quando confirmarem um item existente, ou com novos identificadores na sequência.

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
| RF08 | RH (toda a organização) e gestor (times sob sua responsabilidade) configuram coletas: modalidade, período, questionário e participantes. | E01 | Essencial | Proposto |
| RF09 | Abrir a coleta publica cópia imutável do questionário e congela os participantes. | E01 | Essencial | Proposto |
| RF10 | Nas coletas recíprocas, gerar as avaliações nos dois sentidos para cada par, sem duplicatas; a autoavaliação é tratada no RF22. | E01 | Essencial | Proposto |
| RF11 | Avaliador mantém respostas em rascunho dentro do período da coleta. | E01 | Essencial | Proposto |
| RF12 | Avaliador envia o questionário completo; depois do envio, as respostas ficam imutáveis. | E01 | Essencial | Proposto |
| RF13 | RH e gestor, no escopo da RN14, acompanham, encerram e cancelam coletas, cancelando pendências no encerramento. | E01 | Essencial | Proposto |
| RF14 | Consultar histórico individual com filtros, respeitando permissões. | E01, ENU | Essencial | Proposto |
| RF15 | Analisar resultados por usuário: médias normalizadas, proporções de Sim/Não e evolução. | E01, ENU | Essencial | Proposto |
| RF16 | Registrar eventos de auditoria das mudanças administrativas e transições de estado. | E01, DOC, SA | Importante | Proposto |
| RF17 | Avaliação 360°: o responsável seleciona o avaliado e os participantes por papel (gestor, colegas, subordinados e o próprio avaliado). | E01, E02, ENU, SA | Essencial | Proposto |
| RF18 | Plano de ação vinculado a um feedback, com metas, ações, responsáveis, prazos e pontos de verificação, e registro do progresso. | E01, ENU, SA | Essencial | Proposto |
| RF19 | Classificar cada feedback como formal ou informal e como positivo ou construtivo, em eixos independentes. | E01, ENU | Essencial | Proposto |
| RF20 | Registrar feedback informal motivado por um evento, sem abrir uma coleta. | E01, ENU | Essencial | Proposto |
| RF21 | Registrar o contexto do feedback: fato motivador, impactos, data, emissor, receptor e conteúdo, com questionário opcional. | E01 | Essencial | Proposto |
| RF22 | Autoavaliação: o colaborador avalia a si mesmo, isoladamente ou como parte de um 360°. | E01, E02 | Essencial | Proposto |
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
| RN01 | Reciprocidade (coletas recíprocas): cada par gera dois sentidos, criados e cancelados na mesma transação. | E01 | Essencial | Proposto |
| RN02 | Unicidade de avaliação por coleta, avaliador e receptor, e de resposta por pergunta; avaliador e receptor só coincidem na autoavaliação. | E01, E02 | Essencial | Proposto |
| RN03 | Elegibilidade: usuários e times ativos; relação de trabalho no modo PARES. | E01 | Essencial | Proposto |
| RN04 | Composição: parâmetro com um grupo atual; sem repetição na mesma coleta. | E01 | Essencial | Proposto |
| RN05 | Preservação: a abertura congela questionário, modo e pares. | E01 | Essencial | Proposto |
| RN06 | Tipo de avaliação: valores aceitos conforme `ESCALA_0_10`, `ESCALA_0_5` ou `BOOLEANO`. | E01 | Essencial | Validado |
| RN07 | Estados da coleta e transições permitidas. | E01 | Essencial | Proposto |
| RN08 | Estados da avaliação; feedback herda o estado. | E01 | Essencial | Proposto |
| RN09 | Independência e liberação: nas coletas recíprocas, resultado visível só com o par completo e a coleta encerrada; nas demais modalidades, a liberação segue a RN15. | E01 | Essencial | Pendente (PV03, PV04) |
| RN10 | Fórmulas de cálculo dos indicadores. | E01, DOC | Essencial | Proposto |
| RN11 | Comparabilidade entre coletas. | E01 | Importante | Proposto |
| RN12 | Não há exclusão física de dados. | E01 | Essencial | Validado — conflito C01 |
| RN13 | Ciclo de desenvolvimento: o plano de ação sucede o feedback que o motivou e antecede o feedback que avalia seus resultados; é opcional quando não há ação acordada. | E01 | Essencial | Proposto |
| RN14 | Escopo de atuação: o gestor cria e acompanha avaliações e planos dos times sob sua responsabilidade; o RH atua em toda a organização. | E01 | Essencial | Proposto |
| RN15 | Regras por modalidade: recíproca (pares ou times) com dois sentidos; 360° com atribuições por papel, sem reciprocidade; autoavaliação com avaliador igual ao receptor; feedback informal sem coleta. | E01, E02 | Essencial | Proposto — liberação por modalidade pendente (PV04) |
| RN16 | Feedback baseado em fatos: o registro descreve fatos e impactos, sem verificação automática da veracidade pelo sistema. | E01 | Importante | Proposto |
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
| RNF01 | *Security* | Autenticação e autorização validadas no servidor, negando por padrão. Consolida RNF-DOC-01. | E01, DOC, SA | Essencial | Proposto |
| RNF02 | *Reliability* / *Security* (*integrity*) | Operações críticas transacionais, sem duplicatas sob concorrência. Consolida RNF-DOC-07. | E01, DOC | Essencial | Proposto |
| RNF03 | *Interaction capability* / *Flexibility* | Uso por teclado, rótulos e telas de 360 a 1.440 px. Consolida RNF-DOC-13 e RNF-DOC-14. | E01, DOC | Importante | Proposto |
| RNF04 | *Performance efficiency* | 95% das consultas em até 2 s com 50 usuários simultâneos. Consolida RNF-DOC-15. | E01, DOC | Importante | Pendente (PV07) |
| RNF05 | *Reliability* (*recoverability*) | Backup diário e restauração em até 4 h. Consolida RNF-DOC-09. | E01, DOC | Importante | Pendente (PV07) |
| RNF06 | *Security* (*accountability*) | Auditoria protegida contra alteração. Consolida RNF-DOC-06. | E01, DOC | Essencial | Proposto |
| RNF07 | *Security* (*confidentiality*) | Restringir dados ao escopo autorizado e não registrar respostas em logs. | E01, DOC, SA | Essencial | Pendente (PV05) |
| RNF08 | *Security* (*confidentiality*) | Comunicação cifrada com TLS/HTTPS. Consolida RI03 e RNF-DOC-04. | E01, DOC, SA | Essencial | Proposto |
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
| Modalidades de feedback (chefe-colaborador, pares, 360°) | RF08, RF10, RF17, RF22, RN15 | Coberto |
| Tipos de feedback (formal, informal, positivo e construtivo) | RF19, RF20, RF21 | Coberto |
| Questionários de competências | RF05 a RF09 | Coberto |
| Relatórios e indicadores | RF15, RN10, RNF12 | Coberto |
| Histórico e evolução | RF14, RF15, RN11 | Coberto |
| Planos de ação e desenvolvimento | RF18, RN13 | Coberto |
| Confidencialidade, anonimato e LGPD | RN09, RNF07, RNF16, RF-DOC-01 a 14 | Parcial; conflitos C01 e C02 |
| Plataforma web e uso em dispositivos móveis | RI01, RNF03 | Coberto |

## 9. Correspondência com a síntese e o sistema análogo

### 9.1. Síntese das entrevistas

| ID local | Requisito nesta lista |
| --- | --- |
| SIN-RF01, SIN-RF07, SIN-RF08 | RF21 |
| SIN-RF02, SIN-RF03 | RF19 |
| SIN-RF04 | RF10, RF17, RF22 |
| SIN-RF05 | RF08, RN14 |
| SIN-RF06 | RF17 |
| SIN-RF09, SIN-RF10 | RF18 |
| SIN-RF11 | RF20 |
| SIN-RF12 | RF01 a RF04 |
| SIN-RF13 | RF05 a RF07 |
| SIN-RF14 | RF08 a RF10, RF17 |
| SIN-RF15 | RF11, RF12 |
| SIN-RF16 | RF13 |
| SIN-RF17 | RF14, RF15, RN10, RN11 |
| SIN-RF18 | RF16 |
| SIN-RN01 | RN12 |
| SIN-RN02 | RN16 |
| SIN-RN03 | RN13 |
| SIN-RN04 | RN01, RN02, RN15 |
| SIN-RN05 | RN05, RN09, RN15 |
| SIN-RN06 | RN10, RN11 |
| SIN-RN07 | RN14 |
| SIN-RNF01 a SIN-RNF05 | RNF01 a RNF07 |

### 9.2. Sistema análogo

A análise do Culture Amp usa identificadores próprios, que não se confundem com os desta lista. Ela confirma itens existentes e não gerou requisito sem correspondência.

| Proposta da análise (SA) | Requisito nesta lista |
| --- | --- |
| Feedback 360° (seção 3.2) | RF17 |
| Feedback contínuo (seção 3.3) | RF20, RF21 |
| Planos de ação e metas (seções 3.5 e 3.6) | RF18, RN13 |
| RNF-LGPD-01 e RNF-LGPD-06 (finalidade e necessidade) | RF-DOC-01, RN-DOC-01, RN-DOC-04 |
| RNF-LGPD-02 e RN01 da análise (acesso autorizado) | RF01, RNF01 |
| RNF-LGPD-03 e RN03 da análise (confidencialidade) | RNF07 |
| RNF-LGPD-04 (registro de operações) | RF16, RNF06 |
| RNF-LGPD-05 (direitos dos titulares) | RF-DOC-03 a RF-DOC-06 |
| RNF-LGPD-07 (retenção e descarte) | RF-DOC-08 (conflito C01) |
| RNF-LGPD-08 (proteção em trânsito e armazenamento) | RNF08, RNF10 |
| RN02, RN04 e RN05 da análise (ciclo válido, registro do envio, imutabilidade) | RF12, RN07, RN08 |

Calibração, reuniões individuais, reconhecimento e pesquisas de engajamento (seções 3.7 a 3.11 da análise) ficam fora desta versão.

## 10. Próximos passos

1. Conferir a síntese com as transcrições quando forem recebidas (#41, #6) e incorporar os questionários (#7, #8).
2. Discutir as prioridades, a liberação por modalidade (PV04) e os conflitos C01 e C02 com o stakeholder (#25).
3. Atualizar a situação dos itens validados e refletir as mudanças na especificação e na matriz de rastreabilidade.
