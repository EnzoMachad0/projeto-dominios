# Síntese dos requisitos das entrevistas

| Campo | Informação |
| --- | --- |
| Elaboração | Heitor Barbosa Souza |
| Versão | 0.1 — 15 de novembro de 2026 |
| Situação | Preliminar, aguardando conferência com as transcrições |
| Acompanhamento | Issue #6; transcrições na #41; consolidação dos requisitos na #40 |

## 1. Objetivo e fontes

Esta síntese reúne as necessidades, os requisitos e as regras de negócio das duas entrevistas de levantamento de requisitos, E01 e E02, com base nas entrevistas e nas anotações elaboradas a partir delas. As anotações da primeira entrevista orientam o entendimento das modalidades, da estrutura do feedback e do acompanhamento por planos de ação.

As transcrições de [E01](entrevistas/E01-transcricao.md) e [E02](entrevistas/E02-transcricao.md) ainda são aguardadas. A síntese será conferida quando forem recebidas, complementando as referências às perguntas e respostas. As formulações são uma interpretação dos registros disponíveis, não uma transcrição literal das falas.

| Fonte | Conteúdo utilizado |
| --- | --- |
| E01 e suas anotações | Feedback baseado em fatos, classificações, modalidades, participação do gestor e do RH, planos de ação e preservação dos feedbacks |
| E01 e E02 e as anotações elaboradas a partir delas | Organização de coletas, questionários, perfis, respostas, histórico e acompanhamento dos resultados |

As correspondências com o projeto atual seguem a [lista geral](../requisitos/lista-geral.md), a [especificação de requisitos](../requisitos/especificacao-requisitos.md), a [especificação suplementar](../requisitos/especificacao-suplementar.md) e o [dicionário de dados](../dicionario-dados.md).

### Convenções

- `SIN-RFxx`, `SIN-RNxx` e `SIN-RNFxx` são identificadores locais desta síntese, separados dos IDs oficiais RF, RN e RNF.
- Os requisitos sintetizados são candidatos à consolidação na #40 e à validação na #25. A correspondência com um requisito existente pode ser parcial e não indica que todos os detalhes já estão especificados ou modelados.
- As regras operacionais inferidas para detalhar participantes, permissões e acompanhamento são identificadas como propostas. Não representam confirmações literais dos entrevistados.

## 2. Entendimento do sistema e do processo

### 2.1. Finalidade e escopo

O sistema deve documentar a comunicação sobre desempenho a partir de fatos, seus impactos e oportunidades de desenvolvimento. A primeira versão contempla feedback entre chefe e colaborador, entre pares, avaliação 360° e autoavaliação, além das classificações formal/informal e positivo/construtivo, planos de ação e acompanhamento.

Formalidade e finalidade são dimensões distintas: um feedback pode ser formal ou informal e ter caráter positivo ou construtivo. O positivo registra o comportamento e seus benefícios para o colaborador, a liderança, o time ou a organização. O construtivo contextualiza os fatos, reconhece aspectos positivos e promove reflexão sobre o que pode melhorar.

### 2.2. Registro e questionários

O feedback é um registro com fato motivador, impactos, tipo, data, emissor, receptor e conteúdo. Quando fizer parte de uma avaliação estruturada, pode incluir um questionário de competências com notas, respostas booleanas e comentários. As respostas complementam o registro do feedback; o questionário é opcional conforme a modalidade e o objetivo da avaliação.

O feedback informal pode ser registrado a qualquer momento, motivado por um evento, sem exigir abertura de coleta. Essa forma de operação é proposta a partir da caracterização do feedback informal nas anotações. Deve preservar a identificação do emissor, do receptor e do contexto, respeitando as permissões de acesso.

### 2.3. Perfis, abertura e participantes

RH e gestor podem criar e abrir avaliações. O gestor atua nos times sob sua responsabilidade; o RH pode organizar avaliações em toda a organização. O profissional participa como avaliador, receptor e autor de sua autoavaliação.

Na avaliação 360°, o colaborador recebe avaliações do gestor, de colegas e de subordinados, quando esses vínculos existirem, além de realizar sua autoavaliação. Como detalhamento proposto, o responsável pela avaliação — gestor ou RH — seleciona o colaborador avaliado e os participantes dentro do seu escopo, considerando vínculos de gestão e de trabalho. A participação dos colaboradores da equipe é organizada segundo seus papéis em relação ao avaliado, sem presumir que todos na organização avaliam todas as pessoas.

Coletas por pares ou times utilizam questionários e atribuições entre os participantes elegíveis. Nas coletas recíprocas, cada par gera duas avaliações independentes. No 360°, as atribuições seguem os papéis dos participantes, sem exigir reciprocidade entre todos. A autoavaliação admite emissor e receptor como a mesma pessoa, inclusive como parte de um 360°. A abertura preserva participantes e questionário para manter o histórico.

### 2.4. Plano de ação e acompanhamento

O desenvolvimento segue o ciclo **feedback inicial → plano de ação → acompanhamento → novo feedback**. O primeiro feedback identifica os fatos e o que precisa melhorar. O plano estabelece metas, ações, responsáveis pela execução, prazos e pontos de verificação. O acompanhamento registra o progresso e os indicadores observáveis; o novo feedback avalia os resultados e pode gerar ajustes no plano.

