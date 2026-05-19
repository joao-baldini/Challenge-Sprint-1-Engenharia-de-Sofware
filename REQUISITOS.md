# 👥 1. Personas dos Usuários
## Para mapear com precisão as necessidades do chão de fábrica da Metaindústria, foram consolidadas duas personas principais que interagem direto ou indiretamente com o ecossistema.

👷 Persona 1: O Operador de Campo
Nome: Carlos Eduardo, 34 anos.

Papel: Operador de Linha de Montagem / Célula Robotizada.

Perfil: Profissional focado em bater as metas de produção da sua célula. Possui rotina dinâmica, cansativa e lida com maquinário pesado diariamente.

Necessidades: Executar suas tarefas diárias com foco na produtividade, sem que os sistemas de segurança gerem travas burocráticas ou limitem sua agilidade física de forma desnecessária.

Dores: Tem receio de sistemas de monitoramento estritamente punitivos (que geram advertências automáticas por deslizes simples) e se incomoda com alarmes falsos de sensores antigos que interrompem o ritmo de trabalho.

🦺 Persona 2: O Supervisor de Segurança (SST)
Nome: Mariana Souza, 29 anos.

Papel: Engenheira / Técnica de Saúde e Segurança do Trabalho.

Perfil: Responsável por garantir o índice zero de acidentes em três turnos de produção. Precisa auditar processos, investigar quase-acidentes e orientar os operadores.

Necessidades: Identificar gargalos de segurança em tempo real (ex: setores com menor índice de uso de luvas) e intervir cirurgicamente em situações de risco iminente antes do pior acontecer.

Dores: Perde muito tempo assistindo a gravações antigas de câmeras após os incidentes ocorrerem, ou preenchendo planilhas manuais de auditoria de EPI, atuando sempre de forma reativa.

# 📋 Requisitos

## 🟢 Requisitos Funcionais (RF)

### Os Requisitos Funcionais descrevem as ações, comportamentos e funções específicas que o sistema SafeHorizon deve executar de forma computacional.

- RF001 - Processamento de Feed de Vídeo: O sistema deve ser capaz de capturar e processar continuamente fluxos de vídeo vindos de câmeras industriais (via protocolo RTSP) instaladas nas células de trabalho.   

- RF002 - Classificação de EPIs em Tempo Real: O sistema deve identificar, através de modelos de visão computacional, o uso correto ou a ausência de capacetes, coletes refletivos e luvas em cada operador visível no frame.   

- RF003 - Mapeamento de Esqueleto (Pose Estimation): O sistema deve extrair os pontos articulados do corpo do trabalhador para identificar posturas inadequadas e estimar a biomecânica de risco ergonômico.   

- RF004 - Monitoramento de Perímetro e Zonas de Risco: O sistema deve rastrear as coordenadas da posição do operador e prever se ele está em trajetória de colisão ou aproximação indevida de áreas restritas ou maquinário móvel.   

- RF005 - Emissão de Alerta Proativo Local: O sistema deve disparar sinais lógicos imediatos para atuadores físicos (sinalizadores sonoros ou visuais instalados na fábrica) ao prever um risco de acidente iminente.   
PDF

- RF006 - Dashboard Operacional do Supervisor: O sistema deve disponibilizar uma interface gráfica web contendo o feed analítico das câmeras e um painel de notificações centralizado para o supervisor de SST.   

- RF007 - Persistência de Eventos Críticos: O sistema deve registrar em banco de dados histórico cada evento de risco previsto, contendo data, hora, setor, tipo de inconformidade e nível de severidade.   

- RF008 - Emissão de Relatório de Conformidade: O sistema deve permitir que o gestor filtre e gere relatórios estatísticos de segurança agrupados por setor, turno ou tipo de risco para análise de tendências.   

## 🔴 Requisitos Não Funcionais (RNF)

### Os Requisitos Não Funcionais definem as características de qualidade, restrições técnicas, critérios de performance e segurança que validam o funcionamento do software.

- RNF001 - Desempenho / Latência: O pipeline completo (captura do frame, inferência da IA, lógica preditiva e disparo do alerta local) não deve ultrapassar a latência máxima permitida, garantindo tempo hábil de evasão. O critério de sucesso estabelecido é de menos de 300 milissegundos por ciclo de frame.   

- RNF002 - Confiabilidade / Precisão da IA: Os modelos de Visão Computacional (YOLOv8/MediaPipe) devem manter um índice rigoroso de acerto para mitigar alarmes falsos no chão de fábrica. O critério de sucesso estabelecido é uma Precisão Média Mínima (mAP@0.5) de 88%.   

- RNF003 - Arquitetura de Dados: A persistência estruturada do histórico de eventos, logs e cadastro de funcionários deve ser realizada de forma nativa em um banco de dados relacional robusto (Oracle SQL).   

- RNF004 - Disponibilidade Operacional: A camada local do backend responsável por processar a IA e emitir os alarmes sonoros nas células de trabalho deve ser tolerante a falhas na rede externa, operando com disponibilidade de 99,9% em rede local LAN industrial.   

- RNF005 - Privacidade / LGPD: O sistema deve focar o processamento preditivo na análise biomecânica e de objetos, aplicando técnicas de descaracterização (blur/ofuscamento) em rostos para preservar a privacidade biométrica, em conformidade com as diretrizes de governança de dados.   

- RNF006 - Escalabilidade: A API de backend desenvolvida deve suportar requisições concorrentes e o processamento simultâneo de múltiplas câmeras de forma assíncrona (FastAPI em Python).   

# ⚠️ Restrições do Sistema
### As restrições limitam as escolhas técnicas e de design do projeto impostas pelo ambiente, orçamento ou regras de negócio do Challenge:


- RS001 - Execução em Bordas (Edge Computing): Os modelos de processamento de imagem em tempo real devem ser otimizados para rodar de forma eficiente em hardware padrão de testes (como computadores de borda industriais ou instâncias controladas disponibilizadas na Fase 4).   

- RS002 - Independência de Nuvem Externa para Alertas: O subsistema de segurança crítica (detecção e geração de alertas) não pode depender de conexões WAN (Internet) de nuvem pública para funcionar, mitigando riscos de quedas de link externo no chão de fábrica.   

- RS003 - Vedação de Simulações Estáticas: O sistema não poderá utilizar telas mocadas ou simuladas (MVPs "ocos") na entrega final. Todos os fluxos descritos de detecção, alertas e persistência SQL devem ser totalmente funcionais e integrados.   

- RS004 - Viabilidade Econômica: A solução desenvolvida deve se limitar ao orçamento viável do projeto, priorizando tecnologias e ferramentas economicamente viáveis em relação a custos e prazos de implementação industrial.   
