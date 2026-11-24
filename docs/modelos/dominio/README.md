# Modelos de domínio e de dados

## Opção de modelagem adotada

A equipe adotou **os dois modelos**, com papéis diferentes:

| Modelo | Nível | Pergunta que responde | Documento |
| --- | --- | --- | --- |
| Modelo de domínio | Conceitual (Larman, cap. 9) | Quais conceitos existem no negócio e como se relacionam? | [modelo-dominio.md](modelo-dominio.md) |
| Modelo entidade-relacionamento (MER) | Lógico | Como esses conceitos serão armazenados, com chaves, cardinalidades e restrições? | [modelo-entidade-relacionamento.md](modelo-entidade-relacionamento.md) |

O modelo de domínio usa a notação de classes da UML apenas com conceitos e associações, sem operações nem detalhes de implementação. O MER usa a notação pé de galinha (*crow's foot*) e detalha chaves primárias, estrangeiras e unicidades. Os atributos completos, com tipos e validações, estão no [dicionário de dados](../../dicionario-dados.md).

## Arquivos

| Arquivo | Tipo | Conteúdo |
| --- | --- | --- |
| [modelo-dominio.md](modelo-dominio.md) | Descrição | Conceitos, linguagem do negócio, responsabilidades, fluxo e exemplos. |
| [modelo-entidade-relacionamento.md](modelo-entidade-relacionamento.md) | Descrição | Entidades, chaves, restrições, cancelamento e auditoria. |
| [modelo-dominio.mmd](modelo-dominio.mmd) | Fonte editável | Diagrama de classes conceitual em Mermaid. |
| [mer-organizacao-catalogo.mmd](mer-organizacao-catalogo.mmd) | Fonte editável | MER da estrutura organizacional e do catálogo de perguntas. |
| [mer-coletas-respostas.mmd](mer-coletas-respostas.mmd) | Fonte editável | MER das coletas, avaliações e respostas, com as modalidades recíproca, 360° e autoavaliação. |
| [mer-feedback-desenvolvimento.mmd](mer-feedback-desenvolvimento.mmd) | Fonte editável | MER dos registros de feedback e dos planos de ação. |
| `exportacoes/*.png` | Exportação | Imagens geradas a partir das fontes. |

As fontes podem ser editadas em qualquer editor de texto e visualizadas no GitHub, no [Mermaid Live Editor](https://mermaid.live) ou no VS Code com extensão compatível. Para regenerar as exportações:

```bash
npx -p @mermaid-js/mermaid-cli mmdc -i modelo-dominio.mmd -o exportacoes/modelo-dominio.png -b white -s 2
```

## Entidades e rastreabilidade

| Conceito (domínio) | Entidade (MER) | Requisitos | Casos de uso |
| --- | --- | --- | --- |
| Usuário | USUARIO | RF01, RF02 | CU-06, CU-08 |
| Time | TIME | RF03 | CU-06 |
| Relação de trabalho | RELACAO_TRABALHO | RF04 | CU-07 |
| Grupo de parâmetros e Parâmetro | GRUPO_PARAM, PARAM | RF05, RF06, RF07 | CU-05 |
| Coleta | COLETA, COLETA_TIME, COLETA_PAR | RF08, RF09, RF13 | CU-01, CU-03 |
| Participante selecionado | COLETA_PARTICIPANTE | RF17, RF22, RN15 | CU-09 |
| Grupo e Parâmetro da coleta | COLETA_GRUPO, COLETA_PARAM | RF09, RN04, RN05 | CU-01 |
| Avaliação | AVALIACAO | RF10, RF12, RF17, RF22, RN01 a RN03, RN15 | CU-01, CU-02, CU-09 |
| Registro de feedback | REGISTRO_FEEDBACK | RF19, RF20, RF21, RN16 | CU-02, CU-10 |
| Plano de ação, ação e acompanhamento | PLANO_ACAO, ACAO_PLANO, ACOMPANHAMENTO_ACAO | RF18, RN13, RN14 | CU-11 |
| Feedback | FEEDBACK | RF11, RF12, RN06 | CU-02 |
| Histórico e análise | Consultas sobre AVALIACAO e FEEDBACK | RF14, RF15, RN09 a RN11 | CU-04 |
| — | EVENTO_AUDITORIA | RF16, RNF06 | Todos os que alteram dados |

Os identificadores de requisitos seguem a [lista geral](../../requisitos/lista-geral.md) e os de casos de uso seguem o [índice de casos de uso](../../casos-de-uso/README.md).

## Dúvidas registradas

- Os requisitos documentais de eliminação e anonimização (RF-DOC-07 e RF-DOC-08) seguem a decisão da PV05 (conflito C01 resolvido): sem exclusão física no uso operacional e anonimização irreversível ao fim do prazo de retenção (RN12).
- O 360°, a autoavaliação, o feedback informal, a classificação e os planos de ação (RF17 a RF22) foram modelados na consolidação da issue #40. O anonimato segue a identificação por modalidade (RN-DOC-02, conflito C02 resolvido).
- As imagens em `exportacoes/` foram regeradas a partir das fontes `.mmd` em 23/11/2026, incluindo o MER de feedback e desenvolvimento.
- Multiplicidade de perfis por conta, gestor único por time e grupo único por parâmetro foram validados (PV01 e PV06; E01, E02).
