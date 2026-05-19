# Challenge - Sprint 1 - Engenharia de Sofware

# 🛡️ Projeto FutureVision: Visão Computacional e Prevenção Proativa na Metaindústria

## 👥 Integrantes: João Viviani Baldini - 558596 / Lucas Costa Sanson - 556042 / Giuliano Ferreira Venceslau - 558674 / Eric Perez Martinez Melillo Siciliano - 558651 / Enrico Nikolay Meirelles Zeronian - 558557


### 1. Contexto e Problema Abordado: 

O ambiente industrial da Metaindústria lida diariamente com cenários complexos onde a integridade física dos operadores está exposta a riscos de alta gravidade (máquinas pesadas, zonas de alta temperatura e movimentação de cargas). O modelo tradicional de segurança do trabalho atua de forma punitiva ou reativa: identifica-se a infração (ex: operador sem capacete) após o evento ou o acidente já ter ocorrido.  O problema central reside na latência humana e reativa. A falta de ferramentas inteligentes que consigam interpretar dados comportamentais em tempo real impede que supervisores ajam antes que o risco se converta em um acidente de trabalho incapacitante ou fatal.  

### 2. Proposta de Solução: Segurança ProativaA solução SafeHorizon quebra o status quo ao implementar um sistema de Proteção Ativa de Funcionários baseado em Inteligência Artificial Preditiva e Visão Computacional. Em vez de apenas gerar relatórios de infrações, o ecossistema aprende padrões de comportamento no chão de fábrica para antecipar o risco. 

- Como a solução funciona na prática (Arquitetura Evolutiva):

  I. Detecção de EPIs (Fase 1): Câmeras industriais processam feeds de vídeo locais para validar o uso correto de capacetes, coletes e luvas.  
  
  II. Análise de Postura e Áreas de Risco (Fase 2): Modelos de Pose Estimation calculam a proximidade de operadores em relação a   zonas de perigo (ex: robôs industriais em operação) e desvios ergonômicos críticos antes do toque.  
  
  III. Alerta Cirúrgico (Fase 3): Caso um operador caminhe em direção a uma área restrita sem o EPI adequado ou de forma insegura, um alerta visual e sonoro é disparado imediatamente na célula de trabalho e um evento crítico é enviado ao Dashboard do Supervisor.

### 3. Tecnologias Selecionadas e Justificativa Técnica

Para atender aos rigorosos requisitos de baixa latência e alta confiabilidade exigidos pela SPI e pelo ambiente industrial, a pilha tecnológica foi definida da seguinte forma: 

- Linguagem de programação principal: Python, pois é uma ótima linguagem para tratar de projetos que utilizam de ciência de dados e IA, permitindo integração nativa com bibliotecas de Visão Computacional.
- Visão Computacional: OpenCV + Ultralytics (YOLOv8), oferece inferência state-of-the-art em tempo real (essencial para prevenção ativa) com excelente custo-benefício computacional.
- Estimativa de Pose: Media Pipe, tem um framework leve e altamente otimizado para mapeamento de pontos articulados corporais, ideal para detecção de riscos ergonômicos.
- Backend / API: FastAPI, possui um framework assíncrono em Python de altíssima performance (equivalente a Go e Node.js), garantindo que os alertas cheguem ao dashboard sem gargalos.
- Banco de Dados Relacional: Oracle Database, principalmente, por termos familiaridade com o uso e sua capacidade de governança de dados para cadastro de funcionários, histórico de alertas consolidados e métricas de conformidade.
- Frontend & Dashboard: Streamlit / React, pois é possivel criar interfaces ricas e dinâmicas para exibição de fluxos de vídeo analíticos e dashboards industriais acionáveis para os tomadores de decisão.

### 4. Personas dos Usuários

Persona 1 - O Operador de Campo 

- Nome: Carlos Eduardo, 34 anos.
- Papel: Operador de Linha de Montagem na Metaindústria.
- Função: Executar suas tarefas diárias com foco na produtividade, sem que os sistemas de segurança atrapalhem sua mobilidade ou adicionem processos burocráticos ao seu dia.
- Problema: Sistemas de segurança antigos que geram alarmes falsos ou advertências por falhas operacionais simples sem um aviso prévio amigável.

Persona 2: O Supervisor de Segurança (Técnico de SST)

- Nome: Mariana Souza, 29 anos.
- Papel: Supervisora de Saúde e Segurança do Trabalho.
- Função: Identificar gargalos de segurança (ex: setores com menor índice de uso de luvas) e intervir cirurgicamente em situações de risco iminente.  
- Problema: Passar horas assistindo a gravações de câmeras de segurança ou preenchendo planilhas manuais após os incidentes acontecerem.

### 5. Engenharia de Requisitos e Restrições

🟢 Requisitos Funcionais 

- (RF)RF001 - Processamento de Feed de Vídeo: O sistema deve capturar e processar fluxos de vídeo em tempo real vindos de câmeras IP industriais.  

- RF002 - Classificação de EPIs: O modelo deve identificar a presença ou ausência de capacetes, coletes refletivos e luvas em cada operador visível.  

- RF003 - Cálculo de Perímetro de Risco: O sistema deve calcular via pose estimation a distância entre o operador e as coordenadas da zona de perigo configurada.

- RF004 - Disparo de Alertas Proativos: O sistema deve emitir um alerta visual/sonoro na tela do dashboard operacional e enviar um sinal lógico para atuadores de campo quando um risco iminente for previsto.

- RF005 - Dashboard de Métricas (Analytics): O sistema deve fornecer uma interface web para o Gestor visualizar gráficos de conformidade por turno, setor e tipo de EPI.  

🔴 Requisitos Não Funcionais 

- (RNF)RNF001 - Tempo de Resposta (Latência): O pipeline de inferência de visão computacional e emissão do alerta preditivo não deve ultrapassar 300 milissegundos para garantir a janela de evasão do operador.

- RNF002 - Confiabilidade da IA: O modelo de detecção de EPIs deve apresentar uma precisão mínima ($mAP@0.5$) de 88% nas condições de iluminação padrão do chão de fábrica.

- RNF003 - Segurança e Privacidade: O sistema deve tratar dados em conformidade com as diretrizes de governança, ofuscando rostos que não estejam em situação de risco para preservar a privacidade, focando apenas no comportamento biomecânico.

- RNF004 - Arquitetura de Integração: O banco de dados do sistema deve ser estruturado em Oracle SQL, garantindo consistência e suporte a subconsultas complexas para relatórios regulatórios.

⚠️ Restrições do Sistema

- RS001: O processamento inicial (Edge Computing) deve ser compatível com hardware padrão estipulado pela parceria (como instâncias otimizadas ou microcomputadores industriais de teste).

- RS002: A solução não deve depender de conexão constante com a internet externa para as funções críticas de disparo de alertas locais (deve operar em rede industrial fechada/LAN).
