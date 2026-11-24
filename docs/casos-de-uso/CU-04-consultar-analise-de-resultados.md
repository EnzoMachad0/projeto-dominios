# CU-04 — Consultar análise de resultados

| Campo | Informação |
| --- | --- |
| Autoria | Enzo de Oliveira Machado |
| Versão | 0.2 — 23 de novembro de 2026 |
| Formato | Completo, estilo essencial (Larman, cap. 6) |
| Situação | Validado (E01, E02) |

## Escopo

Sistema de gestão de competências e feedback. Nesta versão, a consulta cobre as coletas recíprocas por pares ou times já descritas na especificação. Com a consolidação da issue #40, os resultados do 360°, da autoavaliação e dos feedbacks informais seguem a RN15 da especificação; seu detalhamento neste caso de uso é a próxima extensão.

## Nível

Objetivo do usuário (*user goal*): consultar o próprio histórico e compreender os resultados e sua evolução em uma sessão de trabalho. A consulta de resultados de um time pelo gestor e a liberação dos resultados ao avaliado são variantes do mesmo objetivo.

## Ator principal

**Participante**, de qualquer perfil (RH, Gestor ou Profissional), ao consultar seus próprios envios e resultados recebidos. **Gestor** também pode solicitar resultados dos times sob sua responsabilidade, e liberá-los aos avaliados; o RH faz o mesmo em toda a organização (RN09, RN14).

## Partes interessadas e interesses

| Parte interessada | Interesse |
| --- | --- |
| Participante | Rever o que enviou, conhecer os resultados recebidos já liberados e acompanhar sua evolução sem exposição antecipada. |
| Avaliador | Preservar a independência das respostas e a confidencialidade de seus rascunhos. |
| Gestor | Acompanhar resultados dos times sob sua responsabilidade com indicadores corretos e sem acesso indevido. |
| RH | Consultar análises dentro da política aprovada e identificar ausência de dados sem interpretar lacunas como notas baixas. |
| Organização (controladora dos dados) | Restringir o acesso a dados pessoais e apresentar indicadores fiéis às respostas e aos questionários publicados. |

## Pré-condições

O participante está autenticado (CU-08). A autorização é reavaliada em cada consulta (RF01).

## Garantias de sucesso (pós-condições)

1. O participante vê apenas registros para os quais tem permissão: seus envios e os resultados recebidos já liberados pelo gestor ou pelo RH, de avaliações enviadas e não canceladas (RF14, RN09).
2. Os indicadores apresentados consideram somente respostas válidas e ativas das avaliações elegíveis, usam os tipos e textos copiados na coleta e distinguem notas de respostas Sim/Não (RF15, RN05, RN10).
3. A evolução compara somente versões equivalentes; mudanças de pergunta, tipo ou composição de grupo não são ocultadas por uma série contínua indevida (RN11).
4. A consulta não altera avaliações, respostas, questionários nem estados de coleta.

## Garantias mínimas

Em consulta sem dados, falta de autorização ou falha, nenhum dado é alterado. O sistema não revela o conteúdo de rascunhos de terceiros, resultados ainda não liberados ou registros fora do escopo autorizado, inclusive por filtros ou acesso direto a identificadores.

## Gatilho

O participante deseja rever avaliações enviadas ou acompanhar os resultados recebidos após uma coleta.

## Fluxo principal de sucesso

