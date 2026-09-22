Challenge - Sprint 1, 2 e 3 - Engenharia de Software
🛡️ Projeto FutureVision: Visão Computacional e Prevenção Proativa na Metaindústria
👥 Integrantes: João Viviani Baldini - 558596 / Lucas Costa Sanson - 556042 / Giuliano Ferreira Venceslau - 558674 / Eric Perez Martinez Melillo Siciliano - 558651 / Enrico Nikolay Meirelles Zeronian - 558557

💡 1. Contexto e Problema Abordado:
O ambiente industrial da Metaindústria lida diariamente com cenários complexos onde a integridade física dos operadores está exposta a riscos de alta gravidade (máquinas pesadas, zonas de alta temperatura e movimentação de cargas). O modelo tradicional de segurança do trabalho atua de forma punitiva ou reativa: identifica-se a infração (ex: operador sem capacete) após o evento ou o acidente já ter ocorrido.
O problema central reside na latência humana e reativa. A falta de ferramentas inteligentes que consigam interpretar dados comportamentais em tempo real impede que supervisores ajam antes que o risco se converta em um acidente de trabalho incapacitante ou fatal.

✅ 2. Proposta de Solução:
Nossa proposta quebra o status quo ao implementar um sistema de Proteção Ativa de Funcionários baseado em Inteligência Artificial Preditiva e Visão Computacional. Em vez de apenas gerar relatórios de infrações, o ecossistema aprende padrões de comportamento no chão de fábrica para antecipar o risco.
Como a solução funciona na prática (Arquitetura Evolutiva): I. Detecção de EPIs (Fase 1): Câmeras industriais processam feeds de vídeo locais para validar o uso correto de capacetes, coletes e luvas. II. Análise de Postura e Áreas de Risco (Fase 2): Modelos de Pose Estimation calculam a proximidade de operadores em relação a zonas de perigo (ex: robôs industriais em operação) e desvios ergonômicos críticos antes do toque. III. Alerta Cirúrgico (Fase 3): Caso um operador caminhe em direção a uma área restrita sem o EPI adequado ou de forma insegura, um alerta visual e sonoro é disparado imediatamente na célula de trabalho e um evento crítico é enviado ao Dashboard do Supervisor.

💻3. Tecnologias Selecionadas e Justificativa Técnica
Para atender aos rigorosos requisitos de baixa latência e alta confiabilidade exigidos pela SPI e pelo ambiente industrial, a pilha tecnológica foi definida da seguinte forma:
Linguagem de programação principal: Python, pois é uma ótima linguagem para tratar de projetos que utilizam de ciência de dados e IA, permitindo integração nativa com bibliotecas de Visão Computacional.
Visão Computacional: OpenCV + Ultralytics (YOLOv8), oferece inferência state-of-the-art em tempo real (essencial para prevenção ativa) com excelente custo-benefício computacional.
Estimativa de Pose: Media Pipe, tem um framework leve e altamente otimizado para mapeamento de pontos articulados corporais, ideal para detecção de riscos ergonômicos.
Backend / API: FastAPI, possui um framework assíncrono em Python de altíssima performance (equivalente a Go e Node.js), garantindo que os alertas cheguem ao dashboard sem gargalos.
Banco de Dados Relacional: Oracle Database, principalmente, por termos familiaridade com o uso e sua capacidade de governança de dados para cadastro de funcionários, histórico de alertas consolidados e métricas de conformidade.
Frontend & Dashboard: Streamlit / React, pois é possivel criar interfaces ricas e dinâmicas para exibição de fluxos de vídeo analíticos e dashboards industriais acionáveis para os tomadores de decisão.

🗺️ 4. Modelagem do Sistema (UML)
Os diagramas abaixo foram modelados de forma integrada para garantir a coesão técnica do ecossistema: os Casos de Uso guiam o fluxo das Atividades, e as Classes fornecem a estrutura de dados necessária para suportá-los.
Diagramas de Casos de Uso, Atividades e Classes renderizados no Documento de Modelagem UML (DIAGRAMAS.md)

📋 5. Engenharia de Requisitos

Análise detalhada de personas, requisitos funcionais (RF), não funcionais (RNF) e restrições no Documento de Levantamento de Requisitos (REQUISITOS.md)

📲 6. Protótipo da aplicação e instruções de uso

Na Sprint 3, os fluxos que ainda estavam apenas visuais foram corrigidos e implementados (busca, filtros, chips de seleção, validação de formulários e os botões que não tinham ação nas Sprints anteriores), e duas novas telas foram adicionadas: Login e Monitoramento (Câmeras ao vivo). Detalhes da evolução no item 7 abaixo.

👨‍🏫 Instruções para uso

Login

Ao abrir o app, a primeira tela é o login do supervisor
Informe qualquer matrícula e senha (não vazias) e toque em Entrar — é uma simulação de autenticação para fins de protótipo, sem validação de credencial real
Use Esqueci minha senha para simular o fluxo de recuperação

Tela Principal — Home

Ao entrar você verá o dashboard com os totais de alertas abertos, conformidade geral, colaboradores e setores ativos
Os alertas críticos recentes aparecem em destaque no topo
Use o menu principal para navegar entre as funcionalidades
O ícone 🚪 no canto superior do header encerra a sessão e retorna à tela de login

Fluxo 1 — EPIs por Colaborador

