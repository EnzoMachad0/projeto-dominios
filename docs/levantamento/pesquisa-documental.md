# Pesquisa documental — legislação e normas aplicáveis

| Campo | Informação |
| --- | --- |
| Sistema | Gestão de competências e feedback |
| Normas pesquisadas | LGPD (Lei nº 13.709/2018) e ISO/IEC 25010 |
| Edição da ISO/IEC 25010 utilizada | **ISO/IEC 25010:2023, segunda edição (2023-11)** |
| Data de consulta das fontes | 08/11/2026 |
| Situação | Requisitos candidatos propostos, ainda não validados com o stakeholder |

## 1. Síntese

- **A LGPD se aplica ao sistema.** Avaliações, comentários, notas e planos de desenvolvimento são dados pessoais do avaliado e, em muitos casos, também do avaliador.
- **"Anônimo" na interface não significa "anonimizado" na LGPD.** Se a organização ou o sistema puder restabelecer o vínculo entre a resposta e seu autor, o dado continua sendo pessoal (ver [D-03](#6-dúvidas-de-interpretação-e-pendências)). Esse é o ponto de maior impacto no projeto.
- **A segurança precisa ser considerada desde a concepção** (LGPD, art. 46, §2º). Controle de acesso, registro de auditoria e proteção da identidade dos avaliadores devem entrar na especificação, e não ser deixados para depois.
- **A ISO/IEC 25010:2023 não impõe requisitos.** Ela é um modelo de referência com nove características. A equipe a usa para classificar e completar os requisitos não funcionais. A edição de 2023 substituiu a de 2011 e mudou nomes importantes: *usability* passou a ser *interaction capability*, e *portability* passou a ser *flexibility*.
- **Resultado:** 37 requisitos candidatos ([seção 5](#5-requisitos-candidatos)), todos ligados à sua fonte, e 13 dúvidas registradas ([seção 6](#6-dúvidas-de-interpretação-e-pendências)).

## 2. Método e fontes consultadas

A pesquisa priorizou fontes primárias: texto legal compilado, resoluções e guias da autoridade nacional e prévia oficial da norma. Fontes secundárias foram usadas somente onde o texto primário não estava acessível, e isso está indicado na coluna **Acesso**.

| ID | Referência | Acesso |
| --- | --- | --- |
| F01 | BRASIL. **Lei nº 13.709, de 14 de agosto de 2018** (LGPD), texto compilado. Disponível em: <https://www.planalto.gov.br/ccivil_03/_ato2015-2018/2018/lei/l13709.htm>. Acesso em: 8 nov. 2026. | Texto oficial, dispositivos citados neste documento |
| F02 | BRASIL. **Lei nº 15.352, de 25 de fevereiro de 2026** (transforma a ANPD em Agência Nacional de Proteção de Dados). Disponível em: <https://www2.camara.leg.br/legin/fed/lei/2026/lei-15352-25-fevereiro-2026-798731-publicacaooriginal-178208-pl.html>. Acesso em: 8 nov. 2026. | Localizada em busca e citada nas notas de F01; texto integral não analisado |
| F03 | ANPD. **Resolução CD/ANPD nº 2, de 27 de janeiro de 2022** (agentes de tratamento de pequeno porte). DOU, 28 jan. 2022. Cópia disponível em: <https://www.gov.br/palmares/pt-br/midias/arquivos-menu-acesso-a-informacao/legislacao/resolucao-cd-anpd-n2-2022.pdf>. Acesso em: 8 nov. 2026. | Texto publicado no DOU |
| F04 | ANPD. **Resolução CD/ANPD nº 15, de 24 de abril de 2024** (comunicação de incidente de segurança). Disponível em: <https://bibliotecadigital.mj.gov.br/bitstream/1/12879/2/RES_ANPD_2024_15.html>. Acesso em: 8 nov. 2026. | Texto integral; alterações posteriores não verificadas |
| F05 | ANPD. **Resolução CD/ANPD nº 18, de 16 de julho de 2024** (atuação do encarregado). Cópia disponível em: <https://www.lgpd.ms.gov.br/wp-content/uploads/2024/08/RESOLUCAO-CD_ANPD-No-18-DE-16-DE-JULHO-DE-2024-RESOLUCAO-CD_ANPD-No-18-DE-16-DE-JULHO-DE-2024.pdf>. Acesso em: 8 nov. 2026. | Texto publicado no DOU |
| F06 | ANPD. **Guia Orientativo das Hipóteses Legais de Tratamento de Dados — Legítimo Interesse**. Lançado em 2 fev. 2024. Disponível em: <https://www.gov.br/anpd/pt-br/centrais-de-conteudo/materiais-educativos-e-publicacoes/guia_legitimo_interesse.pdf/@@display-file/file>. Acesso em: 8 nov. 2026. | Trechos obtidos em busca; leitura integral pendente |
| F07 | ANPD. **Guia Orientativo sobre Segurança da Informação para Agentes de Tratamento de Pequeno Porte**. Versão 1.0, out. 2021. Disponível em: <https://www.gov.br/anpd/pt-br/centrais-de-conteudo/materiais-educativos-e-publicacoes/guia-vf.pdf/@@display-file/file>. Acesso em: 8 nov. 2026. | Texto integral; caráter de boas práticas |
| F08 | ANPD. **Relatório de Impacto à Proteção de Dados Pessoais (RIPD)**. Página publicada em 6 abr. 2023 e modificada em 23 set. 2026. Disponível em: <https://www.gov.br/anpd/pt-br/canais_atendimento/agente-de-tratamento/relatorio-de-impacto-a-protecao-de-dados-pessoais-ripd>. Acesso em: 8 nov. 2026. | Página integral |
| F09 | ISO; IEC. **ISO/IEC 25010:2023 — Systems and software engineering — Systems and software Quality Requirements and Evaluation (SQuaRE) — Product quality model**. 2. ed. Genebra, nov. 2023. Prévia disponível em: <https://assets.vde-verlag.de/iec-normen/preview-pdf/info_isoiec25010%7Bed2.0%7Den.pdf>. Acesso em: 8 nov. 2026. | Prévia oficial: capa, sumário, prefácio, introdução e escopo. Norma completa é paga |
| F10 | ISO. **ISO/IEC 25010:2023** (página de catálogo). Disponível em: <https://www.iso.org/standard/78176.html>. Acesso em: 8 nov. 2026. | Página bloqueou a leitura direta; dados de edição vistos em resultado de busca |
| F11 | SONARSOURCE. **ISO/IEC 25010 Explained**. Disponível em: <https://www.sonarsource.com/resources/library/iso-iec-25010-explained/>. Acesso em: 8 nov. 2026. | Secundária: lista de subcaracterísticas |
| F12 | TNLAB. **ISO/IEC 25010:2023 — SQuaRE Product Quality Model**. Disponível em: <https://tnlab.org/en/iso-iec-250102023-square-product-quality-model/>. Acesso em: 8 nov. 2026. | Secundária: lista de subcaracterísticas, usada para confronto com F11 |
| F13 | ISO 25000 PORTAL. **ISO/IEC 25010**. Disponível em: <https://iso25000.com/en/iso-25000-standards/iso-25010>. Acesso em: 8 nov. 2026. | Secundária: descrição de parte das características |
| F14 | MATTOS FILHO. **ANPD não aprova Guia Orientativo sobre tratamento de dados pessoais de alto risco**. Disponível em: <https://www.mattosfilho.com.br/unico/anpd-guia-dados-risco/>. Acesso em: 8 nov. 2026. | Secundária: trecho obtido em busca |

Fontes internas usadas para delimitar o escopo: [README](../../README.md), [processo de requisitos](../PROCESSO_REQUISITOS.md) e [roteiro de entrevista](../roteiro-entrevista-stakeholder.md).

## 3. LGPD

### 3.1. Situação da norma

A LGPD foi alterada principalmente pela Lei nº 13.853/2019. Em 2026, a Lei nº 15.352 transformou a Autoridade Nacional de Proteção de Dados em **Agência Nacional de Proteção de Dados**, mantendo a sigla ANPD (F01, F02). Documentos anteriores usam o nome antigo.

### 3.2. Conceitos aplicados ao sistema

| Conceito (F01) | Aplicação ao sistema |
| --- | --- |
| Dado pessoal (art. 5º, I) | Cadastro, cargo, equipe, notas, comentários, histórico, metas e planos de desenvolvimento. |
| Dado pessoal sensível (art. 5º, II) | Não é objetivo do sistema, mas pode surgir em comentários livres, como menção a saúde, religião ou filiação sindical. |
| Titular (art. 5º, V) | Avaliado e avaliador. Um mesmo feedback pode conter dados de ambos. |
| Controlador e operador (art. 5º, VI e VII; art. 39) | Em princípio, a organização que usa o sistema é controladora. Um eventual fornecedor do sistema tende a ser operador ([D-01](#6-dúvidas-de-interpretação-e-pendências)). |
| Dado anonimizado (art. 5º, III e XI; art. 12) | Só deixa de ser dado pessoal se a identificação não puder ser revertida com meios próprios ou esforços razoáveis. |
| Pseudonimização (art. 13, §4º) | Definida para estudos em saúde pública, mas útil por analogia: há associação possível por informação adicional mantida separadamente. |
| Perfil comportamental (art. 12, §2º) | Dados usados para formar o perfil de pessoa identificada podem ser considerados dados pessoais, o que alcança indicadores individuais de desempenho. |

### 3.3. Pontos relevantes para os requisitos

| Tema | Dispositivos | O que importa para o sistema |
| --- | --- | --- |
| Princípios | Art. 6º | Finalidade, adequação e necessidade limitam o que os questionários coletam e quem vê o quê. Transparência exige explicar o tratamento. Não discriminação alcança relatórios e comparações. Responsabilização exige capacidade de demonstrar as medidas adotadas. |
| Bases legais | Arts. 7º e 10 | Cada finalidade precisa de uma base legal. Execução de contrato (art. 7º, V) e legítimo interesse (art. 7º, IX) são candidatas; a escolha é do controlador ([D-02](#6-dúvidas-de-interpretação-e-pendências)). |
| Consentimento | Arts. 5º, XII, e 8º | Deve ser livre, informado e inequívoco, para finalidade determinada, revogável por procedimento gratuito. O controlador tem o ônus da prova. |
| Dados sensíveis | Art. 11; F06 | Exigem hipótese própria. Segundo a ANPD, legítimo interesse não se aplica a dados sensíveis (F06). |
| Transparência | Art. 9º | Finalidade, forma e duração, identificação e contato do controlador, compartilhamento, responsabilidades e direitos devem ser de acesso facilitado. |
| Término e eliminação | Arts. 15 e 16 | Os dados são eliminados ao fim do tratamento, salvo exceções legais. A lei não fixa prazo para avaliações ([D-06](#6-dúvidas-de-interpretação-e-pendências)). |
| Direitos do titular | Arts. 18 e 19 | Confirmação, acesso, correção, anonimização, bloqueio ou eliminação, portabilidade, informação sobre compartilhamento e revogação. O atendimento é gratuito. A confirmação e o acesso são imediatos em formato simplificado, ou em até 15 dias por declaração clara e completa (art. 19, I e II). |
| Decisões automatizadas | Art. 20 | O titular pode pedir revisão de decisão tomada unicamente por tratamento automatizado que afete seus interesses, inclusive sobre perfil profissional, e tem direito a informações sobre os critérios. |
| Poder público | Art. 23 | Aplicável apenas se a organização usuária for pública ([D-01](#6-dúvidas-de-interpretação-e-pendências)). |
| Registro e impacto | Arts. 37, 38 e 10, §3º; F08 | O controlador e o operador mantêm registro das operações. A ANPD pode exigir o RIPD. A própria ANPD recomenda elaborá-lo antes do início do tratamento de alto risco. |
| Encarregado | Art. 41; F05, arts. 3º, 8º e 9º; F03, art. 11 | Identidade e contato do encarregado devem ser publicados em local de destaque. Agentes de pequeno porte dispensados precisam oferecer canal de comunicação com o titular. |
| Segurança | Arts. 46 e 49; F07 | Medidas técnicas e administrativas contra acesso indevido e incidentes, observadas **desde a concepção** do produto. |
| Incidentes | Art. 48; F04, arts. 5º, 6º, 9º e 10 | Comunicar à ANPD e aos titulares em **3 dias úteis** a partir do conhecimento de que dados pessoais foram afetados, quando houver risco ou dano relevante. O prazo é contado em dobro para pequeno porte. O registro do incidente é guardado por no mínimo **5 anos**, mesmo se não houver comunicação. |
| Governança | Art. 50 | Programa de governança e boas práticas são facultativos, mas podem demonstrar responsabilização. |
| Sanções | Arts. 42 e 52 | Reparação de danos e sanções, incluindo multa de até 2% do faturamento no Brasil, limitada a R$ 50 milhões por infração. |

### 3.4. Medidas de segurança orientadas pela ANPD (F07)

O guia é voltado a agentes de pequeno porte e tem caráter de boas práticas. A equipe o usa como referência mínima, porque não há padrão técnico obrigatório identificado nesta pesquisa:

- controle de acesso com autenticação, autorização e auditoria, com níveis de permissão proporcionais à necessidade (seção 3.2.1, §§ 34–35);
- política de complexidade de senhas e proibição de senhas padrão (§§ 36–37), além de autenticação multifator para dados pessoais (seção 3.2.1);
- pseudonimização e criptografia para dados sensíveis armazenados (§ 46);
- cópias de segurança regulares, completas, em local separado e sem sincronização em tempo real (§ 49);
- conexões cifradas com TLS/HTTPS (§ 53);
- autenticação multifator e critérios de segurança em serviços de nuvem (seção 3.4).

## 4. ISO/IEC 25010

### 4.1. Edição utilizada

A equipe adota a **ISO/IEC 25010:2023, segunda edição, publicada em novembro de 2023** (F09, F10). Segundo o prefácio, ela, junto com a ISO/IEC 25002 e a ISO/IEC 25019, cancela e substitui a ISO/IEC 25010:2011 (F09). Ela trata apenas do modelo de qualidade do **produto**; o modelo de **qualidade em uso** passou para a ISO/IEC 25019.

Não foi possível confirmar se existe versão brasileira ABNT alinhada à edição de 2023 ([D-11](#6-dúvidas-de-interpretação-e-pendências)).

### 4.2. Principais mudanças em relação a 2011 (F09)

| Edição de 2011 | Edição de 2023 |
| --- | --- |
| Usabilidade (*usability*) | Capacidade de interação (*interaction capability*) |
| Portabilidade (*portability*) | Flexibilidade (*flexibility*) |
| Sem essa característica | Nova característica: *safety* |
| Estética da interface | *User engagement* |
| Maturidade (*maturity*) | *Faultlessness* |
| Acessibilidade | Dividida em *inclusivity* e *user assistance* |
| — | Novas subcaracterísticas: *self-descriptiveness*, *resistance* e *scalability* |

Material didático anterior a 2023 costuma usar a nomenclatura antiga. Na especificação suplementar, a equipe deve usar a nomenclatura de 2023.

### 4.3. Modelo aplicado ao sistema

O prefácio (F09) confirma as nove características e parte das mudanças. A lista completa de subcaracterísticas vem de F11 e F12, que coincidem entre si. Os termos em português são traduções livres da equipe.

| Característica | Subcaracterísticas | Relevância | Justificativa |
| --- | --- | --- | --- |
| *Security* (segurança) | *Confidentiality, integrity, non-repudiation, accountability, authenticity, resistance* | **Alta** | Protege feedbacks, resultados e identidade dos avaliadores. Tem relação direta com a LGPD, art. 46. |
| *Functional suitability* (adequação funcional) | *Functional completeness, functional correctness, functional appropriateness* | **Alta** | Indicadores errados podem prejudicar decisões sobre pessoas. |
| *Interaction capability* (capacidade de interação) | *Appropriateness recognizability, learnability, operability, user error protection, user engagement, inclusivity, user assistance, self-descriptiveness* | **Alta** | O usuário precisa saber quem verá sua resposta antes de enviá-la. |
| *Reliability* (confiabilidade) | *Faultlessness, availability, fault tolerance, recoverability* | Média | Respostas não podem se perder, especialmente perto do fim de um ciclo. |
| *Maintainability* (manutenibilidade) | *Modularity, reusability, analysability, modifiability, testability* | Média | Regras de visibilidade precisam ser testáveis e passíveis de mudança. |
| *Flexibility* (flexibilidade) | *Adaptability, scalability, installability, replaceability* | Média | O processo de requisitos prevê futura utilização em dispositivos móveis. |
| *Performance efficiency* (eficiência de desempenho) | *Time behaviour, resource utilization, capacity* | Média | Pode haver picos no encerramento de ciclos. |
| *Compatibility* (compatibilidade) | *Co-existence, interoperability* | Baixa, a confirmar | Depende de haver integração com sistemas de RH. |
| *Safety* (segurança operacional) | *Operational constraint, risk identification, fail safe, hazard warning, safe integration* | Baixa, a confirmar | O sistema não controla equipamentos nem processos físicos. Danos à reputação e à privacidade foram tratados em *security*. |

> *Security* e *safety* costumam ser traduzidos como "segurança". Para evitar ambiguidade, este documento mantém os termos em inglês na classificação dos requisitos.

## 5. Requisitos candidatos

Os identificadores usam o sufixo **DOC** para indicar origem documental e evitar colisão com os requisitos de entrevistas e questionários. Prioridade não é atribuída aqui, pois será discutida com o stakeholder na etapa 3.3 do processo.

**Natureza da origem:**

- **Legal:** decorre de obrigação da LGPD ou de resolução da ANPD. A obrigação recai sobre o agente de tratamento; o texto do requisito é a interpretação da equipe sobre como o sistema pode apoiá-la.
- **Orientação:** decorre de guia da ANPD.
- **Qualidade:** derivado do modelo da ISO/IEC 25010, que não estabelece obrigação.
- **Interpretação:** proposta da equipe a partir da fonte indicada.

**Situação:** *Proposto* pode seguir para validação. *Pendente* depende da dúvida indicada.

### 5.1. Requisitos funcionais

| ID | Requisito candidato | Origem | Natureza | Situação |
| --- | --- | --- | --- | --- |
| RF-DOC-01 | O sistema deve apresentar, antes do primeiro uso e sempre disponível depois, aviso com finalidades, forma e duração do tratamento, controlador e contato, compartilhamentos e direitos do titular. | F01, arts. 6º, VI, e 9º | Legal | Proposto |
| RF-DOC-02 | O sistema deve exibir o contato do encarregado ou o canal de comunicação com o titular em local de destaque e de fácil acesso. | F01, art. 41, §1º; F05, art. 9º; F03, art. 11, §1º | Legal | Proposto |
| RF-DOC-03 | O titular deve poder consultar, em formato simplificado e de imediato, os dados pessoais que o sistema mantém sobre ele, respeitadas as regras de confidencialidade do avaliador. | F01, arts. 18, I e II, e 19, I | Legal | Pendente (D-04) |
| RF-DOC-04 | O sistema deve registrar requisições de titulares com tipo, data, responsável, resposta e situação, e alertar antes do vencimento do prazo de 15 dias para declaração completa. | F01, arts. 18, §§3º e 5º, e 19, II | Legal | Proposto |
| RF-DOC-05 | O sistema deve permitir corrigir dados cadastrais incompletos, inexatos ou desatualizados. | F01, art. 18, III | Legal | Proposto |
| RF-DOC-06 | O sistema deve permitir que o titular registre contestação sobre feedback recebido, mantendo o conteúdo original e a contestação associados. | F01, arts. 6º, V, e 18, III | Interpretação | Pendente (D-05) |
| RF-DOC-07 | O sistema deve permitir anonimizar, bloquear ou eliminar dados pessoais, registrando a medida e o motivo de eventual retenção por exceção legal. | F01, arts. 16 e 18, IV e VI | Legal | Proposto |
| RF-DOC-08 | O sistema deve permitir configurar o prazo de retenção por tipo de dado e sinalizar os registros vencidos para eliminação ou anonimização. | F01, arts. 15 e 16 | Legal | Pendente (D-06) |
| RF-DOC-09 | O sistema deve exportar os dados do titular em formato estruturado e de uso comum. | F01, arts. 18, V, e 19, §3º | Legal | Pendente (D-02, D-13) |
| RF-DOC-10 | Quando o consentimento for a base legal adotada, o sistema deve registrar titular, finalidade, versão do texto e data, e permitir a revogação de forma gratuita. | F01, arts. 8º e 18, IX | Legal | Pendente (D-02) |
| RF-DOC-11 | O sistema deve informar ao titular com quais terceiros seus dados foram compartilhados e comunicar a eles correções, eliminações, anonimizações ou bloqueios. | F01, art. 18, VII e §6º | Legal | Pendente (D-01) |
| RF-DOC-12 | O sistema deve gerar relatório das operações de tratamento, com categorias de dados, finalidades, perfis com acesso e prazos de retenção. | F01, art. 37; F03, art. 9º | Legal | Proposto |
| RF-DOC-13 | O sistema deve permitir listar os titulares e as categorias de dados afetados em um incidente, a partir do período e do escopo informados. | F01, art. 48; F04, arts. 6º, §2º, 9º e 10 | Interpretação | Proposto |
| RF-DOC-14 | O campo de comentário livre deve orientar o avaliador a não incluir dados sensíveis, nem informações que revelem sua identidade em avaliações anônimas. | F01, arts. 6º, III, 11 e 12 | Interpretação | Proposto |

### 5.2. Regras de negócio

| ID | Regra candidata | Origem | Natureza | Situação |
| --- | --- | --- | --- | --- |
| RN-DOC-01 | Cada dado solicitado em cadastros e questionários deve estar associado a uma finalidade definida; dados sem finalidade não devem ser coletados. | F01, art. 6º, I a III | Legal | Proposto |
| RN-DOC-02 | Cada modalidade de avaliação deve definir previamente um regime de identificação do avaliador: identificado, confidencial ou anônimo, informado antes do início da resposta. | F01, arts. 5º, III, 6º, VI, e 12; README | Interpretação | Pendente (D-03) |
| RN-DOC-03 | Resultados agregados de avaliações anônimas só devem ser exibidos quando houver um número mínimo de respondentes, a ser definido. | F01, arts. 5º, III, e 12 | Interpretação | Pendente (D-03) |
| RN-DOC-04 | Dados de avaliação só devem ser usados para as finalidades informadas; nova finalidade exige reavaliação de base legal e novo aviso aos titulares. | F01, arts. 6º, I, e 9º | Legal | Proposto |
| RN-DOC-05 | Questionários não devem solicitar dados pessoais sensíveis, salvo hipótese legal aprovada pelo controlador. | F01, arts. 5º, II, 6º, III e IX, e 11; F06 | Legal | Proposto |
| RN-DOC-06 | Decisões que afetem o colaborador não devem ser tomadas unicamente por tratamento automatizado; quando existirem, devem admitir pedido de revisão e explicação dos critérios. | F01, art. 20 | Legal | Pendente (D-09) |

### 5.3. Requisitos não funcionais

| ID | Característica ISO/IEC 25010:2023 | Requisito candidato | Origem | Natureza | Situação |
| --- | --- | --- | --- | --- | --- |
| RNF-DOC-01 | *Security* / *confidentiality* | Todo acesso a feedbacks e resultados deve ser autorizado no servidor conforme o perfil e o vínculo do usuário com o avaliado, negando o acesso por padrão. | F01, arts. 6º, III e VII, e 46; F07, §§34–35; F09 | Legal | Proposto |
| RNF-DOC-02 | *Security* / *confidentiality* | Em avaliações anônimas, nenhuma tela, relatório, exportação ou registro de auditoria disponível aos perfis do sistema deve revelar o autor da resposta. | F01, arts. 12 e 46; README | Interpretação | Pendente (D-03) |
| RNF-DOC-03 | *Security* / *authenticity* | O acesso deve exigir autenticação individual, com política de complexidade de senha, sem credenciais padrão, e autenticação multifator para perfis administrativos. | F07, seção 3.2.1, §§36–37 | Orientação | Proposto |
| RNF-DOC-04 | *Security* / *confidentiality* | Toda comunicação entre cliente e servidor deve usar conexão cifrada com TLS/HTTPS. | F01, art. 46; F07, §53 | Orientação | Proposto |
| RNF-DOC-05 | *Security* / *confidentiality* | Credenciais, vínculos de identidade de avaliadores e comentários devem ser armazenados de forma protegida, de modo que uma cópia indevida da base não os torne inteligíveis. | F01, arts. 46 e 48, §3º; F04, art. 5º, IV; F07, §46 | Interpretação | Proposto |
| RNF-DOC-06 | *Security* / *accountability* e *non-repudiation* | O sistema deve registrar usuário, ação, objeto, data e hora em acessos e alterações de dados de avaliação, em registro protegido contra alteração pelos perfis comuns. | F01, arts. 6º, X, e 37; F07, §34; F09 | Orientação | Proposto |
| RNF-DOC-07 | *Security* / *integrity* | Após o envio definitivo, uma avaliação só deve ser alterada por regra prevista e com histórico da alteração. | F01, art. 6º, V; F09 | Qualidade | Proposto |
| RNF-DOC-08 | *Security* / *resistance* | O sistema deve limitar tentativas sucessivas de autenticação e não pode apresentar vulnerabilidades críticas conhecidas na liberação, conforme critério de verificação a definir. | F01, art. 46; F09, F11 | Interpretação | Pendente (D-12) |
| RNF-DOC-09 | *Reliability* / *recoverability* | Devem ser feitas cópias de segurança regulares, completas, em local separado e sem sincronização em tempo real, com restauração testada e metas de recuperação a definir. | F07, §49; F11 | Orientação | Pendente (D-12) |
| RNF-DOC-10 | *Functional suitability* / *functional correctness* | Cada indicador deve ter fórmula documentada e reproduzir o resultado esperado em um conjunto de casos de referência. | F01, art. 6º, V; F09, F11 | Qualidade | Proposto |
| RNF-DOC-11 | *Interaction capability* / *self-descriptiveness* | A tela de resposta deve indicar o regime de identificação e quem poderá visualizar o conteúdo antes do envio. | F01, art. 6º, VI; F11, F13 | Interpretação | Pendente (D-03) |
| RNF-DOC-12 | *Interaction capability* / *user error protection* | O sistema deve preservar rascunhos e pedir confirmação antes do envio definitivo de uma avaliação. | F11, F13 | Qualidade | Proposto |
| RNF-DOC-13 | *Interaction capability* / *inclusivity* e *user assistance* | As interfaces devem atender a um nível de acessibilidade a definir. | F09, F11 | Qualidade | Pendente (D-12) |
| RNF-DOC-14 | *Flexibility* / *adaptability* | As interfaces web devem funcionar em telas de dispositivos móveis, conforme tamanhos mínimos a definir. | Processo de requisitos, §1; F11 | Qualidade | Pendente (D-12) |
| RNF-DOC-15 | *Performance efficiency* / *time behaviour* e *capacity*; *Reliability* / *availability* | O sistema deve atender às metas de tempo de resposta, usuários simultâneos e disponibilidade durante os ciclos, a definir. | F11, F13 | Qualidade | Pendente (D-12) |
| RNF-DOC-16 | *Maintainability* / *testability* | As regras de visibilidade por perfil e por regime de identificação devem ser cobertas por testes automatizados. | F01, art. 46, §2º; F11 | Interpretação | Proposto |
| RNF-DOC-17 | *Compatibility* / *interoperability* | Caso haja integração com sistemas de RH, a troca de dados deve seguir formato documentado e transmitir somente os dados necessários. | F01, art. 6º, III; F11, F13 | Qualidade | Pendente (D-01) |

## 6. Dúvidas de interpretação e pendências

Este documento é uma análise acadêmica de requisitos e não substitui parecer jurídico.

| ID | Dúvida | Por que importa | Quem pode esclarecer |
| --- | --- | --- | --- |
| D-01 | Qual é a organização usuária, ela é pública ou privada, seria agente de pequeno porte e haverá fornecedor ou integrações? | Define controlador e operador e a incidência do art. 23, dos prazos em dobro (F04) e da dispensa de encarregado (F03). Atenção: o tratamento de alto risco afasta o regime diferenciado (F03, art. 3º, I). | Stakeholder |
| D-02 | Qual base legal se aplica a cada finalidade? Execução de contrato (art. 7º, V) contém a expressão "a pedido do titular". Legítimo interesse exige análise por finalidade (art. 10; F06). O consentimento pode não ser livre em relação de emprego, avaliação da equipe a partir do art. 5º, XII. Não foi encontrada orientação específica da ANPD sobre avaliação de desempenho. | Afeta RF-DOC-09, RF-DOC-10 e o aviso de privacidade. | Stakeholder; professor; assessoria jurídica em caso real |
| D-03 | O que "anonimato" significa no sistema? Se houver vínculo recuperável entre resposta e autor, o dado continua sendo pessoal. Mesmo sem vínculo técnico, grupos pequenos e o estilo do comentário podem permitir reidentificação. | Define arquitetura, RN-DOC-02, RN-DOC-03, RNF-DOC-02 e RNF-DOC-11, além do número mínimo de respondentes. Ligada às perguntas 16 a 18 do roteiro. | Stakeholder; professor |
| D-04 | Como conciliar o direito de acesso do avaliado (art. 18, II) com a proteção da identidade do avaliador, que também é titular? | Define o conteúdo que o avaliado recebe em caso de requisição. | Professor; assessoria jurídica em caso real |
| D-05 | O direito de correção (art. 18, III) alcança opiniões e notas subjetivas? A equipe propõe contestação associada, sem alterar o original. | Afeta RF-DOC-06. | Professor; stakeholder |
| D-06 | Por quanto tempo manter avaliações e históricos? A LGPD não fixa prazo. Prazos trabalhistas e políticas internas não foram pesquisados. | Afeta RF-DOC-08 e o acompanhamento de evolução entre ciclos. | Stakeholder; assessoria jurídica em caso real |
| D-07 | Como tratar dado sensível inserido espontaneamente em comentário? Moderação prévia traz novo tratamento e pode afetar a confidencialidade. | Afeta RF-DOC-14 e o fluxo de moderação, se houver. | Stakeholder; professor |
| D-08 | O tratamento é de alto risco? Pode atender ao critério geral de afetar significativamente direitos (F03, art. 4º, I, "b"), mas falta critério específico, salvo decisão automatizada ou uso de dados sensíveis (F03, art. 4º, II, "c" e "d"). A ANPD não aprovou guia específico sobre alto risco (F14). | Indica a necessidade de RIPD (F08) e a perda do regime de pequeno porte. | Professor; assessoria jurídica em caso real |
| D-09 | Cálculo de nota ou classificação configura decisão "unicamente" automatizada? A equipe entende que não, se uma pessoa decidir com base no resultado, mas o sistema pode condicionar essa decisão na prática. | Afeta RN-DOC-06. Depende do uso dos resultados (perguntas 19 a 24 do roteiro). | Stakeholder; professor |
| D-10 | Dados coletados pela equipe em entrevistas e questionários estão na exceção de fins acadêmicos (art. 4º, II, "b")? Mesmo nesse caso, aplicam-se os arts. 7º e 11, e o processo já prevê cuidado antes de publicar. A exceção não alcançaria o uso real do sistema por uma organização. | Afeta o tratamento dos registros da própria disciplina. | Professor |
| D-11 | Existe ABNT NBR ISO/IEC 25010 alinhada à edição de 2023, e quais são os termos oficiais em português? O acesso ao texto completo da norma também está pendente, inclusive para conferir definições e subcaracterísticas obtidas em fontes secundárias. | Afeta a nomenclatura da especificação suplementar. | Equipe, por consulta ao catálogo da ABNT e à biblioteca da UFG |
| D-12 | Quais são as metas de resposta, usuários simultâneos, disponibilidade, recuperação, acessibilidade, dispositivos e critério de vulnerabilidades? As fontes consultadas não fixam valores. | Sem metas, RNF-DOC-08, 09, 13, 14 e 15 não são verificáveis. | Stakeholder; equipe |
| D-13 | A portabilidade (art. 18, V) depende de regulamentação da ANPD, não identificada nesta pesquisa. A cópia eletrônica integral (art. 19, §3º) depende da base legal. Lei Brasileira de Inclusão, legislação trabalhista e normas de segurança, como a família ISO/IEC 27000, não foram pesquisadas e podem gerar requisitos adicionais. | Afeta RF-DOC-09 e pode ampliar o escopo normativo. | Equipe; professor |
