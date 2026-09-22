🎨 Documentação de Design e UX — SPI Alert (FutureVision)

Este documento apresenta a arquitetura de interface, os fluxos de navegação e as principais decisões de Experiência do Usuário (UX) implementadas no protótipo funcional do SPI Alert, desenvolvido em HTML, CSS e JavaScript.

A evolução do protótipo priorizou não apenas a representação visual dos requisitos da Sprint 1, mas também a simulação funcional das principais interações do usuário, aproximando a experiência de um aplicativo real para uso no ambiente industrial.

🗺️ 1. Mapa de Telas (Screen Map)

A arquitetura foi organizada para oferecer acesso rápido às informações de segurança, EPIs e conformidade, mantendo uma navegação simples e adequada ao uso em dispositivos móveis.

🔐 Acesso ao Sistema

login — Autenticação do usuário
Tela inicial do SPI Alert, com campos de matrícula e senha. O acesso ao ambiente operacional ocorre após o preenchimento dos dados, simulando a autenticação de um supervisor ou usuário autorizado.

🏠 Módulo Principal — Dashboard

home — Painel central
Concentra os principais indicadores operacionais, como alertas abertos, índice de conformidade, quantidade de colaboradores e setores ativos. Também apresenta alertas críticos recentes e atalhos para os demais módulos.

⚠️ Módulo de Alertas — Gestão de Riscos

lista-alertas — Central de alertas
Exibe os riscos identificados e permite filtrá-los de acordo com seu status: Abertos, Em Análise ou Resolvidos.

detalhe-alerta — Detalhamento da ocorrência
Apresenta informações como tipo do risco, colaborador envolvido, localização, câmera responsável pela detecção, nível de confiança da IA e tempo de resposta. Disponibiliza ações de tratamento e escalonamento.

emitir-alerta — Registro manual de risco
Permite selecionar tipo de risco, severidade e localização por meio de chips interativos, além de registrar câmera, colaborador e descrição da ocorrência.

sucesso-alerta — Confirmação da emissão
Fornece feedback imediato ao usuário, apresentando os dados selecionados durante o registro do alerta.

👷 Módulo de EPIs — Gestão de Colaboradores

lista-colaboradores — Consulta de colaboradores
Permite localizar funcionários por meio de busca em tempo real e filtrar os registros pelas condições Todos, Irregulares e Vencendo.

perfil-colaborador — Ficha individual
Centraliza os dados do colaborador e seus EPIs cadastrados, apresentando equipamento, validade e situação de conformidade.

cadastro-epi — Registro de EPI
Permite selecionar o tipo e a condição do equipamento e registrar CA, data de entrega, validade e observações. Os campos obrigatórios são validados antes da conclusão.

sucesso-epi — Confirmação do cadastro
Apresenta o resultado do registro utilizando o EPI efetivamente selecionado pelo usuário.

📊 Módulo de Compliance — Relatórios

relatorio — Painel de conformidade
Apresenta indicadores consolidados e percentuais de conformidade por setor, além de alertas, colaboradores e EPIs próximos ao vencimento. Inclui ações de exportação e compartilhamento.

🔗 2. Mapeamento entre Telas e Casos de Uso

O protótipo mantém correspondência entre a interface e os principais casos de uso definidos na Sprint 1.

Caso de Uso	Telas relacionadas	Interação representada
UC5 — Visualizar Dashboard	home	Visualização dos principais indicadores de segurança e conformidade e acesso aos módulos operacionais.
UC4 — Emitir Alerta Proativo	lista-alertas, detalhe-alerta, emitir-alerta, sucesso-alerta	Consulta, classificação, registro e tratamento de ocorrências de risco.
UC2 — Detectar Uso de EPIs	lista-colaboradores, perfil-colaborador	Consulta da situação dos EPIs associados aos colaboradores e identificação de irregularidades.
UC6 — Gerar Relatório	relatorio	Consolidação dos indicadores de conformidade por setor para acompanhamento e auditoria.

Além desses casos de uso, o protótipo incorpora o fluxo de autenticação, necessário para representar o acesso controlado às funcionalidades do sistema.

🧠 3. Decisões de UI/UX para o Ambiente Industrial
📱 Interface Mobile e Field-Ready

