# Pauta de validação com o stakeholder

Atende à issue #25 e à etapa 3.5 do [processo de requisitos](../PROCESSO_REQUISITOS.md). Autoria: Luiz Augusto Vaz. Situação: **pauta não utilizada**. A validação ocorreu nas entrevistas E01 e E02, conforme registro da equipe em 23/11/2026; as decisões estão na [lista geral](../requisitos/lista-geral.md) (versão 0.3, seção 7) e no [registro da E02](../levantamento/entrevistas/E02-entrevista-professora.md).

## Objetivo

Confirmar com o responsável pelo negócio o escopo da primeira versão, as prioridades e as decisões pendentes, e registrar o que for validado. Duração sugerida: 45 minutos.

## Antes da reunião

- Enviar ao stakeholder, com antecedência, o [documento de visão](../visao.md) e os diagramas do [processo de negócio](../modelos/processo/README.md).
- Definir quem conduz e quem registra. O registrador anota as respostas com as palavras do stakeholder.
- Levar a [lista geral](../requisitos/lista-geral.md) aberta, para atualizar a coluna "Situação" depois.
- Pedir autorização para gravar, se houver gravação, como nas entrevistas.

## Roteiro

| # | Tema | Tempo | O que perguntar | Itens afetados |
| --- | --- | --- | --- | --- |
| 1 | Abertura | 3 min | Objetivo da reunião e como as respostas serão registradas | — |
| 2 | Processo atual | 7 min | O processo atual do BPMN corresponde ao que acontece? As dores D1 a D6 são as principais? | BPMN, visão 2.1 |
| 3 | Escopo das modalidades | 8 min | A primeira versão deve ter coleta recíproca, 360°, autoavaliação e feedback informal? | RF10, RF17, RF20, RF22, RN15 |
| 4 | Liberação dos resultados (PV03, PV04) | 7 min | Quem vê o quê, e quando, em cada modalidade? A reciprocidade obriga os dois a responder? | RN09, RN15 |
| 5 | Anonimato (C02) | 5 min | As avaliações devem ser identificadas ou anônimas? Em quais modalidades? | RN-DOC-02, RN-DOC-03, RNF16 |
| 6 | Retenção de dados (C01, PV05) | 5 min | Nada é excluído, ou os dados devem ser anonimizados ao fim de um prazo? Qual prazo? | RN12, RF-DOC-07, RF-DOC-08 |
| 7 | Plano de ação | 5 min | Quem cria, quem acompanha, com que frequência há verificação? | RF18, RN13, RN14 |
| 8 | Prioridades | 3 min | Os itens marcados como Essenciais são mesmo essenciais? | Lista geral, seções 3 a 5 |
| 9 | Encerramento | 2 min | Ler em voz alta o que foi decidido e confirmar | — |

## Registro das respostas

Preencher durante a reunião. Só marcar como **Validado** o que o stakeholder confirmar explicitamente.

| # | Pergunta | Resposta do stakeholder | Decisão | Validado? |
| --- | --- | --- | --- | --- |
| 2 | Processo atual e dores | | | Sim / Não / Parcial |
| 3 | Modalidades na primeira versão | | | Sim / Não / Parcial |
| 4 | Liberação dos resultados | | | Sim / Não / Parcial |
| 5 | Anonimato | | | Sim / Não / Parcial |
| 6 | Retenção de dados | | | Sim / Não / Parcial |
| 7 | Plano de ação | | | Sim / Não / Parcial |
| 8 | Prioridades | | | Sim / Não / Parcial |

Dados da reunião: data, duração, forma (presencial ou videochamada), participantes da equipe e função genérica do stakeholder. Nome e contato ficam no registro restrito, como nas entrevistas.

## Depois da reunião

1. Atualizar a coluna "Situação" da [lista geral](../requisitos/lista-geral.md) e da [matriz](../rastreabilidade/matriz-rastreabilidade.md) com o que foi validado.
2. Resolver ou registrar de novo os conflitos C01 e C02 e as pendências PV03, PV04 e PV05.
3. Ajustar o BPMN, a visão e a especificação conforme as respostas.
4. Abrir um PR com as mudanças, citando este registro como fonte.
