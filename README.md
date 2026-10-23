
# 🛡️ SPI Alert — FutureVision

## Challenge de Engenharia de Software | Sprints 1, 2, 3 e 4

**Metaindústria | SPI Integração**

---

## 👥 Integrantes

| Nome | RM |
|---|---|
| João Viviani Baldini | 558596 |
| Lucas Costa Sanson | 556042 |
| Giuliano Ferreira Venceslau | 558674 |
| Eric Perez Martinez Melillo Siciliano | 558651 |
| Enrico Nikolay Meirelles Zeronian | 558557 |

---

# 1. Contexto e Problema Abordado

A segurança industrial é um desafio constante para empresas que operam com máquinas pesadas, áreas de risco e atividades que exigem o uso adequado de Equipamentos de Proteção Individual (EPIs).

Na Metaindústria, a identificação de situações de risco e o acompanhamento da conformidade dos EPIs são fundamentais para proteger os colaboradores e apoiar decisões preventivas.

Processos de fiscalização predominantemente manuais podem dificultar a identificação rápida de irregularidades, atrasar respostas e comprometer o acompanhamento das ocorrências.

Diante desse cenário, surgiu o **SPI Alert — FutureVision**, uma proposta de solução tecnológica voltada à gestão inteligente da segurança industrial.

## 1.1 Objetivo do Projeto

Desenvolver uma aplicação que auxilie supervisores e equipes de segurança no gerenciamento de EPIs, no registro de ocorrências e no acompanhamento de indicadores de segurança.

## 1.2 Problema Identificado

Os principais desafios considerados pelo projeto são:

- Dificuldade no acompanhamento dos EPIs dos colaboradores.
- Necessidade de identificar equipamentos vencidos ou em condições inadequadas.
- Registro e acompanhamento de ocorrências de segurança.
- Falta de centralização das informações.
- Necessidade de indicadores para apoiar decisões preventivas.

---

# 2. Proposta de Solução

O **SPI Alert** é uma aplicação web voltada ao gerenciamento de EPIs e ao acompanhamento de riscos industriais.

A solução reúne diferentes funcionalidades em uma única interface, permitindo que o supervisor consulte informações relevantes e acompanhe ocorrências.

## 2.1 Principais Funcionalidades

### Dashboard Operacional

Apresenta indicadores gerais da operação:

- Quantidade de alertas ativos.
- Percentual de EPIs regulares.
- Número de colaboradores cadastrados.
- Quantidade de câmeras cadastradas.
- Alertas recentes.

### Gestão de EPIs

Permite:

- Consultar EPIs registrados.
- Cadastrar equipamentos para colaboradores.
- Informar o Certificado de Aprovação (CA).
- Registrar validade e condição do equipamento.
- Identificar EPIs regulares, próximos do vencimento ou irregulares.
- Pesquisar equipamentos e colaboradores.

### Alertas de Segurança

Permite:

- Emitir alertas manualmente.
- Classificar riscos por severidade.
- Associar alertas a setores e câmeras.
- Consultar o histórico de ocorrências.
- Alterar o status para **Em análise**.
- Marcar ocorrências como **Resolvidas**.

### Monitoramento Industrial

Apresenta uma visualização demonstrativa das câmeras industriais cadastradas:

- CAM-001 — Almoxarifado.
- CAM-003 — Linha de Produção 3.
- CAM-005 — Laboratório Químico.
- CAM-007 — Setor B.

A interface apresenta os alertas ativos associados a cada câmera.

**Importante:** o monitoramento utiliza dados simulados. Não existe transmissão real de vídeo.

### Relatórios de Conformidade

Permite consultar:

- Total de EPIs cadastrados.
- Quantidade de EPIs regulares.
- Quantidade de EPIs irregulares.
- Alertas pendentes.
- Alertas resolvidos.

Também oferece impressão ou salvamento em PDF pelo navegador e preparação de um e-mail com o resumo dos registros.

---

# 3. Tecnologias Utilizadas

## 3.1 Tecnologias da Aplicação Final

| Tecnologia | Finalidade |
|---|---|
| HTML5 | Estrutura das telas |
| CSS3 | Interface visual e responsividade |
| JavaScript | Navegação e funcionalidades |
| LocalStorage | Armazenamento local dos registros |
| SessionStorage | Controle da sessão demonstrativa |
| Git e GitHub | Versionamento e organização do código |
| Trello | Gerenciamento das Sprints e atividades |

## 3.2 Justificativa das Escolhas Técnicas

### HTML5

