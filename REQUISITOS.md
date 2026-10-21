
# 📋 Engenharia de Requisitos — SPI Alert | FutureVision

## Challenge de Engenharia de Software — Sprints 1, 2, 3 e 4

**Projeto:** SPI Alert — FutureVision  
**Contexto:** Metaindústria  
**Entrega:** Sprint 4 — Solução Final

---

# 1. Introdução

Este documento consolida os requisitos funcionais, não funcionais, personas e restrições do projeto SPI Alert — FutureVision.

O projeto foi concebido para apoiar a prevenção de acidentes industriais por meio de visão computacional, análise de riscos e acompanhamento de Equipamentos de Proteção Individual (EPIs).

Durante as quatro Sprints, a solução evoluiu da concepção de uma arquitetura inteligente para uma aplicação web demonstrativa, com funcionalidades de cadastro, gerenciamento de alertas, indicadores e relatórios.

Este documento preserva os requisitos estabelecidos originalmente e apresenta a situação de sua implementação na Sprint 4.

**Nota:** a documentação inicial também utilizava o nome SafeHorizon. O nome adotado para a entrega atual é SPI Alert — FutureVision.

---

# 2. Personas dos Usuários

## 2.1 Persona 1 — Operador de Campo

**Nome:** Carlos Eduardo  
**Idade:** 34 anos  
**Papel:** Operador de Linha de Montagem / Célula Robotizada

### Perfil

Profissional focado em atingir as metas de produção da sua célula. Possui uma rotina dinâmica e cansativa, trabalhando diariamente com maquinário pesado.

### Necessidades

- Executar suas tarefas com produtividade.
- Trabalhar em condições seguras.
- Evitar processos burocráticos desnecessários.
- Receber alertas relevantes sem comprometer o ritmo operacional.

### Dores

- Receio de sistemas de monitoramento excessivamente punitivos.
- Possibilidade de advertências automáticas por pequenos deslizes.
- Alarmes falsos de sensores antigos.
- Interrupções desnecessárias da produção.

### Expectativas

Um sistema de segurança confiável, preventivo e que auxilie o operador sem prejudicar sua produtividade.

---

## 2.2 Persona 2 — Supervisora de Segurança (SST)

**Nome:** Mariana Souza  
**Idade:** 29 anos  
**Papel:** Engenheira / Técnica de Saúde e Segurança do Trabalho

### Perfil

Responsável por garantir a segurança nos três turnos de produção, auditar processos, investigar quase-acidentes e orientar os operadores.

### Necessidades

- Identificar gargalos de segurança em tempo real.
- Reconhecer setores com menor conformidade de EPIs.
- Acompanhar situações de risco.
- Intervir preventivamente.
- Consultar históricos e indicadores de segurança.

### Dores

- Tempo gasto analisando gravações antigas de câmeras.
- Preenchimento manual de planilhas de auditoria.
- Dificuldade para centralizar informações.
- Atuação predominantemente reativa.

### Expectativas

Uma solução que disponibilize informações organizadas, facilite o acompanhamento de riscos e apoie decisões preventivas.

---

# 3. Requisitos Funcionais Originais

Os requisitos RF001 a RF009 foram definidos na concepção e evolução inicial do projeto.

Eles representam o escopo tecnológico originalmente proposto, incluindo visão computacional e automação industrial.

## RF001 — Processamento de Feed de Vídeo

O sistema deve capturar e processar continuamente fluxos de vídeo provenientes de câmeras industriais, utilizando o protocolo RTSP.

**Situação na Sprint 4:** Não implementado.

A aplicação apresenta câmeras demonstrativas, mas não captura nem processa vídeo real.

## RF002 — Classificação de EPIs em Tempo Real

O sistema deve identificar, por meio de modelos de visão computacional, o uso correto ou a ausência de capacetes, coletes refletivos e luvas.

**Situação na Sprint 4:** Não implementado.

O cadastro e a classificação dos EPIs são realizados com base em dados informados pelo usuário.

