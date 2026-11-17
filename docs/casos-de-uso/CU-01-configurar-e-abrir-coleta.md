# CU-01 — Configurar e abrir coleta

| Campo | Informação |
| --- | --- |
| Autoria | Brenner Rodrigues Sardinha |
| Versão | 0.1 — 16 de novembro de 2026 |
| Formato | Completo, estilo essencial (Larman, cap. 6) |
| Situação | Proposto para validação |

## Escopo

Sistema de gestão de competências e feedback.

## Nível

Objetivo do usuário (*user goal*): o RH prepara uma coleta e a abre, publicando o questionário e gerando as avaliações mútuas. A preparação pode ser interrompida e retomada em outra sessão; a abertura é concluída em uma única operação. Criar, consultar e alterar uma coleta em preparação fazem parte deste caso de uso. O cancelamento de uma coleta em preparação está no CU-03.

## Ator principal

**RH.**

## Partes interessadas e interesses

| Parte interessada | Interesse |
| --- | --- |
| RH | Montar a coleta com rapidez, conferir antes da abertura quem avaliará quem e quantas avaliações serão geradas, e não ter de corrigir atribuições depois. |
| Avaliador | Receber somente avaliações sobre colegas com quem trabalha, com um questionário claro e um prazo definido. |
| Receptor | Ser avaliado por pessoas que conhecem seu trabalho, sempre com reciprocidade e pelo mesmo questionário dos demais. |
| Gestor | Ter coletas comparáveis entre ciclos para os times sob sua responsabilidade (RN11). |
| Organização (controladora dos dados) | Tratar apenas os dados necessários dos participantes elegíveis e preservar a configuração publicada e sua autoria (RN05, RF16). |

## Pré-condições

1. O RH está autenticado (CU-08) e autorizado a administrar coletas (RF01).
2. O catálogo possui ao menos um grupo ativo com um parâmetro ativo (CU-05).
3. Existem usuários ativos lotados em times ativos (CU-06). No modo PARES, também existem relações de trabalho ativas entre eles (CU-07).

## Garantias de sucesso (pós-condições)

1. A coleta está em **ABERTA**, com título, período (início inclusivo, fim exclusivo) e modo de seleção registrados (RF08, RN07).
2. O questionário publicado contém apenas os grupos e perguntas ativos selecionados, com cópias de título, descrição, pergunta, tipo de avaliação e ordem. As cópias, o modo e as seleções ficam imutáveis; mudanças posteriores no catálogo não os alteram (RF09, RN04, RN05).
3. Para cada par válido, existem exatamente duas avaliações em **RASCUNHO**, A sobre B e B sobre A, sem autoavaliações nem duplicatas (RF10, RN01, RN02).
4. No modo TIMES, cada time selecionado com `n` integrantes elegíveis gerou `n × (n − 1) / 2` pares e `n × (n − 1)` avaliações, sem combinações entre times distintos. No modo PARES, cada par selecionado possui relação de trabalho ativa no instante da abertura (RF10, RN03).
5. Cada avaliação guarda as cópias de nome, cargo, time e setor de avaliador e receptor no instante da abertura. Mudanças posteriores de lotação não recalculam participantes (RN05).
6. A abertura, as cópias do questionário, todas as avaliações e os eventos de auditoria foram registrados como uma única operação (RF09, RF16, RNF02).

## Garantias mínimas

Em desistência ou falha, nenhuma coleta fica parcialmente aberta: ou todas as avaliações e cópias são registradas com a transição para **ABERTA**, ou nenhuma delas. A configuração já salva em preparação é preservada, e seleções retiradas são desativadas, nunca excluídas (RN12). Uma repetição da abertura não gera avaliações duplicadas. O catálogo e as coletas já publicadas não são alterados.

## Gatilho

O RH decide iniciar um ciclo de feedback, por exemplo no calendário de avaliações da organização ou a pedido de um gestor.

## Fluxo principal de sucesso

