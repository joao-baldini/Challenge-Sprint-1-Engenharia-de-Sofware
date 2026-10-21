
# 🗺️ Diagramas UML e Arquitetura — SPI Alert | FutureVision

## Challenge de Engenharia de Software — Sprints 1, 2, 3 e 4

**Projeto:** SPI Alert — FutureVision  
**Contexto:** Metaindústria  
**Entrega:** Sprint 4 — Aplicação Final

---

# 1. Introdução

Este documento apresenta a modelagem do sistema SPI Alert — FutureVision e sua evolução ao longo das quatro Sprints do projeto.

O objetivo é representar os principais atores, funcionalidades, fluxos operacionais, estruturas de dados e componentes tecnológicos da solução.

A documentação diferencia:

- **Arquitetura implementada:** aplicação web com HTML, CSS, JavaScript e armazenamento local.
- **Arquitetura evolutiva:** proposta futura de integração com câmeras industriais, inteligência artificial, APIs e banco de dados corporativo.

Essa distinção permite demonstrar a evolução do projeto sem confundir os recursos planejados com aqueles efetivamente desenvolvidos.

---

# 2. Diagrama de Casos de Uso — Sprint 4

## 2.1 Objetivo

Representar as funcionalidades disponíveis para o supervisor de segurança na aplicação final.

O supervisor é o principal ator do sistema.

## 2.2 Diagrama

```mermaid
flowchart LR
    Supervisor((Supervisor de SST))

    subgraph SPI["SPI Alert — Aplicação Final"]
        UC1([Realizar login demonstrativo])
        UC2([Visualizar dashboard])
        UC3([Consultar EPIs])
        UC4([Cadastrar EPI])
        UC5([Consultar alertas])
        UC6([Emitir alerta])
        UC7([Atualizar status do alerta])
        UC8([Consultar monitoramento simulado])
        UC9([Visualizar relatórios])
        UC10([Imprimir ou salvar PDF])
        UC11([Restaurar dados demonstrativos])
        UC12([Encerrar sessão])
    end

    Supervisor --> UC1
    Supervisor --> UC2
    Supervisor --> UC3
    Supervisor --> UC4
    Supervisor --> UC5
    Supervisor --> UC6
    Supervisor --> UC7
    Supervisor --> UC8
    Supervisor --> UC9
    Supervisor --> UC10
    Supervisor --> UC11
    Supervisor --> UC12

    UC10 -.-> UC9
```

## 2.3 Descrição dos Casos de Uso

| Código | Caso de Uso | Resultado Esperado |
|---|---|---|
| UC01 | Login demonstrativo | Liberar acesso com campos preenchidos |
| UC02 | Visualizar dashboard | Apresentar indicadores operacionais |
| UC03 | Consultar EPIs | Exibir e pesquisar equipamentos cadastrados |
| UC04 | Cadastrar EPI | Adicionar registro ao armazenamento local |
| UC05 | Consultar alertas | Exibir ocorrências e respectivos status |
| UC06 | Emitir alerta | Registrar nova ocorrência |
| UC07 | Atualizar alerta | Alterar situação da ocorrência |
| UC08 | Monitoramento | Exibir câmeras e alertas associados |
| UC09 | Relatórios | Consolidar indicadores dos registros |
| UC10 | Exportar relatório | Utilizar a impressão ou salvar como PDF |
| UC11 | Restaurar dados | Recuperar base demonstrativa inicial |
| UC12 | Encerrar sessão | Retornar à tela de login |

**Observação:** o sistema não realiza identificação automática de riscos por inteligência artificial nesta versão.

---

# 3. Diagrama de Atividades — Fluxo de Acesso e Navegação

## 3.1 Objetivo

Representar o processo de acesso à aplicação e utilização dos módulos disponíveis.

## 3.2 Diagrama

```mermaid
flowchart TD
    A([Início]) --> B[Abrir aplicação no navegador]
    B --> C[Exibir tela de login]
    C --> D[Informar matrícula e senha]
    D --> E{Campos preenchidos?}

    E -- Não --> F[Exibir mensagem de erro]
    F --> D

    E -- Sim --> G[Iniciar sessão demonstrativa]
    G --> H[Exibir dashboard]
    H --> I{Selecionar funcionalidade}

    I --> J[Gestão de EPIs]
    I --> K[Gestão de Alertas]
    I --> L[Monitoramento Simulado]
    I --> M[Relatórios]

    J --> N[Consultar ou cadastrar equipamentos]
    K --> O[Consultar, emitir ou resolver alertas]
    L --> P[Visualizar câmeras e ocorrências]
    M --> Q[Consultar indicadores e imprimir relatório]

    N --> R[Retornar ao menu]
    O --> R
    P --> R
    Q --> R

    R --> I
    I --> S[Encerrar sessão]
    S --> T([Fim])
```

