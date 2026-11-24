# CU-02 — Responder e enviar avaliação

| Campo | Informação |
| --- | --- |
| Autoria | Luiz Augusto Vaz |
| Versão | 0.1 — 8 de novembro de 2026 |
| Formato | Completo, estilo essencial (Larman, cap. 6) |
| Situação | Proposto para validação |

## Escopo

Sistema de gestão de competências e feedback.

## Nível

Objetivo do usuário (*user goal*): o participante conclui uma avaliação em uma sessão de trabalho.

## Ator principal

**Participante** no papel de avaliador. Pode ter qualquer perfil (RH, Gestor ou Profissional).

## Partes interessadas e interesses

| Parte interessada | Interesse |
| --- | --- |
| Avaliador | Responder com tranquilidade, salvar o progresso, saber quem verá as respostas e não perder o que já preencheu. |
| Receptor | Receber uma avaliação completa, coerente com o questionário e feita sem influência da avaliação que ele próprio enviou. |
| RH | Acompanhar o preenchimento e obter dados válidos e comparáveis para a análise. |
| Gestor | Contar com resultados confiáveis sobre os times que acompanha. |
| Organização (controladora dos dados) | Tratar os dados pessoais conforme a LGPD, restringindo o acesso a quem tem permissão. |

## Pré-condições

1. O participante está autenticado (CU-08).
2. Existe uma coleta **ABERTA**, dentro do período de resposta (início inclusivo, fim exclusivo — RN07).
3. Existe uma avaliação atribuída ao participante como avaliador, em estado **RASCUNHO** (gerada no CU-01).

## Garantias de sucesso (pós-condições)

1. A avaliação passa a **ENVIADA**, com instante de envio registrado.
2. Existe exatamente uma resposta ativa e válida para cada pergunta ativa do questionário publicado (RN02, RN06).
3. As respostas ficam imutáveis (RF12, RN08).
4. A avaliação inversa (receptor sobre avaliador) não é alterada (RN01).
5. O envio fica registrado na auditoria, sem o conteúdo dos comentários (RF16).

## Garantias mínimas

Em qualquer falha ou desistência, as respostas já salvas em rascunho são preservadas, nenhuma avaliação fica parcialmente enviada e nenhum conteúdo da avaliação recebida é exibido ao avaliador.

## Gatilho

O participante decide responder a uma avaliação pendente, por exemplo depois de ser informado da abertura de uma coleta.

## Fluxo principal de sucesso

1. O participante solicita ver suas avaliações pendentes.
2. O sistema apresenta as avaliações em rascunho das coletas abertas, com receptor, coleta, prazo e progresso de preenchimento.
3. O participante escolhe uma avaliação.
4. O sistema apresenta o questionário publicado da coleta, organizado por grupo e na ordem definida, informando quem poderá ver as respostas e quando (RNF13). Para cada pergunta, oferece a entrada compatível com o tipo: nota inteira para escalas e opção explícita Sim ou Não para booleanos, sem resposta pré-selecionada (RF11).
5. O participante responde às perguntas e, se quiser, escreve comentários.
6. O sistema valida cada resposta conforme o tipo copiado na coleta (RN06) e a salva como rascunho.
7. O participante repete os passos 5 e 6 até responder a todas as perguntas.
8. O participante solicita o envio.
9. O sistema apresenta um resumo das respostas e pede confirmação, avisando que não será possível alterá-las depois (RNF13).
10. O participante confirma.
11. O sistema verifica se a coleta continua aberta e dentro do período, se há uma resposta ativa e válida para cada pergunta ativa e se a avaliação ainda está em rascunho. Em seguida, registra o envio de forma atômica (RF12, RNF02).
12. O sistema informa que a avaliação foi enviada e atualiza a lista de pendências.

## Extensões (fluxos alternativos)

**\*a. A qualquer momento, o participante interrompe o preenchimento.**

1. O sistema mantém as respostas já salvas em rascunho.
2. O participante pode retomar depois a partir do passo 1, enquanto a coleta estiver aberta e no período.

**2a. Não há avaliações pendentes.**

1. O sistema informa que não há avaliações a responder. O caso de uso termina.

**3a. O participante tenta abrir uma avaliação de outro avaliador, por exemplo pelo identificador no endereço.**

