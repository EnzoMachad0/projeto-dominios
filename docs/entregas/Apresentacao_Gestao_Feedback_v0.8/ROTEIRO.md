# Roteiro — Gestão e feedback v0.7

37 minutos de exposição + 3 minutos de reserva.

## 01. Requisitos de um sistema de gestão e feedback — 0.5 min

Apresentar a proposta e a equipe: Brenner Rodrigues Sardinha, Danilo Sucupira Galvão, Enzo de Oliveira Machado, Heitor Barbosa Souza e Luiz Augusto Vaz. Explicar o recorte: trabalho de levantamento e especificação, com protótipo. Não é uma aplicação implementada. A ilustração é conceitual, gerada por IA. Fonte: README.md; ilustração conceitual gerada com imagegen.

## 02. O que torna um feedback útil? — 1.25 min

Tempo de abertura conceitual: contrastar uma avaliação vaga com uma devolutiva concreta. O exemplo de reunião é fictício. Um feedback útil descreve comportamentos observáveis, explicita seus efeitos e permite reconhecer o que manter ou combinar o que melhorar. A estrutura dos registros será apresentada depois, no RF21. A base conceitual vem das anotações e da síntese das entrevistas, seções 2.1 e 2.4; não tratar o exemplo como ocorrência relatada pela professora.

## 03. Sumário — 0.75 min

Apresentar o objetivo acadêmico, a metodologia e o percurso da fala. A organização do trabalho entra antes do levantamento; a demonstração dos arquivos vem depois dos requisitos. A apresentação permanece sem uma seção de modelagem. Fonte: README.md e processo de requisitos.

## 04. Organização do trabalho — 0.5 min

Anunciar a organização do trabalho: apresentar a divisão de responsabilidades, o quadro de tarefas e o fluxo de revisão e integração dos documentos. Nos próximos slides, demonstrar os registros reais do GitHub.

## 05. Divisão das tarefas na equipe — 1 min

Explicar a distribuição com tarefas concretas, sem sugerir exclusividade: vários artefatos receberam colaboração e revisão de outras pessoas. Cada integrante produziu um caso de uso completo, como registra o índice de casos de uso. As demais contribuições foram conferidas nas issues e PRs do GitHub em 23/11/2026. Fontes: docs/casos-de-uso/README.md; issues 2 a 24; PRs 27, 28, 38, 39, 42 a 45 e 47.

## 06. Kanban do GitHub: acompanhamento — 1.5 min

Usar a captura exata enviada por Heitor nesta revisão: quatro colunas, sem cartões visíveis, com contadores em zero. A imagem mostra a organização do fluxo e não deve ser usada para contar as tarefas realizadas. Mostrar o quadro pelo link para navegar nos registros disponíveis. Não reutilizar os contadores ou cartões da representação da v0.4. Fonte visual: print fornecido pelo usuário; endereço do GitHub Projects da equipe.

## 07. Branches e integração por pull request — 1.5 min

Explicar o fluxo de versionamento com um exemplo verificável, sem entrar em comandos Git. Abrir o PR 47 e mostrar as abas Conversation e Files changed. A revisão alinhou códigos de fontes, prioridade de RF07 e RF16 e outros vínculos documentais. A branch de origem é docs/consistencia-artefatos e a base é main. Não afirmar que há proteção automática de branch configurada. Fonte: PR 47 e issue 46 do repositório.

## 08. Organização do repositório — 1 min

Abrir o repositório a partir do README e mostrar docs. A árvore é um recorte, não a listagem completa: docs/modelos, dicionario-dados.md e outros arquivos também existem. Distinguir o fonte editável Markdown dos PDFs consolidados. Evitar abrir todas as pastas; mostrar uma cadeia representativa depois. Fonte: árvore local do repositório e README.md.

## 09. Levantamento de requisitos — 0.4 min

Anunciar as três partes exatamente na ordem solicitada. Explicar a contribuição de cada uma e que observar algo no análogo não equivale à aprovação pelo stakeholder. Os questionários previstos no processo permanecem pendentes. Fonte: docs/PROCESSO\_REQUISITOS.md; docs/requisitos/lista-geral.md.