1. O RH solicita criar uma coleta.
2. O sistema solicita o título, o início e o fim do período de respostas e o modo de seleção, PARES ou TIMES, sem modo pré-selecionado (RF08).
3. O RH informa o título e o período e escolhe o modo TIMES.
4. O sistema valida se o título foi preenchido, com até 150 caracteres, e se o início é anterior ao fim. Registra a coleta em **PREPARACAO**, com o RH como criador, e o evento de auditoria (RF08, RF16, RN07).
5. O sistema apresenta os grupos ativos do catálogo, com seus parâmetros ativos e o tipo de avaliação de cada um.
6. O RH seleciona os grupos e, em cada um, as perguntas que farão parte do questionário, definindo a ordem dos grupos e das perguntas.
7. O sistema verifica se cada grupo selecionado tem ao menos uma pergunta e se nenhuma pergunta de origem foi escolhida duas vezes. Registra a seleção como cópias de preparação (RF08, RN04).
8. O sistema apresenta os times ativos, com o gestor responsável e a quantidade de integrantes elegíveis de cada um: usuários ativos lotados no time (RN03).
9. O RH seleciona um ou mais times.
10. O sistema registra a seleção dos times, sem duplicar um time já selecionado, e o evento de auditoria (RF08).
11. O RH solicita a abertura da coleta.
12. O sistema verifica se a configuração está completa e apresenta uma prévia para confirmação (RF09, RNF13):
    - o título e o período, destacando que o preenchimento só começa no início;
    - o questionário, com grupos, perguntas, tipos de avaliação e ordem;
    - os participantes de cada time e as quantidades de pares e de avaliações por time e no total;
    - o aviso de que, após a abertura, o questionário, o modo e os participantes não podem ser alterados, e ajustes exigirão outra coleta (RN05).
13. O RH confirma a abertura.
14. O sistema revalida a autorização, o estado **PREPARACAO**, o período e a composição. Resolve os integrantes elegíveis de cada time naquele instante e confere se coincidem com a prévia confirmada. Em seguida, na mesma operação (RF09, RF10, RN03, RNF02):
    - recopia os textos e tipos de avaliação atuais dos itens selecionados e congela o questionário;
    - gera, para cada par, as duas avaliações em **RASCUNHO**, com as cópias de contexto do avaliador e do receptor;
    - registra o estado **ABERTA** e os eventos de auditoria, sem conteúdo de respostas.
15. O sistema informa que a coleta foi aberta e quantas avaliações foram geradas. As avaliações ficam disponíveis aos avaliadores no CU-02 a partir do início do período (RN07).

## Extensões (fluxos alternativos)

**\*a. Antes da confirmação da abertura, o RH interrompe a preparação.**

1. O sistema mantém a coleta em **PREPARACAO**, com tudo o que já foi registrado. Nenhuma avaliação é criada.
2. O RH pode retomá-la depois pela extensão 1a.

**\*b. A sessão expirou ou o usuário não está autorizado, inclusive em acesso direto à operação.**

1. O sistema rejeita a operação, sem alterar a coleta e sem revelar dados dos participantes (RF01, RNF01). O caso de uso termina.

**1a. O RH retoma uma coleta em preparação.**

1. O sistema apresenta as coletas em **PREPARACAO**, com título, período, modo e situação da configuração (questionário e seleção completos ou não).
2. O RH escolhe uma coleta. O sistema apresenta a configuração atual.
3. O RH pode alterar título e período, conforme os passos 3 e 4, ou seguir para o passo 5, 8 ou 11.

**1b. O RH decide cancelar uma coleta em preparação.**

1. O fluxo segue no CU-03, extensão 5a. Este caso de uso termina.

**3a. O RH escolhe o modo PARES.**

1. O fluxo segue nos passos 4 a 7. No passo 8, o sistema apresenta os usuários ativos lotados em times ativos e, para cada um, as pessoas com quem possui relação de trabalho ativa (RN03).
2. O RH seleciona os pares. Pessoas de times diferentes podem formar um par se tiverem relação de trabalho.
3. O sistema verifica se os dois usuários são distintos e têm relação de trabalho ativa, e registra o par uma única vez, tratando A com B e B com A como o mesmo par (RF10). Se o par for inválido, indica o motivo e não o registra.
4. No passo 12, a prévia apresenta os pares e informa que cada um gera duas avaliações. O fluxo continua no passo 11.

**3b. O RH troca o modo de uma coleta em preparação.**

1. O sistema avisa que as seleções do modo anterior serão retiradas e pede confirmação.
2. O RH confirma.
3. O sistema desativa as seleções anteriores e registra o novo modo e o evento de auditoria na mesma operação, sem apagar registros (RF08, RN12). O fluxo volta ao passo 8.