## RF003 — Mapeamento de Esqueleto (Pose Estimation)

O sistema deve extrair pontos articulados do corpo do trabalhador para identificar posturas inadequadas e estimar riscos ergonômicos.

**Situação na Sprint 4:** Não implementado.

A aplicação permite registrar manualmente alertas relacionados a postura, mas não realiza análise biomecânica.

## RF004 — Monitoramento de Perímetro e Zonas de Risco

O sistema deve rastrear a posição do operador e prever aproximações perigosas de áreas restritas ou maquinário móvel.

**Situação na Sprint 4:** Não implementado.

O sistema permite registrar ocorrências de zona perigosa, sem rastreamento automático de pessoas.

## RF005 — Emissão de Alerta Proativo Local

O sistema deve disparar sinais lógicos imediatos para atuadores físicos, como sinalizadores sonoros ou visuais, ao prever um risco iminente.

**Situação na Sprint 4:** Não implementado.

Os alertas são criados manualmente e não acionam dispositivos industriais.

## RF006 — Dashboard Operacional do Supervisor

O sistema deve disponibilizar uma interface web contendo o feed analítico das câmeras e um painel centralizado de notificações para o supervisor de SST.

**Situação na Sprint 4:** Parcialmente implementado.

O dashboard apresenta indicadores e alertas cadastrados, mas não possui feed analítico de câmeras reais.

## RF007 — Persistência de Eventos Críticos

O sistema deve registrar em banco de dados o histórico de eventos críticos, contendo data, hora, setor, tipo de inconformidade e nível de severidade.

**Situação na Sprint 4:** Parcialmente implementado.

Os eventos são registrados com essas informações e armazenados no LocalStorage. Não existe persistência em banco de dados SQL.

## RF008 — Emissão de Relatório de Conformidade

O sistema deve permitir a geração de relatórios estatísticos de segurança agrupados por setor, turno ou tipo de risco, possibilitando análise de tendências.

**Situação na Sprint 4:** Parcialmente implementado.

A aplicação disponibiliza um resumo geral de EPIs e alertas, com impressão ou salvamento em PDF pelo navegador. Não implementa todos os agrupamentos previstos originalmente.

## RF009 — Autenticação e Controle de Acesso

O sistema deve exigir identificação do supervisor por matrícula e senha para liberar o acesso ao dashboard, histórico de eventos e relatórios.

Também deve garantir acesso apenas a usuários autorizados e permitir o encerramento explícito da sessão.

**Origem:** requisito incorporado na Sprint 3.

**Situação na Sprint 4:** Parcialmente implementado.

A interface exige matrícula e senha preenchidas e disponibiliza o encerramento da sessão. Entretanto, não existe autenticação real ou validação de usuários autorizados.

---

# 4. Requisitos Funcionais Incorporados na Sprint 4

Os requisitos abaixo documentam as funcionalidades adicionadas à aplicação demonstrativa para apoiar os processos de gestão de EPIs e alertas.

## RF010 — Cadastro de EPIs

O sistema deve permitir o registro de equipamentos associados a colaboradores.

### Dados necessários

- Colaborador.
- Tipo de EPI.
- Número do Certificado de Aprovação.
- Data de validade.
- Condição do equipamento.

**Situação:** Implementado no código demonstrativo.

## RF011 — Classificação de Validade e Condição

O sistema deve classificar os equipamentos conforme a validade e a condição informadas.

### Classificações

- Regular.
- Vencendo.
- Irregular.

**Situação:** Implementado no código demonstrativo.

## RF012 — Emissão Manual de Alertas

O supervisor deve conseguir registrar ocorrências informando:

- Tipo de risco.
- Severidade.
- Setor.
- Câmera.
- Descrição.

**Situação:** Implementado no código demonstrativo.

## RF013 — Atualização do Status de Alertas

O supervisor deve conseguir atualizar o andamento das ocorrências.

### Estados previstos

- Aberto.
- Em análise.
- Resolvido.

