# Cerimônias Scrum — Sprint 3

## Projeto FutureVision — SPI Alert

### Integrantes

- João Viviani Baldini — RM 558596
- Lucas Costa Sanson — RM 556042
- Giuliano Ferreira Venceslau — RM 558674
- Eric Perez Martinez Melillo Siciliano — RM 558651
- Enrico Nikolay Meirelles Zeronian — RM 558557

---

# 1. Sprint Planning

## Objetivo da Sprint 3

O objetivo da Sprint 3 foi evoluir o protótipo do SPI Alert desenvolvido nas Sprints anteriores, cobrindo fluxos ainda não representados, corrigindo interações que existiam apenas visualmente e refinando a arquitetura e a documentação do projeto.

Também foi definido como objetivo organizar e registrar o trabalho do grupo utilizando Scrum e um board no Trello.

## Itens selecionados para a Sprint 3

Durante o planejamento, foram priorizadas as seguintes atividades:

- Criar a tela de Login;
- Criar a tela de Monitoramento de câmeras;
- Implementar o fluxo de logout;
- Corrigir a navegação do protótipo;
- Implementar a busca de colaboradores;
- Implementar filtros de colaboradores;
- Implementar filtros de alertas;
- Tornar os chips dos formulários interativos;
- Implementar validação no cadastro de EPI;
- Implementar validação na emissão de alertas;
- Corrigir botões que ainda não possuíam ação;
- Padronizar a navegação inferior;
- Atualizar a documentação de UX;
- Atualizar os diagramas UML;
- Refinar a arquitetura técnica;
- Atualizar o README;
- Configurar o board Scrum no Trello;
- Documentar as cerimônias Scrum;
- Preparar a entrega final da Sprint 3.

## Organização do trabalho

As atividades selecionadas foram registradas no board do Trello e distribuídas entre:

- Product Backlog;
- Sprint Backlog — Sprint 3;
- Em andamento;
- Em revisão;
- Concluído.

O status dos cards foi atualizado de acordo com a evolução das atividades.

---

# 2. Definition of Done — DoD

Uma tarefa da Sprint 3 é considerada concluída quando:

- A funcionalidade ou documentação estiver finalizada;
- O resultado estiver de acordo com o escopo definido para a Sprint;
- Não houver erros que impeçam seu uso ou visualização;
- A alteração estiver registrada no repositório GitHub, quando aplicável;
- A documentação relacionada estiver atualizada;
- O card correspondente estiver atualizado no Trello;
- O item estiver disponível para revisão pelo grupo.

---

# 3. Registros das Dailies

As Dailies da Sprint 3 foram registradas de forma resumida e assíncrona, acompanhando a evolução das atividades do grupo.

## Daily 1 — Evolução do Protótipo

### Realizado

Foi revisado o protótipo desenvolvido nas Sprints anteriores e identificados fluxos e componentes que ainda estavam incompletos ou apenas visuais.

Foram identificadas como prioridades a implementação da autenticação, do monitoramento de câmeras e a correção das interações existentes.

### Próximas atividades

- Desenvolver a tela de Login;
- Desenvolver a tela de Monitoramento;
- Revisar os fluxos de navegação;
- Identificar botões e componentes sem funcionalidade.

### Impedimentos

Foram identificados elementos visuais do protótipo que ainda não possuíam comportamento funcional, exigindo ajustes no HTML, CSS e JavaScript.

---

## Daily 2 — Funcionalidades e UX

### Realizado

Foram implementadas e revisadas funcionalidades de interação do protótipo, incluindo:

- Busca de colaboradores;
- Filtros de colaboradores;
- Filtros de alertas;
- Chips de seleção;
- Validação dos formulários;
- Feedback visual das ações;
- Navegação inferior.

A tela de Login foi incorporada ao fluxo inicial e a tela de Monitoramento passou a representar visualmente as câmeras da planta.

### Próximas atividades

- Revisar documentação de UX;
- Atualizar os diagramas UML;
- Revisar arquitetura técnica;
- Atualizar README.

### Impedimentos

Foi necessário garantir que as novas funcionalidades permanecessem coerentes com os requisitos e com os fluxos definidos anteriormente.

---

## Daily 3 — Documentação e Entrega

### Realizado

Foi realizada a revisão da documentação do projeto para adequá-la à evolução realizada na Sprint 3.

Os diagramas foram atualizados para representar:

- Autenticação;
- Dashboard;
- Gestão de colaboradores;
- Gestão de EPIs;
- Monitoramento por câmeras;
- Processamento por visão computacional;
- Gestão de alertas;
- Relatórios de conformidade.

Também foi criado e organizado o board Scrum no Trello.

### Próximas atividades

- Finalizar README;
- Finalizar documentação das cerimônias;
- Revisar os arquivos no GitHub;
- Preparar os links necessários para a entrega.

### Impedimentos

Não foram identificados impedimentos críticos para a conclusão da Sprint.

---

# 4. Sprint Review

## Objetivo

Revisar os itens planejados para a Sprint 3 e verificar a evolução do SPI Alert em relação às versões anteriores.

## Entregas realizadas

A Sprint 3 resultou na evolução do protótipo e da documentação do projeto.

### Novos fluxos

Foram adicionados:

- Login do supervisor;
- Logout;
- Monitoramento das câmeras da planta.

### Melhorias funcionais

Foram implementados ou corrigidos:

- Busca de colaboradores em tempo real;
- Filtros da lista de colaboradores;
- Filtros da lista de alertas;
- Chips de seleção interativos;
- Validação do formulário de cadastro de EPI;
- Validação do formulário de emissão de alerta;
- Feedback visual para ações do usuário;
- Navegação entre as principais áreas do sistema.

### Documentação

Foram revisados ou atualizados:

- README;
- Documentação de UX;
- Diagramas UML;
- Arquitetura funcional;
- Documentação Scrum.

### Gestão do projeto

Foi estruturado um board Scrum no Trello contendo:

- Product Backlog;
- Sprint Backlog;
- Em andamento;
- Em revisão;
- Concluído.

As tarefas foram organizadas de acordo com o status do trabalho desenvolvido durante a Sprint.

---

# 5. Resultado da Sprint 3

A Sprint 3 ampliou o protótipo do SPI Alert e aproximou a interface de uma experiência funcional.

O sistema passou a representar de maneira mais completa o fluxo do supervisor, desde o acesso ao sistema até o acompanhamento de câmeras, consulta de alertas, gestão de EPIs e análise dos indicadores de conformidade.

A atualização dos diagramas e da documentação também buscou manter alinhamento entre requisitos, arquitetura técnica, protótipo e funcionalidades apresentadas.

---

# 6. Próximos Passos — Product Backlog

Os seguintes itens permanecem como possíveis evoluções futuras do produto:

- Integração real com câmeras industriais;
- Integração do protótipo com backend FastAPI;
- Persistência dos alertas no Oracle Database;
- Autenticação real de usuários;
- Integração completa com o modelo YOLO para detecção de EPIs;
- Análise de postura e áreas de risco;
- Notificações de alertas em tempo real;
- Evolução dos relatórios de conformidade;
- Testes de usabilidade com usuários.=