Utilizado para organizar a estrutura da aplicação, seus formulários, tabelas e diferentes telas.

### CSS3

Responsável pela identidade visual do SPI Alert, pela organização dos componentes e pela adaptação a diferentes tamanhos de tela.

### JavaScript

Implementa as regras de negócio e as interações do usuário, incluindo cadastro de EPIs, emissão e atualização de alertas, filtros e indicadores.

### LocalStorage

Permite manter os registros demonstrativos salvos no navegador mesmo depois de atualizar ou fechar a página.

### SessionStorage

Utilizado para controlar a sessão de acesso durante a navegação.

## 3.3 Tecnologias Previstas para Evolução Futura

A arquitetura conceitual do projeto também considerou:

- **Python:** processamento e integração de componentes inteligentes.
- **OpenCV:** processamento de imagens.
- **YOLOv8:** detecção de objetos e equipamentos de proteção.
- **MediaPipe:** análise de postura corporal.
- **FastAPI:** desenvolvimento de APIs.
- **Oracle Database:** armazenamento centralizado.
- **Streamlit ou React:** evolução da interface.

Essas tecnologias fazem parte da proposta de evolução do sistema e **não estão integradas à aplicação HTML entregue na Sprint 4**.

---

# 4. Arquitetura do Sistema

## 4.1 Visão Geral

A arquitetura da versão demonstrativa utiliza uma aplicação web executada diretamente no navegador.

### Fluxo da Aplicação

1. O supervisor acessa a aplicação.
2. A interface apresenta as funcionalidades disponíveis.
3. O JavaScript processa as ações realizadas.
4. Os registros são armazenados no LocalStorage.
5. As informações atualizadas são apresentadas no dashboard, nas listas e nos relatórios.

### Estrutura Lógica

**Usuário → Interface HTML/CSS → JavaScript → LocalStorage → Indicadores e Relatórios**

## 4.2 Camada de Interface

Responsável pela apresentação das telas e pela interação com o usuário.

## 4.3 Camada de Regras de Negócio

Implementada em JavaScript.

Responsável por:

- Registrar EPIs.
- Verificar validade e condição dos equipamentos.
- Cadastrar ocorrências.
- Atualizar status dos alertas.
- Calcular indicadores.
- Filtrar e apresentar informações.

## 4.4 Camada de Dados

Os registros são mantidos no armazenamento local do navegador.

A aplicação possui uma base inicial de dados simulados para permitir a demonstração das funcionalidades.

## 4.5 Arquitetura Evolutiva

A proposta de evolução futura prevê:

**Câmeras Industriais → Visão Computacional → Análise de Risco → Backend/API → Banco de Dados → Dashboard do Supervisor**

Essa arquitetura permitiria futuramente integrar equipamentos, identificar riscos por inteligência artificial e centralizar informações em um ambiente corporativo.

## 4.6 Documentação Complementar

Os diagramas UML e a arquitetura conceitual estão disponíveis em:

[Consultar DIAGRAMAS.md](DIAGRAMAS.md)

O documento de arquitetura final deverá consolidar as decisões técnicas das quatro Sprints.

---

# 5. Engenharia de Requisitos

A definição dos requisitos considerou o contexto de segurança industrial da Metaindústria e as necessidades de acompanhamento dos supervisores.

## 5.1 Requisitos Funcionais Implementados

- RF01 — Permitir acesso demonstrativo à aplicação.
- RF02 — Exibir indicadores gerais de segurança.
- RF03 — Consultar registros de EPIs.
- RF04 — Cadastrar EPIs para colaboradores.
- RF05 — Identificar validade e condição dos equipamentos.
- RF06 — Emitir alertas de risco.
- RF07 — Consultar o histórico de alertas.
- RF08 — Atualizar o status das ocorrências.
- RF09 — Visualizar o monitoramento demonstrativo.
- RF10 — Consultar relatórios de conformidade.
- RF11 — Manter os registros no navegador.
- RF12 — Restaurar os dados iniciais da demonstração.

## 5.2 Requisitos Não Funcionais

- Interface simples e intuitiva.
- Navegação organizada.
- Compatibilidade com navegadores modernos.
- Layout adaptável.
- Execução sem instalação de servidor.
- Organização e legibilidade do código.

## 5.3 Documentação de Requisitos

As personas, os requisitos e as definições elaboradas ao longo do projeto estão documentados em:

[Consultar REQUISITOS.md](REQUISITOS.md)

**Observação:** funcionalidades de autenticação corporativa, visão computacional real e integração com câmeras industriais permanecem como requisitos de evolução futura.