**Situação:** Implementado no código demonstrativo.

## RF014 — Monitoramento Demonstrativo

O sistema deve apresentar câmeras cadastradas e a quantidade de alertas ativos associados a cada uma.

**Situação:** Implementado como simulação.

Não existe transmissão de imagens ao vivo.

## RF015 — Armazenamento Local

Os registros de EPIs e alertas devem permanecer armazenados no navegador após recarregamento da aplicação.

**Situação:** Implementado com LocalStorage.

## RF016 — Indicadores Dinâmicos

O dashboard deve apresentar indicadores calculados com base nos registros disponíveis.

**Situação:** Implementado no código demonstrativo.

## RF017 — Restauração da Base Demonstrativa

O sistema deve permitir restaurar os registros iniciais após confirmação do usuário.

**Situação:** Implementado no código demonstrativo.

## RF018 — Consulta e Exportação de Relatórios

O sistema deve disponibilizar um resumo dos registros e permitir impressão ou salvamento em PDF pelo navegador.

**Situação:** Implementado de forma simplificada.

---

# 5. Matriz de Atendimento — Sprint 4

| Código | Funcionalidade | Atendimento |
|---|---|---|
| RF001 | Processamento RTSP | Não implementado |
| RF002 | Detecção automática de EPIs | Não implementado |
| RF003 | Análise de postura | Não implementado |
| RF004 | Monitoramento automático de perímetro | Não implementado |
| RF005 | Alertas com atuadores físicos | Não implementado |
| RF006 | Dashboard com feed analítico | Parcial |
| RF007 | Persistência de eventos em banco SQL | Parcial |
| RF008 | Relatórios estatísticos por setor, turno e risco | Parcial |
| RF009 | Autenticação e controle de acesso | Parcial |
| RF010 | Cadastro de EPIs | Implementado |
| RF011 | Classificação de EPIs | Implementado |
| RF012 | Emissão manual de alertas | Implementado |
| RF013 | Atualização de status | Implementado |
| RF014 | Monitoramento demonstrativo | Implementado |
| RF015 | Armazenamento local | Implementado |
| RF016 | Dashboard dinâmico | Implementado |
| RF017 | Restauração de dados | Implementado |
| RF018 | Relatório simplificado | Implementado |

**Observação:** as situações refletem o escopo do código desenvolvido, não uma homologação definitiva. Os testes finais devem verificar os fluxos implementados.

---

# 6. Requisitos Não Funcionais Originais

## RNF001 — Desempenho e Latência

O processamento completo de captura de frame, inferência da IA, análise de riscos e emissão do alerta deve apresentar latência inferior a 300 milissegundos por ciclo de frame.

**Situação:** Não validado. O pipeline de visão computacional não está implementado.

## RNF002 — Confiabilidade e Precisão da IA

Os modelos de visão computacional devem alcançar precisão média mínima de 88% (mAP@0.5), de acordo com os critérios estabelecidos na concepção.

**Situação:** Não validado. Não há inferência real de IA na aplicação entregue.

## RNF003 — Arquitetura de Dados

A persistência dos eventos, históricos, logs e cadastros deve utilizar banco de dados relacional Oracle SQL.

**Situação:** Não atendido. A aplicação utiliza LocalStorage.

## RNF004 — Disponibilidade Operacional

O backend local responsável por IA e alertas deve funcionar independentemente da rede externa, com disponibilidade de 99,9% em ambiente LAN industrial.

**Situação:** Não validado. Não existe backend industrial implementado.

## RNF005 — Privacidade e LGPD

O sistema deve priorizar análise biomecânica e de objetos, utilizando técnicas de descaracterização de rostos e proteção da privacidade biométrica.

**Situação:** Não implementado para processamento de imagens, pois não há captura de vídeo real.

## RNF006 — Escalabilidade

A API deve suportar requisições concorrentes e processamento assíncrono de múltiplas câmeras utilizando FastAPI em Python.

**Situação:** Não implementado.

---

