# Processo de requisitos

## 1. Objetivo e aplicação

Estabelecer e manter um conjunto de requisitos que represente as necessidades das partes interessadas, seja viável e permita verificar e validar a solução desenvolvida.

Este processo é geral e pode ser aplicado a qualquer domínio. É uma definição simplificada para o projeto, baseada principalmente na ISO/IEC/IEEE 29148:2018 e nos processos de ciclo de vida da ISO/IEC/IEEE 12207:2026 e da ISO/IEC/IEEE 15288:2023. A simplificação organiza as atividades e os registros; não constitui uma declaração de conformidade integral às normas.

## 2. Responsabilidades

| Papel | Responsabilidade |
| --- | --- |
| Partes interessadas ou representantes designados | Informar necessidades e restrições, esclarecer dúvidas, validar os requisitos e registrar concordância. |
| Responsável pelos requisitos | Conduzir as atividades, documentar requisitos e decisões, manter versões e rastreabilidade. |
| Equipe técnica | Avaliar viabilidade, riscos e dependências; revisar requisitos; definir e executar sua verificação. |
| Responsável pela aprovação | Aprovar a versão de referência e decidir sobre mudanças, considerando as partes interessadas afetadas. |

Em equipes pequenas, uma pessoa pode acumular papéis. Os responsáveis e a autoridade para aprovação devem ser identificados no início do trabalho.

## 3. Execução do processo

O fluxo inicial é: **preparar → analisar o problema → definir requisitos das partes interessadas → definir requisitos do sistema/software → revisar e validar → aprovar**. A gestão acompanha todas as etapas, e os requisitos aprovados orientam a implementação, a verificação e a validação da solução.

O processo é iterativo: novas informações podem exigir a revisão de etapas anteriores. Quando o sistema for decomposto em elementos, repetir a definição de requisitos nos níveis necessários, preservando os vínculos com os requisitos de origem.

### 3.1 Preparar o trabalho

- Identificar os responsáveis, as partes interessadas e as fontes de informação.
- Definir como levantar, registrar, revisar e aprovar requisitos, considerando o ciclo de vida adotado.
- Disponibilizar as ferramentas e os registros necessários. Para este projeto, arquivos Markdown versionados no repositório são suficientes para organizar as informações.

**Resultado:** abordagem de trabalho e responsabilidades definidas.

### 3.2 Analisar o negócio ou a missão

- Descrever o problema ou a oportunidade, os objetivos e os resultados esperados.
- Delimitar o escopo, o contexto de uso e as restrições conhecidas.
- Descrever os conceitos preliminares de operação e considerar implantação, suporte e retirada de uso.
- Avaliar alternativas de solução, sua viabilidade e seus riscos; registrar a alternativa escolhida e a justificativa.

**Resultado:** problema, objetivos, limites e orientação da solução documentados.

### 3.3 Definir necessidades e requisitos das partes interessadas

- Levantar necessidades por entrevistas, reuniões, observação ou análise de documentos, conforme necessário.
- Considerar usuários, adquirentes, operação, manutenção e outras partes afetadas durante o ciclo de vida.
- Descrever cenários de uso, interações externas, restrições e expectativas de qualidade e desempenho.
- Analisar e priorizar as necessidades; resolver divergências e transformá-las em requisitos das partes interessadas.
- Confirmar com os representantes designados que os requisitos expressam suas necessidades e registrar sua concordância.

**Resultado:** requisitos das partes interessadas acordados e ligados às necessidades e às respectivas fontes.

### 3.4 Definir requisitos do sistema/software

- Transformar os requisitos das partes interessadas em requisitos técnicos do sistema e, quando necessário, do software e de seus elementos.
- Especificar funções, interfaces, dados, desempenho, características de qualidade e restrições necessárias.
- Definir limites mensuráveis para as características críticas e as condições em que devem ser atendidas.
- Registrar os atributos de cada requisito e sua relação com os requisitos de origem.
- Definir como comprovar o atendimento de cada requisito: teste, análise, inspeção ou demonstração.

**Resultado:** especificação de requisitos suficientemente detalhada para orientar arquitetura, implementação e verificação.

### 3.5 Revisar e validar os requisitos

- **Verificar os requisitos:** revisar sua redação, estrutura e qualidade com os critérios da seção 4.
- **Validar os requisitos:** confirmar com as partes interessadas que eles representam corretamente as necessidades e o uso pretendido. Usar revisão de cenários e, quando útil, modelos ou protótipos.
- Avaliar viabilidade técnica, custo, prazo, riscos e dependências do conjunto.
- Corrigir omissões, ambiguidades e conflitos; registrar decisões e resolver pendências do escopo a aprovar.

