# Análise do Culture Amp — Sistema Análogo para o Projeto de Gestão de Competências

## 1. Objetivo da análise

Este documento apresenta uma análise do **Culture Amp** como sistema análogo para o projeto acadêmico de Gestão de Competências, cujo escopo envolve diferentes modalidades de feedback, avaliações por múltiplas fontes, questionários, análise de resultados, confidencialidade, histórico e planos de desenvolvimento.

O objetivo não é reproduzir integralmente a plataforma, mas identificar funcionalidades, processos, regras de negócio e características de qualidade que possam orientar o levantamento de requisitos e o desenvolvimento do sistema acadêmico.


## 2. Caracterização geral

O [Culture Amp](https://www.cultureamp.com/) é uma plataforma SaaS (*Software as a Service*) de gestão de pessoas, desempenho, desenvolvimento profissional e engajamento de colaboradores.

A plataforma integra processos de Recursos Humanos e permite que organizações coletem avaliações, registrem feedbacks, acompanhem metas e utilizem dados para apoiar decisões relacionadas ao desenvolvimento dos colaboradores.

### 2.1 Principais áreas da plataforma

| Área | Finalidade | Relação com o projeto |
| --- | --- | --- |
| Engage | Pesquisas de engajamento, clima e experiência dos colaboradores | Complementar |
| Perform | Avaliações de desempenho, feedback, metas e calibração | Essencial |
| Develop | Desenvolvimento profissional, competências e evolução | Essencial |

A nomenclatura e a composição dos produtos podem variar conforme a oferta comercial vigente.

### 2.2 Público-alvo

- Empresas de diferentes portes.
- Departamentos de Recursos Humanos.
- Gestores e líderes de equipes.
- Profissionais responsáveis pelo desenvolvimento de talentos.
- Colaboradores que participam de avaliações de desempenho.

### 2.3 Problemas organizacionais abordados

| Problema | Solução oferecida pela plataforma |
| --- | --- |
| Avaliações subjetivas | Questionários e critérios estruturados |
| Falta de comunicação | Feedback contínuo |
| Visão limitada do desempenho | Avaliações de múltiplas fontes |
| Ausência de acompanhamento | Metas e planos de desenvolvimento |
| Falta de histórico | Registros de ciclos e avaliações |
| Dificuldade de analisar resultados | Relatórios e recursos analíticos |
| Baixo engajamento | Pesquisas e indicadores organizacionais |

## 3. Levantamento das funcionalidades

### 3.1 Avaliação de desempenho (*Performance Reviews*)

A plataforma permite organizar ciclos de avaliação nos quais colaboradores, gestores e colegas participam de um processo estruturado. Os ciclos podem ser configurados de acordo com as necessidades da organização, por exemplo, trimestral, semestral ou anualmente.

Principais funcionalidades:

1. Criação e configuração de ciclos de avaliação.
2. Definição de datas de início e encerramento.
3. Seleção dos colaboradores participantes.
4. Configuração dos formulários e perguntas.
5. Definição dos avaliadores.
6. Realização de autoavaliações.
7. Avaliação por gestores.
8. Feedback entre colegas.
9. Feedback ascendente, quando configurado.
10. Consolidação dos resultados.
11. Compartilhamento das avaliações.
12. Acompanhamento do status das avaliações.

A organização pode configurar quais modalidades de avaliação serão utilizadas em cada ciclo.

### 3.2 Feedback 360°

O feedback 360° reúne diferentes perspectivas sobre o desempenho de um colaborador. Em vez de depender apenas da avaliação do gestor, o processo pode considerar opiniões de pessoas que trabalham com o avaliado.

| Modalidade | Descrição | Exemplo |
| --- | --- | --- |
| Autoavaliação | O colaborador avalia o próprio desempenho | Identificar pontos fortes e dificuldades |
| Gestor | O superior avalia o colaborador | Avaliar cumprimento de metas |
| Pares | Colegas avaliam o colaborador | Avaliar colaboração e comunicação |
| Subordinados | Colaboradores avaliam seus gestores | Avaliar liderança e relacionamento |

Fluxo geral:

1. O administrador configura um ciclo.
2. São selecionados os colaboradores participantes.
3. São definidos ou indicados os avaliadores, conforme as regras do ciclo.
4. O sistema envia solicitações de avaliação.
5. Os avaliadores respondem aos questionários.
6. O colaborador realiza sua autoavaliação, quando prevista.
7. O gestor realiza sua avaliação.
8. As respostas são consolidadas.
9. Os resultados podem passar por calibração.
10. A avaliação é compartilhada conforme as permissões e regras de confidencialidade.

**Relação com o projeto:** atende ao requisito de reunir visões de gestores, colegas e outras fontes para produzir uma avaliação mais abrangente.

### 3.3 Feedback contínuo (*Continuous Feedback*)

Além dos ciclos formais, a plataforma oferece mecanismos para registrar e solicitar feedback ao longo da rotina de trabalho.

Possibilidades incluem:

- Envio de feedback a qualquer momento.
- Solicitação de feedback a colegas.
- Feedback entre integrantes da equipe.
- Registro de elogios e reconhecimentos.
- Compartilhamento de observações construtivas.
- Acompanhamento do feedback recebido.

Essa abordagem permite que o feedback não fique restrito às avaliações semestrais ou anuais.

| Tipo previsto na atividade | Aplicação possível |
| --- | --- |
| Formal | Avaliações organizadas em ciclos |
| Informal | Feedback contínuo |
| Positivo | Reconhecimento de comportamentos e resultados |
| Construtivo | Identificação de oportunidades de melhoria |

A classificação formal/informal e positivo/construtivo é uma interpretação dos usos possíveis, não necessariamente quatro categorias obrigatórias e independentes na interface da plataforma.

### 3.4 Questionários e formulários de avaliação

Os questionários padronizam a coleta de informações sobre o desempenho e as competências dos colaboradores. As perguntas podem orientar os avaliadores na análise de comportamentos, resultados e habilidades.

Dimensões que podem ser avaliadas:

- Comunicação.
- Trabalho em equipe.
- Liderança.
- Organização.
- Proatividade.
- Resolução de problemas.
- Conhecimento técnico.
- Cumprimento de objetivos.

Exemplos de perguntas que poderiam ser utilizadas em um sistema acadêmico:

| Pergunta | Tipo de resposta sugerido |
| --- | --- |
| O colaborador demonstra boa comunicação? | Escala de 1 a 5 |
| Cumpre os prazos estabelecidos? | Escala de 1 a 5 |
| Colabora com os demais integrantes da equipe? | Escala de 1 a 5 |
| Quais são seus principais pontos fortes? | Texto livre |
| Quais competências precisam melhorar? | Texto livre |
| Que recomendação você daria para o desenvolvimento desse colaborador? | Texto livre |

Essas perguntas são exemplos elaborados para o projeto, não uma reprodução dos formulários proprietários da Culture Amp.

### 3.5 Gestão de metas (*Goal Management*)

A plataforma oferece recursos para definir e acompanhar metas em diferentes níveis da organização, relacionando objetivos individuais aos objetivos de equipes e da empresa.

Exemplo acadêmico:

- Meta: melhorar a comunicação profissional.
- Indicador: avaliação média da competência comunicação.
- Valor inicial: 2,5.
- Objetivo: atingir 4,0.
- Prazo: seis meses.
- Acompanhamento: avaliações periódicas.

O exemplo ilustra como o feedback pode ser convertido em objetivos mensuráveis.

### 3.6 Desenvolvimento profissional e planos de ação

Os recursos de desenvolvimento permitem relacionar os resultados das avaliações a ações de melhoria.

Possibilidades:

- Identificar competências que precisam ser desenvolvidas.
- Estabelecer objetivos profissionais.
- Planejar ações de desenvolvimento.
- Registrar compromissos.
- Acompanhar a evolução.
- Apoiar conversas entre gestores e colaboradores.

Exemplo: um colaborador recebe avaliações que apontam uma oportunidade de melhoria em liderança. O gestor e o colaborador podem estabelecer ações como participar de treinamento, conduzir reuniões, receber acompanhamento e realizar uma nova avaliação após determinado período.

### 3.7 Reuniões individuais (*1-on-1*)

A plataforma oferece recursos para organizar conversas individuais entre gestores e colaboradores.

Essas reuniões podem ser utilizadas para:

- Discutir resultados das avaliações.
- Conversar sobre dificuldades.
- Acompanhar metas.
- Definir prioridades.
- Discutir oportunidades de crescimento.
- Registrar assuntos importantes.

O objetivo é conectar o feedback registrado no sistema a conversas e ações concretas.

### 3.8 Reconhecimento (*Shoutouts*)

O recurso Shoutouts permite reconhecer contribuições e comportamentos positivos dos colaboradores.

Exemplos:

- Reconhecimento por colaboração.
- Destaque por cumprimento de metas.
- Reconhecimento por iniciativa.
- Agradecimento pela ajuda prestada à equipe.

Esse recurso está relacionado ao feedback positivo e pode contribuir para o engajamento.

### 3.9 Análises e relatórios de desempenho

A plataforma oferece recursos para transformar os feedbacks coletados em informações úteis para gestores e RH.

Entre as possibilidades documentadas estão:

- Acompanhamento do andamento dos ciclos.
- Quantidade de avaliações solicitadas e concluídas.
- Visualização de resultados.
- Consulta ao histórico de desempenho.
- Análise de feedbacks recebidos.
- Comparação entre ciclos.
- Identificação de pontos fortes e oportunidades de melhoria.
- Visualizações para calibração.

A Culture Amp também documenta recursos de inteligência artificial que podem resumir destaques e oportunidades a partir de fontes de feedback, quando disponíveis e habilitados.

### 3.10 Calibração das avaliações

A calibração busca reduzir diferenças injustificadas na maneira como gestores avaliam colaboradores.

Exemplo: um gestor atribui notas muito altas para quase toda a equipe, enquanto outro atribui notas baixas mesmo para desempenhos semelhantes. A calibração permite analisar avaliações em conjunto e discutir critérios antes da divulgação dos resultados.

A plataforma oferece recursos de visualização e análise para apoiar esse processo. A calibração não elimina automaticamente a subjetividade: depende de critérios organizacionais e da análise dos responsáveis.

### 3.11 Pesquisas de engajamento e experiência

O módulo Engage contempla pesquisas relacionadas à experiência dos colaboradores, como:

- Satisfação no trabalho.
- Engajamento.
- Clima organizacional.
- Inclusão.
- Bem-estar.
- Experiência de integração.
- Experiência de desligamento.
- Percepção sobre liderança.

Essas pesquisas são complementares ao escopo acadêmico. Não é necessário implementar todo o módulo de engajamento para atender à proposta da disciplina.

### 3.12 Administração e acompanhamento

A plataforma oferece recursos administrativos, como:

- Gerenciamento de colaboradores.
- Configuração de ciclos.
- Definição de participantes.
- Gerenciamento de permissões.
- Acompanhamento de pendências.
- Configuração de prazos.
- Integrações com sistemas de RH.
- Controle de acesso às informações.

## 4. Confidencialidade, anonimato e proteção de dados

A confidencialidade é importante porque os colaboradores precisam sentir segurança para fornecer avaliações honestas, inclusive sobre seus superiores.

### 4.1 Diferença entre anonimato e confidencialidade

- **Anonimato:** a identidade do avaliador não é apresentada junto à resposta.
- **Confidencialidade:** as informações são protegidas e somente pessoas autorizadas podem acessá-las.

A Culture Amp oferece mecanismos de controle de acesso e regras de confidencialidade. Entretanto, o anonimato não é absoluto em todas as situações.

Por exemplo, se apenas uma pessoa responder à avaliação de um gestor, o gestor poderá deduzir quem forneceu a resposta, mesmo que o nome não seja exibido.

Para o sistema acadêmico, recomenda-se:

1. Não apresentar o nome do avaliador ao avaliado quando o feedback for configurado como anônimo.
2. Permitir consulta aos resultados somente por usuários autorizados.
3. Impedir a divulgação de resultados de grupos com quantidade insuficiente de respostas.
4. Registrar e auditar acessos administrativos.
5. Exibir resultados consolidados respeitando as regras de confidencialidade.
6. Alertar quando a quantidade de respostas puder comprometer o anonimato.

Como regra de projeto, o grupo poderia estabelecer um mínimo de três respostas por grupo de avaliadores para liberar resultados agregados. Esse número seria uma decisão do grupo, não uma regra universal da Culture Amp.

### 4.2 Controle de acesso

Os papéis e permissões podem variar conforme o produto e a configuração. Para fins de análise, podem ser identificados os seguintes perfis:

| Perfil | Responsabilidade |
| --- | --- |
| Administrador da conta | Gerenciamento geral da plataforma |
| Administrador de desempenho | Configuração dos ciclos de avaliação |
| RH / HRBP | Acompanhamento de colaboradores e avaliações conforme permissões |
| Gestor | Avaliação e acompanhamento de subordinados |
| Colaborador | Participação nas avaliações e acompanhamento do desenvolvimento |
| Avaliador | Responder solicitações de feedback |

### 4.3 LGPD — Lei Geral de Proteção de Dados

A legislação brasileira aplicável é a Lei nº 13.709/2018. Como o projeto envolve informações sobre desempenho, comportamento e opiniões de colaboradores, é necessário considerar a proteção de dados pessoais desde a concepção do sistema.

Aspectos a investigar e contemplar:

- Definição das finalidades de tratamento.
- Identificação dos papéis de controlador e operador.
- Transparência sobre a coleta e utilização dos dados.
- Controle de acesso.
- Proteção das informações confidenciais.
- Registro de operações relevantes.
- Regras de retenção e descarte.
- Atendimento aos direitos dos titulares.
- Proteção dos dados durante transmissão e armazenamento.
- Avaliação de transferências internacionais, quando aplicável.

A Culture Amp disponibiliza documentação contratual de tratamento de dados (*Data Processing Addendum*). Isso não deve ser interpretado como comprovação automática de conformidade integral com a LGPD. A adequação depende do contexto de uso, dos contratos, das configurações e das operações de tratamento.

### 4.4 Requisitos LGPD propostos

| ID | Requisito proposto | Justificativa |
| --- | --- | --- |
| RNF-LGPD-01 | O sistema deverá informar a finalidade da coleta de dados. | Transparência |
| RNF-LGPD-02 | O sistema deverá permitir acesso somente a usuários autorizados. | Segurança |
| RNF-LGPD-03 | O sistema deverá proteger informações confidenciais. | Privacidade |
| RNF-LGPD-04 | O sistema deverá registrar operações relevantes de acesso e alteração. | Auditoria |
| RNF-LGPD-05 | O sistema deverá permitir atender solicitações dos titulares conforme a legislação. | Direitos dos titulares |
| RNF-LGPD-06 | O sistema deverá limitar a coleta aos dados necessários para sua finalidade. | Necessidade |
| RNF-LGPD-07 | O sistema deverá estabelecer regras de retenção e descarte de dados. | Ciclo de vida dos dados |
| RNF-LGPD-08 | O sistema deverá proteger os dados durante transmissão e armazenamento. | Segurança |

Esses requisitos são propostas para o sistema acadêmico, não afirmações de que todos estejam disponíveis exatamente da mesma maneira na Culture Amp.
