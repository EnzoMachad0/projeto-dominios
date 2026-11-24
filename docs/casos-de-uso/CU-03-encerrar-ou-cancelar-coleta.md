# CU-03 — Encerrar ou cancelar coleta

| Campo | Informação |
| --- | --- |
| Autoria | Heitor Barbosa Souza |
| Versão | 0.2 — 23 de novembro de 2026 |
| Formato | Completo, estilo essencial (Larman, cap. 6) |
| Situação | Validado (E01, E02) |

## Escopo

Sistema de gestão de competências e feedback.

## Nível

Objetivo do usuário (*user goal*): o RH finaliza uma coleta em uma sessão de trabalho, encerrando a participação para disponibilizar os resultados elegíveis ou cancelando a coleta para retirá-la das análises.

## Ator principal

**RH.**

## Partes interessadas e interesses

| Parte interessada | Interesse |
| --- | --- |
| RH | Acompanhar a situação das avaliações e finalizar a coleta sem perder os registros. |
| Avaliador | Ter seus envios preservados e saber quando não pode mais responder. |
| Receptor | Consultar apenas resultados liberados pelo gestor ou pelo RH (RN09). |
| Gestor | Usar resultados de coletas encerradas, sem incluir coletas canceladas ou pares incompletos. |
| Organização (controladora dos dados) | Preservar a rastreabilidade da operação e restringir o acesso aos dados pessoais. |

## Pré-condições

1. O RH está autenticado (CU-08) e autorizado a administrar coletas (RF01).
2. Existe uma coleta **ABERTA** para encerramento, ou **PREPARACAO** ou **ABERTA** para cancelamento (RF13, RN07).

## Garantias de sucesso (pós-condições)

1. No encerramento, a coleta passa de **ABERTA** para **ENCERRADA**, com o instante registrado em `encerrada_em`. Avaliações em rascunho passam a **CANCELADA**, com instante e motivo de encerramento da coleta, preservando suas respostas (RF13, RN01, RN08).
2. Avaliações já **ENVIADA** mantêm seu estado, instante de envio e conteúdo. Avaliações já **CANCELADA** também são preservadas.
3. Após o encerramento, as avaliações enviadas e não canceladas ficam disponíveis para o gestor ou o RH liberar ao avaliado. A consulta e a liberação são feitas no CU-04 (RN09).
4. No cancelamento, a coleta passa de **PREPARACAO** ou **ABERTA** para **CANCELADA**, com instante e justificativa registrados. Todos os seus pares ficam fora das análises, inclusive os que possuem os dois sentidos enviados (RF13).
5. No cancelamento de uma coleta aberta, avaliações em rascunho passam a **CANCELADA**, preservando suas respostas; avaliações já enviadas ou canceladas não são alteradas. Este tratamento dos rascunhos foi validado (E01, E02).
6. Nenhum novo preenchimento ou envio é permitido na coleta finalizada. Não há reabertura nem exclusão física de registros (RN07, RN08, RN12).
7. A transição da coleta, as mudanças nas avaliações e a auditoria são registradas como uma única operação, sem persistência parcial (RF16, RNF02).

## Garantias mínimas

Em desistência ou falha anterior à conclusão, a operação não altera parcialmente a coleta nem suas avaliações. Os registros e os envios existentes permanecem preservados. Se a operação já tiver sido concluída, uma repetição não desfaz o resultado nem cria outra transição. Alterações válidas realizadas por outros participantes não são desfeitas.

## Gatilho

O RH decide finalizar uma coleta, por término do período, decisão de encerramento antecipado ou necessidade de cancelamento.

## Fluxo principal de sucesso

