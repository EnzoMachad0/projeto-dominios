# Padrões de projeto

Autoria: Luiz Augusto Vaz. Versão 0.1 — 21 de novembro de 2026. Situação: **proposta para revisão da equipe**.

Este documento diz quais padrões de projeto o sistema adota e por quê, sempre a partir de um requisito. Os padrões aparecem nos [diagramas de classes e de sequência](README.md) e se encaixam nos componentes da [visão arquitetural C4](../arquitetura/README.md). Como a tecnologia ainda não foi escolhida, os padrões são descritos de forma independente de linguagem.

Três famílias são usadas:

- **GRASP** (Larman, *Utilizando UML e padrões*, cap. 17 e 25): princípios para decidir qual classe recebe cada responsabilidade. O grupo já segue Larman na visão e no modelo de domínio.
- **GoF** (Gamma et al., *Padrões de projeto*): soluções clássicas para problemas recorrentes entre classes.
- **Arquiteturais e de persistência** (Fowler, *Padrões de arquitetura de aplicações corporativas*): organização das camadas e do acesso a dados.

## 1. GRASP — atribuição de responsabilidades

| ID | Padrão | Onde é aplicado | Responsabilidade atribuída | Motivo (requisito) |
| --- | --- | --- | --- | --- |
| PP01 | *Information Expert* (Especialista) | `Avaliacao.estaCompleta()`, `Coleta.aceitaRespostas()`, `Escala.validar()` | Quem tem os dados faz a verificação: a avaliação conhece suas respostas, a coleta conhece seu período e estado, a escala conhece seus limites. | RF12, RN06, RN07 |
| PP02 | *Creator* (Criador) | `Coleta` cria `Avaliacao` e `QuestionarioPublicado`; `PlanoAcao` cria `AcaoPlano` | Quem contém (composição) cria. A coleta agrega as avaliações e o questionário publicado; o plano agrega suas ações. | RF09, RF10, RF18 |
| PP03 | *Controller* (Controlador) | `ControladorColeta`, `ControladorResposta`, `ControladorAnalise`, `ControladorFeedback` | Um controlador por grupo de casos de uso recebe as operações do sistema vindas da interface e coordena o domínio, sem conter regra de negócio. | CU-01 a CU-04, CU-10, CU-11 |
| PP04 | *Low Coupling* (Baixo acoplamento) | Controladores dependem de interfaces (`RepositorioColetas`, `Auditoria`, `UnidadeDeTrabalho`) | Troca do banco ou da forma de auditar sem mexer no domínio. | AD05 (tecnologia em aberto) |
| PP05 | *High Cohesion* (Alta coesão) | Componentes C4 de nível 3 e seus controladores | Cada componente trata um assunto: coletas, respostas, análise, feedback. | C4 nível 3 |
| PP06 | *Polymorphism* (Polimorfismo) | `Escala` (0–10, 0–5, booleana), `GeradorAvaliacoes` (por modalidade), `EstadoColeta` | O comportamento que varia por tipo fica em subclasses, e não em `if`/`switch` espalhados. | RN06, RN15, RN07 |
| PP07 | *Pure Fabrication* (Invenção pura) | `PoliticaVisibilidade`, `CalculadoraIndicadores`, repositórios | Classes que não existem no domínio, criadas para manter o domínio coeso e as regras transversais em um só lugar. | RN09, RN10, RNF14 |
| PP08 | *Indirection* (Indireção) | `Auditoria` entre os controladores e o banco | Quem faz a operação não conhece onde o evento é gravado. | RF16, RNF06 |
| PP09 | *Protected Variations* (Variações protegidas) | Interfaces `Escala`, `GeradorAvaliacoes` e `PoliticaVisibilidade` | Os pontos que ainda dependem de decisão do stakeholder ficam atrás de interfaces: novas escalas, novas modalidades e a regra de liberação (PV04) ou de anonimato (C02). | PV04, C02, RN15 |

## 2. GoF — padrões clássicos