Assim, o plano sucede o feedback que o motivou e antecede o feedback que avalia seus resultados. Sua criação é opcional quando não houver ação de desenvolvimento acordada, inclusive em feedbacks positivos ou informais.

Como distribuição de responsabilidades proposta, o gestor cria e acompanha os planos das pessoas dos times sob sua responsabilidade, e o RH coordena e acompanha os planos no âmbito da organização. O colaborador participa da definição das ações e executa as atividades que lhe forem atribuídas. Essa participação não implica permissão administrativa sobre planos de terceiros.

### 2.5. Necessidades atendidas

| Necessidade | Resposta esperada do sistema |
| --- | --- |
| Documentar o desempenho com contexto | Registrar fatos, impactos, participantes e conteúdo do feedback |
| Contemplar diferentes perspectivas e situações | Oferecer feedback de liderança, pares, 360°, autoavaliação e registro informal |
| Orientar o desenvolvimento | Relacionar feedbacks a metas, ações e verificações |
| Acompanhar os resultados | Consultar histórico, indicadores e evolução dos planos |
| Preservar os registros | Utilizar desativação e cancelamento no uso operacional, sem apagar o histórico |

A descrição de dores concretas e do processo atual da organização será complementada com as transcrições. As necessidades acima não são apresentadas como relatos de incidentes específicos.

## 3. Requisitos funcionais sintetizados

| ID local | Requisito | Origem | Correspondência para consolidação na #40 |
| --- | --- | --- | --- |
| SIN-RF01 | Registrar o fato motivador, os impactos, a classificação, a data, o emissor, o receptor e o conteúdo do feedback, podendo associar um questionário. | E01 e anotações | Detalhar o registro contextual e sua relação com as respostas de RF11 e RF12 |
| SIN-RF02 | Classificar o feedback como positivo ou construtivo. | E01 e anotações | RF19 |
| SIN-RF03 | Classificar o feedback como formal ou informal, independentemente do caráter positivo ou construtivo. | E01 e anotações | RF19 |
| SIN-RF04 | Permitir feedback entre chefe e colaborador, entre pares, avaliação 360° e autoavaliação na primeira versão. | Entrevistas e anotações | RF10, RF17 e detalhamento das modalidades |
| SIN-RF05 | Permitir que RH e gestor criem e abram avaliações, com atuação organizacional para o RH e limitada aos times sob responsabilidade para o gestor. | E01 e anotações; detalhamento de permissões proposto | RF08 e RF17; ampliar as permissões de configuração |
| SIN-RF06 | Definir participantes do 360° conforme os papéis de gestor, colegas, subordinados e avaliado, selecionados pelo responsável dentro do escopo autorizado. | Entrevistas e anotações; seleção proposta | RF17; detalhar os vínculos e a seleção de participantes |
| SIN-RF07 | Apoiar o registro do comportamento positivo e dos benefícios para a liderança, o time e a organização. | E01 e anotações | Conteúdo de SIN-RF01 e classificação de RF19 |
| SIN-RF08 | Apoiar feedback construtivo com reconhecimento de aspectos positivos, apresentação dos fatos e reflexão sobre como melhorar. | E01 e anotações | Conteúdo de SIN-RF01 e classificação de RF19 |
| SIN-RF09 | Criar planos de ação vinculados ao feedback inicial, com metas, ações, responsáveis, prazos e pontos de verificação; permitir sua criação e acompanhamento pelo gestor e pelo RH em seus respectivos escopos. | E01 e anotações; responsabilidades propostas | RF18 |
| SIN-RF10 | Registrar o progresso das ações e suas verificações, relacionando o feedback posterior aos resultados e permitindo ajustes no plano. | E01 e anotações; ciclo de acompanhamento proposto | RF18, com vínculo ao histórico de RF14 |
| SIN-RF11 | Registrar feedback informal motivado por um evento sem exigir a abertura de uma coleta. | E01 e anotações; operação proposta | RF20 |
| SIN-RF12 | Autenticar usuários e restringir operações por perfil e escopo; manter usuários, times e relações de trabalho. | Entrevistas e anotações | RF01 a RF04 |
| SIN-RF13 | Manter grupos e perguntas, definir tipos de resposta e remanejar perguntas sem alterar questionários já publicados. | Entrevistas e anotações | RF05 a RF07 |
| SIN-RF14 | Configurar coletas recíprocas com seleção por pares ou times e avaliações 360° com participantes por papel, preservando participantes e questionários e gerando as atribuições correspondentes. | Entrevistas e anotações; composição das modalidades proposta | RF08 a RF10 e RF17 |
| SIN-RF15 | Salvar respostas em rascunho e enviar avaliações completas, preservando independência e imutabilidade após o envio. | Entrevistas e anotações | RF11 e RF12 |
| SIN-RF16 | Acompanhar avaliações e encerrar ou cancelar coletas, preservando os registros. | Entrevistas e anotações | RF13 |
| SIN-RF17 | Consultar histórico individual e indicadores numéricos/booleanos, comparando resultados equivalentes e acompanhando a evolução do colaborador. | Entrevistas e anotações | RF14, RF15, RN10 e RN11 |
| SIN-RF18 | Registrar eventos administrativos e transições sem copiar o conteúdo dos comentários para a auditoria. | Proposta de suporte ao funcionamento do sistema | RF16 |