# 7. Requisitos Não Funcionais da Aplicação Demonstrativa

Além dos requisitos originais, a aplicação HTML considera:

## RNF007 — Usabilidade

A interface deve apresentar navegação compreensível e organização consistente entre os módulos.

## RNF008 — Compatibilidade

A aplicação deve ser executável em navegadores modernos.

## RNF009 — Portabilidade

A versão demonstrativa deve ser executável sem instalação de servidor.

## RNF010 — Persistência Local

Os registros devem permanecer disponíveis no mesmo navegador após atualização da página, enquanto os dados locais forem preservados.

## RNF011 — Feedback ao Usuário

O sistema deve apresentar confirmações e mensagens após operações de cadastro e atualização.

## RNF012 — Clareza Visual

A interface deve permitir identificar equipamentos irregulares e alertas por meio de informações textuais e visuais.

---

# 8. Restrições Originais do Sistema

## RS001 — Execução em Bordas (Edge Computing)

Os modelos de processamento de imagens devem ser otimizados para execução em hardware de borda industrial ou ambientes controlados de teste.

**Situação:** Não aplicado na versão HTML. O processamento de imagens não foi implementado.

## RS002 — Independência de Nuvem Externa

O subsistema de detecção e geração de alertas críticos não poderá depender de conexões WAN com nuvem pública.

**Situação:** Não validado, pois não existe subsistema automatizado de detecção e atuação industrial.

## RS003 — Vedação de Simulações Estáticas

A concepção original determina que a entrega final não utilize telas simuladas sem funcionalidades reais.

Os fluxos de detecção, alertas e persistência SQL deveriam ser funcionais e integrados.

**Situação:** Não atendida integralmente pela solução HTML atual.

A Sprint 4 permite a utilização de dados industriais simulados, mas a aplicação entregue não implementa a detecção automática de riscos nem a persistência SQL previstas originalmente.

Essa divergência deve ser considerada na avaliação do atendimento aos requisitos e na definição dos próximos incrementos técnicos.

## RS004 — Viabilidade Econômica

A solução deve respeitar as condições econômicas do projeto, priorizando tecnologias viáveis quanto a custos e prazos.

**Situação:** A versão HTML reduz dependências de infraestrutura, mas não foi apresentada uma análise econômica completa da implantação industrial.

---

# 9. Regras de Negócio da Aplicação

## RN01 — Associação de EPIs

Cada registro de EPI deve estar associado a um colaborador da base demonstrativa.

## RN02 — Condição do Equipamento

Um EPI informado como danificado deve ser classificado como irregular.

## RN03 — Validade

Equipamentos vencidos devem ser classificados como irregulares.

## RN04 — Próximo Vencimento

Equipamentos não danificados, com vencimento em até 30 dias, devem ser classificados como Vencendo.

## RN05 — Novo Alerta

Todo alerta emitido manualmente deve iniciar com o status Aberto.

## RN06 — Resolução

Alertas resolvidos não devem ser contabilizados como pendentes.

## RN07 — Persistência

Cadastros e alterações devem ser salvos no LocalStorage.

## RN08 — Restauração

A opção de restauração deve substituir os registros do usuário pelos dados demonstrativos iniciais.

---

# 10. Evolução dos Requisitos por Sprint

## Sprint 1 — Concepção

- Definição das personas Carlos Eduardo e Mariana Souza.
- Levantamento das necessidades do operador e da supervisora.
- Proposta de monitoramento inteligente.
- Definição dos requisitos iniciais de visão computacional.
- Definição das restrições técnicas.

## Sprint 2 — Modelagem

- Detalhamento da solução.
- Modelagem dos principais processos.
- Organização de funcionalidades.
- Evolução da arquitetura e da interface.

## Sprint 3 — Protótipo Interativo

- Incorporação do requisito RF009.
- Desenvolvimento do fluxo de login demonstrativo.
- Melhorias nos formulários.
- Busca e filtros.
- Evolução do monitoramento demonstrativo.
- Organização dos artefatos Scrum.