| ID | Padrão | Classes | Problema que resolve | Requisitos |
| --- | --- | --- | --- | --- |
| PP10 | *State* | `Coleta` + `EstadoColeta` (`EmPreparacao`, `Aberta`, `Encerrada`, `Cancelada`) | A coleta tem transições permitidas e proibidas. Cada estado responde por si se pode abrir, encerrar, cancelar ou aceitar respostas, e um estado final simplesmente recusa tudo. Ver o [diagrama de estados da coleta](README.md#21-coleta). | RN07, RF13 |
| PP11 | *Strategy* | `Escala` (`Escala0a10`, `Escala0a5`, `EscalaBooleana`) | Validar e normalizar a resposta muda conforme o tipo copiado na coleta. A calculadora de indicadores chama `normalizar()` sem saber qual escala é. | RN06, RN10, RNF12 |
| PP12 | *Factory Method* | `FabricaGeradores` + `GeradorAvaliacoes` (`GeradorReciprocoPares`, `GeradorReciprocoTimes`, `Gerador360`, `GeradorAutoavaliacao`) | Cada modalidade gera as avaliações de um jeito: dois sentidos por par, todos os pares de um time, uma por participante e papel, ou avaliador igual ao receptor. A coleta pede o gerador à fábrica e não conhece as regras de cada modalidade. | RF10, RF17, RF22, RN01, RN15 |
| PP13 | *Observer* (síncrono) | Operações do domínio publicam eventos; `Auditoria` os registra | Toda mudança administrativa gera um evento de auditoria sem que cada operação precise montar o registro. É síncrono e na mesma transação, como define a AD03. | RF16, RNF06, AD03 |
| PP14 | *Template Method* | `GeradorAvaliacoes` | Os geradores compartilham o mesmo esqueleto: validar elegibilidade (RN03), gerar, remover duplicatas (RN02). Só o passo "gerar" muda por modalidade. | RN02, RN03 |

## 3. Arquiteturais e de persistência

| ID | Padrão | Onde | Problema que resolve | Requisitos |
| --- | --- | --- | --- | --- |
| PP15 | Camadas (*Layers*) | Apresentação (aplicação web) → Aplicação (controladores) → Domínio → Infraestrutura (repositórios, banco) | Cada camada só conhece a de baixo. O domínio não depende de banco nem de tela. | AD01, AD05 |
| PP16 | *Repository* | `RepositorioColetas`, `RepositorioAvaliacoes`, `RepositorioFeedbacks` | O domínio pede objetos por interface, e a forma de guardar fica na infraestrutura. Consultas operacionais filtram registros ativos, e consultas históricas autorizadas veem tudo. | RN12 |
| PP17 | *Unit of Work* | `UnidadeDeTrabalho.executarEmTransacao` | Abrir a coleta, gerar as avaliações e registrar a auditoria são confirmados juntos ou desfeitos juntos. O mesmo vale para o envio e o encerramento. | RNF02, RN01, AD03 |
| PP18 | Bloqueio pessimista (*Pessimistic Offline Lock*) | Leitura "com bloqueio" nos diagramas de envio e encerramento | Um envio e um encerramento simultâneos na mesma coleta não podem deixar uma resposta pela metade. | RNF02 |
| PP19 | *Policy* / *Specification* | `PoliticaVisibilidade` | A regra "quem vê o quê e quando" fica em um único lugar, testável isoladamente, em vez de repetida em cada tela e consulta. | RN09, RN14, RN15, RNF01, RNF14, AD02 |
| PP20 | Exclusão lógica (*Soft Delete*) | Todas as entidades (campos de ativo, cancelado e motivo) | Nada é apagado: cadastros são desativados, coletas e avaliações são canceladas. | RN12 |
| PP21 | *Snapshot* (cópia imutável) | `QuestionarioPublicado`, `ParametroDaColeta` | A coleta guarda uma cópia do questionário no momento da abertura. Mudar o catálogo depois não altera coletas publicadas nem resultados históricos. | RF07, RF09, RN05, RN11 |
| PP22 | *Data Transfer Object* | Respostas da API para a aplicação web | A API devolve só o que o perfil pode ver, e nunca a entidade inteira. | RNF01, RNF07, RNF16 |

## 4. Padrões considerados e não adotados

| Padrão | Motivo para não adotar agora |
| --- | --- |
| Microsserviços | Descartado na AD01: as regras dependem de transações únicas, e o volume previsto é pequeno. |
| *Event Sourcing* | A auditoria simples (PP13) atende o RF16. Reconstruir estado a partir de eventos aumentaria a complexidade sem requisito que peça isso. |
| CQRS completo | As consultas de análise (RF14, RF15) cabem no mesmo modelo. Pode ser revisto se as metas do RNF04 exigirem. |
| *Singleton* | Não há recurso que precise de instância única no domínio. Configurações e conexões ficam a cargo da tecnologia escolhida. |

## 5. Pontos que dependem de decisão

- **Anonimato (C02, resolvido):** nas coletas recíprocas e no 360° (exceto o gestor direto), a `PoliticaVisibilidade` (PP19) e o DTO (PP22) escondem o autor; pode ser preciso separar o vínculo entre resposta e autor no banco. As interfaces de PP09 foram pensadas para essa mudança.
- **Liberação (PV04, resolvida):** feita pelo gestor ou pelo RH em todas as modalidades; fica na `PoliticaVisibilidade`.
- **Novas escalas ou modalidades:** entram como uma nova `Escala` (PP11) ou um novo `GeradorAvaliacoes` (PP12), sem alterar as classes existentes.