## 3.3 Regras do Fluxo

- A matrícula e a senha precisam estar preenchidas.
- O acesso é demonstrativo, sem autenticação em servidor.
- O supervisor pode navegar entre os módulos.
- Os cadastros e atualizações são processados pelo JavaScript.
- A sessão pode ser encerrada pelo usuário.

---

# 4. Diagrama de Atividades — Cadastro de EPI

## 4.1 Objetivo

Representar o funcionamento do cadastro e da classificação de Equipamentos de Proteção Individual.

## 4.2 Diagrama

```mermaid
flowchart TD
    A([Início]) --> B[Acessar Gestão de EPIs]
    B --> C[Selecionar colaborador]
    C --> D[Selecionar tipo de EPI]
    D --> E[Informar CA e validade]
    E --> F[Informar condição]
    F --> G{Formulário válido?}

    G -- Não --> H[Solicitar correção dos campos]
    H --> E

    G -- Sim --> I[Gerar identificador]
    I --> J[Registrar EPI]
    J --> K[Salvar no LocalStorage]
    K --> L{Condição e validade}

    L -- Danificado ou vencido --> M[Classificar como irregular]
    L -- Vence em até 30 dias --> N[Classificar como vencendo]
    L -- Demais situações --> O[Classificar como regular]

    M --> P[Atualizar listagem e indicadores]
    N --> P
    O --> P

    P --> Q[Exibir confirmação]
    Q --> R([Fim])
```

## 4.3 Regras de Negócio

### EPI Regular

Equipamento não danificado e com validade superior a 30 dias.

### EPI Vencendo

Equipamento não danificado com vencimento nos próximos 30 dias.

### EPI Irregular

Equipamento com validade expirada ou condição informada como danificada.

Essa classificação é simplificada para fins acadêmicos e não substitui os procedimentos reais de segurança do trabalho.

---

# 5. Diagrama de Atividades — Gestão de Alertas

## 5.1 Objetivo

Representar o ciclo de registro e acompanhamento de uma ocorrência de segurança.

## 5.2 Diagrama

```mermaid
flowchart TD
    A([Início]) --> B[Acessar Alertas]
    B --> C[Selecionar Emitir Alerta]
    C --> D[Informar tipo de risco]
    D --> E[Definir severidade]
    E --> F[Informar setor e câmera]
    F --> G[Descrever ocorrência]
    G --> H{Formulário válido?}

    H -- Não --> G
    H -- Sim --> I[Registrar alerta com status Aberto]

    I --> J[Salvar no LocalStorage]
    J --> K[Atualizar histórico e dashboard]
    K --> L[Consultar alerta]

    L --> M{Ação do supervisor}

    M -- Encaminhar --> N[Atualizar para Em análise]
    M -- Resolver --> O[Atualizar para Resolvido]

    N --> P[Salvar alteração]
    O --> P

    P --> Q[Atualizar indicadores]
    Q --> R([Fim])
```

## 5.3 Estados de uma Ocorrência

```mermaid
stateDiagram-v2
    [*] --> Aberto
    Aberto --> EmAnalise: Encaminhar para análise
    Aberto --> Resolvido: Resolver diretamente
    EmAnalise --> Resolvido: Finalizar ocorrência

    state "Em análise" as EmAnalise
```

## 5.4 Classificação de Severidade

Os alertas podem ser classificados como:

- Crítico.
- Alto.
- Médio.
- Baixo.

A severidade é informada pelo supervisor durante o registro demonstrativo.

---

# 6. Diagrama de Classes — Modelo Lógico da Sprint 4

## 6.1 Objetivo

Representar as principais entidades de informação da aplicação.

Como o código utiliza objetos JavaScript, o diagrama abaixo é uma **representação lógica dos dados**, e não a descrição de classes JavaScript implementadas.

## 6.2 Diagrama

