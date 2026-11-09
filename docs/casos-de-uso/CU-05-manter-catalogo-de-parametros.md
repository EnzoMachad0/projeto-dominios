# CU-05 — Manter catálogo de parâmetros

| Campo | Informação |
| --- | --- |
| Autoria | Danilo Sucupira Galvão |
| Versão | 0.1 — 9 de novembro de 2026 |
| Formato | Completo, estilo essencial (Larman, cap. 6) |
| Situação | Proposto para validação |

## Escopo

Sistema de gestão de competências e feedback.

## Nível

Objetivo do usuário (*user goal*): o RH conclui as alterações no catálogo em uma sessão de trabalho. As operações de cadastrar, consultar, alterar e desativar parâmetros e grupos estão reunidas em um único caso de uso "Manter", como o Larman admite para operações desse tipo.

## Ator principal

**RH.**

## Partes interessadas e interesses

| Parte interessada | Interesse |
| --- | --- |
| RH | Manter um catálogo organizado e reutilizável, sem risco de alterar coletas já publicadas. |
| Participante (avaliador) | Responder a perguntas claras, com tipo de resposta adequado ao que se pergunta. |
| Gestor | Comparar os resultados dos times entre ciclos, sem distorções causadas por mudanças no catálogo (RN11). |
| Organização (controladora dos dados) | Usar questionários que não solicitam dados pessoais sensíveis, conforme a LGPD (RN-DOC-05). |

## Pré-condições

1. O RH está autenticado (CU-08), com perfil RH.

## Garantias de sucesso (pós-condições)

1. Cada parâmetro cadastrado ou alterado está ativo, com pergunta e tipo de avaliação válidos e exatamente um grupo atual, que está ativo (RF05, RN04, RN06).
2. As coletas publicadas mantêm as cópias de grupos e perguntas (RF07, RN05).
3. Cada operação está registrada na auditoria (RF16).

## Garantias mínimas

Em qualquer falha ou desistência, nenhum item do catálogo é excluído fisicamente (RN12), nenhum parâmetro fica sem grupo ou com mais de um grupo atual, nenhuma operação fica registrada pela metade e as coletas publicadas permanecem inalteradas.

## Gatilho

O RH precisa preparar uma nova coleta ou revisar o catálogo de competências.

## Fluxo principal de sucesso

1. O RH solicita a consulta ao catálogo de parâmetros.
2. O sistema apresenta os grupos ativos, com título e descrição, e os parâmetros ativos de cada grupo, com pergunta e tipo de avaliação (RF05, RF06).
3. O RH inicia o cadastro de um parâmetro e indica o grupo que o receberá.
4. O sistema solicita a pergunta e o tipo de avaliação, informa os tipos aceitos (escala de 0 a 10, escala de 0 a 5 ou Sim/Não) e orienta que a pergunta não solicite dados pessoais sensíveis (RN06, RN-DOC-05).
5. O RH informa a pergunta e o tipo de avaliação.
6. O sistema valida se a pergunta foi preenchida, com até 1.000 caracteres; se o tipo está entre os aceitos; e se o grupo escolhido continua ativo (RF05, RN06).
7. O sistema registra, de forma atômica, o parâmetro como ativo e vinculado a um único grupo atual, junto com o evento de auditoria da operação (RF05, RN04, RF16, RNF02).
8. O sistema informa que o parâmetro foi cadastrado e apresenta o catálogo atualizado.
9. O RH repete os passos 3 a 8 até concluir os cadastros desejados.

## Extensões (fluxos alternativos)

**\*a. A qualquer momento, antes do registro, o RH abandona a operação.**

1. O sistema não registra dados parciais, e o catálogo permanece como estava.

**\*b. Um usuário sem perfil RH tenta cadastrar, alterar, remanejar ou desativar itens do catálogo, inclusive por chamada direta.**

1. O sistema rejeita a operação sem alterar o catálogo (RF01, RNF01). O caso de uso termina.

**2a. Não há grupo ativo.**

1. O sistema informa que todo parâmetro precisa pertencer a um grupo ativo.
2. O RH cadastra um grupo (extensão 3d). O fluxo volta ao passo 3.

**3a. O RH altera a pergunta ou o tipo de avaliação de um parâmetro ativo.**

1. O RH escolhe o parâmetro e informa os novos valores.
2. Se o parâmetro já foi publicado em alguma coleta, o sistema avisa duas coisas: as coletas publicadas mantêm a versão anterior, e os resultados da nova versão não serão comparados automaticamente com os anteriores (RN05, RN11; aviso proposto, ver questões em aberto).
3. O RH confirma a alteração.
4. O sistema valida como no passo 6 e registra, de forma atômica, a alteração e o evento de auditoria, sem alterar cópias de coletas publicadas (RF05, RF16, RNF02). O fluxo continua no passo 8.

**3b. O RH desativa um parâmetro.**

1. O RH escolhe o parâmetro e solicita a desativação.
2. O sistema marca o parâmetro como inativo, sem excluí-lo, e registra o evento de auditoria (RN12, RF16). O parâmetro deixa de ser oferecido em novas coletas, e as coletas publicadas não mudam (RN05). O fluxo continua no passo 8.

**3c. O RH remaneja um parâmetro para outro grupo.**