**Resultado:** requisitos revisados e validados, com os resultados e as decisões registrados.

### 3.6 Aprovar e estabelecer a versão de referência

- Submeter o conjunto revisado ao responsável pela aprovação e registrar a concordância das partes interessadas designadas.
- Identificar a versão aprovada, a data, os participantes e o escopo da aprovação.
- Preservar essa versão como **linha de base (baseline)**, por exemplo, associando-a a um commit ou tag do repositório.
- Disponibilizar a versão aprovada à equipe e às partes interessadas pertinentes.

**Resultado:** conjunto aprovado que serve de referência para o desenvolvimento e o controle de mudanças. A aprovação pode ocorrer por incremento, com seu escopo claramente definido.

### 3.7 Gerenciar os requisitos e suas mudanças

- Manter identificação, versão, situação e rastreabilidade dos requisitos durante o ciclo de vida.
- Registrar cada proposta de mudança, sua origem, justificativa e requisitos afetados.
- Analisar impactos em escopo, arquitetura, implementação, testes, custo, prazo, riscos e outros requisitos.
- Registrar a decisão do responsável pela aprovação: aprovar, rejeitar ou adiar, com justificativa.
- Para mudanças aprovadas, atualizar os registros e vínculos, repetir as revisões necessárias, estabelecer a nova versão de referência e comunicar a decisão aos envolvidos.
- Acompanhar pendências, mudanças e cobertura de verificação para identificar problemas e orientar ajustes no processo.

**Resultado:** acordo sobre os requisitos mantido, com histórico das alterações e de seus impactos.

### 3.8 Verificar e validar a solução

- **Verificar a solução:** executar os métodos definidos para comprovar o atendimento aos requisitos aprovados e vincular as evidências aos respectivos identificadores.
- **Validar a solução:** avaliar com as partes interessadas se ela atende às necessidades no contexto de uso pretendido.
- Registrar resultados e desvios. Se houver necessidade de alterar requisitos, aplicar o controle de mudanças.

**Resultado:** evidências de atendimento aos requisitos e às necessidades, ou desvios registrados para tratamento.

## 4. Critérios de qualidade

Cada requisito deve ser necessário, apropriado ao seu nível, inequívoco, completo, singular, viável, verificável, correto em relação à necessidade de origem e conforme o padrão de redação adotado.

O conjunto deve ser completo para o escopo definido, consistente, viável, compreensível e passível de validação. Um conjunto com informações ainda a definir não deve ser declarado completo; durante sua elaboração, registrar essas pendências com responsável e prazo de resolução.

Usar linguagem direta, uma obrigação por requisito e condições claras. Descrever o resultado necessário, evitando impor soluções de implementação sem justificativa. Substituir expressões vagas, como “rápido” ou “fácil de usar”, por condições e medidas que permitam comprovar o atendimento. Documentar e validar as premissas.

## 5. Registros mínimos

As informações podem ser mantidas em um único documento de requisitos, desde que os níveis e vínculos fiquem claros. Não é necessário criar um arquivo separado para cada atividade.

| Registro | Conteúdo mínimo adotado pelo projeto |
| --- | --- |
| Contexto e necessidades | Problema, objetivos, escopo, partes interessadas, fontes, cenários de uso, restrições e premissas. |
| Especificação dos requisitos | Requisitos das partes interessadas e do sistema/software, com os atributos indicados abaixo. |
| Revisões e aprovação | Pendências, decisões e justificativas, participantes, concordância, data e identificação da versão aprovada. |
| Mudanças e evidências | Solicitações, análise de impacto, decisões, versões alteradas e resultados de verificação e validação. |

Para cada requisito, registrar:

- **ID e versão:** identificador único e estável; não reutilizar o ID de um requisito removido.
- **Nível e tipo:** parte interessada, sistema ou software; funcional, qualidade, desempenho, interface ou restrição.
- **Descrição:** obrigação, condições e resultado esperado.
- **Origem e justificativa:** necessidade, fonte ou requisito de origem e motivo de sua inclusão.
- **Responsável, prioridade e situação:** quem o mantém, importância acordada e estado atual.
- **Verificação:** método e critérios objetivos de atendimento, incluindo medidas e limites quando necessários.
- **Riscos e dependências:** fatores que afetam sua viabilidade ou seu atendimento.
- **Vínculos:** requisitos relacionados, elementos da solução e evidências de verificação e validação, conforme disponíveis.

Manter rastreabilidade nos dois sentidos, permitindo partir de uma necessidade para seus requisitos e evidências e retornar destes à origem:

**Necessidade ↔ requisito da parte interessada ↔ requisito do sistema/software ↔ elemento da solução ↔ evidência.**