1. O RH solicita acompanhar as coletas.
2. O sistema apresenta as coletas com título, período e estado.
3. O RH escolhe uma coleta aberta.
4. O sistema apresenta a situação das avaliações: pendentes, enviadas e canceladas. O acompanhamento não revela o conteúdo dos rascunhos de terceiros (RF13, RN09).
5. O RH solicita o encerramento.
6. O sistema apresenta as consequências e pede confirmação: o preenchimento será bloqueado, as pendências serão canceladas com seus conteúdos preservados, os envios serão mantidos e a coleta não poderá ser reaberta. Se o prazo ainda não terminou, destaca que o encerramento será antecipado (decisão validada, E01, E02).
7. O RH confirma o encerramento.
8. O sistema revalida a autorização e o estado da coleta. Registra o estado **ENCERRADA**, o instante do encerramento, o cancelamento das avaliações ainda em rascunho com instante e motivo, e os eventos de auditoria, sem alterar os envios existentes (RF13, RF16, RN01, RN07, RN08).
9. O sistema informa que a coleta foi encerrada e apresenta sua situação final. Resultados recebidos elegíveis passam a poder ser consultados no CU-04, conforme RN09.

## Extensões (fluxos alternativos)

**\*a. Antes da confirmação, o RH abandona a operação.**

1. O sistema não efetua a finalização. Permanecem as regras do período e do estado atual da coleta.

**\*b. A sessão expirou ou o usuário não está autorizado, inclusive em acesso direto à operação.**

1. O sistema rejeita a operação, sem alterar a coleta ou revelar conteúdo de avaliações (RF01, RNF01). O caso de uso termina.

**2a. Não há coletas.**

1. O sistema informa que não há coletas para acompanhar. O caso de uso termina.

**3a. O RH escolhe uma coleta em preparação.**

1. O sistema informa que ela pode ser cancelada, mas não encerrada. Não há avaliações atribuídas antes da abertura.
2. Se o RH solicitar o cancelamento, segue a extensão 5a; caso contrário, o fluxo volta ao passo 2.

**3b. A coleta já está encerrada ou cancelada.**

1. O sistema apresenta o estado final e não permite outra finalização nem reabertura (RN07). O caso de uso termina.

**5a. O RH solicita cancelar uma coleta em preparação ou aberta.**

1. O sistema solicita uma justificativa e informa que a coleta inteira ficará fora das análises, mesmo se houver avaliações enviadas. Explica que os dados serão preservados e a coleta não poderá ser reaberta. Esse cancelamento da coleta não é o cancelamento individual de um par, cuja restrição está na RN01.
2. O RH informa a justificativa e confirma o cancelamento.
3. O sistema verifica se a justificativa foi preenchida e possui até 500 caracteres, conforme o dicionário de dados (PV07). Se inválida, informa o problema e solicita a correção, sem cancelar a coleta.
4. O sistema revalida a autorização e o estado da coleta. Registra **CANCELADA**, `cancelada_em`, `motivo_cancelamento`, o cancelamento das avaliações ainda em rascunho com instante e motivo, e os eventos de auditoria, na mesma operação. Preserva os envios, as avaliações já canceladas, as respostas, as seleções e os questionários. Em preparação, não cria avaliações.
5. O sistema informa que a coleta foi cancelada. O preenchimento e os envios ficam bloqueados, e todos os seus pares são excluídos das análises. O caso de uso termina.

**6a. Não há avaliações enviadas.**

1. O sistema informa que o encerramento não produzirá resultados para liberar (RN09). O RH pode confirmar ou desistir; o fluxo continua no passo 7.

**7a. O RH não confirma o encerramento.**

1. O sistema não encerra a coleta. O fluxo volta ao passo 4.

**8a. A coleta foi finalizada por outra operação desde a consulta.**

1. O sistema informa o estado atual, não registra outra transição e não repete o cancelamento das pendências. O caso de uso termina. Esta verificação também se aplica à extensão 5a.

**8b. Um participante envia uma avaliação enquanto o RH finaliza a coleta.**

1. O sistema considera uma ordem consistente para as operações: se o envio foi concluído antes da finalização, preserva-o; se a finalização ocorreu primeiro, rejeita o envio e preserva o conteúdo já salvo. Não permite que a mesma avaliação seja enviada e cancelada simultaneamente. Esta garantia também se aplica à extensão 5a.

**8c. Falha durante a finalização.**