**4a. Título vazio ou acima de 150 caracteres, ou início igual ou posterior ao fim.**

1. O sistema indica o campo e a condição inválida e preserva os demais dados informados (RI01). O fluxo volta ao passo 3.

**5a. Não há grupo ativo com parâmetro ativo.**

1. O sistema informa que o questionário depende do catálogo (CU-05). A coleta permanece em **PREPARACAO**. O caso de uso termina.

**6a. O RH retira um grupo ou uma pergunta da seleção.**

1. O sistema desativa a cópia de preparação, sem apagá-la. Retirar um grupo também retira suas perguntas (RF08, RN12).
2. Se o RH voltar a selecionar o item, o sistema reativa a mesma cópia, sem duplicatas. O fluxo volta ao passo 6.

**7a. Um grupo selecionado ficou sem pergunta ativa ou a mesma pergunta de origem foi escolhida em dois grupos.**

1. O sistema indica o grupo ou a pergunta com problema e não registra a seleção inválida (RN04, CA05). O fluxo volta ao passo 6.

**8a. Um time tem menos de dois integrantes elegíveis.**

1. O sistema apresenta o time com essa indicação e informa que ele impedirá a abertura se for selecionado (RF09, CA06B).

**9a. O RH retira um time ou par da seleção.**

1. O sistema desativa o vínculo da seleção, sem apagá-lo. Se o RH voltar a selecioná-lo, reativa o mesmo vínculo (RF08, RN12). O fluxo volta ao passo 9.

**12a. A configuração está incompleta ou inválida.**

1. O sistema não apresenta a prévia e lista os problemas encontrados: questionário vazio, grupo sem pergunta, seleção vazia, time com menos de dois integrantes elegíveis ou par sem relação de trabalho ativa (RF09, CA05, CA06B).
2. A coleta permanece em **PREPARACAO**. O fluxo volta ao passo 5 ou ao passo 8, conforme o problema.

**12b. O catálogo mudou desde a seleção das perguntas.**

1. O sistema apresenta as divergências: pergunta ou tipo de avaliação alterado, pergunta remanejada para outro grupo ou pergunta e grupo desativados (CU-05).
2. O RH atualiza explicitamente o questionário: aceita a versão atual ou retira a pergunta. Uma pergunta ou grupo desativado no catálogo deve ser retirado. O sistema não move perguntas nem altera textos sem essa ação (RF07, RN05).
3. O fluxo volta ao passo 11.

**13a. O RH não confirma a abertura.**

1. A coleta permanece em **PREPARACAO**, sem avaliações. O fluxo volta ao passo 5.

**14a. A composição mudou desde a prévia.**

1. Exemplos: um integrante entrou, saiu ou foi desativado; um time foi desativado; uma relação de trabalho foi desfeita.
2. O sistema não abre a coleta, apresenta a prévia atualizada com as diferenças destacadas e pede nova confirmação (RF09, CA06C). O fluxo volta ao passo 12.

**14b. A coleta já foi aberta ou cancelada por outra operação, por exemplo por um duplo clique ou por outra pessoa do RH.**

1. O sistema informa o estado atual, não registra outra transição e não gera avaliações duplicadas (RF10, RNF02, CA06). O caso de uso termina.

**14c. O fim do período já passou.**

1. O sistema não abre a coleta e solicita um novo período, pois ninguém poderia responder (RN07; regra proposta, ver questões em aberto). O fluxo volta ao passo 3.

**14d. Falha durante a abertura.**

1. O sistema desfaz a operação inteira: a coleta permanece em **PREPARACAO**, sem avaliações, sem cópias publicadas e sem eventos de abertura (RNF02, CA06C).
2. O sistema informa a falha. O RH pode tentar de novo a partir do passo 11.

**15a. A resposta de confirmação não chega ao RH, por exemplo por perda da conexão.**

1. O RH consulta novamente a coleta. O sistema apresenta o estado efetivamente registrado; uma nova solicitação de abertura segue a extensão 14b.

## Requisitos especiais

