# Challenge — Sprints 1, 2 e 3 — Engenharia de Software

# 🛡️ Projeto FutureVision: Visão Computacional e Prevenção Proativa na Metaindústria

## 👥 Integrantes

- **João Viviani Baldini** — RM 558596
- **Lucas Costa Sanson** — RM 556042
- **Giuliano Ferreira Venceslau** — RM 558674
- **Eric Perez Martinez Melillo Siciliano** — RM 558651
- **Enrico Nikolay Meirelles Zeronian** — RM 558557

---

## 💡 1. Contexto e Problema Abordado

O ambiente industrial da Metaindústria lida diariamente com cenários complexos onde a integridade física dos operadores está exposta a riscos de alta gravidade, como máquinas pesadas, zonas de alta temperatura e movimentação de cargas.

O modelo tradicional de segurança do trabalho atua de forma punitiva ou reativa: identifica-se a infração, como um operador sem capacete, após o evento ou quando o acidente já ocorreu.

O problema central reside na latência humana e reativa. A falta de ferramentas inteligentes capazes de interpretar dados comportamentais em tempo real impede que supervisores ajam antes que o risco se converta em um acidente de trabalho incapacitante ou fatal.

---

## ✅ 2. Proposta de Solução

Nossa proposta quebra o status quo ao implementar um sistema de **Proteção Ativa de Funcionários**, baseado em Inteligência Artificial Preditiva e Visão Computacional.

Em vez de apenas gerar relatórios de infrações, o ecossistema aprende padrões de comportamento no chão de fábrica para antecipar riscos.

### Como a solução funciona na prática — Arquitetura Evolutiva

**I. Detecção de EPIs — Fase 1**

Câmeras industriais processam feeds de vídeo locais para validar o uso correto de capacetes, coletes e luvas.

**II. Análise de Postura e Áreas de Risco — Fase 2**

Modelos de *Pose Estimation* calculam a proximidade dos operadores em relação a zonas de perigo, como robôs industriais em operação, além de identificar desvios ergonômicos críticos.

**III. Alerta Cirúrgico — Fase 3**

Caso um operador caminhe em direção a uma área restrita sem o EPI adequado ou de forma insegura, um alerta visual e sonoro é disparado imediatamente na célula de trabalho e um evento crítico é enviado ao Dashboard do Supervisor.

---

## 💻 3. Tecnologias Selecionadas e Justificativa Técnica

Para atender aos requisitos de baixa latência e alta confiabilidade exigidos pela SPI e pelo ambiente industrial, a pilha tecnológica foi definida da seguinte forma:

### Python

Linguagem de programação principal do projeto, escolhida por sua ampla utilização em ciência de dados e Inteligência Artificial e pela integração com bibliotecas de Visão Computacional.

### OpenCV + Ultralytics YOLOv8

Responsáveis pela Visão Computacional e detecção de objetos em tempo real, possibilitando a identificação de EPIs e situações de risco.

### MediaPipe

Framework utilizado para estimativa de pose e mapeamento de pontos articulados do corpo, permitindo a análise de postura e riscos ergonômicos.

### FastAPI

Framework utilizado como backend/API da solução, permitindo comunicação rápida entre os componentes de processamento e a interface do sistema.

### Oracle Database

Banco de dados relacional utilizado para armazenamento de informações de funcionários, EPIs, histórico de alertas e métricas de conformidade.

### Streamlit / React

Tecnologias consideradas para construção da interface e dos dashboards operacionais, permitindo a visualização de informações e fluxos analíticos.

---

## 🗺️ 4. Modelagem do Sistema — UML

Os diagramas foram modelados de forma integrada para garantir a coesão técnica do ecossistema.

Os **Casos de Uso** representam as principais interações dos usuários com o sistema, o **Diagrama de Atividades** demonstra o fluxo operacional e o **Diagrama de Classes** apresenta a estrutura das principais entidades da solução.

Os diagramas atualizados estão disponíveis em:

➡️ [DIAGRAMAS.md](DIAGRAMAS.md)

---

## 📋 5. Engenharia de Requisitos

A análise detalhada de personas, requisitos funcionais (RF), requisitos não funcionais (RNF) e restrições do projeto está disponível no documento:

➡️ [REQUISITOS.md](REQUISITOS.md)

---

## 📲 6. Protótipo da Aplicação e Instruções de Uso

Na Sprint 3, os fluxos que ainda estavam apenas visuais foram corrigidos e implementados.

