# Auditoria de conformidade com normas ISO

Autoria: Luiz Augusto Vaz. Versão 0.1 — 21 de novembro de 2026. Situação: **proposta para revisão da equipe**.

## 1. Natureza desta auditoria

Esta é uma **auditoria interna de documentação**, feita pela própria equipe em contexto acadêmico. Ela não é certificação, não substitui auditoria por organismo acreditado e não declara conformidade formal com nenhuma norma.

- **Objeto:** os artefatos da primeira etapa no repositório (requisitos, casos de uso, modelos de domínio, processo, arquitetura C4, modelo de projeto e rastreabilidade), considerando também os PRs #51 e #52.
- **Critério:** a estrutura pública e os requisitos gerais de cada norma listada na seção 2. O texto das normas não é reproduzido aqui. Para a versão final, confira os itens nas normas oficiais (ISO ou ABNT).
- **Limite de fase:** o sistema ainda não foi construído. Normas sobre processos organizacionais, operação ou produto em execução são avaliadas apenas quanto ao que os requisitos já preveem.
- **Base:** `main` no commit `93c8446`, mais as branches `docs/arquitetura-c4` e `docs/projeto-design`.

### 1.1. Classificação dos resultados

| Resultado | Significado |
| --- | --- |
| **C** — Conforme | Os artefatos atendem ao que a norma pede para esta fase. |
| **CP** — Conforme parcialmente | Atende em parte; há achados menores ou pendências já registradas. |
| **NC** — Não conforme | Falta algo que a norma pede para esta fase, ou há conflito não resolvido. |
| **NA** — Não aplicável | A norma trata de algo fora do escopo do produto ou desta fase. |

| Gravidade do achado | Significado |
| --- | --- |
| **Maior** | Impede verificar, validar ou cumprir um requisito central. Deve ser tratado antes da entrega. |
| **Menor** | Lacuna pontual que não compromete o conjunto. |
| **Observação** | Ponto de atenção ou oportunidade de melhoria. |

## 2. Normas avaliadas e aplicabilidade

| Norma | Assunto | Por que se aplica | Já citada no projeto? | Resultado |
| --- | --- | --- | --- | --- |
| ISO/IEC/IEEE 29148:2018 | Engenharia de requisitos | Substitui a IEEE 830-1998, usada na especificação | Não (cita IEEE 830) | **CP** |
| ISO/IEC 25010:2023 | Modelo de qualidade do produto | Base dos RNF | Sim | **CP** |
| ISO/IEC 25019:2023, 25023, 25040 | Qualidade em uso, medição e avaliação | Complementam a 25010 | Só a 25019, de passagem | **Observação** |
| ISO/IEC/IEEE 42010:2022 | Descrição de arquitetura | Visão C4 e decisões AD01 a AD05 | Não | **CP** |
| ISO/IEC 19505 (UML) e ISO/IEC 19510 (BPMN) | Notações de modelagem | Casos de uso, domínio, projeto e processo | Não | **CP** |
| ISO/IEC 27001:2022 e 27002:2022 | Segurança da informação | Dados pessoais de desempenho; RNF de segurança | Só no sistema análogo e como pendência (D-13) | **CP**, com um **NC** |
| ISO/IEC 29100, 27701 e 29134 | Privacidade, gestão de privacidade e avaliação de impacto | Tratamento de dados pessoais; complementam a LGPD | Não | **CP**, com um **NC** |
| ISO 9241-110:2020 e 9241-210:2019 | Princípios de interação e projeto centrado no usuário | RNF03, RNF13 e protótipo no Figma | Não | **CP** |
| ISO/IEC 40500:2012 | Acessibilidade web (WCAG 2.0) | RNF03 | Não (cita WCAG 2.2 AA "a definir") | **CP** |
| ISO 10667-1 e 10667-2:2020 | Avaliação de pessoas em contexto de trabalho | É o domínio do sistema | Não | **CP** |
| ISO 30414 | Relatórios de capital humano | Indicadores de RH | Não | **NA** nesta versão |
| ISO/IEC/IEEE 12207 e 15288; ISO/IEC 29110 | Processos de ciclo de vida; pequenas equipes | Processo de requisitos e revisão por PR | Não | **CP** |

