# Dicionário de dados e glossário

Este documento tem duas partes: o **glossário** (seção final), que padroniza os termos do domínio conforme o capítulo 7 de Larman, e o **dicionário de dados**, que define os dados do [modelo entidade-relacionamento](modelos/dominio/modelo-entidade-relacionamento.md). Tipos, tamanhos e políticas adicionais são propostas sujeitas às pendências da especificação. Cada item informa o nome técnico, o tipo e as regras principais.

## Convenções gerais

`UUID` é um identificador de 128 bits. `VARCHAR(n)` limita o tamanho em caracteres. `BOOLEAN` admite verdadeiro ou falso. Instantes usam tipo com fuso ou equivalente, persistidos em UTC e exibidos no fuso da organização. `TIMESTAMPTZ` é a notação lógica adotada, sem impor um SGBD.

Todas as entidades, exceto eventos de auditoria, devem ter `criado_em` e `atualizado_em`, ambos `TIMESTAMPTZ` obrigatórios e gerenciados pelo servidor. Relações de trabalho também usam esses campos para registrar ativação e alteração. Campos obrigatórios de texto não admitem conteúdo vazio após remoção de espaços externos.

IDs primários são obrigatórios, únicos e imutáveis. FKs apontam para IDs existentes. Não há exclusão física de nenhuma entidade nem expurgo automático: cadastros, vínculos, cópias em preparação e respostas em rascunho são desativados; coletas e avaliações são canceladas. `ativo` inicia como verdadeiro. Registros inativos continuam disponíveis em consultas históricas autorizadas. Texto livre deve ser tratado como conteúdo, sem execução de HTML ou scripts.

## USUARIO

- `id` — UUID, PK.
- `id_time` — UUID, FK de TIME, opcional durante cadastro; obrigatório com time ativo para novas coletas.
- `nome` — VARCHAR(150), obrigatório.
- `cargo` — VARCHAR(100), obrigatório; não concede permissões.
- `email` — VARCHAR(254), obrigatório, único e normalizado; identificador de conta proposto.
- `role` — ENUM `RH | PROF | GESTOR`, obrigatório e sem padrão automático. PROF significa profissional. Um perfil por conta permanece como proposta.
- `ativo` — BOOLEAN, obrigatório; falso bloqueia autenticação e novas atribuições.
- `trabalha_com` — propriedade derivada dos vínculos ativos em RELACAO_TRABALHO; coleção de usuários, sem coluna física.

## TIME

- `id` — UUID, PK.
- `nome` — VARCHAR(100), obrigatório.
- `setor` — VARCHAR(100), obrigatório; atributo textual nesta versão.
- `id_gestor` — UUID, FK de USUARIO, opcional; quando informado, usuário ativo com role GESTOR.
- `ativo` — BOOLEAN, obrigatório; falso impede novas participações de seus membros em coletas, preservando o histórico.

Nomes de times e nomes de usuários não são identificadores únicos. Seletores devem exibir contexto suficiente para distinguir homônimos.

## RELACAO_TRABALHO

- `id_usuario_a` — UUID, PK composta e FK de USUARIO.
- `id_usuario_b` — UUID, PK composta e FK de USUARIO.
- `ativo` — BOOLEAN, obrigatório; desvincular marca falso.

O par deve estar em ordem canônica, com A menor que B. O relacionamento é simétrico e não admite autorrelação. Reativar não cria outra linha para o mesmo par.

O vínculo é exigido para pares selecionados manualmente. Na seleção por times, a geração combina todos os integrantes elegíveis de cada time independentemente desta tabela e não cria vínculos individuais automaticamente.

## GRUPO_PARAM

- `id` — UUID, PK.
- `titulo` — VARCHAR(120), obrigatório.
- `descricao` — VARCHAR(1.000), opcional; corresponde ao campo `descrição` informado pelo usuário.
- `ativo` — BOOLEAN, obrigatório.
- `list_id_params` — coleção derivada de PARAM pelo campo `id_grupo_param`; não é coluna física. A consulta pode incluir itens inativos quando o filtro administrativo solicitar.

## PARAM