Foram adicionadas funcionalidades de:

- Busca;
- Filtros;
- Chips de seleção;
- Validação de formulários;
- Correção de botões sem ação;
- Navegação entre telas.

Também foram adicionadas duas novas telas:

- **Login**
- **Monitoramento — Câmeras ao vivo**

### 👨‍🏫 Instruções para uso

### Login

Ao abrir o app, a primeira tela apresentada é o login do supervisor.

Informe qualquer matrícula e senha não vazias e toque em **Entrar**.

A autenticação é simulada para fins de protótipo, sem validação de credencial real.

A opção **Esqueci minha senha** simula o fluxo de recuperação de senha.

### Tela Principal — Home

Após o login, o usuário acessa o dashboard com:

- Total de alertas abertos;
- Conformidade geral;
- Quantidade de colaboradores;
- Setores ativos;
- Alertas críticos recentes.

O menu principal permite navegar entre as funcionalidades.

O ícone de logout no header encerra a sessão e retorna à tela de login.

---

### Fluxo 1 — EPIs por Colaborador

1. Na Home, acesse **EPIs por Colaborador**.
2. Utilize a barra de busca para localizar um colaborador pelo nome.
3. Utilize as abas **Todos**, **Irregulares** e **Vencendo** para filtrar a lista.
4. Selecione um colaborador para visualizar seus EPIs cadastrados.
5. Clique em **+ EPI** para cadastrar um novo equipamento.
6. Selecione o tipo de EPI e sua condição.
7. Preencha o número do CA, data de entrega e validade.
8. Clique em **Registrar EPI**.

O formulário verifica os campos obrigatórios antes de permitir o cadastro.

---

### Fluxo 2 — Alertas de Risco

1. Na Home, acesse **Alertas de Risco**.
2. Visualize os alertas classificados por severidade: Crítico, Alto, Médio ou Baixo.
3. Utilize as abas **Abertos**, **Em Análise** e **Resolvidos**.
4. Selecione um alerta para visualizar localização, câmera, colaborador e confiança da IA.
5. Para emitir um alerta manual, clique em **+ Emitir**.
6. Selecione o tipo de risco, severidade e localização.
7. Informe a câmera e a descrição.
8. Clique em **Emitir Alerta**.

---

### Fluxo 3 — Relatório de Conformidade

Na Home, acesse **Relatório de Conformidade**.

A tela apresenta:

- Índice geral de conformidade da fábrica;
- Conformidade por setor;
- Quantidade de alertas;
- EPIs próximos do vencimento.

As opções **Exportar PDF** e **Enviar por E-mail** fornecem retorno visual no protótipo.

---

### Fluxo 4 — Monitoramento

Na Home, acesse **Monitoramento**.

A tela apresenta as câmeras ativas da planta:

- CAM-001;
- CAM-003;
- CAM-005;
- CAM-007.

Também são apresentados os respectivos setores e status.

Câmeras com alerta ativo ficam destacadas visualmente e permitem acessar o detalhe do alerta correspondente.

---

### Navegação

O aplicativo possui uma barra de navegação inferior com acesso rápido a:

- 🏠 Home
- ⚠️ Alertas
- 👷 EPIs
- 📊 Relatório

---

## 🔄 7. Evolução do Protótipo — Sprint 3

O protótipo de alta fidelidade foi revisado para cobrir fluxos que ainda não existiam nas entregas anteriores, corrigir interações que estavam apenas visuais e refinar a experiência de uso conforme os requisitos funcionais definidos no `REQUISITOS.md`.

### Protótipo atualizado

➡️ [spi-prototipo.html](spi-prototipo.html)

### Novas telas e fluxos adicionados

| Tela / Fluxo | Justificativa |
|---|---|
| **Login** | O fluxo de autenticação ainda não havia sido implementado. Na Sprint 3, o aplicativo passou a iniciar pelo login e somente permite o acesso ao dashboard após o preenchimento de matrícula e senha. Também foi incluído o logout para completar o ciclo da sessão. |
| **Monitoramento — Câmeras ao vivo** | O botão de Monitoramento já existia no menu, mas não possuía ação. A nova tela representa visualmente o monitoramento das câmeras industriais e aproxima o protótipo dos requisitos de processamento de vídeo e dashboard operacional. |

### Correções de usabilidade e funcionalidades