1. O RH escolhe o parâmetro ativo e o grupo de destino.
2. O sistema verifica se o grupo de destino está ativo e é diferente do grupo atual. Se não estiver ativo ou for o mesmo grupo, informa o motivo, e o fluxo volta ao passo 1 desta extensão (RF07).
3. O sistema transfere o parâmetro de forma atômica, mantendo um único grupo atual, e registra o evento de auditoria (RF07, RN04, RF16, RNF02). As coletas publicadas mantêm o grupo original. As coletas em preparação só recebem a mudança por atualização explícita do questionário (RF07, CA04). O fluxo continua no passo 8.

**3d. O RH mantém um grupo de parâmetros.**

1. O RH faz uma de duas coisas:
   - cadastra um grupo, informando o título (até 120 caracteres) e, se quiser, uma descrição (até 1.000 caracteres);
   - escolhe um grupo existente para alterar esses dados ou desativá-lo (RF06).
2. O sistema valida e registra a operação e o evento de auditoria. O grupo nunca é excluído fisicamente, e as coletas publicadas mantêm o título e a descrição copiados (RF06, RF16, RN05, RN12).
3. Se o grupo a desativar ainda tiver parâmetros ativos, o sistema impede a desativação e lista os parâmetros que precisam ser remanejados ou desativados antes (regra proposta, ver questões em aberto). O fluxo continua no passo 8.

**6a. Pergunta vazia, pergunta acima de 1.000 caracteres ou tipo de avaliação não aceito.**

1. O sistema indica o problema e preserva os dados informados. O fluxo volta ao passo 5.

**6b. O grupo escolhido foi desativado durante o cadastro, por exemplo por outro usuário do RH.**

1. O sistema informa que o grupo não está mais ativo e não registra o parâmetro.
2. O fluxo volta ao passo 3, preservando a pergunta e o tipo de avaliação informados.

**7a. Falha durante o registro.**

1. O sistema desfaz a operação inteira: nenhum parâmetro e nenhum evento de auditoria são registrados (RNF02).
2. O sistema informa a falha e preserva os dados informados. O RH pode tentar de novo a partir do passo 6.

## Requisitos especiais

- Autorização e validações sempre no servidor, inclusive em chamadas diretas à API (RNF01).
- Cadastro, alteração, remanejamento e desativação são atômicos. Duas pessoas do RH alterando o mesmo item ao mesmo tempo não geram duplicatas nem um parâmetro com dois grupos (RNF02).
- Uso por teclado, com rótulos e mensagens de erro em texto, em telas de 360 a 1.440 px (RNF03).
- A consulta ao catálogo (passo 2) segue a meta de desempenho das consultas: 95% em até 2 s com 50 usuários simultâneos (RNF04, pendente na PV07).
- Os eventos de auditoria do catálogo ficam protegidos contra alteração (RNF06).

## Lista de variantes tecnológicas e de dados

- O tipo de avaliação aparece ao RH como "Escala de 0 a 10", "Escala de 0 a 5" e "Sim/Não", e é armazenado como `ESCALA_0_10`, `ESCALA_0_5` e `BOOLEANO` (RN06).
- O remanejamento pode ser feito escolhendo o grupo de destino ou arrastando o parâmetro. O resultado essencial é o mesmo.
- Por padrão, a consulta mostra só os itens ativos. Um filtro administrativo pode incluir os inativos.
- Os parâmetros são cadastrados um a um. A importação em lote não está prevista nesta versão.
- Acesso por navegador, em computador ou celular.

## Frequência de ocorrência

Baixa, concentrada na preparação de coletas e em revisões periódicas do catálogo. O stakeholder não informou estimativa de volume.

## Questões em aberto

- **Competências por cargo e por pessoa:** nas anotações da E01, a cliente citou competências fixas, competências por cargo e competências particulares de uma pessoa. O modelo atual não relaciona grupo com cargo nem com usuário. Falta decidir se a associação entra neste caso de uso ou em outro (pergunta feita no PR #29).
- **PV06:** o grupo único por parâmetro (primeira parte do RN04) ainda é uma proposta de modelagem, pendente de validação.
- **Aviso de comparabilidade (3a.2):** o sistema deve avisar que alterar a pergunta ou o tipo de um parâmetro já publicado separa a série histórica (RN11)? A regra foi proposta neste caso de uso.
- **Coletas em preparação:** o que acontece com uma coleta em preparação que contém um parâmetro alterado (3a) ou desativado (3b)? O RF07 trata só do remanejamento.
- **Bloqueio de desativação de grupo (3d.3):** um grupo com parâmetros ativos não pode ser desativado? A regra foi proposta neste caso de uso.
- **Reativação:** parâmetros e grupos desativados podem ser reativados?
- **Perguntas repetidas:** pode haver duas perguntas com o mesmo texto no mesmo grupo?

## Rastreabilidade

| Elemento | Referência |
| --- | --- |
| Requisitos funcionais | RF01, RF05, RF06, RF07, RF16 |
| Regras de negócio | RN04, RN05, RN06, RN11, RN12, RN-DOC-05 |
| Requisitos não funcionais | RNF01, RNF02, RNF03, RNF04, RNF06 |
| Critérios de aceitação | CA01, CA04 |
| Entidades | GRUPO_PARAM, PARAM, COLETA_GRUPO, COLETA_PARAM, EVENTO_AUDITORIA |
| Diagrama | [Diagrama de casos de uso](README.md) |
