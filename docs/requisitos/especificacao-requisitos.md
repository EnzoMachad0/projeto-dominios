# Especificação de requisitos (IEEE 830)

Sistema de criação e gerenciamento de feedbacks. Versão 0.2. Data: 8 de novembro de 2026. Situação: proposta para validação. Estrutura adotada: IEEE 830-1998 (seções 1 a 3), complementada por pendências (seção 4) e rastreabilidade (seção 5).

## 1 Introdução

### 1.1 Propósito

Especificar o comportamento esperado de um sistema que permita cadastrar usuários e times, organizar parâmetros em grupos, executar coletas com avaliações mútuas e consultar o histórico e a análise dos feedbacks por usuário. O público inclui a equipe de desenvolvimento, os responsáveis pelo negócio e os avaliadores acadêmicos.

A organização segue as seções de introdução, descrição geral e requisitos específicos da estrutura solicitada de IEEE 830. Trata-se de uma especificação de projeto, sem declaração de certificação ou conformidade formal.

### 1.2 Escopo

O núcleo compreende a manutenção de feedbacks, usuários, times, grupos e parâmetros; a configuração de coletas com seleção por pares ou por times; a avaliação recíproca entre participantes; o remanejamento de parâmetros; e a consulta de resultados individuais ao longo do tempo. Na seleção por times, todos os integrantes elegíveis de cada time avaliam uns aos outros nos dois sentidos. Não há exclusão física de dados: operações de retirada de uso devem desativar registros ou cancelar coletas e avaliações, preservando os dados.

Os perfis de acesso são os valores do ENUM informado: `RH`, `PROF` e `GESTOR`. `PROF` significa profissional e representa o participante comum. Os três perfis podem participar de avaliações. A proposta de um único perfil por conta permanece sujeita a validação.

O PDF da disciplina apresenta objetivos adicionais de gestão de competências. Feedback 360°, anonimato, planos de ação e metas de desenvolvimento são extensões a validar, não funcionalidades confirmadas no núcleo desta versão. Esta distinção é importante para a aprovação acadêmica do escopo.

### 1.3 Definições e convenções

CRUD é a sigla convencional para criar, consultar, atualizar e excluir; neste projeto, a última operação é substituída por desativação ou cancelamento, sem exclusão física. Coleta é uma campanha delimitada no tempo. Avaliação é o questionário respondido por um avaliador sobre um receptor em uma coleta. Feedback é a resposta a um parâmetro desse questionário. Parâmetro é uma pergunta com um tipo de avaliação definido em `score`: escala de 0 a 10, escala de 0 a 5 ou booleano. Grupo reúne parâmetros de um mesmo tema.

Os identificadores `RF` representam requisitos funcionais, `RNF` requisitos não funcionais, `RN` regras de negócio, `CA` critérios de aceitação e `PV` pendências de validação. “Deve” indica comportamento requerido na proposta. As decisões adicionais identificadas como propostas dependem de aprovação do responsável pelo negócio.

### 1.4 Referências e origem