Na Home, toque em EPIs por Colaborador
Use a barra de busca para encontrar um colaborador pelo nome, ou as abas (Todos/Irregulares/Vencendo) para filtrar a lista
Toque no colaborador para ver a lista de EPIs cadastrados com status e validade
Toque em + EPI para cadastrar um novo equipamento
Selecione o tipo de EPI e a condição nos chips, preencha o número do CA, data de entrega e validade
Toque em Registrar EPI para salvar (o formulário valida CA e validade preenchidos)

Fluxo 2 — Alertas de Risco

Na Home, toque em Alertas de Risco
Visualize os alertas organizados por nível de severidade (Crítico, Alto, Médio, Baixo) e use as abas (Abertos/Em Análise/Resolvidos) para filtrar
Toque em um alerta para ver o detalhe completo com localização, câmera, colaborador e confiança da IA
Para emitir um novo alerta manualmente, toque em + Emitir
Selecione o tipo de risco, severidade e localização nos chips, e informe a câmera e a descrição
Toque em Emitir Alerta para registrar e notificar a equipe

Fluxo 3 — Relatório de Conformidade

Na Home, toque em Relatório de Conformidade
Visualize o índice geral de conformidade da fábrica
Consulte a conformidade por setor com barra de progresso, número de alertas e EPIs vencendo
Toque em Exportar PDF para gerar o relatório
Toque em Enviar por E-mail para compartilhar com a equipe

Fluxo 4 — Monitoramento (novo na Sprint 3)

Na Home, toque em Monitoramento
Visualize as câmeras ativas da planta (CAM-001, CAM-003, CAM-005, CAM-007), seus setores e status em tempo real
Câmeras com alerta ativo ficam destacadas visualmente — toque para ver o detalhe do alerta correspondente

Navegação O app possui uma barra de navegação inferior com acesso rápido a:

🏠 Home
⚠️ Alertas
👷 EPIs
📊 Relatório
🔄 7. Evolução do Protótipo — Sprint 3

O protótipo de alta fidelidade foi revisado para cobrir fluxos que ainda não existiam nas entregas anteriores, corrigir interações que estavam apenas visuais (sem função) e refinar a experiência de uso conforme os requisitos funcionais (RF) definidos no REQUISITOS.md.

Protótipo atualizado: spi-prototipo.html

Novas telas / fluxos adicionados
Tela	Motivo da adição
Login	A folha de estilos do protótipo já continha as classes de layout (.login-screen, .login-logo) desde a Sprint 1, mas a tela nunca havia sido implementada — o fluxo de autenticação era um gap identificado na revisão da Sprint 3. Agora o app abre no login e só libera acesso ao dashboard após o supervisor informar matrícula e senha; um botão de logout foi adicionado no header da Home para fechar o ciclo de sessão.
Monitoramento (Câmeras ao vivo)	O botão "Monitoramento" existia desde a Sprint 1 no menu principal, mas não tinha nenhuma ação associada — um dos botões não funcionais citados na Sprint anterior. É também a única tela do escopo que representa visualmente o RF001 (processamento de feed de vídeo das câmeras industriais) e reforça o RF006 (dashboard operacional do supervisor com feed analítico), ambos sem nenhuma tela correspondente até então. A tela lista as câmeras (CAM-001, CAM-003, CAM-005, CAM-007), seus setores e destaca visualmente as que possuem alerta ativo.
Correções de usabilidade e funções que estavam quebradas

Durante a revisão, foram identificadas e corrigidas diversas interações que existiam apenas como elementos visuais estáticos (sem função de fato), o que contrariava a proposta de protótipo navegável do projeto:
Navegação por breadcrumb (topo) não destacava a seção correta ao trocar de tela — corrigido.
Abas de filtro (Todos/Irregulares/Vencendo na tela de EPIs, e Abertos/Em Análise/Resolvidos na tela de Alertas) eram apenas visuais — agora filtram a lista de verdade.
Campo de busca de colaborador não fazia nada — agora filtra em tempo real por nome.
Chips de seleção (tipo de EPI, severidade do alerta, localização, condição do equipamento) não respondiam a clique — agora têm seleção única por grupo.
Botões sem ação: "Gerar Ficha Individual", "Escalar para Segurança", "Exportar PDF" e "Enviar por E-mail" agora dão retorno visual (toast de confirmação) ao usuário.
Formulários de cadastro de EPI e de emissão de alerta permitiam avançar em branco — agora validam os campos obrigatórios (CA, validade, descrição) antes de confirmar.
Telas de perfil do colaborador e detalhe do alerta não tinham navegação inferior, deixando o usuário "preso" na tela — adicionada a barra de navegação padrão.

🗂️ 8. Gestão Ágil — Scrum
Board Trello: <!-- TODO: colar aqui o link do board público do Trello -->
Colunas: Product Backlog, Sprint Backlog, Em andamento, Em revisão, Concluído
Cards refletindo as tarefas reais da Sprint 3 (evolução do protótipo, documentação, arquitetura), com responsável e status atualizados.
Artefatos Scrum documentados:
Product Backlog priorizado
Sprint Backlog da Sprint 3
Definition of Done (DoD)
Cerimônias da Sprint 3: <!-- TODO: colar aqui o link do documento/pasta com as atas -->
Ata de Planning
Registro das Dailies (assíncrono)
Ata de Review

🏗️ 9. Arquitetura Técnica (refinamento)
<!-- TODO: descrever aqui as decisões de arquitetura consolidadas até a Sprint 3, com base na stack já definida no item 3 (Python, OpenCV/YOLOv8, MediaPipe, FastAPI, Oracle Database, Streamlit/React) -->

**Aplicação disponível em [(spi-prototipo.html)](spi-prototipo.html) (Botão de download próximo ao canto superior direito)**
