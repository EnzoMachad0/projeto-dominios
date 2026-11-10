# Especificação suplementar

Versão 0.1 — 8 de novembro de 2026. Situação: proposta para validação.

## 1. Objetivo e referência

Este documento detalha os requisitos não funcionais (RNF) do sistema de gestão de competências e feedback. Ele complementa a [especificação de requisitos](especificacao-requisitos.md), que trata dos requisitos funcionais e das regras de negócio. Segundo Larman, a especificação suplementar reúne o que não cabe nos casos de uso: atributos de qualidade, restrições, aspectos legais e de implantação.

**Modelo de qualidade:** ISO/IEC 25010:2023, segunda edição, com a nomenclatura de 2023 adotada na [pesquisa documental](../levantamento/pesquisa-documental.md). Os termos em português são traduções livres da equipe, pois a versão ABNT alinhada a 2023 não foi confirmada (D-11).

**Identificadores:** os mesmos da [lista geral](lista-geral.md). Entre parênteses aparece o requisito documental consolidado (`RNF-DOC-xx`).

## 2. Como ler cada requisito

Cada RNF informa:

- **Requisito:** o que o sistema deve atender.
- **Condição:** em que situação o requisito é avaliado.
- **Verificação:** como a equipe comprova o atendimento.
- **Situação:** *Proposto* ou *Pendente*. Metas numéricas ainda não acordadas com o stakeholder são marcadas como **meta proposta** e não são decisões validadas.

## 3. Requisitos por característica de qualidade

### 3.1. *Security* — segurança da informação

Característica de relevância alta: protege feedbacks, resultados e identidade dos avaliadores, e se relaciona diretamente ao art. 46 da LGPD.

| ID | Subcaracterística | Requisito | Condição | Verificação | Situação |
| --- | --- | --- | --- | --- | --- |
| RNF01 (RNF-DOC-01) | *Confidentiality* | Toda operação deve validar autenticação e autorização no servidor conforme perfil e vínculo com o avaliado, negando o acesso por padrão. | Qualquer requisição, inclusive acesso direto pelo identificador do registro. | Testes automatizados de autorização por perfil, incluindo CA02. | Proposto |
| RNF06 (RNF-DOC-06) | *Accountability*, *non-repudiation* | Registrar usuário, ação, objeto e instante das mudanças administrativas e transições de estado, em registro que perfis comuns não alteram nem excluem. | Toda operação que altera dados ou estados. | Inspeção dos eventos após roteiro de operações; tentativa de alteração por perfil comum deve falhar. | Proposto |
| RNF07 | *Confidentiality* | Restringir os dados ao escopo autorizado e não registrar conteúdo de respostas ou comentários em logs técnicos. | Logs de aplicação e de erro. | Inspeção de logs após preencher e enviar avaliações de teste. | Pendente (PV05) |
| RNF08 (RNF-DOC-04) | *Confidentiality* | Toda comunicação entre cliente e servidor deve usar TLS/HTTPS. | Ambiente de produção. | Varredura da configuração TLS e tentativa de acesso por HTTP, que deve ser redirecionado. | Proposto |
| RNF09 (RNF-DOC-03) | *Authenticity* | Autenticação individual com política de complexidade de senha, sem credenciais padrão, e autenticação multifator para o perfil RH. | Login e criação de conta. | Testes de cadastro com senhas fracas e de login do RH sem segundo fator. | Proposto |
| RNF10 (RNF-DOC-05) | *Confidentiality* | Credenciais armazenadas com *hash* adaptativo; comentários e vínculos de identidade protegidos contra leitura em cópia indevida da base. | Armazenamento em banco e em backup. | Inspeção do banco de homologação. | Proposto |
| RNF11 (RNF-DOC-08) | *Resistance* | Limitar tentativas sucessivas de autenticação e não liberar versão com vulnerabilidade crítica conhecida. | Login e liberação de versão. | Teste de força bruta controlado e relatório de análise de dependências. Limite e ferramenta: a definir. | Pendente (D-12) |
| RNF16 (RNF-DOC-02) | *Confidentiality* | Em avaliações anônimas, nenhuma tela, relatório, exportação ou auditoria acessível aos perfis deve revelar o autor. | Somente se o anonimato for adotado. | Revisão de todas as saídas com dados de teste. | Pendente (conflito C02) |

### 3.2. *Functional suitability* — adequação funcional

| ID | Subcaracterística | Requisito | Condição | Verificação | Situação |
| --- | --- | --- | --- | --- | --- |
| RNF12 (RNF-DOC-10) | *Functional correctness* | Cada indicador deve ter fórmula documentada (RN10) e reproduzir o resultado esperado em casos de referência. | Cálculo de médias, proporções e conclusão. | Casos de teste do CA10 e planilha de referência comparada com o sistema. | Proposto |

### 3.3. *Reliability* — confiabilidade

| ID | Subcaracterística | Requisito | Condição | Verificação | Situação |
| --- | --- | --- | --- | --- | --- |
| RNF02 (RNF-DOC-07) | *Faultlessness*; *Security* / *integrity* | Abertura da coleta, geração das avaliações e envio devem ser transacionais; requisições simultâneas não podem gerar duplicatas nem respostas parciais. | Operações concorrentes sobre a mesma coleta ou avaliação. | Teste de concorrência com requisições paralelas (CA06, CA08). | Proposto |
| RNF05 (RNF-DOC-09) | *Recoverability* | Backup diário, completo, em local separado e sem sincronização em tempo real. **Meta proposta:** perda máxima de 24 h e restauração em até 4 h. | Falha do banco de dados. | Simulação de restauração em homologação, com tempo medido. | Pendente (PV07) |

