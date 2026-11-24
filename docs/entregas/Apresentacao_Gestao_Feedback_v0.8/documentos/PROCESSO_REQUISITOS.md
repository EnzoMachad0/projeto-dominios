# Processo de requisitos

## 1. Objetivo

Este documento explica como a equipe vai levantar, organizar, documentar e validar os requisitos de um sistema web de avaliação e feedback.

O levantamento deve esclarecer como funcionam as avaliações, quem participa, quais informações são necessárias e como os resultados serão utilizados. Serão investigados os tipos de feedback, os questionários, a confidencialidade e o anonimato, o histórico e o acompanhamento de metas e planos de melhoria. Também serão consideradas a futura utilização em dispositivos móveis e a proteção de dados pessoais.

## 2. Organização do trabalho

As atividades serão distribuídas entre os integrantes e acompanhadas em um quadro Kanban, com as colunas **A fazer**, **Em andamento**, **Em revisão** e **Concluído**. Cada atividade terá um responsável e um prazo.

A equipe será responsável pelo levantamento e pela documentação. O stakeholder ajudará a explicar o processo de negócio, esclarecer dúvidas e confirmar os entendimentos. Os documentos serão armazenados e versionados no GitHub, na pasta `docs/`.

## 3. Etapas do processo

### 3.1. Levantar as informações

A equipe utilizará as seguintes fontes:

- **Documentos de apoio:** identificar o escopo inicial e pesquisar documentos relevantes, incluindo a LGPD e a ISO/IEC 25010.
- **Duas entrevistas:** preparar perguntas, conversar com os participantes, registrar as respostas e produzir as transcrições e a síntese dos requisitos identificados.
- **Dois questionários:** coletar respostas de pessoas diferentes das entrevistadas, guardar os questionários preenchidos e sintetizar os requisitos encontrados.
- **Um sistema análogo:** analisar suas funcionalidades e registrar o que pode contribuir para o projeto.

As entrevistas e os questionários terão os dados de identificação necessários para registrar a origem das informações. Antes de publicar esses registros, a equipe definirá o acesso adequado para preservar os dados pessoais dos participantes.

**Resultado:** registros das fontes consultadas, transcrições, questionários respondidos e sínteses dos requisitos.

### 3.2. Entender o processo de negócio

Com base nas informações coletadas, a equipe descreverá como a avaliação e o feedback acontecem atualmente, quem participa, quais são as principais dificuldades e quais melhorias são esperadas.

Esse entendimento será representado em um diagrama BPMN. Dúvidas e informações ainda não confirmadas serão registradas para esclarecimento com o stakeholder.

**Resultado:** processo de negócio em BPMN e definição inicial do problema, dos objetivos e do escopo.

### 3.3. Organizar e priorizar os requisitos

A equipe reunirá os requisitos identificados nas diferentes fontes, eliminará duplicidades e resolverá contradições. Eles serão classificados em:

- **Requisitos funcionais (RF):** o que o sistema deve permitir fazer.
- **Requisitos não funcionais (RNF):** condições de qualidade e restrições que o sistema deve atender.
- **Regras de negócio (RN):** condições do processo de avaliação que orientam o comportamento do sistema.

Cada item terá um identificador, uma descrição clara, sua fonte, prioridade e situação, como **proposto**, **validado** ou **pendente**. A prioridade será discutida com o stakeholder para definir o que é essencial e o que pode ficar para uma versão futura.

As descrições devem permitir verificar o atendimento ao requisito. Informações não confirmadas serão marcadas como pendentes, sem serem tratadas como decisões do stakeholder.

**Resultado:** lista geral de requisitos, com prioridades e vínculo com suas fontes.

### 3.4. Produzir os artefatos

Os requisitos organizados servirão de base para os documentos e modelos da entrega:

| Artefato | O que será registrado |
| --- | --- |
| Documento de visão | Problema, objetivos, envolvidos, escopo e principais funcionalidades. |
| Diagrama e descrição dos casos de uso | Interações entre os usuários e o sistema, incluindo pelo menos um caso de uso completo por integrante. |
| Especificação de requisitos | Requisitos detalhados, seguindo a estrutura IEEE 830 e/ou EOR. |
| Especificação suplementar | Requisitos não funcionais, considerando a ISO/IEC 25010. |
| Modelo entidade-relacionamento/modelo de domínio | Principais dados e conceitos do sistema e seus relacionamentos. |
| Dicionário de dados e glossário | Termos, definições, formatos, tipos, tamanhos, unidades, relacionamentos e regras de validação, conforme aplicável. |
| Protótipos no Figma | Telas e fluxos que ajudem a visualizar e discutir o funcionamento do sistema. |
| Matriz de rastreabilidade | Relações entre requisitos, fontes e artefatos, contemplando a rastreabilidade horizontal e vertical. |

O documento de visão e os casos de uso seguirão as orientações propostas por Larman. Os arquivos exportados e os links dos protótipos serão registrados no repositório.

**Resultado:** documentação e modelos coerentes com os requisitos levantados.

### 3.5. Revisar e validar

A equipe revisará os documentos para identificar informações incompletas, contradições, requisitos duplicados e descrições vagas. Também verificará se os modelos e protótipos estão de acordo com os requisitos.

Os principais entendimentos, fluxos e prioridades serão apresentados ao stakeholder para confirmar se representam suas necessidades. As correções e as dúvidas restantes serão registradas, com responsável pelo acompanhamento.

**Resultado:** requisitos revisados e registro do que foi validado e do que continua pendente.

## 4. Mudanças durante o trabalho

O processo poderá voltar a etapas anteriores quando surgirem novas informações. Cada alteração relevante terá sua origem e justificativa registradas em uma issue ou no histórico do documento. A equipe avaliará os documentos afetados e atualizará os requisitos, modelos, protótipos e vínculos de rastreabilidade necessários.

## 5. Entrega

Até **10/11/2026**, a equipe reunirá no repositório o planejamento Kanban, este processo de requisitos, os registros e as sínteses do levantamento e todos os artefatos descritos acima. Antes da apresentação, verificará se os arquivos e links estão acessíveis e se a documentação está consistente.
