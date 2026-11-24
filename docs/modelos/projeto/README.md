# Modelo de projeto (design)

Autoria: Luiz Augusto Vaz. Versão 0.1 — 21 de novembro de 2026. Situação: **proposta para revisão da equipe**.

Detalha como o sistema cumpre os requisitos por dentro, abaixo do nível 3 da [visão arquitetural C4](../arquitetura/README.md). Segue a sequência de Larman (*Utilizando UML e padrões*): contratos de operação → diagramas de interação → diagrama de classes de projeto, guiados pelos [padrões de projeto](padroes-de-projeto.md). Nenhuma linguagem foi escolhida (AD05): nomes e tipos são ilustrativos.

## 1. Artefatos

| Artefato | Arquivos | Responde |
| --- | --- | --- |
| [Diagramas de estado](#2-diagramas-de-estado) | `estado-*.mmd` | Em que estados vivem coleta, avaliação, plano e ação, e o que muda cada um? |
| [Contratos de operação](#3-contratos-de-operação) | Este README | O que cada operação crítica exige antes e garante depois? |
| [Diagramas de sequência](#4-diagramas-de-sequência) | `sequencia-*.mmd` | Quais objetos colaboram em cada fluxo principal e em que ordem? |
| [Diagrama de classes de projeto](#5-diagrama-de-classes-de-projeto) | `classes-*.mmd` | Quais classes, operações e dependências o sistema terá? |
| [Padrões de projeto](padroes-de-projeto.md) | `padroes-de-projeto.md` | Por que as responsabilidades foram divididas assim (PP01 a PP22)? |

Os diagramas estão em Mermaid: os `.mmd` são as fontes editáveis, e o mesmo conteúdo aparece nos blocos abaixo, que o GitHub desenha direto na página.

## 2. Diagramas de estado

### 2.1. Coleta

RN07, RF09, RF13 — CU-01, CU-03. Implementado com o padrão *State* (PP10). Fonte: [estado-coleta.mmd](estado-coleta.mmd).

```mermaid
stateDiagram-v2
    [*] --> PREPARACAO : configurar coleta (RF08)
    PREPARACAO --> PREPARACAO : editar questionário e participantes
    PREPARACAO --> ABERTA : abrir [questionário válido e pares válidos] / publicar cópia, congelar participantes, gerar avaliações (RF09, RF10, RF17)
    PREPARACAO --> CANCELADA : cancelar [justificativa]
    ABERTA --> ENCERRADA : encerrar / cancelar avaliações em rascunho (RF13)
    ABERTA --> CANCELADA : cancelar [justificativa] / cancelar avaliações em rascunho
    ENCERRADA --> [*]
    CANCELADA --> [*]

    note right of ABERTA
        Respostas aceitas só dentro do período
        (início inclusivo, fim exclusivo).
        Fim do período não encerra sozinho.
    end note
    note right of CANCELADA
        Estados finais não reabrem (RN07).
        Coleta cancelada não entra em análises.
    end note
```

### 2.2. Avaliação

RN08, RF11, RF12 — CU-02, CU-03. Fonte: [estado-avaliacao.mmd](estado-avaliacao.mmd).

```mermaid
stateDiagram-v2
    [*] --> RASCUNHO : coleta aberta gera a avaliação (RF10, RF17, RF22)
    RASCUNHO --> RASCUNHO : salvar respostas [coleta ABERTA e dentro do período] (RF11)
    RASCUNHO --> ENVIADA : enviar [todas as respostas válidas] / registrar enviada_em (RF12)
    RASCUNHO --> CANCELADA : coleta encerrada ou cancelada / registrar motivo (RF13)
    ENVIADA --> [*]
    CANCELADA --> [*]

    note right of ENVIADA
        Respostas imutáveis (RF12).
        Não há retorno a rascunho (RN08).
        O feedback herda este estado.
        Se a coleta for cancelada, a avaliação
        enviada sai das análises pelo estado
        da coleta, sem mudar de estado.
    end note
```

### 2.3. Plano de ação e ação do plano

RF18, RN13 — CU-11. Os estados vêm do [dicionário de dados](../../dicionario-dados.md) (PLANO_ACAO e ACAO_PLANO). Fonte: [estado-plano-acao.mmd](estado-plano-acao.mmd).

```mermaid
stateDiagram-v2
    state "Plano de ação" as PLANO {
        [*] --> ATIVO : criar a partir de um feedback [ao menos uma ação com responsável e prazo]
        ATIVO --> ATIVO : ajustar ações / registrar verificação
        ATIVO --> CONCLUIDO : concluir / vincular o feedback seguinte (RN13)
        ATIVO --> CANCELADO : cancelar [motivo]
        CONCLUIDO --> [*]
        CANCELADO --> [*]
    }

    state "Ação do plano" as ACAO {
        [*] --> PENDENTE
        PENDENTE --> EM_ANDAMENTO : registrar primeiro progresso
        EM_ANDAMENTO --> EM_ANDAMENTO : registrar progresso (registros anteriores preservados)
        PENDENTE --> CONCLUIDA : concluir
        EM_ANDAMENTO --> CONCLUIDA : concluir
        PENDENTE --> CANCELADA : cancelar [motivo]
        EM_ANDAMENTO --> CANCELADA : cancelar [motivo]
        CONCLUIDA --> [*]
        CANCELADA --> [*]
    }
```

## 3. Contratos de operação

Para as operações que mudam vários objetos de uma vez. Formato de Larman: pré-condições (o que precisa ser verdade antes) e pós-condições (o que passa a ser verdade depois, em termos de objetos criados, associações formadas e atributos alterados).

### CO01 — `abrir(idColeta)`

| Campo | Conteúdo |
| --- | --- |
| Caso de uso | CU-01 (e CU-09 para o 360°) |
| Referências | RF09, RF10, RF17, RF22, RN03, RN05, RN14, RN15, RNF02 |
| Pré-condições | Coleta em PREPARACAO; usuário é RH ou gestor com a coleta no seu escopo; há ao menos um grupo com parâmetro; período válido; seleção resulta em ao menos um par ou participante elegível. |
| Pós-condições | Foi criado um `QuestionarioPublicado` com cópia de grupos e parâmetros; os participantes foram congelados; foi criada uma `Avaliacao` em RASCUNHO para cada sentido, par ou papel, conforme a modalidade, sem duplicatas; a coleta passou a ABERTA; foi criado um evento de auditoria. Se qualquer passo falhar, nada disso existe. |

### CO02 — `enviar(idAvaliacao)`

| Campo | Conteúdo |
| --- | --- |
| Caso de uso | CU-02 |
| Referências | RF12, RN06, RN08, RNF02 |
| Pré-condições | Usuário é o avaliador; avaliação em RASCUNHO; coleta ABERTA e dentro do período; há exatamente uma resposta válida para cada parâmetro da coleta. |
| Pós-condições | A avaliação passou a ENVIADA, com `enviada_em` registrado; as respostas ficaram imutáveis; a avaliação do sentido oposto não foi alterada; foi criado um evento de auditoria. |

### CO03 — `encerrar(idColeta)`

| Campo | Conteúdo |
| --- | --- |
| Caso de uso | CU-03 |
| Referências | RF13, RN07, RN08, RN09, RN12, RNF02 |
| Pré-condições | Coleta ABERTA; usuário é RH ou gestor com a coleta no seu escopo. |
| Pós-condições | A coleta passou a ENCERRADA, com `encerrada_em` registrado; cada avaliação em RASCUNHO passou a CANCELADA com motivo; avaliações ENVIADAS foram preservadas; as avaliações enviadas ficaram disponíveis para o gestor ou o RH liberar (RN09); foi criado um evento de auditoria. |

### CO04 — `criarPlano(idFeedback, dados)`

| Campo | Conteúdo |
| --- | --- |
| Caso de uso | CU-11 |
| Referências | RF18, RN13, RN14, CA18 |
| Pré-condições | O feedback de origem existe e foi recebido por um colaborador no escopo de quem cria; há ao menos uma ação com responsável e prazo. |
| Pós-condições | Foi criado um `PlanoAcao` ATIVO associado ao feedback de origem; foram criadas as `AcaoPlano` em PENDENTE, cada uma associada ao responsável; foi criado um evento de auditoria. |

## 4. Diagramas de sequência

Fluxos principais dos casos de uso completos e do CU-11. Os fluxos alternativos estão descritos em cada [caso de uso](../../casos-de-uso/README.md).

### 4.1. Abrir coleta (CU-01)

Contrato CO01. Padrões: *Controller*, *Unit of Work*, *Factory Method*, *Creator*. Fonte: [sequencia-abrir-coleta.mmd](sequencia-abrir-coleta.mmd).

```mermaid
sequenceDiagram
    autonumber
    actor RH as RH ou Gestor
    participant Web as Aplicação web
    participant Ctl as ControladorColeta
    participant Pol as PoliticaVisibilidade
    participant UoW as UnidadeDeTrabalho
    participant Rep as RepositorioColetas
    participant Col as Coleta
    participant Fab as FabricaGeradores
    participant Ger as GeradorAvaliacoes
    participant Aud as Auditoria

    RH->>Web: confirma a prévia e abre a coleta
    Web->>Ctl: abrir(idColeta)
    Ctl->>Pol: podeGerir(usuario, coleta)
    alt fora do escopo (RN14)
        Pol-->>Ctl: não
        Ctl-->>Web: 403 acesso negado
    else autorizado
        Ctl->>UoW: executarEmTransacao
        activate UoW
        UoW->>Rep: porId(idColeta)
        Rep-->>UoW: coleta (PREPARACAO)
        UoW->>Col: abrir(agora)
        Col->>Col: validar questionário e período (RF09)
        Col->>Col: publicar cópia imutável e congelar participantes (RN05)
        Col->>Fab: para(modalidade)
        Fab-->>Col: gerador da modalidade
        Col->>Ger: gerar(coleta)
        Ger-->>Col: avaliações em RASCUNHO, sem duplicatas (RF10, RF17)
        Col->>Col: estado = ABERTA
        UoW->>Rep: salvar(coleta)
        UoW->>Aud: registrar(COLETA_ABERTA)
        deactivate UoW
        Note over UoW: Tudo ou nada: falha em qualquer passo desfaz a abertura (RNF02)
        Ctl-->>Web: coleta aberta e total de avaliações
    end
```

### 4.2. Enviar avaliação (CU-02)

Contrato CO02. Padrões: *Information Expert*, *Strategy*, bloqueio pessimista. Fonte: [sequencia-enviar-avaliacao.mmd](sequencia-enviar-avaliacao.mmd).

```mermaid
sequenceDiagram
    autonumber
    actor Av as Avaliador
    participant Web as Aplicação web
    participant Ctl as ControladorResposta
    participant Pol as PoliticaVisibilidade
    participant UoW as UnidadeDeTrabalho
    participant Rep as RepositorioAvaliacoes
    participant A as Avaliacao
    participant E as Escala
    participant Aud as Auditoria

    Av->>Web: revisa respostas e confirma o envio (RNF13)
    Web->>Ctl: enviar(idAvaliacao)
    Ctl->>Pol: é o avaliador desta avaliação?
    Pol-->>Ctl: sim
    Ctl->>UoW: executarEmTransacao
    activate UoW
    UoW->>Rep: porId(idAvaliacao) com bloqueio
    Rep-->>UoW: avaliação (RASCUNHO)
    UoW->>A: enviar(agora)
    A->>A: coleta aceita respostas? (ABERTA e dentro do período)
    loop cada parâmetro da coleta
        A->>E: validar(valor)
        E-->>A: válido ou inválido (RN06)
    end
    alt alguma resposta ausente ou inválida
        A-->>UoW: erro de validação
        UoW-->>Ctl: desfaz
        Ctl-->>Web: indica as perguntas pendentes
    else completa
        A->>A: status = ENVIADA, respostas imutáveis (RN08)
        UoW->>Rep: salvar(avaliacao)
        UoW->>Aud: registrar(AVALIACAO_ENVIADA)
        Ctl-->>Web: envio confirmado
    end
    deactivate UoW
    Note over A: Enviar A sobre B não preenche nem envia B sobre A (RF12)
```

### 4.3. Encerrar coleta (CU-03)

Contrato CO03. Padrões: *State*, *Unit of Work*, bloqueio pessimista. Fonte: [sequencia-encerrar-coleta.mmd](sequencia-encerrar-coleta.mmd).

```mermaid
sequenceDiagram
    autonumber
    actor RH as RH ou Gestor
    participant Web as Aplicação web
    participant Ctl as ControladorColeta
    participant Pol as PoliticaVisibilidade
    participant UoW as UnidadeDeTrabalho
    participant Rep as RepositorioColetas
    participant Col as Coleta
    participant Aud as Auditoria

    RH->>Web: encerra a coleta
    Web->>Ctl: encerrar(idColeta)
    Ctl->>Pol: podeGerir(usuario, coleta)
    Pol-->>Ctl: sim (RN14)
    Ctl->>UoW: executarEmTransacao
    activate UoW
    UoW->>Rep: porId(idColeta) com bloqueio
    Rep-->>UoW: coleta (ABERTA)
    UoW->>Col: encerrar(agora, motivo)
    Col->>Col: estado ABERTA permite encerrar? (RN07)
    loop cada avaliação em RASCUNHO
        Col->>Col: cancelar com motivo "coleta encerrada" (RN08)
    end
    Note over Col: Avaliações ENVIADAS são preservadas — nada é excluído (RN12)
    Col->>Col: estado = ENCERRADA
    UoW->>Rep: salvar(coleta)
    UoW->>Aud: registrar(COLETA_ENCERRADA)
    deactivate UoW
    Note over UoW: Envios concorrentes esperam o bloqueio: ou entram antes, ou são recusados (RNF02)
    Ctl-->>Web: coleta encerrada — avaliações enviadas disponíveis para liberação (RN09)
```

### 4.4. Consultar resultados (CU-04)

Padrões: *Policy*, *Pure Fabrication*, *Strategy*. Fonte: [sequencia-consultar-resultados.mmd](sequencia-consultar-resultados.mmd).

```mermaid
sequenceDiagram
    autonumber
    actor U as Participante ou Gestor
    participant Web as Aplicação web
    participant Ctl as ControladorAnalise
    participant Pol as PoliticaVisibilidade
    participant Rep as RepositorioAvaliacoes
    participant Calc as CalculadoraIndicadores

    U->>Web: abre os resultados de uma pessoa
    Web->>Ctl: indicadores(idUsuario, filtros)
    Ctl->>Pol: pode ver os resultados desta pessoa? (RN14)
    alt não autorizado
        Pol-->>Ctl: não
        Ctl-->>Web: 403 acesso negado (RNF01)
    else autorizado
        Ctl->>Rep: doReceptor(idUsuario, filtros)
        Rep-->>Ctl: avaliações da pessoa
        loop cada avaliação
            Ctl->>Pol: resultadoLiberado(avaliacao)
            Note right of Pol: Todas as modalidades: liberado pelo gestor ou pelo RH (RN09)
        end
        Ctl->>Calc: mediaNormalizada e percentualSim(respostas liberadas)
        Calc-->>Ctl: indicadores separados por versão da pergunta (RN10, RN11)
        Ctl-->>Web: indicadores e histórico
    end
```

### 4.5. Criar plano de ação (CU-11)

Contrato CO04. Padrões: *Creator*, *Unit of Work*. Fonte: [sequencia-criar-plano-acao.mmd](sequencia-criar-plano-acao.mmd).

```mermaid
sequenceDiagram
    autonumber
    actor G as Gestor ou RH
    participant Web as Aplicação web
    participant Ctl as ControladorFeedback
    participant Pol as PoliticaVisibilidade
    participant UoW as UnidadeDeTrabalho
    participant Rep as RepositorioFeedbacks
    participant P as PlanoAcao
    participant Aud as Auditoria

    G->>Web: cria plano a partir de um feedback recebido pelo colaborador
    Web->>Ctl: criarPlano(idFeedback, metas e ações)
    Ctl->>Pol: o colaborador está no escopo de quem cria? (RN14)
    Pol-->>Ctl: sim
    Ctl->>UoW: executarEmTransacao
    activate UoW
    UoW->>P: novo PlanoAcao(feedback de origem) (RN13)
    loop cada ação acordada
        UoW->>P: adicionarAcao(descricao, responsavel, prazo)
    end
    P->>P: ao menos uma ação com responsável e prazo? (CA18)
    P->>P: status = ATIVO
    UoW->>Rep: salvarPlano(plano)
    UoW->>Aud: registrar(PLANO_CRIADO)
    deactivate UoW
    Ctl-->>Web: plano criado — colaborador vê suas ações
```

## 5. Diagrama de classes de projeto

O [modelo de domínio](../dominio/modelo-dominio.md) mostra conceitos; aqui as classes ganham operações, navegabilidade e as interfaces dos padrões. Atributos completos e tipos continuam no [dicionário de dados](../../dicionario-dados.md).

### 5.1. Camada de domínio

Fonte: [classes-dominio.mmd](classes-dominio.mmd).

```mermaid
classDiagram
    direction TB

    class Coleta {
        -id
        -titulo
        -modalidade : Modalidade
        -periodo : Periodo
        -estado : EstadoColeta
        +adicionarGrupo(grupo GrupoParametro)
        +selecionarParticipantes(selecao)
        +abrir(agora) List~Avaliacao~
        +encerrar(agora, motivo)
        +cancelar(agora, justificativa)
        +aceitaRespostas(agora) bool
    }

    class EstadoColeta {
        <<interface>>
        +abrir(coleta)
        +encerrar(coleta)
        +cancelar(coleta)
        +aceitaRespostas() bool
    }
    class EmPreparacao
    class Aberta
    class Encerrada
    class Cancelada
    EstadoColeta <|.. EmPreparacao
    EstadoColeta <|.. Aberta
    EstadoColeta <|.. Encerrada
    EstadoColeta <|.. Cancelada
    Coleta --> EstadoColeta : estado atual

    class GeradorAvaliacoes {
        <<interface>>
        +gerar(coleta) List~Avaliacao~
    }
    class GeradorReciprocoPares
    class GeradorReciprocoTimes
    class Gerador360
    class GeradorAutoavaliacao
    GeradorAvaliacoes <|.. GeradorReciprocoPares
    GeradorAvaliacoes <|.. GeradorReciprocoTimes
    GeradorAvaliacoes <|.. Gerador360
    GeradorAvaliacoes <|.. GeradorAutoavaliacao
    class FabricaGeradores {
        +para(modalidade) GeradorAvaliacoes
    }
    FabricaGeradores ..> GeradorAvaliacoes : cria
    Coleta ..> FabricaGeradores : usa ao abrir

    class QuestionarioPublicado {
        <<imutável>>
        +grupos : List~GrupoDaColeta~
        +parametros() List~ParametroDaColeta~
    }
    class ParametroDaColeta {
        <<imutável>>
        -pergunta
        -escala : Escala
        -ordem
    }
    Coleta "1" *-- "1" QuestionarioPublicado : publica ao abrir
    QuestionarioPublicado "1" *-- "1..*" ParametroDaColeta

    class Escala {
        <<interface>>
        +validar(valor) bool
        +normalizar(valor) decimal
    }
    class Escala0a10
    class Escala0a5
    class EscalaBooleana
    Escala <|.. Escala0a10
    Escala <|.. Escala0a5
    Escala <|.. EscalaBooleana
    ParametroDaColeta --> Escala

    class Avaliacao {
        -avaliador : Usuario
        -receptor : Usuario
        -papel
        -status : StatusAvaliacao
        +salvarRascunho(respostas, agora)
        +enviar(agora)
        +cancelar(motivo, agora)
        +estaCompleta() bool
    }
    class Feedback {
        -valor
        -comentario
        +validarCom(escala) bool
    }
    Coleta "1" *-- "0..*" Avaliacao : atribui
    Avaliacao "1" *-- "0..*" Feedback : reúne
    Feedback --> ParametroDaColeta : responde

    class RegistroFeedback {
        -fato
        -impacto
        -formalidade
        -tom
        +classificar(formalidade, tom)
    }
    class PlanoAcao {
        -status
        +adicionarAcao(descricao, responsavel, prazo)
        +registrarVerificacao(texto, agora)
        +concluir(feedbackSeguinte)
        +cancelar(motivo)
    }
    class AcaoPlano {
        -status
        +registrarProgresso(texto, agora)
    }
    RegistroFeedback "1" -- "0..*" PlanoAcao : motiva
    PlanoAcao "1" *-- "1..*" AcaoPlano

    class Usuario {
        -perfil : Perfil
        -ativo : bool
        +podeGerir(time) bool
    }
    Avaliacao --> Usuario : avaliador e receptor
```

### 5.2. Camada de aplicação e infraestrutura

Fonte: [classes-aplicacao.mmd](classes-aplicacao.mmd).

```mermaid
classDiagram
    direction LR

    class ControladorColeta {
        +configurar(dados)
        +abrir(idColeta)
        +encerrar(idColeta)
        +cancelar(idColeta, justificativa)
    }
    class ControladorResposta {
        +salvarRascunho(idAvaliacao, respostas)
        +enviar(idAvaliacao)
    }
    class ControladorAnalise {
        +historico(idUsuario, filtros)
        +indicadores(idUsuario, filtros)
    }
    class ControladorFeedback {
        +registrarInformal(dados)
        +criarPlano(idFeedback, dados)
        +registrarProgresso(idAcao, texto)
    }

    class PoliticaVisibilidade {
        <<serviço>>
        +podeVerResultado(usuario, avaliacao) bool
        +podeGerir(usuario, coleta) bool
        +resultadoLiberado(avaliacao) bool
    }
    class CalculadoraIndicadores {
        <<serviço>>
        +mediaNormalizada(respostas) decimal
        +percentualSim(respostas) decimal
        +percentualConclusao(coleta) decimal
    }
    class UnidadeDeTrabalho {
        <<interface>>
        +executarEmTransacao(operacao)
    }
    class Auditoria {
        <<interface>>
        +registrar(evento)
    }
    class RegistroAuditoriaBanco
    Auditoria <|.. RegistroAuditoriaBanco

    class RepositorioColetas {
        <<interface>>
        +porId(id) Coleta
        +salvar(coleta)
    }
    class RepositorioAvaliacoes {
        <<interface>>
        +porId(id) Avaliacao
        +doReceptor(idUsuario, filtros) List~Avaliacao~
        +salvar(avaliacao)
    }
    class RepositorioFeedbacks {
        <<interface>>
        +salvarRegistro(registro)
        +salvarPlano(plano)
    }

    ControladorColeta --> PoliticaVisibilidade
    ControladorColeta --> RepositorioColetas
    ControladorColeta --> UnidadeDeTrabalho
    ControladorColeta --> Auditoria
    ControladorResposta --> PoliticaVisibilidade
    ControladorResposta --> RepositorioAvaliacoes
    ControladorResposta --> UnidadeDeTrabalho
    ControladorResposta --> Auditoria
    ControladorAnalise --> PoliticaVisibilidade
    ControladorAnalise --> RepositorioAvaliacoes
    ControladorAnalise --> CalculadoraIndicadores
    ControladorFeedback --> PoliticaVisibilidade
    ControladorFeedback --> RepositorioFeedbacks
    ControladorFeedback --> Auditoria
```

| Controlador | Componente C4 | Casos de uso | Operações |
| --- | --- | --- | --- |
| `ControladorColeta` | Coletas | CU-01, CU-03, CU-09 | `configurar`, `abrir` (CO01), `encerrar` (CO03), `cancelar` |
| `ControladorResposta` | Respostas | CU-02 | `salvarRascunho`, `enviar` (CO02) |
| `ControladorAnalise` | Análise e histórico | CU-04 | `historico`, `indicadores` |
| `ControladorFeedback` | Feedback e desenvolvimento | CU-10, CU-11 | `registrarInformal`, `criarPlano` (CO04), `registrarProgresso` |

Os componentes Organização (CU-06, CU-07), Catálogo (CU-05) e Autenticação (CU-08) seguem o mesmo formato — um controlador, um repositório e as regras no domínio — e não foram detalhados por serem cadastros sem regras de interação entre objetos.

## 6. Limites

- Os diagramas descrevem os fluxos principais. Os alternativos estão nos casos de uso e devem ser modelados se a disciplina pedir.
- CU-06 a CU-11 têm só descrição resumida; o CU-11 foi modelado aqui a partir do RF18, da RN13 e do CA18.
- A regra de liberação (PV04: pelo gestor ou pelo RH) e a identificação por modalidade (C02, RN-DOC-02) ficam isoladas na `PoliticaVisibilidade`.
- Nada aqui escolhe linguagem, framework ou banco específico.

## 7. Exportar imagens

A partir desta pasta, com o Node.js instalado:

```bash
for f in *.mmd; do npx -y -p @mermaid-js/mermaid-cli mmdc -i "$f" -o "exportacoes/${f%.mmd}.png" -b white -s 2; done
```