---

# 6. Aplicação Final — Sprint 4

## 6.1 Objetivo da Entrega

A Sprint 4 concentra-se na transformação do protótipo desenvolvido nas etapas anteriores em uma aplicação demonstrativa funcional.

O objetivo é permitir que o avaliador execute o sistema e navegue pelos principais fluxos de gerenciamento de EPIs e segurança industrial.

## 6.2 Funcionalidades Desenvolvidas

### Login Demonstrativo

A aplicação apresenta uma tela de acesso com matrícula e senha.

Para a demonstração, qualquer matrícula e senha não vazias permitem a entrada.

**O login não realiza autenticação real de usuários.**

### Cadastro de EPIs

O usuário seleciona um colaborador e registra:

- Tipo do equipamento.
- Número do CA.
- Data de validade.
- Condição do EPI.

Após o cadastro, o equipamento aparece na listagem.

### Persistência dos Registros

Os EPIs e alertas são armazenados no LocalStorage.

Assim, as informações permanecem disponíveis após atualizar ou reabrir a aplicação no mesmo navegador, desde que seus dados não sejam apagados.

### Emissão e Gestão de Alertas

O sistema permite criar ocorrências e acompanhar seus status.

Os alertas podem ser classificados como:

- Aberto.
- Em análise.
- Resolvido.

### Indicadores Dinâmicos

Os indicadores do dashboard são calculados a partir dos registros disponíveis na aplicação.

### Monitoramento Simulado

O sistema apresenta quatro câmeras cadastradas e os alertas associados a cada uma.

### Relatórios

Os relatórios utilizam os registros demonstrativos disponíveis e podem ser impressos ou salvos em PDF por meio do navegador.

---

# 7. Instalação e Execução

## 7.1 Pré-requisitos

Para executar o SPI Alert, é necessário apenas:

- Computador com navegador atualizado.
- Google Chrome, Microsoft Edge ou Mozilla Firefox.
- Acesso ao repositório GitHub para baixar o projeto.

**Não é necessário instalar Python, Node.js, Oracle ou qualquer servidor.**

## 7.2 Repositório GitHub