- F01 — Entrevista E01 com o stakeholder e esclarecimentos posteriores: entidades, campos, perfis, seleção por pares ou times, PROF como profissional, ausência de exclusão física e score como tipo de avaliação.
- F02 — `trabalho_da_disciplina_de_domnio.pdf`, páginas 1 e 2: contexto de gestão de competências, plataforma web e objetivos complementares; página 3: artefatos de requisitos e modelagem solicitados pela disciplina.
- F03 — [IEEE 830 de 1998](https://standards.ieee.org/ieee/830/1222/): referência para a organização da especificação.
- F04 — [Pesquisa documental sobre LGPD e ISO/IEC 25010](../levantamento/pesquisa-documental.md): requisitos candidatos com sufixo `DOC` (RF-DOC, RN-DOC e RNF-DOC).

F02 é uma fonte de contexto e de expectativas acadêmicas. Orientações de entrevistas, cronograma, pesquisas e prototipação do PDF não constituem ações executadas nem novos pedidos do stakeholder. Não foram inventadas entrevistas, respostas de questionários ou aprovações de stakeholders. Fontes ainda não realizadas (segunda entrevista, questionários e sistema análogo) estão registradas como pendentes na [lista geral](lista-geral.md).

### 1.5 Organização e documentos relacionados

A seção 2 apresenta a visão do produto. A seção 3 descreve requisitos verificáveis. A seção 4 registra decisões pendentes e extensões. A seção 5 conecta necessidades, requisitos, entidades e critérios de aceitação.

Os identificadores são os mesmos da [lista geral de requisitos](lista-geral.md), que também consolida os requisitos documentais. Documentos relacionados:

| Documento | Conteúdo |
| --- | --- |
| [Documento de visão](../visao.md) | Problema, stakeholders, escopo e funcionalidades principais. |
| [Casos de uso](../casos-de-uso/README.md) | Atores, diagrama, índice e descrições completas. |
| [Especificação suplementar](especificacao-suplementar.md) | Requisitos não funcionais detalhados segundo a ISO/IEC 25010:2023. Detalha os RNF01 a RNF07 desta seção 3.4. |
| [Modelo de domínio e MER](../modelos/dominio/README.md) | Conceitos, entidades, cardinalidades e restrições. |
| [Dicionário de dados e glossário](../dicionario-dados.md) | Atributos, tipos, validações e definição dos termos. |

## 2 Descrição geral

### 2.1 Perspectiva do produto

Aplicação web de apoio ao processo de feedback organizacional. A interface permite administrar o catálogo de perguntas e executar coletas independentes. A configuração publicada de cada coleta é preservada, de forma que alterações posteriores no catálogo não modifiquem avaliações anteriores.

### 2.2 Funções do produto

O sistema mantém a estrutura de times e usuários, registra relações de trabalho, organiza questionários, permite escolher pares ou times e cria os dois sentidos de cada avaliação. Para times, gera todos os pares internos entre integrantes elegíveis. Recebe notas e comentários e apresenta resultados por usuário, coleta, grupo e parâmetro.

### 2.3 Perfis e permissões propostas

- `RH`: administra usuários, times, relações de trabalho, catálogo, coletas e atribuições. Acompanha pendências e consulta análises dentro da política de acesso aprovada.
- `GESTOR`: acompanha as coletas e os resultados dos times sob sua responsabilidade, sem administrar perfis ou alterar respostas de terceiros. O vínculo de responsabilidade é explícito no time.
- `PROF` — profissional: responde às próprias avaliações e consulta seus feedbacks enviados e resultados recebidos liberados.

As permissões de consulta propostas não autorizam acesso irrestrito a todo o conteúdo. Acesso a rascunhos é exclusivo do autor. A visualização de resultados individuais pelo RH e pelo gestor deve ser confirmada em PV04. Um usuário de qualquer perfil pode avaliar e receber avaliações.

### 2.4 Ambiente e interfaces gerais

Acesso por navegador com conexão à rede. Interface em português, com formulários de cadastro, montagem da coleta, preenchimento e histórico. Banco de dados relacional é uma proposta de projeto. Linguagem, framework, hospedagem e provedor de identidade não estão definidos. Não há integração externa obrigatória no núcleo.

### 2.5 Restrições

O modelo deve preservar os identificadores e conceitos fornecidos, admitindo normalização para evitar listas em colunas e duplicação de dados. A reciprocidade deve produzir respostas independentes. A movimentação de parâmetros deve preservar as versões publicadas dos questionários e os resultados históricos.

### 2.6 Premissas e dependências propostas

- Cada usuário tem um único perfil e pertence a um time ativo para participar de novas coletas.
- `trabalha_com` representa uma relação simétrica entre dois usuários, inclusive de times diferentes.
- Cada parâmetro pertence a um grupo por vez no catálogo. Coletas podem reutilizar o mesmo parâmetro.
- `score` representa o tipo de avaliação, confirmado pelo stakeholder na E01: `ESCALA_0_10`, `ESCALA_0_5` ou `BOOLEANO`. `valor` contém um inteiro no intervalo correspondente ou um booleano nativo.
- A coleta usa um único questionário para todos os pares incluídos. Não há autoavaliação no núcleo.
- Cada par recebe duas avaliações independentes, A sobre B e B sobre A.
- Cada coleta usa um modo de seleção: `PARES` ou `TIMES`. No modo TIMES, as combinações são internas a cada time selecionado, sem exigir relações individuais em `trabalha_com` e sem gerar combinações entre times diferentes.
- A autenticação depende de um identificador de conta único, aqui proposto como e-mail. Credenciais ficam no mecanismo de autenticação, fora do modelo de negócio.

## 3 Requisitos específicos

### 3.1 Interfaces externas

**RI01 Interface do usuário.** O sistema deve apresentar cadastros de usuários, times, grupos e parâmetros; configuração de coleta com escolha do modo PARES ou TIMES; seleção de pares ou de times conforme o modo; prévia dos participantes e da quantidade de avaliações a gerar; lista de avaliações atribuídas; formulário de respostas; e histórico com análise. Erros devem identificar o campo e a condição inválida, preservando os dados válidos do formulário.

**RI02 Entrada e saída de dados.** O sistema deve receber os atributos documentados no dicionário e apresentar os dados conforme o perfil do usuário autenticado. IDs internos não devem ser exigidos como digitação manual quando houver seleção por nome.

**RI03 Comunicação.** A aplicação web deve usar conexão HTTPS em produção. Nenhuma API pública ou integração com sistemas de RH é exigida nesta versão.

### 3.2 Requisitos funcionais

**RF01 Autenticar e autorizar usuários — essencial, proposta de suporte.** O sistema deve autenticar contas ativas, identificar o perfil e verificar em cada operação o recurso e o escopo de acesso. Uma tentativa de acessar dados de outro usuário deve ser rejeitada se não houver permissão explícita.

**RF02 Manter usuários — essencial, F01.** O RH deve poder criar, listar, consultar, alterar e desativar usuários. O cadastro deve conter nome, cargo, time, perfil e identificador de conta. Não deve haver exclusão física, mesmo sem dependências. A desativação deve impedir novas atribuições e autenticação, preservando registros anteriores.

**RF03 Manter times — essencial, F01.** O RH deve poder criar, consultar, alterar e desativar times, informando nome e setor. Deve ser possível atribuir um gestor ativo com perfil `GESTOR`. A desativação preserva todos os vínculos e registros históricos; não deve haver exclusão física.

**RF04 Manter relações de trabalho — essencial, F01.** O RH deve poder vincular e desvincular usuários que trabalham juntos. O sistema deve impedir vínculos de um usuário consigo mesmo e vínculos duplicados, tratando A com B e B com A como a mesma relação. A desvinculação não deve remover avaliações já atribuídas.

**RF05 Manter parâmetros — essencial, F01.** O RH deve poder cadastrar, consultar, alterar e desativar parâmetros, informando pergunta, score e grupo. O campo score deve permitir escolher o tipo de avaliação ESCALA_0_10, ESCALA_0_5 ou BOOLEANO. Não deve haver exclusão física. Alterações no catálogo não devem atualizar cópias de coletas publicadas.

**RF06 Manter grupos de parâmetros — essencial, F01.** O RH deve poder cadastrar, consultar, alterar e desativar grupos, informando título e descrição. A lista de parâmetros deve ser obtida pelos vínculos dos parâmetros com o grupo. Não deve haver exclusão física.

**RF07 Remanejar parâmetros — essencial, F01.** O RH deve poder transferir um parâmetro ativo entre grupos ativos. A transferência deve ser atômica, mantendo um único grupo atual. Deve afetar o catálogo e novas configurações, preservando coletas já publicadas. Coletas ainda em preparação somente devem incorporar a mudança por atualização explícita do questionário.

**RF08 Configurar coletas — essencial, F01 e modelagem.** O RH deve poder criar, consultar, alterar e cancelar coletas em preparação, definindo título, início, fim, grupos, parâmetros e modo de seleção PARES ou TIMES. No modo PARES, deve selecionar pares elegíveis individualmente; no modo TIMES, deve selecionar um ou mais times ativos. Deve ser possível escolher um subconjunto não vazio dos parâmetros ativos de cada grupo selecionado. A troca de modo na preparação deve desativar em transação as seleções do modo anterior, sem misturar os dois modos e sem apagar registros. As avaliações são criadas somente na abertura. Grupos e perguntas retirados da preparação também devem ser desativados, preservando suas cópias.

**RF09 Publicar questionário da coleta — essencial, derivado de F01.** Ao abrir a coleta, o sistema deve preservar cópias do título e descrição dos grupos e da pergunta, score e ordem dos parâmetros. Deve validar as seleções do modo escolhido, resolver os integrantes elegíveis dos times naquele instante e congelar o conjunto final de pares. Antes da publicação, deve apresentar uma prévia dos participantes e da quantidade de avaliações; se a composição mudar antes da abertura, deve atualizar a prévia para confirmação do RH. Deve rejeitar coleta sem grupo, grupo sem parâmetro, período inválido, seleção vazia, ausência de pares válidos ou time selecionado com menos de dois integrantes elegíveis. Publicação e geração de todas as avaliações devem ser atômicas. O questionário deve permanecer imutável após a abertura.

**RF10 Atribuir avaliações mútuas por pares ou times — essencial, F01.** No modo PARES, o sistema deve criar A sobre B e B sobre A para cada par selecionado com relação de trabalho vigente. No modo TIMES, deve combinar todos os integrantes elegíveis de cada time selecionado, gerando avaliações nos dois sentidos para cada combinação, independentemente de vínculos individuais em `trabalha_com`. Usuários de times diferentes não são combinados automaticamente. Para um time com `n` integrantes elegíveis, devem ser gerados `n × (n − 1) / 2` pares e `n × (n − 1)` avaliações. Repetir a operação ou selecionar o mesmo time novamente não deve gerar duplicatas. Autoavaliações devem ser rejeitadas.

**RF11 Manter feedbacks em rascunho — essencial, F01.** O avaliador deve poder criar, consultar, alterar e desativar suas respostas em avaliação atribuída, enquanto ela estiver em rascunho e a coleta estiver aberta no período permitido. Cada resposta deve conter parâmetro, valor compatível com o tipo de avaliação e comentário opcional. Desativar uma resposta preserva seu registro e torna a pergunta pendente, sem cancelar a avaliação recíproca. Voltar a responder deve reativar a linha existente, respeitando sua unicidade. O formulário deve apresentar entrada numérica para escalas e seleção explícita Sim ou Não para booleanos, sem resposta pré-selecionada.

**RF12 Enviar avaliação — essencial, F01.** O avaliador deve poder enviar o questionário completo. O sistema deve validar todas as respostas e registrar o envio de forma atômica. Após o envio, respostas devem ficar imutáveis. Enviar A sobre B não deve preencher nem enviar B sobre A.

**RF13 Acompanhar e finalizar coletas — essencial, derivado de F01.** O RH deve consultar avaliações pendentes, enviadas e canceladas, encerrar coleta aberta e cancelar coleta em preparação ou aberta com justificativa. No encerramento, avaliações incompletas devem ser canceladas com motivo. Respostas já enviadas devem ser preservadas. Uma coleta cancelada não deve integrar análises.

**RF14 Consultar histórico individual — essencial, F01.** O sistema deve permitir filtrar por usuário, período de encerramento, coleta, grupo e parâmetro, respeitando as permissões. O autor pode consultar seus envios; o receptor consulta resultados liberados de coletas encerradas. Rascunhos de terceiros não devem aparecer em consultas ou relatórios.

**RF15 Analisar resultados por usuário — essencial, F01.** O sistema deve apresentar quantidade de avaliações válidas e respostas ativas, por coleta, grupo e parâmetro. Para escalas numéricas, deve apresentar média normalizada; para booleanos, contagem e proporção de Sim e Não, separadamente das médias numéricas. Grupos com tipos mistos devem apresentar indicadores separados, sem média única que combine booleanos e notas. Deve apresentar evolução entre coletas somente quando houver comparabilidade de perguntas e tipos de avaliação. Resultado sem respostas válidas deve aparecer como “sem dados”.

**RF16 Preservar e auditar histórico — essencial, proposta de suporte.** O sistema deve registrar autor, instante, operação, entidade e identificador das mudanças administrativas, transições de estado e remanejamentos. Os eventos não devem conter texto de comentários nem credenciais. A troca de time do usuário não deve alterar o time registrado nas avaliações antigas.

### 3.3 Regras de negócio propostas

**RN01 Reciprocidade.** Uma atribuição consiste em exatamente dois sentidos entre usuários distintos, na mesma coleta. A criação e o cancelamento devem operar sobre o par em uma transação. No cancelamento, os sentidos em rascunho passam a CANCELADA; um sentido já enviado mantém seu estado e conteúdo, mas o par fica inválido para resultados. O cancelamento de um par com ambos os sentidos enviados não é permitido nesta versão. O encerramento cancela as pendências sem apagar conteúdo enviado.

**RN02 Unicidade.** Só pode existir uma avaliação para a combinação coleta, avaliador e receptor; e uma resposta por avaliação e parâmetro da coleta.

**RN03 Elegibilidade.** A abertura deve validar usuários ativos vinculados a times ativos. No modo PARES, também deve validar a relação de trabalho de cada par selecionado. No modo TIMES, todos os usuários ativos lotados em cada time selecionado são elegíveis entre si, sem exigir vínculo individual prévio; usuários inativos não entram na geração. Cada time selecionado deve ter ao menos dois integrantes elegíveis. Desativações posteriores impedem novos acessos e atribuições, mas não reescrevem o histórico. O RH deve resolver pendências inviabilizadas por cancelamento do par ou encerramento da coleta.

**RN04 Composição.** Um parâmetro possui um grupo atual no catálogo. Na mesma coleta, um parâmetro de origem não pode aparecer duas vezes, mesmo em grupos distintos. O modelo não usa arrays de IDs em colunas.

**RN05 Preservação.** Abertura congela o questionário, o modo de seleção, os times selecionados quando aplicável e os pares finais. Trocas de pergunta, score, grupo, título, setor ou time não alteram os dados históricos copiados. Entradas, saídas e transferências de integrantes após a abertura não recalculam os pares. Ajustes exigem outra coleta. Não é permitido incluir ou remover pares após a abertura nesta versão.

**RN06 Tipo de avaliação.** `score` admite `ESCALA_0_10`, `ESCALA_0_5` ou `BOOLEANO`. A cópia `score_snapshot` determina o tipo aceito no feedback: inteiro de 0 a 10, inteiro de 0 a 5 ou booleano nativo verdadeiro/falso, respectivamente. Zero e falso contam como respostas preenchidas; nulo ou resposta desativada não contam. Não converter automaticamente os números 0 e 1 nem os textos “true” e “false” em booleanos. Rascunhos podem omitir respostas; o envio exige exatamente uma resposta ativa e válida para cada parâmetro ativo da coleta. Comentário é opcional e limitado a 2.000 caracteres, sujeito a PV07.

**RN07 Estados da coleta.** Transições permitidas: `PREPARACAO → ABERTA`, `PREPARACAO → CANCELADA`, `ABERTA → ENCERRADA` e `ABERTA → CANCELADA`. Estados finais não reabrem nesta versão. O período é inclusivo no início e exclusivo no fim; após o fim, o envio é bloqueado mesmo antes do encerramento administrativo.

**RN08 Estados da avaliação e do feedback.** Avaliação inicia em `RASCUNHO` e pode passar a `ENVIADA` ou `CANCELADA`. Não há retorno a rascunho. O status do feedback é herdado da avaliação, evitando estados contraditórios entre respostas do mesmo questionário.

**RN09 Independência e liberação.** O avaliador não pode ver a resposta recebida enquanto estiver respondendo. Como política proposta, o receptor só vê o resultado de um par após ambos enviarem e a coleta ser encerrada. Pares incompletos ou cancelados ficam fora dos resultados recebidos e da análise; o autor mantém acesso ao próprio envio. Esta regra depende de PV03 e PV04.

**RN10 Cálculo.** Para respostas numéricas válidas e ativas, a nota normalizada é `100 × valor / limite_superior`, sendo o limite 10 para ESCALA_0_10 e 5 para ESCALA_0_5, conforme o tipo copiado na coleta. A média numérica é a soma dessas notas dividida pela quantidade de respostas numéricas válidas do recorte, sem pesos adicionais. Booleanos não entram nessa média: o percentual de Sim é `100 × quantidade de verdadeiros / quantidade de respostas booleanas válidas`, com percentual de Não calculado de forma equivalente. “Sim” não significa automaticamente desempenho positivo, pois isso depende da pergunta. Denominador zero produz “sem dados”. Arredondamento para duas casas ocorre apenas na apresentação. O número de avaliações é a contagem distinta de avaliações, não a de respostas. Percentual de conclusão é `avaliações ENVIADAS / avaliações não CANCELADAS × 100`; denominador zero produz “sem avaliações elegíveis”.

**RN11 Comparabilidade.** A série temporal deve separar versões cuja pergunta ou escala tenham mudado. Identidade de parâmetro, texto e score da cópia definem comparabilidade nesta versão. Grupos recompostos devem indicar a mudança de composição e não ser apresentados automaticamente como a mesma métrica. Valores históricos nunca devem ser recalculados com o score atual do catálogo.

**RN12 Preservação sem exclusão.** Nenhum dado deve ser excluído fisicamente, inclusive cadastros sem vínculos, seleções da preparação, cópias de questionário e respostas em rascunho. Cadastros, vínculos e respostas usam desativação lógica; coletas e avaliações usam cancelamento conforme suas transições permitidas. Consultas operacionais consideram apenas registros ativos e seleções vigentes, enquanto consultas históricas autorizadas preservam acesso aos registros anteriores. Respostas enviadas e cópias publicadas não podem ser desativadas nem alteradas; sua inelegibilidade é controlada pelo cancelamento permitido da avaliação ou coleta. Não há expurgo automático ou exclusão em cascata.

### 3.4 Requisitos não funcionais propostos

Os critérios desta seção são metas de projeto a validar, e não capacidades já medidas.

**RNF01 Segurança.** Toda operação deve validar autenticação e autorização no servidor. Testes devem comprovar o bloqueio de consulta e alteração fora do escopo de cada perfil, inclusive por acesso direto ao identificador do registro.

**RNF02 Integridade e concorrência.** Publicação de coleta, geração dos dois sentidos e envio de avaliação devem ser transacionais. Duas requisições simultâneas de atribuição ou envio não devem produzir duplicatas nem conjuntos parciais de respostas.

**RNF03 Usabilidade e acesso.** Os fluxos de preenchimento devem funcionar por teclado, apresentar rótulos para os campos e erros textuais, e permitir uso em larguras de 360 a 1.440 pixels sem rolagem horizontal nos formulários.

**RNF04 Desempenho.** Meta proposta: 95% das consultas de cadastros e histórico com paginação devem responder em até 2 segundos, sob 50 usuários simultâneos e base de até 100.000 respostas, em ambiente de homologação documentado. Análises usam a mesma meta, com filtros por usuário e coleta. Infraestrutura e massa do ensaio devem ser registradas.

**RNF05 Recuperação.** Deve existir cópia de segurança diária e procedimento de restauração verificado em homologação. Meta proposta: perda máxima de 24 horas de dados e restauração em até 4 horas, sujeita à definição de infraestrutura.

**RNF06 Rastreabilidade.** Os eventos de auditoria devem permitir identificar quem alterou uma configuração e quando. Usuários comuns não devem poder editar ou excluir esses eventos.

**RNF07 Privacidade.** A aplicação deve restringir dados ao escopo autorizado e evitar conteúdo de respostas nos logs técnicos. A política definida para esta versão preserva os dados sem exclusão física nem expurgo automático. A compatibilização dessa política com as necessidades jurídicas da organização depende de PV05. Estes controles não constituem, por si, declaração de conformidade com a LGPD mencionada no enunciado.

### 3.5 Requisitos de dados

O modelo deve manter usuários, times, relações de trabalho, grupos e parâmetros do catálogo, coletas com seu modo de seleção, vínculos dos pares ou times selecionados por coleta, cópias dos grupos e parâmetros por coleta, avaliações, respostas e eventos de auditoria. Seleções usam indicador de atividade; os pares finais ficam materializados nas avaliações dos dois sentidos na abertura. Score e sua cópia são tipos enumerados; valor admite um número inteiro ou booleano nativo, validado conforme o tipo da cópia. Chaves estrangeiras devem impedir referências inexistentes. As referências e restrições de escopo estão detalhadas no [MER](../modelos/dominio/modelo-entidade-relacionamento.md) e no [dicionário](../dicionario-dados.md).

### 3.6 Critérios de aceitação

- **CA01 Preservação:** criar, consultar e alterar os cadastros permitidos; desativar um cadastro sem vínculos e outro com histórico deve manter ambos armazenados. Cancelar uma coleta em preparação, trocar seu modo e desativar uma resposta em rascunho também deve preservar os registros. Desativar resposta enviada deve falhar. Nenhuma operação deve executar exclusão física de dados.
- **CA02 Permissões:** dado um PROF, acessar o ID de avaliação de terceiro deve ser rejeitado; um gestor de outro time também deve ter acesso rejeitado.
- **CA03 Relação de trabalho:** cadastrar A com B e depois B com A deve resultar em um único vínculo; cadastrar A com A deve falhar.
- **CA04 Remanejamento:** publicar C1 com P1 em G1, mover P1 para G2 e montar C2 deve manter P1 em G1 no histórico de C1 e permitir P1 em G2 em C2.
- **CA05 Questionário:** tentar abrir coleta vazia, com grupo vazio ou com parâmetro repetido deve falhar sem alterar o estado.
- **CA06 Reciprocidade:** atribuir o par A e B duas vezes deve deixar exatamente duas avaliações, A sobre B e B sobre A. Uma falha ao criar um sentido deve impedir a criação do outro.
- **CA06A Geração por time:** selecionar um time com A, B e C ativos, sem vínculos individuais de trabalho, deve gerar exatamente A sobre B, B sobre A, A sobre C, C sobre A, B sobre C e C sobre B. Repetir a geração não deve aumentar as seis avaliações. Um quarto integrante inativo não deve entrar nas combinações.
- **CA06B Múltiplos times e limites:** selecionar dois times distintos, com três e dois integrantes elegíveis, deve gerar seis e duas avaliações, totalizando oito, sem combinações entre os times. Selecionar novamente o mesmo time não deve duplicar seu vínculo nem suas avaliações. Um time com menos de dois integrantes elegíveis deve impedir a abertura e informar o motivo.
- **CA06C Preservação e atomicidade:** alterar a composição do time antes da abertura deve atualizar a prévia e exigir confirmação do RH; após a abertura, adicionar, remover ou transferir integrantes não deve alterar as avaliações. Uma falha durante a geração por time deve reverter a abertura e todas as atribuições dessa operação.
- **CA07 Respostas:** com score ESCALA_0_5, aceitar 0 e 5 e rejeitar -1, 6 e 2,5; com ESCALA_0_10, aceitar 0 e 10 e rejeitar 11. Com BOOLEANO, aceitar verdadeiro e falso e rejeitar números e textos. Falso e zero devem permitir envio, enquanto nulo e resposta desativada devem impedir completude. Reativar a resposta deve reutilizar a mesma linha, sem duplicatas.
- **CA08 Envio:** enviar a avaliação completa deve gravar um único envio, impedir alterações posteriores e manter a avaliação inversa independente. Requisições concorrentes não devem produzir dois envios.
- **CA09 Liberação:** com somente A enviado, B não deve visualizar esse conteúdo; com os dois sentidos enviados e coleta encerrada, os resultados devem ser liberados segundo o perfil. Par cancelado não deve entrar na análise.
- **CA10 Análise:** duas respostas numéricas válidas, 2 em ESCALA_0_5 e 10 em ESCALA_0_10, devem gerar 40% e 100%, com média numérica 70%. Duas respostas booleanas válidas, verdadeiro e falso, devem gerar 50% de Sim e 50% de Não, sem alterar a média numérica. Rascunho, resposta desativada e par incompleto não devem alterar os indicadores. Sem respostas válidas do tipo consultado, mostrar “sem dados”.
- **CA11 Histórico:** trocar usuário de time e alterar pergunta e score do catálogo deve manter time, pergunta e score antigos na coleta publicada; a série deve separar versões incompatíveis.
- **CA12 Encerramento:** após o fim, impedir novos envios; ao encerrar, cancelar pendências com motivo, preservar envios e impedir reabertura. Cancelar a coleta deve excluí-la das análises sem apagá-la.
- **CA13 Qualidade:** comprovar os critérios de RNF01 a RNF07 por testes de autorização e concorrência, inspeção de logs, ensaio de carga, uso por teclado e simulação de restauração; registrar ambiente e evidências.

## 4 Pendências e extensões

### 4.1 Decisões pendentes de validação

- **PV01 parcialmente resolvida:** `PROF` significa profissional, confirmado pelo stakeholder na E01. Permanece pendente apenas a possibilidade de múltiplos perfis por conta; a proposta mantém um único valor do ENUM.
- **PV02 resolvida:** `score` é o tipo de avaliação do parâmetro, confirmado pelo stakeholder na E01. Tipos documentados: ESCALA_0_10, ESCALA_0_5 e BOOLEANO. Não representa nota máxima numérica, peso nem nota atribuída.
- **PV03:** confirmar se reciprocidade obriga ambos a responder e se resultados de pares incompletos devem ser liberados. A proposta cria ambos e libera somente pares completos após encerramento.
- **PV04:** aprovar a matriz de acesso a notas, comentários e identidades. A proposta é identificada, com acesso limitado por perfil; não promete anonimato, especialmente em pares de duas pessoas.
- **PV05:** validar com os responsáveis da organização a política de privacidade e suas necessidades jurídicas, considerando a decisão confirmada de preservar dados sem exclusão física.
- **PV06:** confirmar grupo único por parâmetro, relação de trabalho simétrica, um time por usuário e um gestor responsável por time. Estas são decisões propostas de modelagem.
- **PV07:** aprovar limites de texto, uso de valores inteiros nas escalas, metas de desempenho e recuperação. Os tipos de avaliação já foram confirmados.
- **PV08:** confirmar com a disciplina se o núcleo atende à entrega ou se as extensões do PDF devem integrar a versão obrigatória.

### 4.2 Extensões presentes no contexto acadêmico

O enunciado cita feedback chefe-colaborador, por pares e 360°; classificações formal, informal, positivo e construtivo; anonimato; recursos visuais de evolução; planos de ação e metas de desenvolvimento. O núcleo cobre avaliação mútua por pares e análise numérica histórica. As demais modalidades, classificações, visualizações e planejamento de desenvolvimento precisam de requisitos e entidades adicionais antes da implementação.

Entrevistas, questionários, BPMN, protótipos Figma e outros artefatos listados no enunciado também exigem trabalhos próprios. Esta especificação consolida o que foi levantado até aqui e não substitui as demais fontes de elicitação previstas no processo de requisitos.

## 5 Rastreabilidade

- CRUD de usuários e `trabalha_com` — F01 → RF02 e RF04 → Usuario e RelacaoTrabalho → CA01 e CA03.
- CRUD de times — F01 → RF03 → Time → CA01.
- CRUD de grupos e parâmetros — F01 → RF05 e RF06 → GrupoParametro e Parametro → CA01 e CA05.
- Remanejamento — F01 → RF07 e RF09, RN04 e RN05 → Parametro, ColetaGrupo e ColetaParametro → CA04 e CA11.
- Coletas com grupos — F01 → RF08 e RF09 → Coleta, ColetaGrupo e ColetaParametro → CA05.
- Avaliação mútua por pares ou times — F01 → RF08 a RF10 e RF12, RN01 a RN03 e RN05 → Coleta, ColetaTime e Avaliacao → CA06, CA06A a CA06C e CA08.
- CRUD de feedback — F01 → RF11 e RF12, RN06 e RN08 → Feedback e Avaliacao → CA01, CA07 e CA08.
- Histórico e análise individual — F01 → RF14 e RF15, RN09 a RN11 → Avaliacao e Feedback com cópias do questionário → CA09 a CA11.
- Perfis RH, PROF e GESTOR — F01 → RF01 e seção 2.3 → Usuario e Time → CA02.
- Ciclo da coleta — proposta derivada → RF13, RN07 → Coleta e Avaliacao → CA12.
- Segurança e preservação — proposta de suporte e contexto F02 → RF16 e RNF01 a RNF07 → EventoAuditoria e demais entidades → CA11 e CA13.