- `id` — UUID, PK.
- `id_grupo_param` — UUID, FK de GRUPO_PARAM, obrigatório; aponta para um grupo ativo na criação e no remanejamento.
- `pergunta` — VARCHAR(1.000), obrigatório.
- `score` — ENUM `ESCALA_0_10 | ESCALA_0_5 | BOOLEANO`, obrigatório e sem padrão automático; define o tipo de avaliação, não uma nota nem um peso. ESCALA_0_10 admite inteiros de 0 a 10, ESCALA_0_5 admite inteiros de 0 a 5 e BOOLEANO admite verdadeiro ou falso, exibidos como Sim ou Não.
- `ativo` — BOOLEAN, obrigatório.

Alterar pergunta ou score modifica o catálogo para futuras configurações; as cópias publicadas não são atualizadas.

## COLETA

- `id` — UUID, PK.
- `id_criador` — UUID, FK de USUARIO, obrigatório; criador deve ter role RH no momento da criação.
- `titulo` — VARCHAR(150), obrigatório.
- `modo_selecao` — ENUM `PARES | TIMES`, obrigatório e escolhido pelo RH, sem padrão automático. PARES permite selecionar pares individuais; TIMES permite selecionar um ou mais times e gerar todas as combinações internas nos dois sentidos.
- `inicio_em` — TIMESTAMPTZ, obrigatório; início inclusivo para responder.
- `fim_em` — TIMESTAMPTZ, obrigatório e posterior ao início; fim exclusivo para responder.
- `status` — ENUM `PREPARACAO | ABERTA | ENCERRADA | CANCELADA`, obrigatório; inicia em PREPARACAO.
- `encerrada_em` — TIMESTAMPTZ, opcional; obrigatório se ENCERRADA e ausente nos demais estados.
- `cancelada_em` — TIMESTAMPTZ, opcional; obrigatório se CANCELADA e ausente nos demais estados.
- `motivo_cancelamento` — VARCHAR(500), opcional; obrigatório se CANCELADA.

Fim do período bloqueia respostas, mas não muda sozinho o estado nesta proposta. Encerramento administrativo define a data utilizada nos filtros históricos. Abrir antes do início permite preparar atribuições, mas o preenchimento só é liberado a partir do início.

Modo e seleções podem ser alterados somente durante a preparação. Trocar o modo desativa os vínculos de seleção anteriores em transação, sem apagar registros. As avaliações são criadas somente na abertura, que congela o modo e o conjunto final de pares; mudanças posteriores no time não recalculam participantes. Cancelar a coleta preserva seus vínculos e cópias, inclusive na preparação.

## COLETA_PAR

- `id_coleta` — UUID, PK composta e FK de COLETA, obrigatório.
- `id_usuario_a` — UUID, PK composta e FK de USUARIO, obrigatório.
- `id_usuario_b` — UUID, PK composta e FK de USUARIO, obrigatório, com A menor que B pela ordenação canônica.
- `ativo` — BOOLEAN, obrigatório; indica se o par integra a seleção manual vigente.

Registra pares selecionados na preparação, sem criar avaliações antecipadamente. Na abertura do modo PARES, deve existir pelo menos um vínculo ativo com usuários, times e relação de trabalho válidos. No modo TIMES, todos os vínculos desta tabela devem estar inativos. Desativar preserva a linha; reativar reutiliza a mesma PK. Após abertura, as seleções são imutáveis. Aplicam-se os campos comuns `criado_em` e `atualizado_em`.

## COLETA_TIME

- `id_coleta` — UUID, PK composta e FK de COLETA, obrigatório.
- `id_time` — UUID, PK composta e FK de TIME, obrigatório; o time deve estar ativo na seleção e na abertura.
- `ativo` — BOOLEAN, obrigatório; indica se o time integra a seleção vigente.

Registra os times escolhidos no modo TIMES, sem lista de IDs em uma coluna. A combinação coleta e time é única. Não pode haver vínculos ativos no modo PARES e deve haver ao menos um vínculo ativo na abertura do modo TIMES. Vínculos desativados permanecem armazenados em qualquer modo; reativar reutiliza a mesma linha. Aplicam-se os campos comuns `criado_em` e `atualizado_em`.