## 4. Regras de negócio sintetizadas

| ID local | Regra | Origem | Correspondência para consolidação na #40 |
| --- | --- | --- | --- |
| SIN-RN01 | Preservar os dados no uso operacional, usando desativação de cadastros e cancelamento de coletas ou avaliações, sem exclusão física. | E01 e anotações para feedbacks; abrangência operacional da RN12 existente | RN12; a política de retenção continua vinculada a PV05/C01 |
| SIN-RN02 | O feedback deve se apoiar em fatos e impactos registrados, sem pressupor verificação automática da veracidade pelo sistema. | E01 e anotações | Estrutura de SIN-RF01 |
| SIN-RN03 | O plano sucede o feedback inicial e antecede o feedback de avaliação dos resultados; é opcional quando não houver ação de desenvolvimento acordada. | E01 e anotações; ciclo de acompanhamento proposto | RF18 |
| SIN-RN04 | Avaliações entre pessoas distintas não admitem atribuições duplicadas; pares recíprocos geram dois sentidos independentes. A autoavaliação é tratada separadamente, com emissor igual ao receptor, e o 360° gera atribuições conforme os papéis selecionados. | Entrevistas e anotações; detalhamento por modalidade proposto | RN01 a RN03, RF10 e RF17 |
| SIN-RN05 | A abertura preserva o questionário e os participantes; os envios são imutáveis. No modo de pares recíprocos, a liberação segue o par completo e a coleta encerrada. Essa condição não é aplicada automaticamente a feedback informal, autoavaliação ou 360°; o acesso deve ser definido por modalidade. | Entrevistas e anotações; separação das modalidades proposta | RN04 a RN09; detalhar o acesso por modalidade na #40 |
| SIN-RN06 | Os indicadores separam escalas numéricas de respostas booleanas e comparam versões equivalentes de perguntas e tipos de resposta. | Proposta de cálculo já registrada no projeto | RN10 e RN11 |
| SIN-RN07 | O gestor administra avaliações e planos dos times sob sua responsabilidade; o RH atua no âmbito organizacional. Seleção de participantes e consulta de resultados devem respeitar o escopo autorizado. | Detalhamento operacional proposto | RF01, RF08, RF17, RF18 e política de acesso |

## 5. Requisitos não funcionais relacionados

Os requisitos abaixo são propostas técnicas já registradas no projeto e relacionadas ao funcionamento descrito nesta síntese. Não são apresentados como metas numéricas confirmadas nas entrevistas. O detalhamento e a validação permanecem na especificação suplementar.

| ID local | Requisito proposto | Correspondência atual |
| --- | --- | --- |
| SIN-RNF01 | Verificar autenticação e autorização no servidor e restringir o acesso ao conteúdo e aos logs. | RNF01 e RNF07 |
| SIN-RNF02 | Garantir atomicidade e impedir duplicações sob concorrência nas operações críticas. | RNF02 |
| SIN-RNF03 | Oferecer uso por teclado, mensagens textuais e formulários adequados a telas de computador e celular. | RNF03 |
| SIN-RNF04 | Definir metas verificáveis de desempenho, backup e restauração. Os valores atuais da especificação suplementar permanecem propostas sujeitas à validação. | RNF04, RNF05 e PV07 |
| SIN-RNF05 | Proteger a auditoria contra alteração e preservar a identificação das operações administrativas. | RNF06 |

## 6. Encaminhamento para os demais artefatos

A primeira versão deve contemplar as modalidades e o acompanhamento descritos nesta síntese. Na #40, a lista geral, a visão, a especificação, os modelos, o dicionário e a rastreabilidade devem incorporar o registro contextual do feedback, o questionário opcional, as permissões de RH e gestor, o 360°, a autoavaliação, o feedback informal e os planos de ação.

Os IDs existentes serão preservados sempre que representarem o mesmo requisito. O detalhamento deve distinguir modalidades e seus respectivos participantes, regras de geração e permissões de acesso. Os requisitos locais desta síntese não alteram automaticamente os demais documentos.

## 7. Conferência e validação

| Próximo passo | Issue |
| --- | --- |
| Receber, revisar e disponibilizar as duas transcrições e os dados de identificação das coletas | #41 |
| Conferir a síntese com as transcrições, complementar omissões e vincular os requisitos às perguntas e respostas efetivas | #6 |
| Incorporar os requisitos e atualizar prioridades, vínculos e demais artefatos | #40 |
| Validar interpretações e propostas operacionais e técnicas com o stakeholder | #25 |

Quando as transcrições chegarem, acrescentar referências como `E01-Rxx` e `E02-Rxx` somente onde houver respostas reais e registrar a validação das propostas. A síntese não substitui os entregáveis de transcrição.