1. O participante solicita seu histórico e sua análise de resultados.
2. O sistema identifica o participante e apresenta os próprios envios e os resultados recebidos que já podem ser consultados. Para estes, considera somente avaliações **ENVIADA** cujo resultado foi liberado pelo gestor ou pelo RH; não inclui avaliações nem coletas **CANCELADAS** (RF14, RN09).
3. O participante filtra por coleta, período de encerramento, grupo ou parâmetro e escolhe um resultado recebido.
4. O sistema revalida a permissão e apresenta o histórico do recorte com coleta, período, participantes permitidos pela política de acesso e as perguntas e tipos preservados na publicação. Exibe notas, respostas Sim/Não e comentários sem identificar o avaliador nas coletas recíprocas e no 360°, exceto a resposta do gestor direto no 360° (RF14, RN05, RN-DOC-02).
5. O participante solicita a análise do recorte.
6. O sistema informa a quantidade distinta de avaliações elegíveis e a quantidade de respostas válidas e ativas por coleta, grupo e parâmetro. Para escalas, normaliza cada nota como `100 × valor / limite_superior` (10 ou 5, conforme o tipo copiado) e calcula a média das notas normalizadas sem pesos adicionais. Para booleanos, apresenta as contagens e proporções de Sim e Não em separado, sem incluí-las na média numérica (RF15, RN10).
7. O participante solicita a evolução entre coletas.
8. O sistema compara somente perguntas da mesma origem com texto e tipo copiados equivalentes. Se a composição de um grupo mudou, sinaliza a mudança e não une automaticamente os resultados do grupo em uma única série. Usa sempre os valores históricos, sem recalculá-los com o catálogo atual (RN11).
9. O sistema apresenta os resultados e a evolução do recorte, com valores arredondados para duas casas apenas na apresentação, e informa a quantidade de dados considerada em cada indicador.

## Extensões (fluxos alternativos)

**\*a. A sessão expirou ou o participante não está autorizado para o recorte solicitado.**

1. O sistema rejeita a consulta, inclusive por identificador informado diretamente, sem revelar o conteúdo nem confirmar a existência de registros fora do escopo autorizado (RF01, RNF01). O caso de uso termina.

**2a. Não há resultados recebidos liberados.**

1. O sistema informa que ainda não há resultados recebidos disponíveis, sem revelar respostas ainda não liberadas. Os próprios envios continuam consultáveis, se existirem (RN09).
2. Se não houver envios nem resultados, o sistema informa que o histórico está vazio. O caso de uso termina.

**2b. O participante consulta uma avaliação que ele enviou.**

1. O sistema mostra somente seu próprio envio e suas respostas preservadas, mesmo que o sentido inverso não tenha sido enviado. Não mostra a resposta recebida nem a inclui na análise antes da liberação (RF14, RN09).
2. O participante pode voltar ao passo 2 para escolher outro registro.

**2c. A avaliação não foi enviada, foi cancelada ou ainda não teve o resultado liberado.**

1. O sistema não apresenta o conteúdo como resultado recebido nem o inclui nos indicadores. Um envio do próprio participante, se houver, segue a extensão 2b. O fluxo volta ao passo 2 (RN09, CA09).

**3a. O participante usa filtros sem resultados elegíveis.**

1. O sistema apresenta o recorte como vazio, sem inferir nota zero ou expor registros não liberados. O participante pode ajustar os filtros; o fluxo volta ao passo 3.

**3b. Um gestor solicita resultados de um time sob sua responsabilidade.**

1. O sistema verifica o vínculo explícito do gestor com o time. Um time fora de sua responsabilidade segue a extensão *a (RF01, RNF01).
2. Para o recorte autorizado, o gestor vê os resultados individuais, inclusive os ainda não liberados, e o fluxo prossegue no passo 4 (RN09, RN14).

**3c. O RH solicita resultados de outra pessoa.**

1. O RH consulta os resultados individuais de qualquer pessoa da organização, inclusive os ainda não liberados, e o fluxo prossegue no passo 4 (RN09, RN14). A identificação do avaliador segue a RN-DOC-02.

**3d. O gestor ou o RH libera resultados ao avaliado.**

1. No recorte autorizado, o gestor ou o RH seleciona avaliações enviadas e solicita a liberação.
2. O sistema revalida a autorização, registra a liberação e o evento de auditoria e passa a exibir esses resultados ao avaliado (RN09, RF16). Nas coletas recíprocas e no 360°, só libera resultados anônimos quando o número mínimo de respondentes for atingido (RN-DOC-03). O fluxo volta ao passo 3.

**6a. Não há respostas válidas do tipo consultado.**