Cada time selecionado deve possuir pelo menos dois usuários ativos na abertura. Para `n` integrantes elegíveis, são gerados `n × (n − 1) / 2` pares e `n × (n − 1)` avaliações, sem autoavaliações nem combinações entre times distintos. A prévia deve refletir os integrantes atuais e ser confirmada novamente se mudar antes da abertura. A geração não depende de RELACAO_TRABALHO.

Os participantes efetivos ficam registrados nas avaliações e seus campos históricos. COLETA_TIME preserva a seleção do time, mas não implica inclusão automática de futuros integrantes na coleta aberta.

## COLETA_GRUPO

- `id` — UUID, PK.
- `id_coleta` — UUID, FK de COLETA, obrigatório.
- `id_grupo_origem` — UUID, FK de GRUPO_PARAM, obrigatório; rastreia a origem do grupo.
- `titulo_snapshot` — VARCHAR(120), obrigatório; cópia do título publicada.
- `descricao_snapshot` — VARCHAR(1.000), opcional; cópia da descrição publicada.
- `ordem` — INTEGER positivo, obrigatório; único entre os grupos ativos da coleta.
- `ativo` — BOOLEAN, obrigatório; permite retirar o grupo da preparação sem apagá-lo. Sua desativação também desativa as perguntas selecionadas daquele grupo.

O mesmo grupo de origem aparece no máximo uma vez por coleta. Reativação reutiliza a linha existente. As cópias podem ser atualizadas explicitamente durante a preparação, permanecendo imutáveis, inclusive quanto à atividade, após a abertura. Apenas grupos ativos são publicados.

## COLETA_PARAM

- `id` — UUID, PK; identidade da pergunta dentro de uma coleta.
- `id_coleta` — UUID, FK de COLETA, obrigatório e consistente com o grupo da coleta.
- `id_coleta_grupo` — UUID, FK de COLETA_GRUPO, obrigatório; referencia conjuntamente ID e coleta conforme o MER.
- `id_param_origem` — UUID, FK de PARAM, obrigatório.
- `pergunta_snapshot` — VARCHAR(1.000), obrigatório; texto copiado na publicação.
- `score_snapshot` — ENUM `ESCALA_0_10 | ESCALA_0_5 | BOOLEANO`, obrigatório; cópia do tipo de avaliação usada na validação e nas análises históricas.
- `ordem` — INTEGER positivo, obrigatório e único entre as perguntas ativas dentro do grupo da coleta.
- `ativo` — BOOLEAN, obrigatório; permite retirar a pergunta da preparação sem apagar a cópia. Pergunta ativa exige grupo da coleta ativo.

Um parâmetro de origem aparece no máximo uma vez por coleta. Reativação reutiliza a linha existente. Após a abertura, grupo, texto, tipo de avaliação, ordem e atividade são imutáveis. Apenas perguntas ativas de grupos ativos compõem o questionário publicado.

## AVALIACAO

- `id` — UUID, PK.
- `id_coleta` — UUID, FK de COLETA, obrigatório.
- `id_avaliador` — UUID, FK de USUARIO, obrigatório; autor do questionário.
- `id_receptor` — UUID, FK de USUARIO, obrigatório e diferente do avaliador.
- `id_time_avaliador_snapshot` — UUID, FK de TIME; obrigatório na abertura.
- `id_time_receptor_snapshot` — UUID, FK de TIME; obrigatório na abertura.
- `nome_avaliador_snapshot` e `nome_receptor_snapshot` — VARCHAR(150) cada, obrigatórios na abertura.
- `cargo_avaliador_snapshot` e `cargo_receptor_snapshot` — VARCHAR(100) cada, obrigatórios na abertura.
- `nome_time_avaliador_snapshot` e `nome_time_receptor_snapshot` — VARCHAR(100) cada, obrigatórios na abertura.
- `setor_avaliador_snapshot` e `setor_receptor_snapshot` — VARCHAR(100) cada, obrigatórios na abertura.
- `status` — ENUM `RASCUNHO | ENVIADA | CANCELADA`, obrigatório; inicia em RASCUNHO, mesmo quando ainda não há resposta.
- `enviada_em` — TIMESTAMPTZ, opcional; obrigatório se ENVIADA e ausente nos demais estados.
- `cancelada_em` — TIMESTAMPTZ, opcional; obrigatório se CANCELADA e ausente nos demais estados.
- `motivo_cancelamento` — VARCHAR(500), opcional; obrigatório se CANCELADA.