- Autorização, estados, período, composição e elegibilidade são validados no servidor, inclusive em chamadas diretas à API (RF01, RNF01).
- A abertura é atômica e idempotente: duas solicitações simultâneas não produzem duas transições nem avaliações duplicadas, e uma falha não deixa avaliações parciais (RNF02).
- A prévia do passo 12 e a confirmação protegem o RH contra erros de uso, pois a abertura não pode ser desfeita (RNF13, aplicado a este fluxo como proposta).
- Os eventos de auditoria da configuração e da abertura ficam protegidos contra alteração e não copiam dados além dos identificadores e metadados administrativos (RF16, RNF06).
- Configuração e prévia operáveis por teclado, com rótulos e mensagens de erro textuais, em telas de 360 a 1.440 px (RNF03, aplicado a este fluxo como proposta).
- Nas listas de times e usuários, homônimos são distinguidos por cargo, time ou setor, sem exigir digitação de identificadores (RI02).

## Lista de variantes tecnológicas e de dados

- O período é informado no fuso da organização e armazenado em UTC.
- A abertura pode ocorrer antes do início do período: as avaliações são geradas, mas o preenchimento só é liberado a partir do início (dicionário de dados, COLETA).
- A ordem dos grupos e das perguntas pode ser definida por arrastar ou por números de ordem; o resultado essencial é o mesmo.
- A seleção de pares pode partir de um usuário e listar seus vínculos de trabalho, ou apresentar todos os pares possíveis; o resultado essencial é o mesmo.
- Acesso por navegador em computador ou celular.

## Frequência de ocorrência

Uma abertura por coleta, conforme o calendário de ciclos da organização, que ainda não foi informado pelo stakeholder. A preparação pode envolver várias sessões. No modo TIMES, o volume da abertura cresce com o quadrado do tamanho do time: um time de 10 integrantes elegíveis gera 90 avaliações.

## Questões em aberto e decisões propostas

- **Fim do período já passado (14c):** a abertura com o fim no passado é rejeitada nesta elaboração. A regra é proposta e deve ser validada.
- **Início no passado:** pode-se abrir uma coleta cujo início já passou? Nesta elaboração, sim, desde que o fim seja futuro; o preenchimento fica liberado imediatamente.
- **Gestor responsável fora do time:** no modo TIMES, só entram os usuários lotados no time. O gestor responsável que não está lotado no time não participa automaticamente. Falta confirmar se isso atende ao feedback gestor-colaborador previsto no enunciado (PV08).
- **Quem pode alterar a preparação:** qualquer pessoa do RH ou somente o criador? Esta elaboração permite qualquer pessoa do RH, com o registro de autoria na auditoria.
- **Aviso aos participantes:** os avaliadores são informados da abertura? Não há requisito de notificação nesta versão (mesma questão do CU-02).
- **PV06:** a premissa de um time por usuário evita que a mesma pessoa apareça em dois times selecionados. Se a premissa mudar, a geração precisa evitar pares repetidos entre times.
- **Lacuna L07:** a abertura rejeita autoavaliações (RF10); o RF17 (360°) as inclui. A decisão depende de PV08.

## Rastreabilidade

| Elemento | Referência |
| --- | --- |
| Requisitos funcionais | RF01, RF07 (atualização explícita), RF08, RF09, RF10, RF16 |
| Regras de negócio | RN01, RN02, RN03, RN04, RN05, RN07, RN12 |
| Requisitos não funcionais | RNF01, RNF02, RNF03 (aplicação proposta), RNF06, RNF13 (aplicação proposta) |
| Interfaces | RI01, RI02 |
| Critérios de aceitação | CA01, CA05, CA06, CA06A, CA06B, CA06C |
| Entidades | COLETA, COLETA_TIME, COLETA_PAR, COLETA_GRUPO, COLETA_PARAM, AVALIACAO, EVENTO_AUDITORIA; leitura de USUARIO, TIME, RELACAO_TRABALHO, GRUPO_PARAM e PARAM |
| Especificação | [Especificação de requisitos](../requisitos/especificacao-requisitos.md), RF08 a RF10, RN03 a RN05 e RN07 |
| Dados e estados | [Dicionário de dados](../dicionario-dados.md), COLETA a AVALIACAO; [MER](../modelos/dominio/modelo-entidade-relacionamento.md), composição de coletas e atribuição |
| Matriz | [Matriz de rastreabilidade](../rastreabilidade/matriz-rastreabilidade.md) |
| Diagrama | [Diagrama de casos de uso](README.md) |