## 10. Entrevista com a professora: o que fizemos — 1.1 min

Apresentar a professora como stakeholder segundo o contexto informado por Heitor. A frase está nas anotações, não é uma transcrição de gravação: a apresentação corrige apenas acentuação da anotação. O repositório tem E01 e E02, que não devem ser automaticamente atribuídas à mesma pessoa. Fonte: anotações da entrevista, linha 8.

## 11. Entrevista: requisitos identificados — 1 min

Relacionar a linguagem original aos identificadores sem ler toda a tabela. Destacar que a especificação está majoritariamente proposta. O plano e a participação do 360° receberam interpretações adicionais, discutidas depois. A existência de RH também está nas notas e aparece nas permissões. Fonte: anotações da entrevista; lista-geral.md; síntese das entrevistas.

## 12. Pesquisa geral: o que pesquisamos — 1.25 min

Apresentar a pesquisa como entendimento do domínio e das soluções, além das referências legais e de qualidade. Os conceitos de feedback estão sistematizados na síntese das entrevistas (seções 2.1 a 2.5), e os padrões de sistemas aparecem no enunciado e na análise do Culture Amp. A análise aprofundada desse análogo vem na próxima parte. LGPD, ANPD e ISO/IEC 25010 estão documentadas em pesquisa-documental.md. Não atribuir à equipe estudos ou obras específicas que não constam dos arquivos.

## 13. Pesquisa geral: requisitos identificados — 1 min

Distinguir requisitos reforçados por fontes complementares de requisitos originados na pesquisa documental. RF19 e RF21 têm origem principal nas entrevistas; RF08 e RF14 a RF16 também estão apoiados no enunciado e nas entrevistas. A pesquisa ajuda a compreender e organizar essas necessidades. RF-DOC-01 e RF-DOC-03 decorrem da pesquisa documental, assim como a consolidação de RNF01, RNF06 e RNF07. Não alterar a origem oficial registrada na lista geral; requisitos documentados permanecem propostas conforme a situação de cada item. Fontes: lista-geral.md, pesquisa-documental.md, síntese das entrevistas e análise do Culture Amp.

## 14. Sistemas análogos: o que analisamos — 0.75 min

Descrever o análogo a partir da análise feita pela equipe. A imagem é uma ilustração oficial de acompanhamento de metas, usada para materializar a referência; não é evidência de implementação no projeto. O interesse está nos padrões de processo. Não apresentar a plataforma comercial inteira. Fonte: docs/levantamento/analise-sistema-analogo-culture-amp.md; https://www.cultureamp.com/platform/perform.

## 15. Sistemas análogos: requisitos identificados — 1 min

Escolher um exemplo da tabela e explicar a passagem da observação para a proposta. Não sugerir que recursos comerciais foram copiados integralmente nem confirmados automaticamente. O análogo também apresenta funcionalidades que não fazem sentido para a primeira versão. Fonte: análise do Culture Amp; docs/visao.md, seção 5.

## 16. Principais requisitos levantados — 0.5 min

Os números são contagens da lista geral. Não somar como funcionalidades independentes nem afirmar aprovação dos 36 IDs. Entre os RF principais, RF05 está marcado como validado; os demais estão propostos. Na sequência, destacar as necessidades anotadas na entrevista, não ler o inventário inteiro. Fonte: docs/requisitos/lista-geral.md, seção 3.

## 17. RF21 | Um feedback com contexto — 1.25 min

Introduzir Ana e Bruno como personagens fictícios para percorrer a apresentação. Mostrar que fato e impacto são diferentes de opinião genérica. O RF21 exige data, participantes, classificação e conteúdo. O questionário pode complementar o registro; não é sinônimo de todo o feedback. A anotação DOCUMENTAR OS FEEDBACKS está representada pelo registro e pelo histórico. Fonte: RF21; RN16; anotações da entrevista, linhas 14 a 21.

## 18. RF19 | Duas classificações — 0.75 min