1. O sistema mostra **“sem dados”** para a média ou proporção cujo denominador é zero; não apresenta zero como resultado calculado. Grupos com notas e booleanos mantêm indicadores separados (RN10, CA10).

**8a. A pergunta, o tipo ou a composição do grupo mudou entre coletas.**

1. O sistema separa versões incompatíveis da série e identifica a mudança de composição do grupo. Mantém visíveis os resultados históricos de cada coleta autorizada, sem fundi-los numa métrica única (RN11, CA11).

**9a. A consulta falha ou a autorização muda durante o fluxo.**

1. O sistema não apresenta dados parciais fora da permissão atual e informa que a consulta não pôde ser concluída. O participante pode solicitá-la novamente a partir do passo 1.

## Requisitos especiais

- Verificar autorização, vínculo com o time e liberação no servidor para cada consulta e filtro, inclusive em chamadas diretas; não expor rascunhos de terceiros ou resultados ainda bloqueados (RNF01, RNF14).
- Calcular os indicadores de forma reproduzível com as fórmulas de RN10 e os dados publicados da coleta; o cenário de CA10 deve produzir média numérica de 70% e 50% de Sim e de Não, sem mistura entre os tipos (RNF12).
- Não incluir respostas nem comentários em logs técnicos (RNF07). O acesso a notas, comentários e identidades segue a RN09 e a RN-DOC-02.
- Apresentar filtros, resultados e mensagens por teclado e em texto, em telas de 360 a 1.440 px, conforme RNF03.
- A consulta paginada de histórico e análise segue a meta de RNF04: 95% em até 2 s com 50 usuários simultâneos e até 100.000 respostas em homologação.

## Lista de variantes tecnológicas e de dados

- Acesso por navegador em computador ou celular; a sequência essencial independe da disposição das telas.
- O período do histórico usa `encerrada_em` da coleta. As perguntas, tipos, nomes e times históricos vêm das cópias publicadas e dos dados preservados na avaliação, não do cadastro atual.
- Um filtro pode reduzir o recorte a uma coleta, grupo ou parâmetro sem mudar as regras de elegibilidade, autorização e cálculo.

## Frequência de ocorrência

Repetida após o encerramento de coletas e durante o acompanhamento da evolução. Não há volume validado pelo stakeholder.

## Decisões validadas (E01, E02)

- **PV03 e PV04:** em todas as modalidades, inclusive 360°, autoavaliação e feedback informal, os resultados são liberados ao avaliado pelo gestor ou pelo RH (RN09, RN15). A liberação não depende do par completo.
- **Conflito C02:** nas coletas recíprocas e no 360°, o avaliador não é identificado ao avaliado, exceto a resposta do gestor direto no 360°; resultados anônimos exigem o número mínimo de respondentes (RN-DOC-02, RN-DOC-03).
- **PV05 / conflito C01:** os dados não são excluídos no uso operacional e são anonimizados ao fim do prazo de retenção (RN12); a consulta apresenta os dados anonimizados sem identificar os titulares.

## Rastreabilidade

| Elemento | Referência |
| --- | --- |
| Requisitos funcionais | RF01, RF14, RF15 |
| Regras de negócio | RN05, RN09, RN10, RN11, RN12, RN14; RN-DOC-02, RN-DOC-03 |
| Requisitos não funcionais | RNF01, RNF03, RNF04, RNF07, RNF12, RNF14 |
| Critérios de aceitação | CA02, CA09, CA10, CA11 |
| Entidades | COLETA, AVALIACAO, FEEDBACK, COLETA_GRUPO, COLETA_PARAM; dados históricos de TIME e USUARIO copiados em AVALIACAO |
| Especificação | [Especificação de requisitos](../requisitos/especificacao-requisitos.md), RF14, RF15 e RN09 a RN11 |
| Dados e estados | [Dicionário de dados](../dicionario-dados.md), COLETA, AVALIACAO e FEEDBACK |
| Matriz | [Matriz de rastreabilidade](../rastreabilidade/matriz-rastreabilidade.md) |
| Diagrama | [Diagrama de casos de uso](README.md) |