```mermaid
classDiagram
    class Colaborador {
        +number id
        +string nome
        +string setor
    }

    class EPI {
        +number id
        +number colab
        +string tipo
        +string ca
        +string validade
        +string condicao
    }

    class Alerta {
        +number id
        +string tipo
        +string severidade
        +string setor
        +string camera
        +string descricao
        +string status
        +string data
    }

    class Camera {
        +string id
        +string setor
    }

    class ArmazenamentoLocal {
        +array epis
        +array alertas
        +salvar()
        +carregar()
    }

    class Aplicacao {
        +entrar()
        +sair()
        +abrir()
        +renderTudo()
        +renderHome()
        +renderEPIs()
        +renderAlertas()
        +renderCameras()
        +renderRelatorio()
    }

    Colaborador "1" --> "0..*" EPI : possui
    Camera "1" --> "0..*" Alerta : associada
    ArmazenamentoLocal "1" o-- "0..*" EPI
    ArmazenamentoLocal "1" o-- "0..*" Alerta
    Aplicacao --> ArmazenamentoLocal : utiliza
    Aplicacao --> Colaborador : consulta
    Aplicacao --> Camera : consulta
```

## 6.3 Descrição das Entidades

### Colaborador

Representa um profissional cadastrado na base demonstrativa.

Possui identificador, nome e setor.

### EPI

Representa o equipamento registrado para determinado colaborador.

Armazena tipo, CA, validade e condição.

### Alerta

Representa uma ocorrência de risco registrada na aplicação.

Armazena severidade, localização, câmera, descrição, status e data.

### Câmera

Representa um ponto de monitoramento industrial simulado, identificado por código e setor.

### Armazenamento Local

Representa o armazenamento de registros de EPIs e alertas no navegador.

### Aplicação

Representa as funções JavaScript responsáveis pela navegação, regras de negócio e atualização da interface.

---

# 7. Diagrama de Arquitetura — Aplicação Implementada

## 7.1 Objetivo

Demonstrar a organização técnica da aplicação entregue na Sprint 4.

## 7.2 Diagrama

```mermaid
flowchart TD
    A[Supervisor de SST] --> B[Navegador Web]

    subgraph FRONT["Aplicação Web — HTML, CSS e JavaScript"]
        C[Interface]
        D[Regras de Negócio]
        E[Dashboard]
        F[Gestão de EPIs]
        G[Gestão de Alertas]
        H[Monitoramento Simulado]
        I[Relatórios]

        C --> D
        D --> E
        D --> F
        D --> G
        D --> H
        D --> I
    end

    B --> C

    D <--> J[(LocalStorage)]
    C <--> K[(SessionStorage)]

    L[Colaboradores Simulados] --> D
    M[Câmeras Simuladas] --> D
```

## 7.3 Componentes

| Componente | Responsabilidade |
|---|---|
| HTML5 | Estrutura das telas e formulários |
| CSS3 | Estilização e responsividade |
| JavaScript | Navegação e regras de negócio |
| LocalStorage | Persistência dos EPIs e alertas |
| SessionStorage | Sessão demonstrativa |
| Dados simulados | Colaboradores e câmeras de exemplo |
| Navegador | Ambiente de execução |

## 7.4 Características

- Aplicação executada diretamente no navegador.
- Não exige instalação de backend.
- Não utiliza banco de dados corporativo.
- Mantém dados de EPIs e alertas localmente.
- Não sincroniza informações entre dispositivos.
- Não processa imagens industriais.

---

# 8. Diagrama de Sequência — Registro de Alerta

## 8.1 Objetivo

Demonstrar a interação entre supervisor, interface, regras de negócio e armazenamento local.

## 8.2 Diagrama

```mermaid
sequenceDiagram
    actor S as Supervisor
    participant UI as Interface Web
    participant JS as JavaScript
    participant DB as LocalStorage

    S->>UI: Acessar tela de alertas
    UI->>JS: Solicitar registros
    JS->>DB: Consultar alertas
    DB-->>JS: Retornar registros
    JS-->>UI: Atualizar listagem

    S->>UI: Preencher novo alerta
    S->>UI: Clicar em Emitir alerta
    UI->>JS: Enviar dados do formulário
    JS->>JS: Validar campos
    JS->>JS: Criar registro com status Aberto
    JS->>DB: Salvar lista atualizada
    JS-->>UI: Atualizar alertas e dashboard
    UI-->>S: Exibir confirmação

    S->>UI: Marcar alerta como Resolvido
    UI->>JS: Solicitar alteração de status
    JS->>DB: Persistir alteração
    JS-->>UI: Atualizar indicadores
    UI-->>S: Exibir status atualizado
```

---

# 9. Diagrama de Arquitetura Evolutiva — Visão Futura

## 9.1 Objetivo

Preservar a concepção original do FutureVision, baseada em inteligência artificial e visão computacional.

Essa arquitetura representa uma possível evolução do projeto, não a implementação entregue na Sprint 4.

## 9.2 Diagrama