**Resumo:** nenhuma norma está em não conformidade geral. Há **25 achados**: 5 maiores, 14 menores e 6 observações (seção 12). As não conformidades pontuais são três: requisitos ainda não validados com o stakeholder (AC04), disponibilidade sem requisito (AC06) e falta de exclusão e de prazo de retenção, que é o conflito C01 já registrado pela equipe (AC14).

## 3. ISO/IEC/IEEE 29148:2018 — engenharia de requisitos

A especificação segue a IEEE 830-1998, como pede o enunciado da disciplina. Essa norma foi substituída pela ISO/IEC/IEEE 29148 (2011, revisada em 2018), que reúne o conteúdo da IEEE 830 e o amplia. Por isso, a auditoria usa a 29148 como critério.

### 3.1. Conteúdo da especificação

| Item esperado | Evidência | Resultado |
| --- | --- | --- |
| Propósito, escopo, definições, referências e visão geral | [Especificação](../requisitos/especificacao-requisitos.md), seção 1 | C |
| Perspectiva, funções, usuários, restrições, premissas e dependências | Especificação, seção 2; [visão](../visao.md) | C |
| Interfaces externas | Especificação, seção 3.1 | C |
| Requisitos funcionais, de dados, de qualidade e restrições de projeto | Especificação, seções 3.2 a 3.5; [suplementar](../requisitos/especificacao-suplementar.md) | C |
| Verificação de cada requisito | Critérios CA01 a CA18; coluna "Verificação" da suplementar | C |
| Rastreabilidade | [Matriz](../rastreabilidade/matriz-rastreabilidade.md) v0.7 | C |
| Necessidades dos stakeholders separadas dos requisitos do sistema | Visão, seção 3.3 (N01 a N08) e lista geral | C |

### 3.2. Características de cada requisito

| Característica | Avaliação | Resultado |
| --- | --- | --- |
| Necessário e adequado | Todo RF, RN e RNF tem fonte (E01, E02, DOC, SA, ENU) e necessidade | C |
| Sem ambiguidade | Termos definidos no [glossário](../dicionario-dados.md); fórmulas explícitas (RN10) | C |
| Completo | Pendências marcadas como "Pendente" com a decisão que falta | C |
| Singular (uma coisa por requisito) | RF13, RF18, RNF03 e RNF11 reúnem mais de uma capacidade | **CP — AC02** |
| Viável | Sem tecnologia escolhida; nada pede algo impossível | C |
| Verificável | RNF03 (nível de acessibilidade), RNF11 (limite de tentativas), RNF04 e RNF05 (metas) ainda sem valor acordado | **CP — AC03** |
| Correto e validado | A maioria está "Proposto"; a validação com o stakeholder não ocorreu | **NC nesta data — AC04** |
| Identificável | IDs únicos e não reutilizados (lista geral, seção 2) | C |
| Priorizado | Essencial, Importante ou Desejável em todos | C |

### 3.3. Achados

