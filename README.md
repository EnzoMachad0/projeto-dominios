# Gestão de Competências e Feedback

Projeto acadêmico desenvolvido para a disciplina de Domínios de Software, com o objetivo de especificar um sistema web para gestão de competências e avaliação de desempenho por meio de feedbacks.

## Atividades previstas

- Avaliações por gestores, colegas e feedback 360°.
- Questionários para avaliação de competências.
- Relatórios e indicadores de desempenho.
- Histórico de feedbacks e acompanhamento de evolução.
- Planos de desenvolvimento individual.
- Confidencialidade, anonimato e proteção de dados conforme a LGPD.

## Tecnologias e ferramentas

- Figma — prototipação das interfaces.
- Git e GitHub — controle de versão e documentação.
- BPMN e UML — modelagem de processos e casos de uso.
- Modelo C4 — visão arquitetural de alto nível ([docs/modelos/arquitetura](docs/modelos/arquitetura)).
- UML de projeto e padrões de projeto (GRASP, GoF) — estados, sequências e classes ([docs/modelos/projeto](docs/modelos/projeto)).

## Status do projeto

Primeira etapa (levantamento e especificação de requisitos) com 16 de 19 entregáveis do enunciado prontos, 1 parcial (BPMN a validar) e 2 pendentes (questionários e sua síntese). A [documentação mestre e o roteiro da apresentação na v1.2](docs/entregas) já incluem a visão arquitetural C4, o modelo e os padrões de projeto e a [auditoria de conformidade com normas ISO](docs/auditoria/auditoria-conformidade-iso.md).

As entrevistas E01 e E02 foram feitas oralmente e não foram gravadas. Por isso, em vez de transcrições, o registro de cada uma é o resumo anotado das respostas, em [docs/levantamento/entrevistas](docs/levantamento/entrevistas), e os requisitos identificados estão na [síntese das entrevistas](docs/levantamento/sintese-entrevistas.md).

### O que ainda falta

| Pendência | Issue |
| --- | --- |
| Atualizar o roteiro da apresentação e os slides 14 e 26, que ainda tratam as transcrições como pendentes | #41 |
| Aplicar os dois questionários e sintetizar seus requisitos | #7, #8 |
| Validar o BPMN do processo atual e do proposto ([docs/modelos/processo](docs/modelos/processo)) | #10 |
| Validar escopo, prioridades, pendências PV e conflitos C01 e C02 com o stakeholder ([pauta](docs/validacao/pauta-validacao-stakeholder.md)) | #25 |
| Revisar a visão arquitetural C4 e o modelo de projeto, e confirmar com o stakeholder a necessidade de notificação por e-mail (lacuna A01) | #25 |
| Tratar os 5 achados maiores da [auditoria de normas ISO](docs/auditoria/auditoria-conformidade-iso.md): metas de RNF, validação, disponibilidade, retenção (C01) e RIPD | #25, #40 |
| Regerar as imagens dos diagramas a partir dos `.mmd` (MER, modelo de domínio e casos de uso) e exportar o MER de feedback e desenvolvimento, que ainda não tem imagem | #40 |
| Ligar cada tela do [protótipo no Figma](#protótipo) aos requisitos na matriz de rastreabilidade (lacuna L03) e testar o protótipo com usuários (achado AC21) | — |
| Adicionar ao repositório a versão em PowerPoint da apresentação, depois da revisão | — |

## Planejamento das atividades

O planejamento e o acompanhamento das atividades estão no [quadro Kanban do GitHub Projects](https://github.com/users/EnzoMachad0/projects/1).

## Protótipo

As telas e os fluxos do sistema estão no [protótipo PulsarRH no Figma](https://www.figma.com/design/pD7rcKYlK7cQ0M5KidV1kL/PulsarRH?node-id=1-3&t=DMEMqjiEkqlY5LWK-1).

## Objetivo acadêmico

Aplicar técnicas de Engenharia de Requisitos para identificar necessidades dos usuários, documentar requisitos e modelar uma solução alinhada às necessidades de gestão de competências e feedback.

## Contexto academico

| Campo | Informacao |
| --- | --- |
| Instituicao | Universidade Federal de Goias (UFG) |
| Unidade | Instituto de Informatica |
| Curso | Bacharelado em Engenharia de Software |
| Disciplina | Domínios de Software |
| Semestre | 2026/2 |

## Equipe

- Brenner Rodrigues Sardinha
- Danilo Sucupira Galvão
- Enzo de Oliveira Machado
- Heitor Barbosa Souza
- Luiz Augusto vaz 