```mermaid
flowchart TD
    A[Câmeras Industriais] --> B[Captura de Vídeo]
    B --> C[OpenCV]

    C --> D[YOLOv8 — Detecção de EPIs]
    C --> E[MediaPipe — Análise de Postura]

    D --> F[Motor de Análise de Riscos]
    E --> F

    F --> G[Serviço de Alertas]
    G --> H[API — FastAPI]
    H --> I[(Oracle Database)]
    H --> J[Dashboard Web]
    J --> K[Supervisor de SST]
```

## 9.3 Tecnologias da Arquitetura Proposta

| Tecnologia | Finalidade Prevista |
|---|---|
| Python | Processamento e integração |
| OpenCV | Captura e tratamento de imagens |
| YOLOv8 | Identificação de objetos e EPIs |
| MediaPipe | Análise de postura corporal |
| FastAPI | Comunicação por API |
| Oracle Database | Armazenamento centralizado |
| React ou Streamlit | Interface de monitoramento |

## 9.4 Diferenças em Relação à Aplicação Atual

| Recurso | Sprint 4 | Evolução Futura |
|---|---|---|
| Cadastro de EPIs | Funcional | Integrado ao banco corporativo |
| Alertas | Registro manual | Detecção automática por IA |
| Dashboard | Dados locais | Dados centralizados |
| Monitoramento | Câmeras simuladas | Vídeo industrial real |
| Persistência | LocalStorage | Oracle Database |
| Acesso | Login demonstrativo | Autenticação segura |
| Relatórios | Dados locais | Relatórios corporativos |

---

# 10. Rastreabilidade Entre Requisitos e Diagramas

A tabela relaciona os principais requisitos funcionais da aplicação com sua representação na modelagem.

| Requisito | Funcionalidade | Diagramas Relacionados |
|---|---|---|
| RF01 | Login | Casos de Uso e Atividades |
| RF02 | Dashboard | Casos de Uso e Arquitetura |
| RF03 | Consulta de EPIs | Casos de Uso e Classes |
| RF04 | Cadastro de EPIs | Atividades e Classes |
| RF05 | Classificação de EPIs | Atividades e Classes |
| RF06 | Emissão de Alertas | Atividades e Sequência |
| RF07 | Histórico de Alertas | Casos de Uso e Classes |
| RF08 | Atualização de Status | Atividades e Sequência |
| RF09 | Monitoramento Simulado | Casos de Uso e Arquitetura |
| RF10 | Relatórios | Casos de Uso e Arquitetura |
| RF11 | Persistência Local | Classes e Arquitetura |
| RF12 | Restauração dos Dados | Casos de Uso |

A numeração acima corresponde ao resumo funcional da Sprint 4. Os requisitos históricos e suas versões devem ser consultados em `REQUISITOS.md`.

---

# 11. Evolução dos Diagramas ao Longo das Sprints

## Sprint 1 — Concepção

A modelagem inicial foi orientada à identificação do problema de segurança industrial e à definição de uma arquitetura de visão computacional.

## Sprint 2 — Refinamento

A documentação evoluiu com maior detalhamento dos requisitos, fluxos e estruturas de dados.

## Sprint 3 — Protótipo Interativo

Os modelos passaram a considerar a experiência de login, a navegação e o monitoramento demonstrativo.

## Sprint 4 — Consolidação

Os diagramas foram atualizados para representar:

- Os módulos efetivamente desenvolvidos.
- As regras de cadastro de EPIs.
- O ciclo de vida dos alertas.
- O armazenamento local.
- Os fluxos funcionais da aplicação.
- A separação entre a arquitetura implementada e a proposta futura.

Essa evolução demonstra a passagem de uma concepção tecnológica para uma aplicação demonstrativa funcional.

---

# 12. Conclusão

A modelagem final do SPI Alert — FutureVision consolida os resultados das quatro Sprints e documenta os principais componentes da aplicação.

Os diagramas demonstram como o supervisor interage com os módulos de gestão de EPIs, alertas, monitoramento simulado e relatórios.

A arquitetura implementada atende à demonstração acadêmica dos fluxos principais, enquanto a arquitetura evolutiva apresenta possibilidades de integração com soluções industriais de inteligência artificial.

---

## Documentos Relacionados

- [README.md](README.md)
- [REQUISITOS.md](REQUISITOS.md)
- [ARQUITETURA_FINAL.md](ARQUITETURA_FINAL.md)
- [CERIMONIAS_SCRUM.md](CERIMONIAS_SCRUM.md)
- [Aplicação HTML](spi-prototipo.html)

**SPI Alert — FutureVision | Sprint 4**
