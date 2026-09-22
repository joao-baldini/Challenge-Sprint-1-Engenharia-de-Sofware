# Diagramas UML — SPI Alert (FutureVision)

## A. Diagrama de Casos de Uso

```mermaid
graph LR
    Operador((Operador de Campo))
    Supervisor((Supervisor de SST))
    Camera((Câmera / Sistema de Visão))

    subgraph SPIAlert["Sistema SPI Alert"]

        UC0(Autenticar Usuário)

        UC1(Processar Feed de Vídeo)
        UC2(Detectar Uso de EPIs)
        UC3(Analisar Postura e Perímetro)

        UC4(Emitir Alerta Proativo)
        UC5(Visualizar Dashboard)
        UC6(Gerar Relatório de Conformidade)

        UC7(Consultar Alertas)
        UC8(Visualizar Detalhe do Alerta)
        UC9(Tratar / Resolver Alerta)
        UC10(Escalar para Segurança)

        UC11(Consultar Colaboradores)
        UC12(Visualizar EPIs do Colaborador)
        UC13(Cadastrar EPI)
        UC14(Validar Dados do EPI)

        UC15(Exportar / Compartilhar Relatório)
    end

    Supervisor --> UC0

    Camera --> UC1
    UC1 -.->|"include"| UC2
    UC1 -.->|"include"| UC3

    UC2 -.->|"extend: ausência de EPI"| UC4
    UC3 -.->|"extend: risco detectado"| UC4

    UC4 -.->|"Notificação visual/sonora"| Operador
    UC4 -.->|"Evento de segurança"| Supervisor

    Supervisor --> UC5

    Supervisor --> UC7
    UC7 --> UC8
    UC8 --> UC9
    UC8 --> UC10

    Supervisor --> UC4

    Supervisor --> UC11
    UC11 --> UC12
    UC12 --> UC13
    UC13 -.->|"include"| UC14

    Supervisor --> UC6
    UC6 --> UC15