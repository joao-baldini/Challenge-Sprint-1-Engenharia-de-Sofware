# Diagramas UML — SPI Alert (FutureVision)

Este documento apresenta os diagramas atualizados do **SPI Alert**, considerando as funcionalidades implementadas no protótipo atual: autenticação, dashboard, visão computacional, detecção de EPIs, gestão de colaboradores, cadastro de EPIs, gestão de alertas e relatórios de conformidade.

---

## A. Diagrama de Casos de Uso

```mermaid
graph TD

    %% Atores
    Supervisor((Supervisor de SST))
    Operador((Operador de Campo))
    Camera((Câmera / Sistema de Visão))

    %% Sistema
    subgraph SPIAlert["Sistema SPI Alert"]

        %% Acesso e Dashboard
        UC0[Autenticar Usuário]
        UC5[Visualizar Dashboard]

        %% Colaboradores e EPIs
        UC11[Consultar Colaboradores]
        UC12[Visualizar EPIs do Colaborador]
        UC13[Cadastrar EPI]
        UC14[Validar Dados do EPI]

        %% Alertas
        UC7[Consultar Alertas]
        UC8[Visualizar Detalhe do Alerta]
        UC9[Tratar / Resolver Alerta]
        UC10[Escalar para Segurança]
        UC4[Emitir Alerta Proativo]

        %% Relatórios
        UC6[Gerar Relatório de Conformidade]
        UC15[Exportar / Compartilhar Relatório]

        %% Visão Computacional
        UC1[Processar Feed de Vídeo]
        UC2[Detectar Uso de EPIs]
        UC3[Analisar Postura e Perímetro]

    end

    %% Supervisor
    Supervisor --> UC0
    Supervisor --> UC5
    Supervisor --> UC11
    Supervisor --> UC7
    Supervisor --> UC4
    Supervisor --> UC6

    %% Gestão de EPIs
    UC11 --> UC12
    UC12 --> UC13
    UC13 -.->|include| UC14

    %% Gestão de Alertas
    UC7 --> UC8
    UC8 --> UC9
    UC8 --> UC10

    %% Relatórios
    UC6 --> UC15

    %% Câmera e IA
    Camera --> UC1
    UC1 -.->|include| UC2
    UC1 -.->|include| UC3

    %% Alertas automáticos
    UC2 -.->|ausência de EPI| UC4
    UC3 -.->|risco detectado| UC4

    %% Notificações
    UC4 -.->|notificação visual / sonora| Operador
    UC4 -.->|evento de segurança| Supervisor
```

---

## B. Diagrama de Atividades

```mermaid
flowchart TD

    A([Início]) --> B[Tela de Login]

    B --> C{Matrícula e senha preenchidas?}

    C -- Não --> D[Solicitar preenchimento]
    D --> B

    C -- Sim --> E[Autenticar Usuário]

    E --> F{Acesso válido?}

    F -- Não --> G[Exibir mensagem de erro]
    G --> B

    F -- Sim --> H[Exibir Dashboard]

    %% Fluxo de monitoramento
    H --> I[Receber Feed da Câmera]
    I --> J[Capturar Frame]
    J --> K[Processar com IA]

    K --> L[Detectar EPIs]
    K --> M[Analisar Postura e Perímetro]

    L --> N[Unificar Análise]
    M --> N

    N --> O{Existe risco ou inconformidade?}

    O -- Não --> P[Registrar Condição Segura]
    P --> I

    O -- Sim --> Q[Criar Evento de Risco]

    Q --> R[Classificar Severidade]
    R --> S[Persistir Evento]
    S --> T[Atualizar Dashboard]
    T --> U[Emitir Alerta]

    %% Tratamento do alerta
    U --> V[Supervisor Visualiza Alerta]

    V --> W{Qual ação será realizada?}

    W -- Resolver --> X[Marcar como Resolvido]
    W -- Analisar --> Y[Manter Em Análise]
    W -- Escalar --> Z[Escalar para Segurança]

    X --> AA[Atualizar Status do Alerta]
    Y --> AA
    Z --> AA

    AA --> H

    %% Ações manuais
    H --> AB{Ação do Supervisor}

    AB --> AC[Consultar Colaboradores]
    AB --> AD[Consultar Alertas]
    AB --> AE[Gerar Relatório]

    %% Fluxo EPI
    AC --> AF[Visualizar Perfil do Colaborador]
    AF --> AG[Visualizar EPIs]
    AG --> AH[Cadastrar Novo EPI]

    AH --> AI{Dados obrigatórios válidos?}

    AI -- Não --> AJ[Exibir Validação]
    AJ --> AH

    AI -- Sim --> AK[Registrar EPI]
    AK --> AL[Exibir Confirmação]
    AL --> H

    %% Fluxo alertas
    AD --> V

    %% Fluxo relatório
    AE --> AM[Consolidar Indicadores]
    AM --> AN[Exibir Conformidade por Setor]
    AN --> AO{Ação com Relatório}

    AO --> AP[Exportar PDF]
    AO --> AQ[Compartilhar / Enviar]

    AP --> H
    AQ --> H
```