O SPI Alert foi projetado em uma área de 390 × 844 px, simulando um dispositivo móvel. Essa decisão favorece o uso por supervisores durante deslocamentos e rondas no ambiente industrial.

A organização vertical das informações prioriza dados críticos e ações frequentes, reduzindo a quantidade de passos necessária para acessar uma função.

🧭 Navegação Consistente

O protótipo utiliza dois recursos complementares de navegação:

Bottom Navigation: acesso permanente aos módulos Home, Alertas, EPIs e Relatórios;
Navegação superior: permite visualizar e acessar rapidamente os principais módulos durante a demonstração do protótipo.

O estado ativo da navegação acompanha a tela exibida, reforçando a orientação do usuário dentro do sistema.

🚦 Hierarquia Visual de Risco

As cores possuem significado funcional e ajudam o usuário a interpretar rapidamente a criticidade das informações:

🔴 Vermelho: situações críticas, irregularidades e riscos que exigem atenção imediata;
🟠 Laranja: atenção, análise ou proximidade de vencimento;
🟢 Verde: condição regular, segura ou resolvida;
🔵 Azul: informações gerenciais, indicadores e elementos de apoio.

A cor não atua isoladamente: badges, textos e ícones complementam a sinalização, facilitando a compreensão do status.

👆 Chips de Seleção Interativos

Os chips utilizados nos formulários deixaram de ser apenas elementos visuais e passaram a funcionar como controles de seleção.

Em cada grupo, somente uma opção pode permanecer selecionada, oferecendo uma interação rápida para escolha de:

Tipo de EPI → Condição → Tipo de Risco → Severidade → Localização.

Esse padrão reduz digitação e aumenta a área disponível para toque, característica importante em interfaces destinadas ao ambiente industrial.

⚙️ 4. Interações Funcionais Implementadas

A nova versão evolui de um protótipo predominantemente visual para uma simulação interativa dos principais fluxos do sistema.

A busca de colaboradores funciona em tempo real, enquanto as abas filtram dinamicamente os registros apresentados. Caso nenhuma informação corresponda ao filtro ou à busca, o sistema apresenta um estado vazio, evitando que uma tela sem conteúdo seja interpretada como erro.

Os formulários também possuem validação antes do avanço. No cadastro de EPI, informações obrigatórias como CA e validade precisam ser informadas. Na emissão de alertas, a descrição da ocorrência é validada antes da confirmação.

As telas de sucesso utilizam as escolhas realizadas pelo usuário durante o fluxo, em vez de apresentar somente informações fixas.

Ações como Monitoramento, Gerar Ficha Individual, Escalar para Segurança, Exportar PDF e Enviar por E-mail também oferecem feedback visual, indicando ao usuário que sua interação foi reconhecida.

🔄 5. Feedback e Prevenção de Erros

Um dos princípios incorporados à nova versão é tornar o estado do sistema visível ao usuário.

O protótipo utiliza feedback imediato para informar o resultado de ações e impedir avanços quando dados essenciais não foram preenchidos. Dessa forma, o usuário recebe confirmação sobre aquilo que realizou e orientação quando precisa corrigir alguma informação.

Esse comportamento é especialmente relevante no contexto do SPI Alert, no qual ações relacionadas à segurança precisam ser claras, rápidas e pouco sujeitas a ambiguidades.

🔤 6. Tipografia e Legibilidade

A interface utiliza duas famílias tipográficas com funções distintas:

DM Sans é empregada nos elementos gerais da interface por favorecer leitura rápida em telas pequenas.

DM Mono é utilizada principalmente para informações estruturadas e numéricas, como matrículas, horários, percentuais e identificadores, ajudando a diferenciar dados operacionais do restante do conteúdo.

🎯 7. Resultado da Evolução do Protótipo

A nova versão do SPI Alert não representa apenas como o sistema deverá parecer, mas também simula como o usuário interage com seus principais fluxos.

A inclusão de autenticação, filtros, busca dinâmica, seleções interativas, validação de formulários, feedbacks e estados vazios torna o protótipo mais adequado para demonstração, validação de requisitos e testes de usabilidade, mantendo alinhamento entre a experiência projetada e os casos de uso definidos para o sistema.