1. O sistema desfaz as alterações desta operação na coleta, nas avaliações e na auditoria, sem desfazer envios válidos anteriores.
2. O sistema informa a falha. O RH pode consultar novamente a situação a partir do passo 1 e tentar outra vez. Esta extensão também se aplica ao cancelamento.

**9a. A resposta de confirmação não chega ao RH, por exemplo por perda da conexão.**

1. O RH consulta novamente a coleta. O sistema apresenta o estado efetivamente registrado; uma nova solicitação de finalização deve revalidá-lo, conforme a extensão 8a.

## Requisitos especiais

- Autorização e validação de estados no servidor, inclusive em acessos diretos (RF01, RNF01).
- A finalização deve ser atômica e coordenada com os envios concorrentes, conforme as garantias das extensões 8a a 8c. É uma extensão da integridade de RNF02 para o RF13, validada (E01, E02).
- As operações devem preservar a auditoria protegida contra alteração, sem copiar comentários ou credenciais para os eventos (RF16, RNF06, RNF07).
- O acompanhamento e a confirmação devem ser operáveis por teclado, com mensagens textuais e uso em telas de 360 a 1.440 px (RNF03).
- O fim do período bloqueia novos envios mesmo enquanto o estado ainda é **ABERTA**. Não há encerramento automático por passagem do tempo (RN07 e dicionário de dados).

## Lista de variantes tecnológicas e de dados

- Acesso por navegador em computador ou celular; a descrição não depende de uma disposição específica de telas.
- Instantes de encerramento e cancelamento são armazenados em UTC, conforme o dicionário. Encerrar preenche `encerrada_em`; cancelar preenche `cancelada_em` e a justificativa. Os estados finais são distintos.
- O encerramento usa como motivo do cancelamento das avaliações pendentes o encerramento da coleta. No cancelamento da coleta, a justificativa informada pelo RH fundamenta também o cancelamento dos rascunhos, sem solicitar um motivo por avaliação.

## Frequência de ocorrência

Uma finalização bem-sucedida por coleta. O acompanhamento pode ocorrer várias vezes antes dela. Não há estimativa de volume validada pelo stakeholder.

## Decisões validadas (E01, E02)

- **Encerramento antecipado:** permitido antes do prazo, com aviso e confirmação explícita no passo 6.
- **Rascunhos ao cancelar a coleta:** passam a **CANCELADA**, preservando os conteúdos e os envios existentes.
- **Atomicidade da finalização:** as garantias das extensões 8a a 8c protegem contra finalização parcial e corrida com o envio (RNF02 aplicado ao RF13).
- **PV03 e PV04:** o encerramento não libera resultados automaticamente; a liberação ao avaliado é feita pelo gestor ou pelo RH (RN09, CU-04).
- **PV07:** a justificativa tem até 500 caracteres, conforme o dicionário de dados.
- **PV05 / conflito C01:** os registros são preservados no uso operacional e anonimizados ao fim do prazo de retenção (RN12).

## Rastreabilidade

| Elemento | Referência |
| --- | --- |
| Requisitos funcionais | RF01, RF13, RF16 |
| Regras de negócio | RN01, RN07, RN08, RN09, RN12 |
| Requisitos não funcionais | RNF01, RNF02, RNF03, RNF06, RNF07 |
| Critérios de aceitação | CA01, CA02, CA09, CA12; concorrência e reversão detalhadas nas extensões 8a a 8c |
| Entidades | COLETA, AVALIACAO, FEEDBACK, EVENTO_AUDITORIA; seleções e cópias da coleta são preservadas |
| Especificação | [Especificação de requisitos](../requisitos/especificacao-requisitos.md), RF13, RN01, RN07 a RN09 e RN12 |
| Dados e estados | [Dicionário de dados](../dicionario-dados.md), COLETA e AVALIACAO; [MER](../modelos/dominio/modelo-entidade-relacionamento.md), cancelamento e preservação |
| Matriz | [Matriz de rastreabilidade](../rastreabilidade/matriz-rastreabilidade.md) |
| Diagrama | [Diagrama de casos de uso](README.md) |