As avaliações são criadas na abertura, com todos os campos históricos preenchidos e congelados. A combinação coleta, avaliador e receptor é única, tanto para pares selecionados manualmente quanto para os gerados por times. No modo TIMES, avaliador e receptor devem pertencer ao mesmo time selecionado por vínculo ativo no instante da abertura. O par inverso é encontrado pela mesma coleta e IDs trocados; não é necessário um `id_feedback_inverso` em cada resposta.

## FEEDBACK

- `id` — UUID, PK.
- `id_coleta` — UUID, obrigatório; participa das FKs compostas para garantir que avaliação e pergunta sejam da mesma coleta.
- `id_avaliacao` — UUID, FK de AVALIACAO, obrigatório.
- `id_coleta_param` — UUID, FK de COLETA_PARAM, obrigatório.
- `valor` — escalar JSON tipado, obrigatório quando a linha existe: inteiro de 0 a 10 para score_snapshot ESCALA_0_10; inteiro de 0 a 5 para ESCALA_0_5; booleano nativo verdadeiro/falso para BOOLEANO. Rejeitar nulo, strings, objetos, arrays, decimais nas escalas e números para perguntas booleanas. Zero e falso são respostas válidas. Pergunta nunca respondida não possui linha de feedback; resposta retirada do rascunho mantém a linha inativa.
- `comentario` — VARCHAR(2.000), opcional; espaços isolados podem ser normalizados para nulo.
- `ativo` — BOOLEAN, obrigatório; falso retira a resposta do preenchimento atual e dos cálculos sem apagar seu valor e comentário. Desativação e reativação são permitidas apenas em rascunho, no período autorizado.
- `id_param` — derivado de COLETA_PARAM.id_param_origem, disponível em consulta.
- `id_avaliador` e `id_receptor` — derivados da avaliação, disponíveis em consulta.
- `status` — derivado de AVALIACAO.status, disponível em consulta.

Uma avaliação só admite uma linha de feedback por pergunta publicada, incluindo linhas inativas. Atualização, desativação e reativação são permitidas apenas ao autor, em rascunho e dentro do período da coleta aberta. Reativar reutiliza o mesmo ID. O envio exige uma resposta ativa para cada pergunta ativa e valida o conjunto inteiro antes de torná-lo imutável; nenhuma linha é excluída fisicamente.

## EVENTO_AUDITORIA

- `id` — UUID, PK.
- `id_ator` — UUID, FK de USUARIO, opcional para operação automática; quando preenchido, preserva o vínculo de autoria.
- `operacao` — VARCHAR(50), obrigatório; valores propostos: `CRIAR`, `ALTERAR`, `DESATIVAR`, `REATIVAR`, `REMANEJAR`, `ATRIBUIR`, `ABRIR`, `ENVIAR`, `ENCERRAR` e `CANCELAR`. Não existe operação de exclusão física.
- `entidade` — VARCHAR(50), obrigatório; nome do tipo de entidade afetada.
- `id_alvo` — UUID, opcional quando o alvo tem PK composta; identifica alvos com chave simples.
- `chave_alvo` — objeto JSON obrigatório com os componentes da PK do alvo; permite identificar também COLETA_PAR, COLETA_TIME e RELACAO_TRABALHO. Os registros continuam armazenados após desativação ou cancelamento.
- `ocorrido_em` — TIMESTAMPTZ, obrigatório, gerenciado pelo servidor.
- `metadados` — objeto JSON opcional com IDs de configuração alterados, estado anterior e posterior e motivo administrativo quando necessário. Não incluir senha, token ou comentário de feedback.

Os eventos não possuem `atualizado_em`, pois são registros de inclusão imutáveis. Acesso é administrativo; não há exclusão física ou expurgo automático dos eventos.