- **AC01 (Menor).** A especificação se declara "IEEE 830-1998", norma substituída. **Recomendação:** manter a estrutura pedida pelo enunciado, mas citar a ISO/IEC/IEEE 29148:2018 nas referências (seção 1.4) como norma vigente e dizer que a estrutura é compatível com ela.
- **AC02 (Menor).** Requisitos não singulares: RF13 (acompanhar, encerrar e cancelar), RF18 (criar, acompanhar e concluir plano), RNF03 (teclado e larguras de tela) e RNF11 (limite de login e vulnerabilidades). **Recomendação:** desdobrar em itens com sufixo (RF13a, RF13b…) ou justificar o agrupamento na lista geral.
- **AC03 (Maior).** RNF sem critério mensurável acordado: RNF03, RNF04, RNF05 e RNF11 (PV07, D-12). **Recomendação:** levar valores propostos à reunião de validação (#25) e registrar a decisão.
- **AC04 (Maior).** O conjunto de requisitos ainda não foi validado com o stakeholder (#25). **Recomendação:** realizar a reunião com a [pauta](../validacao/pauta-validacao-stakeholder.md) e mudar a situação de cada requisito confirmado para "Validado".
- **AC05 (Observação).** As fontes E01 e E02 estão como "conteúdo a validar com participantes reais", sem transcrição (L01, #41). A origem dos requisitos fica sem evidência primária.

## 4. ISO/IEC 25010:2023 — qualidade do produto

### 4.1. Cobertura das características

| Característica (2023) | RNF | Subcaracterísticas cobertas | Sem requisito ou justificativa | Resultado |
| --- | --- | --- | --- | --- |
| *Functional suitability* | RNF12 | *Correctness* | *Completeness*, *appropriateness* | CP |
| *Performance efficiency* | RNF04 | *Time behaviour*, *capacity* | *Resource utilization* | CP |
| *Compatibility* | RNF15 | *Interoperability* | *Co-existence* | CP |
| *Interaction capability* | RNF03, RNF13 | *Inclusivity*, *operability*, *self-descriptiveness*, *user error protection* | *Appropriateness recognizability*, *learnability*, *user engagement*, *user assistance* | CP |
| *Reliability* | RNF02, RNF05 | *Faultlessness*, *recoverability* | ***Availability***, *fault tolerance* | **NC parcial — AC06** |
| *Security* | RNF01, 06 a 11, 16 | *Confidentiality*, *integrity*, *accountability*, *authenticity*, *resistance* | *Non-repudiation* coberto junto com o RNF06 | C |
| *Maintainability* | RNF14 | *Testability* | *Modularity*, *reusability*, *analysability*, *modifiability* | CP |
| *Flexibility* | RNF03 | *Adaptability* | *Scalability*, *installability*, *replaceability* | CP |
| *Safety* | — | Não se aplica, com justificativa (suplementar 3.9) | — | C |

Ponto forte: as nove características da edição de 2023 foram consideradas, com a nomenclatura nova (*interaction capability*, *flexibility*, *safety*), e a única excluída tem justificativa.

### 4.2. Achados

- **AC06 (Maior).** A disponibilidade se perdeu na consolidação. O RNF-DOC-15 da pesquisa documental pedia metas de disponibilidade durante os ciclos, mas o RNF04, que o consolida, trata só de tempo de resposta e capacidade. Um ciclo de avaliação com prazo depende do sistema estar no ar. **Recomendação:** criar um RNF de *availability* (por exemplo, meta proposta de disponibilidade no período das coletas) com a situação "Pendente (PV07)".
- **AC07 (Menor).** Doze subcaracterísticas não têm requisito nem justificativa de exclusão (tabela 4.1). **Recomendação:** acrescentar à suplementar uma tabela "subcaracterística → RNF ou motivo de não se aplicar". A AD01 e os padrões PP04, PP05 e PP09 já sustentam modularidade e modificabilidade e podem ser citados.
- **AC08 (Observação).** Não há medidas no formato da ISO/IEC 25023 nem plano de avaliação conforme a ISO/IEC 25040. Isso cabe à fase de implementação, mas os métodos de verificação da suplementar já são um bom ponto de partida.
- **AC09 (Observação).** A qualidade em uso (ISO/IEC 25019: eficácia, eficiência e satisfação de quem usa) não foi tratada. Para um sistema de RH, a adesão dos avaliadores define o sucesso. **Recomendação:** registrar ao menos uma meta de qualidade em uso, por exemplo, o percentual de conclusão das coletas (já calculado pela RN10).

## 5. ISO/IEC/IEEE 42010:2022 — descrição de arquitetura

| Elemento esperado | Evidência | Resultado |
| --- | --- | --- |
| Identificação do sistema e do propósito da descrição | [Visão arquitetural](../modelos/arquitetura/README.md), introdução | C |
| Stakeholders e suas preocupações (*concerns*) | Público por nível (seção 1) e direcionadores (seção 2), mas sem tabela stakeholder × preocupação | **CP — AC10** |
| Pontos de vista (*viewpoints*) com convenções | Níveis C4 com pergunta e legenda (seção 1) | C |
| Visões (*views*) | Contexto, containers e componentes, mais o [modelo de projeto](../modelos/projeto/README.md) | C |
| Correspondências entre visões | Matriz, seções 3.5 e 3.6; tabelas de componentes | C |
| Decisões e justificativas | AD01 a AD05, com alternativa descartada | C |
| Inconsistências e pontos em aberto | Lacunas A01 a A05 | C |

- **AC10 (Menor).** Falta relacionar cada stakeholder às preocupações que a arquitetura responde (o RH e a privacidade, o professor e a rastreabilidade, a organização e a LGPD). **Recomendação:** incluir na seção 2 da visão arquitetural uma tabela "stakeholder → preocupação → visão que responde".

## 6. ISO/IEC 19505 (UML) e ISO/IEC 19510 (BPMN) — notações

| Artefato | Notação | Avaliação | Resultado |
| --- | --- | --- | --- |
| Diagrama de casos de uso (`.puml`) | UML | Atores, generalização de atores, fronteira do sistema e casos de uso na notação UML | C |
| Diagrama de casos de uso (`.mmd`) | Fluxograma Mermaid | Aproximação visual, sem a notação UML de ator e caso de uso | **CP — AC11** |
| Modelo de domínio e classes de projeto | Diagrama de classes (Mermaid) | Multiplicidades, composição, interfaces e estereótipos; notação próxima da UML | C |
| Diagramas de estado e de sequência | UML (Mermaid) | Estados, guardas, ações, `alt`, `loop`, ativação | C |
| MER | Pé de galinha | Não é UML nem ISO, mas é notação consagrada para modelo lógico e está declarada | C |
| Processo atual e proposto (`.bpmn`) | BPMN 2.0 (XML) | Piscinas, raias, eventos, tarefas e gateways; abre no bpmn.io e no Camunda | C |
| Imagens exportadas | PNG | Desatualizadas ou ausentes (#40) | **CP — AC12** |

- **AC11 (Menor).** Existem duas versões do diagrama de casos de uso, e só a `.puml` está em UML. **Recomendação:** declarar a `.puml` como oficial no [índice de casos de uso](../casos-de-uso/README.md) e usar a imagem dela na documentação mestre.
- **AC12 (Menor).** As exportações em PNG estão desatualizadas (MER, domínio e casos de uso) ou ausentes (C4 e projeto). **Recomendação:** regerar todas a partir dos `.mmd` e `.puml`.
- **AC13 (Observação).** O BPMN não foi validado com o stakeholder (#10). A notação está correta, mas o conteúdo é proposta.

## 7. ISO/IEC 27001 e 27002:2022 — segurança da informação

A certificação ISO/IEC 27001 vale para o sistema de gestão de uma organização, não para um produto: **NA** como certificação. A auditoria verifica se os requisitos do produto dão suporte aos controles do Anexo A que dependem do software.

| Controle (27002:2022) | Tema | Requisitos que atendem | Resultado |
| --- | --- | --- | --- |
| 5.15, 8.3 | Controle de acesso e restrição de acesso à informação | RF01, RNF01, RN14, PP19 | C |
| 5.17, 8.5 | Informação de autenticação e autenticação segura | RNF09, RNF10, RNF11 | **CP — AC15** (sessão) |
| 8.2 | Direitos de acesso privilegiado | RNF09 (segundo fator do RH) | CP — ver AC15 |
| 8.10 | Exclusão de informação | Conflita com a RN12 (C01) | **NC — AC14** |
| 8.11 | Mascaramento de dados | RNF16 (só se houver anonimato) | CP |
| 8.13 | Cópia de segurança | RNF05 | C (meta pendente, AC03) |
| 8.15 | Registro de eventos (*logging*) | RF16, RNF06, RNF07, AD03, AD04 | C |
| 8.16 | Monitoramento de atividades | Ausente | **CP — AC16** |
| 8.17 | Sincronização de relógio | Datas em TIMESTAMPTZ, sem requisito de fonte de horário | **Observação — AC17** |
| 8.24 | Uso de criptografia | RNF08 (TLS), RNF10 (*hash* e proteção) | C |
| 8.25 a 8.29 | Desenvolvimento e testes seguros | RNF11 (vulnerabilidades), RNF14 (testes) | CP — AC18 |
| 5.24 a 5.26 | Gestão de incidentes | RF-DOC-13 (listar titulares afetados) | CP — AC16 |

- **AC14 (Maior).** O controle de exclusão de informação pede eliminar dados quando não são mais necessários, e a RN12 proíbe a exclusão física. É o conflito C01, já registrado e sem decisão. **Recomendação:** decidir na validação (PV05) um prazo de retenção e a forma de anonimizar ou eliminar após esse prazo (RF-DOC-07, RF-DOC-08).
- **AC15 (Menor).** Não há requisito de gestão de sessão (expiração por inatividade, encerramento ao sair, invalidação ao trocar senha). Isso afeta a autenticação segura e o acesso privilegiado do RH. Há também uma diferença de redação: a lista geral fala em segundo fator "para perfis administrativos", e a suplementar, "para o perfil RH". **Recomendação:** criar um RNF de sessão e alinhar os textos do RNF09 (o gestor também é administrativo?).
- **AC16 (Menor).** Não há requisito de monitoramento e alerta de eventos suspeitos (por exemplo, muitas tentativas de login ou acesso fora do escopo), e a resposta a incidentes se resume ao RF-DOC-13. **Recomendação:** um RNF de alerta ao responsável quando houver tentativa repetida de acesso negado.
- **AC17 (Observação).** A auditoria (RF16) depende de horários confiáveis. **Recomendação:** registrar como restrição de implantação que o servidor use fonte de horário sincronizada.
- **AC18 (Observação).** O ciclo de desenvolvimento seguro aparece só nos RNF11 e RNF14. Cabe detalhar na fase de implementação.

## 8. ISO/IEC 29100, 27701 e 29134 — privacidade

A ISO/IEC 27701 trata de um sistema de gestão de privacidade da organização: **NA** como certificação. A ISO/IEC 29100 define princípios de privacidade que se aplicam diretamente aos requisitos. A ISO/IEC 29134 orienta a avaliação de impacto, que corresponde ao RIPD da LGPD.

| Princípio (ISO/IEC 29100) | Requisitos | Resultado |
| --- | --- | --- |
| Consentimento e escolha | RF-DOC-10 pendente; a base legal (D-02) pode não ser consentimento | CP |
| Legitimidade e especificação da finalidade | RN-DOC-01, RN-DOC-04, RF-DOC-01 | C |
| Limitação da coleta e minimização de dados | RN-DOC-05, RF-DOC-14, RNF07 | C |
| Limitação de uso, retenção e divulgação | RF-DOC-08 pendente; conflito C01 | **NC — AC14** |
| Exatidão e qualidade | RF-DOC-05 (via RF02); RF-DOC-06 (contestação) pendente | CP |
| Abertura, transparência e aviso | RF-DOC-01, RF-DOC-02, RNF13 | C |
| Participação e acesso do titular | RF-DOC-03, RF-DOC-09 pendentes | **CP — AC20** |
| Responsabilização | RF16, RNF06, RF-DOC-12, encarregado (RF-DOC-02) | C |
| Segurança da informação | Seção 7 desta auditoria | CP |
| Conformidade com a privacidade | Sem avaliação de impacto (RIPD) | **CP — AC19** |

- **AC19 (Maior).** Não há avaliação de impacto à privacidade. A pesquisa documental (D-08) deixou em aberto se o tratamento é de alto risco, mas avaliar o desempenho de pessoas pode afetar de forma significativa a carreira delas. **Recomendação:** elaborar um RIPD preliminar seguindo o modelo da ANPD (fonte F08 da pesquisa documental), com a estrutura da ISO/IEC 29134: descrição do tratamento, necessidade, riscos e medidas.
- **AC20 (Menor).** Os direitos de acesso, contestação e portabilidade do titular (RF-DOC-03, RF-DOC-06 e RF-DOC-09) estão pendentes e sem caso de uso (L06). **Recomendação:** ao menos um caso de uso resumido "Exercer direitos do titular".

## 9. ISO 9241 e ISO/IEC 40500 — usabilidade e acessibilidade

| Princípio (ISO 9241-110:2020) | Evidência | Resultado |
| --- | --- | --- |
| Adequação às tarefas do usuário | Casos de uso derivados do processo; protótipo no Figma | C |
| Autodescrição | RNF13 (informar quem verá a resposta e quando) | C |
| Conformidade com as expectativas do usuário | Interface em português; glossário com termos a evitar | C |
| Facilidade de aprendizagem | Sem requisito | CP |
| Controlabilidade | Rascunho e retomada (RF11) | C |
| Robustez a erros de uso | Confirmação antes do envio (RNF13); validação por pergunta (CA07) | C |
| Engajamento do usuário | Sem requisito | CP — ver AC09 |

- **AC21 (Menor).** A ISO 9241-210 pede avaliar o projeto com usuários e iterar. O protótipo no Figma não foi avaliado com ninguém de fora da equipe, e as telas não estão ligadas aos requisitos (L03). **Recomendação:** fazer o teste de usabilidade com roteiro já previsto no RNF13, com duas ou três pessoas, e registrar os resultados.
- **AC22 (Menor).** O nível de acessibilidade está "a definir" no RNF03. A ISO/IEC 40500 corresponde à WCAG 2.0, e a WCAG 2.2 nível AA a inclui. **Recomendação:** fixar "WCAG 2.2 nível AA, que atende à ISO/IEC 40500" e verificar com ferramenta automática mais o roteiro de teclado.

## 10. ISO 10667 — avaliação de pessoas em contexto de trabalho

Esta norma trata da prestação de serviços de avaliação de pessoas em organizações, cobrindo tanto quem contrata quanto quem presta o serviço. É a mais próxima do domínio do sistema.

| Tema da norma | Evidência | Resultado |
| --- | --- | --- |
| Informar os participantes sobre a avaliação e o uso dos resultados | RNF13 informa quem vê e quando; RF-DOC-01 é um aviso geral, não da coleta | **CP — AC23** |
| Proteção dos dados e acesso restrito aos resultados | RN09, RN14, RNF01, RNF07 | C |
| Devolutiva dos resultados ao avaliado | RF14, RF15, RN09; planos de ação (RF18) | C |
| Preparo de quem avalia e uso de critérios claros | Catálogo padronizado (RF05 a RF07); fatos e impactos (RN16); sem orientação aos avaliadores | **CP — AC24** |
| Equidade e redução de vieses | Calibração fora do escopo (visão 5.2); nenhum requisito sobre vieses | CP — AC24 |
| Direito de questionar o resultado | RF-DOC-06 pendente | CP — ver AC20 |

- **AC23 (Menor).** Antes de responder, o participante não é informado sobre a finalidade daquela coleta nem sobre o uso que será dado aos resultados (por exemplo, desenvolvimento ou promoção). **Recomendação:** acrescentar ao RF08 um campo "finalidade e uso dos resultados", exibido na tela de resposta junto com a informação do RNF13.
- **AC24 (Menor).** Não há orientação aos avaliadores sobre critérios e vieses comuns, e a calibração está fora do escopo. **Recomendação:** um texto de orientação por coleta e, se o stakeholder concordar, um requisito de orientação mínima antes da primeira resposta.

## 11. Processos de ciclo de vida (ISO/IEC/IEEE 12207 e 15288; ISO/IEC 29110)

| Processo | Evidência | Resultado |
| --- | --- | --- |
| Definição de necessidades e requisitos dos stakeholders | [Processo de requisitos](../PROCESSO_REQUISITOS.md); entrevistas; síntese | CP (transcrições pendentes, AC05) |
| Análise e definição da arquitetura e do projeto | Visão C4; modelo de projeto | C |
| Gestão de configuração | Git, uma branch por issue, PRs, versões nos documentos | C |
| Verificação por revisão | Revisão por PR, mas o #37 (CU-05) e o #45 (Culture Amp) foram integrados sem revisão humana registrada | **CP — AC25** |
| Validação | Pauta pronta; reunião não feita | CP — ver AC04 |
| Planejamento e acompanhamento | Kanban no GitHub Projects (#4) | C |

- **AC25 (Menor).** Dois PRs foram integrados sem revisão registrada, e os artefatos dos PRs #51 e #52 também precisam de revisão de outro integrante. **Recomendação:** registrar a revisão desses PRs antes da entrega.

## 12. Consolidação dos achados e plano de ação

| ID | Gravidade | Norma | Achado | Ação recomendada | Itens afetados | Issue |
| --- | --- | --- | --- | --- | --- | --- |
| AC03 | Maior | 29148, 25010 | RNF sem meta acordada | Definir metas na validação | RNF03, RNF04, RNF05, RNF11 | #25 |
| AC04 | Maior | 29148 | Requisitos não validados | Fazer a reunião de validação | Todos | #25 |
| AC06 | Maior | 25010 | Disponibilidade sem requisito | Criar RNF de disponibilidade | RNF04, RNF-DOC-15 | #40 |
| AC14 | Maior | 27002, 29100 | Sem exclusão nem prazo de retenção | Decidir retenção e anonimização | RN12, RF-DOC-07, RF-DOC-08 (C01) | #25 |
| AC19 | Maior | 29134 | Sem avaliação de impacto à privacidade | RIPD preliminar | RF-DOC, RNF de segurança | Nova |
| AC01 | Menor | 29148 | Cita IEEE 830 substituída | Citar a 29148 como vigente | Especificação 1.4 | #40 |
| AC02 | Menor | 29148 | Requisitos não singulares | Desdobrar ou justificar | RF13, RF18, RNF03, RNF11 | #40 |
| AC07 | Menor | 25010 | Subcaracterísticas sem decisão | Tabela de cobertura na suplementar | Suplementar, seção 3 | #40 |
| AC10 | Menor | 42010 | Sem stakeholder × preocupação | Tabela na visão arquitetural | Arquitetura, seção 2 | PR #51 |
| AC11 | Menor | 19505 | Diagrama de casos de uso duplicado | Declarar a `.puml` oficial | Casos de uso | #13 |
| AC12 | Menor | 19505, 19510 | Imagens desatualizadas | Regerar PNG | `exportacoes/` | #40 |
| AC15 | Menor | 27002 | Sem gestão de sessão; RNF09 divergente | RNF de sessão; alinhar RNF09 | RNF09 | #40 |
| AC16 | Menor | 27002 | Sem monitoramento e alerta | RNF de alerta | RNF11, RF-DOC-13 | #40 |
| AC20 | Menor | 29100 | Direitos do titular pendentes | Caso de uso resumido | RF-DOC-03, 06, 09 | #25 |
| AC21 | Menor | 9241-210 | Protótipo não testado com usuários | Teste de usabilidade | RNF13; L03 | #22 |
| AC22 | Menor | 40500 | Nível de acessibilidade indefinido | Fixar WCAG 2.2 AA | RNF03 | #40 |
| AC23 | Menor | 10667 | Finalidade da coleta não informada | Campo de finalidade no RF08 | RF08, RNF13 | #40 |
| AC24 | Menor | 10667 | Sem orientação aos avaliadores | Texto de orientação por coleta | RF08, RN16 | #25 |
| AC25 | Menor | 12207 | PRs sem revisão registrada | Registrar revisões | PRs #37, #45, #51, #52 | — |
| AC05 | Observação | 29148 | Fontes sem transcrição | Receber as transcrições | E01, E02 | #41 |
| AC08 | Observação | 25023, 25040 | Sem medidas nem plano de avaliação | Fase de implementação | RNF | — |
| AC09 | Observação | 25019 | Qualidade em uso não tratada | Meta de conclusão das coletas | RN10 | #40 |
| AC13 | Observação | 19510 | BPMN não validado | Validar | Processo | #10 |
| AC17 | Observação | 27002 | Horário confiável para a auditoria | Restrição de implantação | RF16 | — |
| AC18 | Observação | 27002 | Desenvolvimento seguro pouco detalhado | Fase de implementação | RNF11, RNF14 | — |

### 12.1. Ordem sugerida

1. **Reunião de validação (#25):** resolve ou encaminha AC03, AC04, AC14, AC20 e AC24 de uma vez.
2. **Ajustes de texto nos requisitos (#40):** AC01, AC02, AC06, AC07, AC15, AC16, AC22 e AC23 são edições na lista geral, na especificação e na suplementar.
3. **RIPD preliminar (AC19):** documento novo em `docs/validacao/` ou `docs/levantamento/`.
4. **Acabamento:** AC10, AC11, AC12, AC21 e AC25.

## 13. Pontos fortes observados

- Rastreabilidade bidirecional completa, da fonte à verificação, agora também com processo, arquitetura e projeto.
- As nove características da ISO/IEC 25010:2023 foram consideradas, com a nomenclatura atualizada e verificação definida para cada RNF.
- Pendências e conflitos (C01, C02, PV01 a PV08, D-01 a D-13) registrados de forma explícita, sem decisões inventadas.
- Requisitos de LGPD levantados a partir de fontes primárias (lei e resoluções da ANPD).
- Decisões de arquitetura com justificativa e alternativa descartada.
- Gestão de configuração disciplinada: uma branch e um PR por tarefa, documentos versionados.