---

## C. Diagrama de Classes

```mermaid
classDiagram

    class Usuario {
        +int idUsuario
        +string nome
        +string matricula
        +string senha
        +string email
        +autenticar() boolean
    }

    class Operador {
        +string setorAtuacao
        +string turno
        +obterHistoricoRisco() List
    }

    class SupervisorSST {
        +string nivelAcesso
        +visualizarDashboard() void
        +consultarAlertas() List
        +consultarColaboradores() List
        +cadastrarEPI() void
        +gerarRelatorio() void
    }

    class EPI {
        +int idEPI
        +string tipo
        +string numeroCA
        +date dataEntrega
        +date dataValidade
        +string condicao
        +string status
        +validarEPI() boolean
    }

    class DispositivoCamera {
        +int idCamera
        +string localizacao
        +string ipAddress
        +boolean statusAtivo
        +capturarStream() Object
    }

    class ProcessadorIA {
        +float thresholdConfianca
        +string versaoModelo
        +detectarEPIs(Object frame) List
        +analisarPose(Object frame) Object
        +calcularConfianca() float
    }

    class AlertaRisco {
        +int idAlerta
        +dateTime dataHora
        +string tipoRisco
        +string nivelSeveridade
        +string localizacao
        +string status
        +float confiancaIA
        +salvarAlerta() boolean
        +dispararNotificacao() void
        +alterarStatus() void
        +escalarSeguranca() void
    }

    class RegistroConformidade {
        +int idRegistro
        +int totalAlertasSetor
        +int totalColaboradores
        +int episVencendo
        +float indiceConformidade
        +compilarMetricas() void
        +gerarRelatorio() void
    }

    %% Herança
    Usuario <|-- Operador
    Usuario <|-- SupervisorSST

    %% EPIs
    Operador "1" --> "*" EPI : possui
    SupervisorSST --> "*" EPI : cadastra

    %% IA
    DispositivoCamera --> ProcessadorIA : fornece frames
    ProcessadorIA --> AlertaRisco : gera

    %% Alertas
    Operador "1" --> "*" AlertaRisco : relacionado
    SupervisorSST --> "*" AlertaRisco : gerencia

    %% Compliance
    RegistroConformidade --> "*" AlertaRisco : consolida
    RegistroConformidade --> "*" EPI : analisa
    SupervisorSST --> RegistroConformidade : consulta
```

---

## D. Diagrama de Arquitetura Funcional

```mermaid
flowchart LR

    A["Câmeras"] --> B["Visão Computacional / IA"]

    B --> C["Detecção de EPIs"]
    B --> D["Análise de Postura e Perímetro"]

    C --> E["Motor de Análise de Risco"]
    D --> E

    E --> F{Risco Detectado?}

    F -- Não --> G["Registrar Condição Segura"]

    F -- Sim --> H["Gerar Alerta"]

    H --> I["Dashboard SPI Alert"]

    I --> J["Gestão de Alertas"]
    I --> K["Gestão de Colaboradores e EPIs"]
    I --> L["Relatórios de Compliance"]

    J --> M["Banco de Dados"]
    K --> M
    L --> M
    G --> M

    M --> I
```

---

## Fluxo Geral do Sistema

O funcionamento do SPI Alert pode ser resumido em dois fluxos principais.

### Fluxo Automatizado

**Câmera → Visão Computacional → Detecção de EPI/Postura → Análise de Risco → Alerta → Dashboard → Supervisor → Tratamento**

### Fluxo Operacional

**Login → Dashboard → Colaboradores/EPIs → Alertas → Relatórios → Compliance**