## Indicadores derivados

- **Resposta válida:** está ativa e pertence a uma avaliação ENVIADA, com inversa ENVIADA, em coleta ENCERRADA. Respeita os filtros e as permissões de consulta.
- **Nota normalizada numérica:** `100 × valor / limite_superior`, usando 10 para ESCALA_0_10 e 5 para ESCALA_0_5 conforme o score_snapshot. Score é um ENUM e nunca um divisor numérico direto.
- **Média numérica do recorte:** soma das notas normalizadas válidas dividida pelo número de respostas numéricas válidas; sem respostas numéricas, não há média. Booleanos não entram nesse cálculo.
- **Distribuição booleana:** contagem de verdadeiro e falso e respectivos percentuais sobre as respostas booleanas válidas. Zero respostas booleanas produz “sem dados”; falso conta como resposta, não como ausência. Os rótulos Sim e Não não pressupõem julgamento positivo ou negativo.
- **Quantidade de avaliações:** contagem distinta de avaliações válidas, separada da contagem de respostas.
- **Conclusão da coleta:** avaliações ENVIADAS divididas pelas não CANCELADAS, multiplicadas por 100; sem denominador, exibir “sem avaliações elegíveis”. É uma medida de preenchimento, distinta da elegibilidade para análise.
- **Série comparável:** mesmo parâmetro de origem, mesmo texto e mesmo tipo de avaliação da cópia; grupos só são comparados diretamente quando a composição também é equivalente. Grupos mistos exibem médias numéricas e distribuições booleanas separadas.

O cálculo utiliza valores históricos, sem arredondar as parcelas. O resultado exibido é arredondado para duas casas decimais.

## Unidades, itens não aplicáveis e pendências

- **Unidades:** tamanhos em caracteres (`VARCHAR(n)`); instantes em UTC (`TIMESTAMPTZ`); notas sem unidade física, normalizadas em percentual (0 a 100) apenas nos indicadores; tempos de desempenho e recuperação, em segundos e horas, estão na [especificação suplementar](requisitos/especificacao-suplementar.md).
- **Não aplicável:** unidade de medida para IDs, textos, booleanos e ENUMs; tamanho para `BOOLEAN`, `UUID`, `TIMESTAMPTZ` e `INTEGER`.
- **Pendente:** limites de texto e uso de inteiros nas escalas (PV07); múltiplos perfis por conta (PV01); dados de anonimato, planos de desenvolvimento, classificação de feedback e 360° ainda não têm atributos, pois dependem de PV08 e do conflito C02; campos de retenção e anonimização dependem do conflito C01.

## Glossário

Termos em ordem alfabética. A coluna **Representação** indica onde o termo aparece no modelo de dados.

