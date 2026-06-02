# 🎨 Documentação de Design e UX - SPI Alert (FutureVision)

Este documento detalha a arquitetura de interface e as decisões de Experiência do Usuário (UX) implementadas no protótipo funcional em código (HTML/CSS/JS). O objetivo é garantir que a interface reflita perfeitamente as necessidades do chão de fábrica e a engenharia de requisitos mapeada na Sprint 1.

## 🗺️ 1. Mapa de Telas (Screen Map)

A navegação foi estruturada para permitir acesso rápido às informações críticas, dividida em quatro grandes módulos operacionais interligados:

*   **🏠 Módulo Principal (Dashboard)**
    *   `home`: Painel central (Visão Geral, Estatísticas Rápidas, Alertas Críticos e Menu de Acesso).
*   **⚠️ Módulo de Alertas (Gestão de Riscos)**
    *   `lista-alertas`: Feed categorizado por severidade (Abertos, Em Análise, Resolvidos).
    *   `detalhe-alerta`: Visão aprofundada da infração (câmera, confiança da IA, timestamp) com botões de ação corretiva.
    *   `emitir-alerta`: Formulário para registro manual de risco, contendo chips de seleção rápida.
    *   `sucesso-alerta`: Tela de confirmação de emissão.
*   **👷 Módulo de EPIs (Governança de Colaboradores)**
    *   `lista-colaboradores`: Tabela de funcionários com filtros de status (Irregulares, Vencendo).
    *   `perfil-colaborador`: Ficha individual detalhando os tipos de EPI e suas respectivas validades.
    *   `cadastro-epi`: Formulário de registro de novos equipamentos de segurança.
    *   `sucesso-epi`: Tela de confirmação de registro.
*   **📊 Módulo de Compliance (Auditoria)**
    *   `relatorio`: Painel gerencial focado em conformidade por setor, exibindo barras de progresso e estatísticas de engajamento.

---

## 🔗 2. Mapeamento: Telas vs. Casos de Uso (Sprint 1)

O protótipo garante que cada ação projetada na arquitetura UML possua suporte visual correspondente.

| Caso de Uso (Sprint 1) | Tela Correspondente no Protótipo | Descrição da Interação |
| :--- | :--- | :--- |
| **UC5 - Visualizar Dashboard** | `home` | O supervisor acompanha em tempo real o índice de conformidade e o contador de alertas críticos ativos logo na abertura do app. |
| **UC4 - Emitir Alerta Proativo** | `lista-alertas` / `detalhe-alerta` | O sistema lista as anomalias capturadas (ex: ausência de capacete) classificadas por severidade, permitindo escalonamento de segurança. |
| **UC2 - Detectar Uso de EPIs** | `perfil-colaborador` | Os dados de detecção da IA e o histórico de validade são confrontados para gerar o status de cada EPI (Ex: "OK" ou "Vencendo"). |
| **UC6 - Gerar Relatório** | `relatorio` | O supervisor visualiza o breakdown percentual de conformidade de setores (ex: Linha de Produção, Setor B) para auditorias. |

---

## 🧠 3. Decisões de UI/UX e Acessibilidade Industrial

O código fonte do protótipo (`spi-prototipo.html`) foi construído com base em princípios rigorosos de usabilidade para o contexto da Metaindústria:

*   **Formato de Dispositivo Móvel (Field-Ready):** A interface foi projetada no escopo de um terminal móvel (390x844px), ideal para supervisores que realizam rondas ativas pela fábrica, garantindo usabilidade com apenas uma mão.
*   **Navegação Dupla (Bottom Nav & Breadcrumb):** Foi implementada uma barra de navegação inferior (`bottom-nav`) para alcance rápido dos polegares, reforçada por um "breadcrumb" superior (`nav-bar`) para garantir que o usuário nunca se perca na hierarquia do sistema.
*   **Sinalização Cromática de Severidade (Tags e Badges):** Para agilizar a tomada de decisão, cores foram aplicadas de forma semântica:
    *   🔴 **Vermelho (`--red`) / Crítico:** Áreas de risco iminente ou alertas abertos de alta gravidade.
    *   🟠 **Laranja (`--orange`) / Atenção:** Equipamentos próximos ao vencimento ou situações em análise.
    *   🟢 **Verde (`--green`) / Seguro:** Setores com alta conformidade e EPIs regulares.
*   **Tipografia Dinâmica e Analítica:** Utilização da família tipográfica `DM Sans` para leitura fluida e `DM Mono` (monoespaçada) especificamente para dados críticos (horários, porcentagens e matrículas), evitando confusão numérica durante a visualização rápida.
*   **Interações Otimizadas (Chips):** Nos formulários (como `emitir-alerta` e `cadastro-epi`), os campos de seleção tradicionais foram substituídos por "Chips" (botões de tag), facilitando o toque em telas menores ou por operadores que eventualmente utilizem luvas de proteção (Fat Finger Design).