Explorar as quatro combinações para mostrar que formal não significa construtivo nem informal significa positivo. A classificação fica disponível no histórico. O feedback informal é motivado por um evento e não cria campanha de avaliação. Fonte: RF19 e RF20; anotações da entrevista, linhas 1 e 12.

## 19. Feedback positivo: reconhecer o efeito — 0.75 min

Retomar literalmente o sentido da anotação sobre estrutura positiva: comportamento, bons impactos e benefícios. O exemplo não é um registro real. A síntese SIN-RF07 já contém essa orientação; o RF21 é genérico e ainda precisa detalhar como o sistema apoia o preenchimento. Não declarar esses passos como campos obrigatórios já validados. Fonte: anotações da entrevista, linha 24; SIN-RF07; RF21.

## 20. Feedback construtivo: gerar uma ação — 1 min

Destacar a sequência anotada pela professora, especialmente a reflexão e a verificação. Explicar a diferença entre apoiar uma boa conversa e exigir mecanicamente elogios em qualquer situação. O sistema não julga a qualidade do feedback automaticamente; registra contexto, ação e evidências. A operacionalização desses passos permanece uma lacuna nos RF oficiais. Fonte: anotações da entrevista, linha 26; SIN-RF08; RF18 e RF21.

## 21. RF17 e RF22 | Perspectivas de avaliação — 0.75 min

Ilustração conceitual gerada por IA, não um diagrama do sistema. A anotação diz que o gestor abre e todos participam, mas RF17 permite RH ou gestor selecionar participantes. Definir se todos significa time, pessoas vinculadas ao avaliado ou organização inteira. A proposta atual organiza papéis sem exigir reciprocidade; a autoavaliação tem avaliador igual ao receptor. Fonte: RF17, RF22 e RN15; anotações da entrevista, linhas 2 a 6.

## 22. RF18 | Plano com verificação observável — 1.25 min

Mostrar o significado dos parâmetros palpáveis anotados: não basta criar uma meta como melhorar. O projeto já prevê ação, responsável, prazo e ponto de verificação. Evidências e critérios testáveis são detalhamento a revisar. A relação temporal do plano com o feedback será apresentada entre as pendências. Fonte: RF18; RN13; anotações da entrevista, linhas 26 e 29.

## 23. RN12 | Preservar o que foi registrado — 0.75 min

Explicar que a especificação ampliou a anotação, proibindo exclusão física de todos os dados. Distinguir cancelamento de exclusão e mencionar que a retenção deve ser compatibilizada com as necessidades de proteção de dados. Não declarar o conflito resolvido. Fonte: anotações da entrevista, linha 31; RN12; RF12 e RF16.

## 24. Qualidade: como o sistema deve funcionar — 1 min

Diferenciar qualidade de funcionalidade. São requisitos propostos, não resultados de ensaios. Evitar citar desempenho como capacidade já comprovada. Conectar cada aspecto a um risco compreensível do processo de avaliação. Fonte: docs/requisitos/especificacao-suplementar.md.

## 25. Resultados e demonstrações — 0.5 min

Apresentar as duas partes desta seção: principais documentos produzidos e demonstração do Figma. Não há mais um bloco separado de funcionamento esperado.

## 26. Os documentos produzidos — 1.5 min

Apresentar o papel de cada documento e a pergunta que ele responde. Visão: por que o sistema existe e para quem? Requisitos: o que precisa fazer e respeitar? Caso de uso: como a interação acontece, inclusive nas falhas? Dicionário: qual o significado dos dados? Rastreabilidade: de onde veio e como conferir? Documentação mestre: onde encontrar a síntese da etapa? Exemplos são extraídos de docs/visao.md, requisitos, CU-02, dicionario-dados.md e matriz-rastreabilidade.md. A seguir, aprofundar três documentos e demonstrar seus arquivos.

## 27. Especificação de requisitos — 2 min

Abrir a especificação e mostrar sua organização: funcionalidades, regras de negócio, requisitos de qualidade e critérios de aceitação. Ler o trecho RF21 como exemplo de requisito com contexto do feedback. Depois localizar RF12 e CA08 para mostrar que a descrição do comportamento tem uma forma concreta de verificação: avaliação completa, envio único, respostas imutáveis e avaliação inversa independente. Na lista geral, mostrar fonte, prioridade e situação. O papel do documento é orientar uma implementação verificável; não afirmar que os testes ou a implementação já foram executados.

