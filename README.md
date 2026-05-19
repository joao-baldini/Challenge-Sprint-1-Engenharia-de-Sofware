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

## 🗺️ 4. Modelagem do Sistema (UML)

Os diagramas abaixo foram modelados de forma integrada para garantir a coesão técnica do ecossistema: os Casos de Uso guiam o fluxo das Atividades, e as Classes fornecem a estrutura de dados necessária para suportá-los.

Diagramas de Casos de Uso, Atividades e Classes renderizados no [Documento de Modelagem UML (DIAGRAMAS.md)](DIAGRAMAS.md)

## 📋 5. Engenharia de Requisitos 

Análise detalhada de personas, requisitos funcionais (RF), não funcionais (RNF) e restrições no [Documento de Levantamento de Requisitos (REQUISITOS.md)](REQUISITOS.md)