### 3.4. *Performance efficiency* — eficiência de desempenho

| ID | Subcaracterística | Requisito | Condição | Verificação | Situação |
| --- | --- | --- | --- | --- | --- |
| RNF04 (RNF-DOC-15) | *Time behaviour*, *capacity* | **Meta proposta:** 95% das consultas paginadas de cadastros, histórico e análise em até 2 s. | 50 usuários simultâneos e base de até 100.000 respostas, em homologação documentada. | Ensaio de carga com registro de infraestrutura e massa de dados. | Pendente (PV07) |

### 3.5. *Interaction capability* — capacidade de interação

| ID | Subcaracterística | Requisito | Condição | Verificação | Situação |
| --- | --- | --- | --- | --- | --- |
| RNF03 (RNF-DOC-13) | *Inclusivity*, *operability* | Fluxos de preenchimento operáveis por teclado, com rótulos e mensagens de erro textuais. Nível de acessibilidade de referência (por exemplo, WCAG 2.2 AA): a definir. | Telas de login, preenchimento e envio. | Roteiro de uso somente com teclado e verificação automática de acessibilidade. | Proposto |
| RNF13 (RNF-DOC-11, RNF-DOC-12) | *Self-descriptiveness*, *user error protection* | A tela de resposta deve informar quem poderá ver o conteúdo e quando; deve preservar rascunhos e pedir confirmação antes do envio definitivo. | Preenchimento de avaliação (CU-02). | Teste de usabilidade com roteiro e inspeção das telas. | Proposto |

### 3.6. *Flexibility* — flexibilidade

| ID | Subcaracterística | Requisito | Condição | Verificação | Situação |
| --- | --- | --- | --- | --- | --- |
| RNF03 (RNF-DOC-14) | *Adaptability* | A interface web deve funcionar em larguras de 360 a 1.440 px sem rolagem horizontal nos formulários, preparando o uso futuro em dispositivos móveis. | Navegadores atuais em celular e computador. | Teste nas larguras-limite. | Proposto |

### 3.7. *Maintainability* — manutenibilidade

| ID | Subcaracterística | Requisito | Condição | Verificação | Situação |
| --- | --- | --- | --- | --- | --- |
| RNF14 (RNF-DOC-16) | *Testability* | Regras de visibilidade por perfil e de liberação de resultados (RN09) devem ser cobertas por testes automatizados. | Cada liberação de versão. | Relatório de testes. | Proposto |

### 3.8. *Compatibility* — compatibilidade

| ID | Subcaracterística | Requisito | Condição | Verificação | Situação |
| --- | --- | --- | --- | --- | --- |
| RNF15 (RNF-DOC-17) | *Interoperability* | Se houver integração com sistemas de RH, a troca deve usar formato documentado e transmitir apenas os dados necessários. | Somente se houver integração. | Revisão do contrato de integração. | Pendente (D-01) |

### 3.9. *Safety* — segurança operacional

Não se aplica nesta versão: o sistema não controla equipamentos nem processos físicos. Danos à privacidade e à reputação foram tratados em *Security*.

## 4. Privacidade, confidencialidade e anonimato

- **Base:** a LGPD se aplica, pois notas, comentários e histórico são dados pessoais do avaliado e do avaliador. Requisitos funcionais de apoio ao titular estão na [lista geral](lista-geral.md) (RF-DOC-01 a RF-DOC-14).
- **Política da primeira versão (proposta da E01):** avaliação identificada, com acesso limitado por perfil e liberação somente após o par completo e a coleta encerrada (RN09). Não há promessa de anonimato, especialmente em pares de duas pessoas.
- **Anonimato:** citado no enunciado e no README, mas ainda não decidido (conflito C02). Se adotado, "anônimo" na interface não equivale a "anonimizado" na LGPD enquanto existir vínculo recuperável entre resposta e autor.
- **Retenção:** a regra de não haver exclusão física (RN12) conflita com a eliminação prevista na LGPD (conflito C01, PV05).

## 5. Restrições de projeto e implantação

| Tema | Restrição | Situação |
| --- | --- | --- |
| Plataforma | Aplicação web acessada por navegador. | Proposto |
| Idioma | Interface em português. | Proposto |
| Armazenamento | Banco de dados relacional. | Proposto |
| Tecnologia | Linguagem, framework, hospedagem e provedor de identidade não definidos. | Em aberto |
| Integrações | Nenhuma integração obrigatória na primeira versão. | Proposto |

## 6. Pendências

| Pendência | RNF afetados | Quem decide |
| --- | --- | --- |
| PV05 — política de privacidade e retenção | RNF07, conflito C01 | Stakeholder e professor |
| PV07 — metas de desempenho, recuperação e limites | RNF04, RNF05 | Stakeholder |
| D-03 / C02 — anonimato | RNF16 | Stakeholder e professor |
| D-12 — metas sem valor nas fontes | RNF03, RNF11 | Stakeholder e equipe |
| D-01 — integrações | RNF15 | Stakeholder |