## 28. Caso de uso completo — 2 min

Demonstrar o CU-02, de autoria de Luiz Augusto Vaz. O ator é o participante no papel de avaliador, que pode ter perfil RH, Gestor ou Profissional. Pré-condições: autenticação, coleta aberta dentro do período e avaliação atribuída em rascunho. Mostrar o fluxo até a confirmação do envio e as garantias de sucesso: ENVIADA, respostas válidas e imutáveis, envio único e independência da avaliação inversa. Abrir a extensão 6a (valor inválido), 8a (perguntas pendentes) e 11c (falha com reversão integral). Relacionar RF11/RF12 e CA07/CA08. Fonte: docs/casos-de-uso/CU-02-responder-e-enviar-avaliacao.md.

## 29. Matriz de rastreabilidade — 2 min

Abrir as linhas RF11 e RF12 da matriz. RF11 se liga a E01, CU-02 e CA01/CA07; RF12 se liga a E01, CU-02 e CA08. Percorrer o vínculo nos dois sentidos: a fonte justifica a necessidade, o caso de uso detalha a interação e o critério de aceitação define o que conferir. Exemplificar impacto: uma mudança no envio exige conferir RF12, CU-02 e CA08. A matriz também mantém situação e relações com outros artefatos, embora esta apresentação não detalhe a modelagem. As figuras mostram colunas selecionadas do documento real.

## 30. Demonstração: seguir uma informação — 1.5 min

Navegar nos arquivos seguindo uma informação real: README para localizar a documentação; lista geral para fonte, prioridade e situação do RF12; CU-02 para resposta em rascunho e envio; matriz para o vínculo com CA08. Abrir o critério CA08 na especificação e conferir as garantias: único envio e imutabilidade. Usar os arquivos locais selecionados no pacote se a rede falhar. Reservar o tempo para mostrar os arquivos, sem ler apenas a tabela.

## 31. Protótipo PulsarRH — 0.5 min

Abrir previamente o Figma e usar o link clicável ou QR. O conector não permitiu acesso ao arquivo durante a preparação desta versão; não foram inventadas capturas. O percurso a seguir deve ser adaptado ao que realmente estiver representado. Não apresentar imagens conceituais desta apresentação como telas do Figma. Fonte: README.md; link do protótipo; matriz de rastreabilidade, L03.

## 32. Percurso 1 | Organizar uma avaliação — 1.75 min

Reservar o tempo para navegar no Figma, em vez de ler o slide. Posicionar o protótipo no perfil administrativo, se essa área existir. Relacionar o que está na interface às decisões de período, questionário e participantes. Não simular funcionalidades indisponíveis. Explicar eventuais lacunas usando a tabela como critério de observação. Se o acesso ao Figma falhar durante a apresentação, usar o tempo para discutir as decisões esperadas, sem alegar demonstração concluída. Fonte: RF01, RF08, RF09, RF17; matriz de rastreabilidade, L03.

## 33. Percurso 2 | Responder e acompanhar — 1.75 min

Demonstrar apenas as telas existentes. Procurar clareza sobre quem verá a resposta, possibilidade de retomar e confirmação do envio. Relacionar o registro de fatos à devolutiva e ao desenvolvimento. O protótipo não valida persistência nem cálculo dos indicadores. A matriz ainda não liga cada tela aos requisitos; essa é uma pendência de rastreabilidade. Fonte: RF11, RF12, RF14, RF18 e RF21; matriz de rastreabilidade, L03.

## 34. Encerramento — 1 min

Encerrar com as contribuições efetivamente produzidas. O principal resultado é a explicitação das necessidades e das decisões, não uma aplicação em produção. Relembrar que o acompanhamento é central para avaliar o efeito do feedback. Agradecer e abrir o tempo de reserva para perguntas. A equipe completa consta no preâmbulo e neste roteiro. Fonte: README.md; documento de visão; pauta de validação.