1. O sistema rejeita o acesso sem revelar o conteúdo nem confirmar a existência do registro (RF01, RNF01). O caso de uso termina.

**4a. O participante tenta consultar a avaliação que recebeu do mesmo par.**

1. O sistema não exibe esse conteúdo enquanto o par não estiver completo e a coleta não estiver encerrada (RN09).

**6a. Valor incompatível com o tipo da pergunta (por exemplo, 6 em uma escala de 0 a 5, número decimal, ou número em pergunta Sim/Não).**

1. O sistema indica a pergunta e a condição inválida, preserva os demais valores e não salva aquele valor (RI01, CA07).
2. O participante corrige o valor; o fluxo volta ao passo 6.

**6b. Comentário acima de 2.000 caracteres.**

1. O sistema informa o limite e não salva o comentário excedente (RN06). O fluxo volta ao passo 5.

**6c. O participante retira uma resposta já dada.**

1. O sistema desativa a resposta, preservando o registro, e a pergunta volta a ficar pendente (RF11).
2. Se o participante responder de novo, o sistema reativa a mesma resposta, sem criar duplicata.

**6d. Falha de conexão ou do servidor ao salvar.**

1. O sistema informa que a resposta não foi salva e mantém o valor na tela para nova tentativa. As respostas salvas antes permanecem.

**8a. Há perguntas sem resposta ativa.**

1. O sistema impede o envio e lista as perguntas pendentes. O fluxo volta ao passo 5.

**10a. O participante não confirma o envio.**

1. A avaliação permanece em rascunho. O fluxo volta ao passo 5.

**11a. O período terminou ou a coleta foi encerrada ou cancelada durante o preenchimento.**

1. O sistema rejeita o envio e informa o motivo. As respostas continuam armazenadas, mas não podem mais ser enviadas (RN07). No encerramento, a avaliação incompleta é cancelada pelo CU-03. O caso de uso termina.

**11b. A avaliação já foi enviada, por exemplo por um duplo clique ou em outra aba.**

1. O sistema não registra um segundo envio e informa que a avaliação já foi enviada (RNF02, CA08).

**11c. Falha durante o registro do envio.**

1. O sistema desfaz a operação inteira: a avaliação permanece em rascunho com todas as respostas (RNF02).
2. O participante pode tentar novamente a partir do passo 8.

## Requisitos especiais

- Validação de período, completude, autoria e imutabilidade sempre no servidor, inclusive em chamadas diretas à API (RNF01).
- Preenchimento operável por teclado, com rótulos e mensagens de erro textuais, em telas de 360 a 1.440 px (RNF03).
- Conteúdo de respostas e comentários não aparece em logs técnicos (RNF07).
- Orientação junto ao comentário para não incluir dados pessoais sensíveis (RF-DOC-14).

## Lista de variantes tecnológicas e de dados

- O valor das escalas é inteiro (0 a 10 ou 0 a 5); o booleano é verdadeiro ou falso, exibido como Sim ou Não.
- A interface pode salvar automaticamente a cada resposta ou por ação explícita; o resultado essencial é o mesmo.
- Acesso por navegador em computador ou celular.

## Frequência de ocorrência

Em cada coleta, uma vez por avaliação atribuída. No modo por times, um time com `n` integrantes gera `n − 1` avaliações para cada participante, e o uso se concentra perto do fim do período.

## Questões em aberto

- **PV03:** a reciprocidade obriga os dois a responder? Pares incompletos ficam fora dos resultados.
- **PV04:** quem pode ver notas, comentários e identidade do avaliador? Afeta a mensagem do passo 4.
- **Conflito C02:** se o anonimato for adotado, o passo 4 e a extensão 4a precisam ser revistos.
- O participante recebe lembretes de avaliações pendentes? Não há requisito de notificação nesta versão.

## Rastreabilidade

| Elemento | Referência |
| --- | --- |
| Requisitos funcionais | RF01, RF11, RF12, RF16 |
| Regras de negócio | RN01, RN02, RN06, RN07, RN08, RN09 |
| Requisitos não funcionais | RNF01, RNF02, RNF03, RNF07, RNF13 |
| Critérios de aceitação | CA07, CA08, CA09 |
| Entidades | AVALIACAO, FEEDBACK, COLETA, COLETA_PARAM, EVENTO_AUDITORIA |
| Diagrama | [Diagrama de casos de uso](README.md) |