Durante a revisão da Sprint 3, foram identificadas e corrigidas interações que existiam apenas como elementos visuais estáticos.

Foram realizadas as seguintes melhorias:

- Correção da navegação por breadcrumb;
- Implementação das abas de filtro na tela de EPIs;
- Implementação das abas de filtro na tela de Alertas;
- Busca de colaboradores em tempo real;
- Chips de seleção interativos;
- Retorno visual nos botões que anteriormente não possuíam ação;
- Validação dos campos obrigatórios nos formulários;
- Inclusão da navegação inferior nas telas internas;
- Implementação do fluxo de login e logout;
- Implementação da tela de Monitoramento.

---

## 🗂️ 8. Gestão Ágil — Scrum

Na Sprint 3, o trabalho do grupo foi organizado utilizando **Scrum**, com acompanhamento das atividades por meio de um board no Trello.

### 📌 Board Scrum — Trello

➡️ [Acessar o Board Scrum da Sprint 3](https://trello.com/invite/b/6ab1ddd41dfe3844ba17ad61/ATTI1a4b448a4c20d288a998f1fd41372de577EBAD2B/spi-alert-sprint-3-futurevision)

O board foi estruturado com as seguintes etapas:

- **Product Backlog**
- **Sprint Backlog — Sprint 3**
- **Em andamento**
- **Em revisão**
- **Concluído**

### 📋 Artefatos Scrum

Foram definidos e documentados:

- Product Backlog priorizado;
- Sprint Backlog da Sprint 3;
- Definition of Done — DoD;
- Responsáveis pelas atividades;
- Status das atividades.

### 🔄 Cerimônias Scrum

Foram documentadas as seguintes cerimônias e registros da Sprint 3:

- Sprint Planning;
- Registros das Dailies;
- Sprint Review.

A documentação completa está disponível em:

➡️ [CERIMONIAS_SCRUM.md](CERIMONIAS_SCRUM.md)

---

## 🏗️ 9. Arquitetura Técnica — Refinamento da Sprint 3

Na Sprint 3, a arquitetura foi refinada para manter alinhamento entre o protótipo, os requisitos funcionais e a evolução futura da solução.

O fluxo técnico proposto é:

**Câmeras Industriais → Visão Computacional → Análise de Risco → Backend/API → Banco de Dados → Dashboard do Supervisor**

### Camada de Captura

As câmeras industriais fornecem os feeds de vídeo utilizados pelo sistema para monitoramento do ambiente produtivo.

### Camada de Inteligência Artificial

O processamento utiliza **OpenCV e YOLOv8** para identificação de EPIs e situações de risco.

O **MediaPipe** complementa a análise por meio da estimativa de pose e identificação de comportamentos ou posturas potencialmente inseguras.

### Camada de Backend

O **FastAPI** é responsável pela comunicação entre os módulos de processamento, dados e interface.

### Camada de Dados

O **Oracle Database** é utilizado para estruturar informações relacionadas a:

- Usuários;
- Colaboradores;
- EPIs;
- Alertas;
- Registros de conformidade.

### Camada de Interface

O dashboard permite ao supervisor acompanhar:

- Indicadores de conformidade;
- Alertas de risco;
- Situação dos EPIs;
- Colaboradores;
- Monitoramento das câmeras;
- Relatórios.

Essa arquitetura permite que a solução evolua do protótipo atual para uma aplicação integrada aos componentes de Visão Computacional e análise de risco.

---

## 📂 10. Principais Arquivos do Projeto

| Arquivo | Descrição |
|---|---|
| `README.md` | Documentação principal do projeto |
| `REQUISITOS.md` | Engenharia de requisitos |
| `DIAGRAMAS.md` | Diagramas UML e arquitetura |
| `CERIMONIAS_SCRUM.md` | Planning, Dailies, Review e DoD da Sprint 3 |
| `spi-prototipo.html` | Protótipo navegável da aplicação |

---

## 🚀 Execução do Protótipo

Para visualizar o protótipo, abra o arquivo:

➡️ [spi-prototipo.html](spi-prototipo.html)

Faça o download do arquivo pelo GitHub e abra-o em um navegador.

Para acessar o sistema, utilize qualquer matrícula e senha não vazias, pois a autenticação atual é simulada para fins de prototipação.

---

## 🛡️ FutureVision — SPI Alert

**Visão Computacional e Inteligência Artificial aplicadas à prevenção proativa de riscos na Metaindústria.**