## Sprint 4 — Aplicação Demonstrativa

- Cadastro de EPIs com persistência local.
- Classificação de equipamentos.
- Emissão manual de alertas.
- Atualização dos status.
- Indicadores dinâmicos.
- Monitoramento demonstrativo.
- Relatórios.
- Consolidação da documentação.

A Sprint 4 implementa funcionalidades de apoio à gestão, mas não substitui integralmente os requisitos originais de automação e visão computacional.

---

# 11. Rastreabilidade dos Requisitos

| Requisito | Evidência ou Documento |
|---|---|
| RF001–RF005 | Arquitetura evolutiva em DIAGRAMAS.md |
| RF006 | Dashboard da aplicação |
| RF007 | Histórico local de alertas |
| RF008 | Módulo de relatórios |
| RF009 | Tela de login e logout |
| RF010–RF011 | Módulo de EPIs |
| RF012–RF013 | Módulo de Alertas |
| RF014 | Monitoramento demonstrativo |
| RF015 | LocalStorage |
| RF016 | Dashboard |
| RF017 | Restauração de dados |
| RF018 | Impressão do relatório |

A indicação de um documento ou tela não significa, por si só, que o requisito original esteja integralmente atendido.

---

# 12. Critérios de Aceite da Aplicação Demonstrativa

Os seguintes testes devem ser realizados antes da entrega:

- [ ] Abrir a aplicação no navegador.
- [ ] Realizar login demonstrativo.
- [ ] Navegar entre os módulos.
- [ ] Cadastrar um EPI.
- [ ] Consultar o EPI cadastrado.
- [ ] Verificar a classificação de validade.
- [ ] Emitir um alerta.
- [ ] Consultar o histórico.
- [ ] Alterar o status do alerta.
- [ ] Verificar a atualização do dashboard.
- [ ] Consultar câmeras simuladas.
- [ ] Consultar relatório.
- [ ] Imprimir ou salvar o relatório como PDF.
- [ ] Atualizar a página e verificar persistência.
- [ ] Restaurar os dados demonstrativos.
- [ ] Encerrar a sessão.

As caixas devem ser marcadas somente após testes reais.

---

# 13. Pendências Técnicas em Relação ao Escopo Original

Para atender integralmente à concepção inicial do FutureVision, ainda seriam necessários:

1. Integração com câmeras RTSP.
2. Processamento de imagens.
3. Detecção automática de EPIs.
4. Análise de postura e zonas de risco.
5. Alertas físicos e automáticos.
6. Backend com FastAPI.
7. Persistência em Oracle Database.
8. Autenticação segura e controle de acesso.
9. Relatórios por setor, turno e tipo de risco.
10. Testes de desempenho, precisão e disponibilidade.
11. Medidas de privacidade para processamento de imagens.

Esses itens representam lacunas da implementação atual diante dos requisitos originais.

---

# 14. Conclusão

A documentação de requisitos do SPI Alert — FutureVision demonstra a evolução do projeto durante as quatro Sprints.

A aplicação final reúne funcionalidades demonstrativas de gestão de EPIs, alertas, indicadores e relatórios.

O escopo implementado apresenta avanços em relação ao protótipo inicial, especialmente no funcionamento dos formulários, armazenamento local e atualização das informações.

Entretanto, os requisitos originais de inteligência artificial, monitoramento industrial automatizado e persistência SQL ainda não foram integralmente implementados.

Essa distinção garante maior clareza sobre o estágio atual do produto e sobre os componentes necessários para sua evolução industrial.

---

## Documentos Relacionados

- [README.md](README.md)
- [DIAGRAMAS.md](DIAGRAMAS.md)
- [ARQUITETURA_FINAL.md](ARQUITETURA_FINAL.md)
- [CERIMONIAS_SCRUM.md](CERIMONIAS_SCRUM.md)
- [Aplicação HTML](spi-prototipo.html)

**SPI Alert — FutureVision | Engenharia de Requisitos — Sprint 4**