[**Acessar o repositório do SPI Alert**](https://github.com/joao-baldini/Challenge-Sprint-1-Engenharia-de-Sofware)

## 7.3 Como Executar

### Passo 1 — Baixar o Projeto

Acesse o repositório GitHub.

Clique em:

**Code → Download ZIP**

### Passo 2 — Extrair os Arquivos

Extraia o conteúdo do arquivo ZIP para uma pasta do computador.

### Passo 3 — Abrir a Aplicação

Localize o arquivo:

`spi-prototipo.html`

Abra o arquivo em um navegador.

### Passo 4 — Fazer Login

Na tela inicial:

1. Digite uma matrícula.
2. Digite uma senha.
3. Clique em **Entrar**.

Como o acesso é demonstrativo, qualquer matrícula e senha não vazias são aceitas.

### Passo 5 — Navegar pelo Sistema

Utilize o menu para acessar:

- Dashboard.
- EPIs.
- Alertas.
- Monitoramento.
- Relatórios.

## 7.4 Arquivo Principal

[**Abrir spi-prototipo.html**](spi-prototipo.html)

---

# 8. Manual de Uso da Aplicação

## 8.1 Dashboard

Após realizar o login, o usuário visualiza os indicadores gerais do sistema.

Esses indicadores oferecem uma visão resumida das condições de segurança registradas.

## 8.2 Como Cadastrar um EPI

1. Acesse o menu **EPIs**.
2. Selecione o colaborador.
3. Escolha o tipo de equipamento.
4. Informe o número do CA.
5. Informe a data de validade.
6. Selecione a condição.
7. Clique em **Registrar EPI**.
8. Confira o novo registro na tabela.

## 8.3 Como Emitir um Alerta

1. Acesse **Alertas**.
2. Escolha o tipo de risco.
3. Selecione a severidade.
4. Informe o setor.
5. Escolha a câmera associada.
6. Descreva a ocorrência.
7. Clique em **Emitir alerta**.

O registro será adicionado ao histórico de ocorrências.

## 8.4 Como Resolver um Alerta

1. Acesse **Alertas**.
2. Localize uma ocorrência pendente.
3. Clique em **Em análise**, se desejar registrar essa etapa.
4. Clique em **Resolver** para finalizar a ocorrência.

O status e os indicadores serão atualizados.

## 8.5 Como Consultar as Câmeras

1. Acesse **Monitoramento**.
2. Visualize as câmeras cadastradas.
3. Consulte a quantidade de alertas ativos associados a cada câmera.

O monitoramento apresentado é simulado.

## 8.6 Como Gerar um Relatório

1. Acesse **Relatórios**.
2. Consulte os indicadores.
3. Clique em **Exportar PDF / Imprimir**.
4. Escolha a opção **Salvar como PDF** no navegador.

## 8.7 Como Restaurar os Dados

A aplicação possui uma opção para restaurar os dados demonstrativos.

**Atenção:** essa ação apaga os registros adicionados durante a utilização e recupera a base inicial de demonstração.

---

# 9. Evolução do Projeto — Sprints 1 a 4

## 9.1 Sprint 1 — Concepção da Solução

### Objetivo

Identificar o problema da Metaindústria e estruturar uma proposta tecnológica para gerenciamento de EPIs e prevenção de riscos.

### Principais Entregas

- Definição do problema.
- Proposta de solução.
- Levantamento inicial de requisitos.
- Definição das tecnologias consideradas.
- Arquitetura conceitual.
- Protótipo inicial.

## 9.2 Sprint 2 — Refinamento do Projeto

### Objetivo

Aprofundar a modelagem e evoluir os fluxos de interação da aplicação.

### Principais Entregas

- Evolução da documentação.
- Refinamento dos fluxos do protótipo.
- Organização das informações.
- Melhorias na experiência de navegação.
- Revisão de requisitos e decisões técnicas.

## 9.3 Sprint 3 — Evolução do Protótipo e Scrum

### Objetivo

Ampliar os fluxos do protótipo, aperfeiçoar a documentação e organizar o acompanhamento ágil do projeto.

### Principais Entregas

- Tela de login.
- Fluxo de monitoramento demonstrativo.
- Melhorias de navegação.
- Busca e filtros.
- Validação de formulários.
- Atualização dos diagramas.
- Organização do Trello.
- Documentação das cerimônias Scrum.

## 9.4 Sprint 4 — Aplicação Final

### Objetivo

Consolidar as entregas anteriores em uma aplicação demonstrativa funcional, acompanhada da documentação final.

### Principais Evoluções do Código

- Cadastro de EPIs com armazenamento local.
- Consulta de registros.
- Validação de validade e condição dos equipamentos.
- Emissão de alertas.
- Atualização do status das ocorrências.
- Indicadores calculados dinamicamente.
- Monitoramento demonstrativo das câmeras.
- Relatórios baseados nos registros.
- Organização da aplicação para execução no navegador.

### Consolidação da Entrega

A Sprint 4 também prevê:

- Atualização final do README.
- Documento de arquitetura consolidado.
- Atualização do Trello.
- Registro da Sprint Review final.
- Vídeo de pitch e demonstração.
- Arquivo TXT com os links de entrega.

---

# 10. Gestão Ágil — Scrum

## 10.1 Metodologia

O projeto foi organizado com base em práticas do Scrum, permitindo distribuir atividades, acompanhar o desenvolvimento e registrar a evolução do produto ao longo das quatro Sprints.

## 10.2 Board Trello

O acompanhamento das atividades foi estruturado com as seguintes listas:

1. Product Backlog.
2. Sprint Backlog.
3. Em andamento.
4. Em revisão.
5. Concluído.

### Link do Trello

[**SPI Alert — FutureVision | Board Scrum**](https://trello.com/b/kyfYSZDH/spi-alert-sprint-4-futurevision)

**Atenção:** o link acima é um convite para o board. Antes da entrega, o grupo deverá confirmar o acesso dos avaliadores e substituir pelo link público de visualização, caso seja diferente.

## 10.3 Artefatos Scrum

Os artefatos considerados no projeto incluem:

- Product Backlog priorizado.
- Sprint Backlogs.
- Distribuição de responsáveis.
- Acompanhamento do andamento das atividades.
- Definition of Done.
- Registro das cerimônias Scrum.

## 10.4 Cerimônias Scrum

As práticas documentadas incluem:

### Sprint Planning

Planejamento das atividades e definição das prioridades da Sprint.

### Daily Scrum

Acompanhamento do progresso e identificação de impedimentos.

### Sprint Review

Apresentação e avaliação das entregas realizadas.

### Definition of Done

Critérios utilizados para considerar uma atividade concluída.

### Documentação das Cerimônias

[**Consultar CERIMONIAS_SCRUM.md**](CERIMONIAS_SCRUM.md)

## 10.5 Sprint Review Final

A Review da Sprint 4 deverá registrar:

- Funcionalidades efetivamente demonstradas.
- Resultados dos testes.
- Problemas identificados e corrigidos.
- Pendências existentes.
- Avaliação final da entrega pelo grupo.

A ata deve refletir a reunião e os resultados reais, após sua realização.

---

# 11. Testes e Validação

## 11.1 Fluxos Validados

Antes da entrega, o grupo deverá testou:

 Abertura do arquivo HTML.
 Login com matrícula e senha preenchidas.
 Navegação entre todas as telas.
 Cadastro de um novo EPI.
 Exibição do EPI na tabela.
 Identificação de EPIs irregulares.
 Emissão de um novo alerta.
 Alteração de status para Em análise.
 Resolução de um alerta.
 Atualização dos indicadores.
 Visualização das câmeras simuladas.
 Consulta aos relatórios.
 Impressão ou salvamento em PDF.
 Persistência após atualização da página.
 Restauração dos dados iniciais.

---

# 12. Limitações da Solução

A aplicação entregue é uma demonstração acadêmica funcional, desenvolvida para apresentar os principais fluxos de gestão de EPIs e acompanhamento de segurança.

## 12.1 Limitações Atuais

- O login não possui autenticação corporativa real.
- Os dados utilizados são simulados.
- Os registros ficam armazenados localmente no navegador.
- Não existe integração com câmeras industriais reais.
- Não existe transmissão de imagens ao vivo.
- Não existe processamento real de inteligência artificial.
- Não existe integração com Oracle Database.
- O envio de e-mail depende do aplicativo configurado no dispositivo.
- O PDF é gerado utilizando a funcionalidade de impressão do navegador.

## 12.2 Possibilidades de Evolução

Uma futura versão poderá incluir:

- Backend com API.
- Banco de dados centralizado.
- Controle de acesso por perfil.
- Integração com câmeras industriais.
- Detecção automática de EPIs com visão computacional.
- Análise de postura.
- Notificações em tempo real.
- Relatórios históricos avançados.
- Integração com sistemas corporativos da Metaindústria.

**O protótipo não substitui procedimentos reais de segurança industrial.**

---

# 13. Vídeo de Pitch e Demonstração

## 13.1 Objetivo

Apresentar o projeto SPI Alert — FutureVision e demonstrar a evolução da solução durante as quatro Sprints.

## 13.2 Conteúdo do Vídeo

O vídeo final, com duração máxima de 5 minutos, deverá apresentar:

1. Integrantes do grupo.
2. Problema identificado na Metaindústria.
3. Proposta de solução.
4. Tecnologias utilizadas.
5. Demonstração da aplicação funcionando.
6. Evolução entre as quatro Sprints.
7. Impacto esperado para a segurança industrial.

## 13.3 Participação do Grupo

O vídeo deverá contar com a participação dos integrantes e suas próprias falas.

**Narrações automatizadas por inteligência artificial não serão utilizadas.**

## 13.4 Link do Vídeo

**SPI Alert — Sprint 4 Demonstração Final**

`https://youtu.be/WIDhLLv6x5U`

---

# 14. Organização do Repositório

## 14.1 Arquivos Principais

| Arquivo | Descrição |
|---|---|
| `README.md` | Documentação principal do projeto |
| `spi-prototipo.html` | Aplicação funcional demonstrativa |
| `REQUISITOS.md` | Engenharia de requisitos |
| `DIAGRAMAS.md` | Diagramas UML e arquitetura conceitual |
| `CERIMONIAS_SCRUM.md` | Registros das cerimônias Scrum |

## 14.2 Documentos Finais Previstos

Os documentos abaixo deverão ser adicionados ao repositório para completar a entrega:

- `ARQUITETURA_FINAL.md` — decisões técnicas e arquitetura final.
- `REVIEW_SPRINT4.md` — registro da Sprint Review final.

---

# 15. Entrega Final da Sprint 4

Conforme o enunciado, o envio final será realizado por meio de **um único arquivo `.txt`**.

Esse arquivo deverá conter:

- Nome e RM de todos os integrantes.
- Link do repositório GitHub final.
- Link do board Trello atualizado.
- Link do vídeo no YouTube, publicado como não listado.

O repositório deverá conter a aplicação e a documentação necessárias para execução e avaliação.

---

# 🛡️ FutureVision — SPI Alert

**Gerenciamento inteligente de EPIs e apoio à prevenção de riscos industriais.**

**Challenge de Engenharia de Software — Metaindústria | SPI Integração**