| Termo | Definição | Representação | Sinônimos e termos a evitar |
| --- | --- | --- | --- |
| Abertura | Transição da coleta de PREPARACAO para ABERTA, que publica o questionário, congela os participantes e gera as avaliações. | `COLETA.status` | Evitar "publicar" como sinônimo da abertura inteira; publicar refere-se só ao questionário. |
| Análise individual | Leitura dos resultados recebidos por uma pessoa, calculada apenas sobre respostas válidas e comparáveis. | Consulta derivada | Relatório individual. |
| Auditoria | Registro imutável de quem fez qual operação, sobre qual registro e quando. | EVENTO_AUDITORIA | Log de auditoria; não confundir com log técnico. |
| Avaliação | Preenchimento do questionário de uma coleta por um avaliador sobre um receptor, em um sentido. | AVALIACAO | Evitar "feedback" para o questionário inteiro. |
| Avaliação 360° | Avaliação de uma pessoa por gestor, colegas, subordinados e por ela mesma. Extensão pendente (RF17). | Não modelada | — |
| Avaliador | Papel de quem responde a uma avaliação. Não é perfil de acesso. | `AVALIACAO.id_avaliador` | Autor. |
| Cancelamento | Encerramento de uma coleta ou avaliação sem efeito para análise, preservando os dados. | Status CANCELADA | Evitar "excluir". |
| Coleta | Campanha de avaliação com título, período, questionário, modo de seleção e estado. | COLETA | Ciclo, campanha. |
| Comentário | Texto livre opcional associado a uma resposta. | `FEEDBACK.comentario` | — |
| Conclusão da coleta | Percentual de avaliações enviadas sobre as não canceladas. | Indicador derivado | Taxa de resposta. |
| Desativação | Retirada lógica de um registro do uso operacional, sem excluí-lo. | Atributo `ativo` | Evitar "excluir" ou "apagar". |
| Encerramento | Transição da coleta de ABERTA para ENCERRADA, que cancela pendências e libera os resultados elegíveis. | `COLETA.encerrada_em` | Fechamento. |
| Feedback | Resposta a uma pergunta de uma avaliação: valor compatível com o tipo e comentário opcional. | FEEDBACK | Resposta. No uso comum, "feedback" também designa o processo como um todo. |
| Gestor | Perfil de acesso de quem acompanha os times sob sua responsabilidade. | `role = GESTOR`, `TIME.id_gestor` | Líder, chefe. |
| Grupo de parâmetros | Conjunto de perguntas de um mesmo tema, como Comunicação. | GRUPO_PARAM | Competência, dimensão. |
| Histórico | Conjunto de avaliações e resultados preservados ao longo das coletas. | AVALIACAO, FEEDBACK e cópias | — |
| Modo de seleção | Forma de definir participantes: PARES (escolha manual) ou TIMES (todos os integrantes de cada time). | `COLETA.modo_selecao` | — |
| Nota normalizada | Valor numérico convertido para a escala de 0 a 100: `100 × valor / limite superior`. | Indicador derivado | — |
| Par | Dois usuários distintos que se avaliam mutuamente em uma coleta. | COLETA_PAR, pares de AVALIACAO | Dupla. |
| Parâmetro | Pergunta de avaliação com tipo definido em `score`. | PARAM | Pergunta, critério. |
| Perfil | Valor que define as permissões de acesso: RH, GESTOR ou PROF. | `USUARIO.role` | Papel de acesso. Não confundir com cargo. |
| Plano de desenvolvimento individual (PDI) | Conjunto de metas e ações de melhoria de uma pessoa. Extensão pendente (RF18). | Não modelado | Plano de ação. |
| Profissional (PROF) | Perfil do participante comum. | `role = PROF` | Colaborador. |
| Questionário da coleta | Cópia imutável dos grupos e perguntas selecionados para uma coleta. | COLETA_GRUPO, COLETA_PARAM | Formulário. |
| Receptor | Papel de quem é avaliado em uma avaliação. Não é perfil de acesso. | `AVALIACAO.id_receptor` | Avaliado. |
| Reciprocidade | Regra de que cada par gera duas avaliações independentes, uma em cada sentido. | RN01 | Avaliação mútua. |
| Relação de trabalho | Vínculo simétrico entre dois usuários que trabalham juntos, exigido no modo PARES. | RELACAO_TRABALHO | `trabalha_com`. |
| Remanejamento | Transferência de um parâmetro para outro grupo no catálogo, sem afetar coletas publicadas. | `PARAM.id_grupo_param` | Mover pergunta. |
| Rascunho | Estado da avaliação ainda editável pelo avaliador. | `AVALIACAO.status = RASCUNHO` | — |
| Resposta válida | Resposta ativa de avaliação enviada, com a inversa enviada, em coleta encerrada. | Indicador derivado | — |
| RH | Perfil de quem administra cadastros, catálogo e coletas. | `role = RH` | Administrador. |
| Score | Tipo de avaliação de um parâmetro: ESCALA_0_10, ESCALA_0_5 ou BOOLEANO. Não é nota nem peso. | `PARAM.score`, `COLETA_PARAM.score_snapshot` | Tipo de avaliação. Evitar "pontuação". |
| Snapshot (cópia) | Valor copiado no momento da abertura para preservar o contexto histórico. | Campos `*_snapshot` | Cópia histórica. |
| Time | Unidade organizacional com nome, setor e gestor responsável. | TIME | Equipe. |
| Usuário | Pessoa cadastrada no sistema, com nome, cargo, time e perfil. | USUARIO | Conta. |
