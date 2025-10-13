# Aula 01 - Introdução à IoT e Arquitetura Básica

## 📊 Informações da Aula

| **Propriedade** | **Valor** |
|-----------------|-----------|
| **Professor** | Afonso Cesar |
| **Unidade** | Semana 01 |
| **Data** | 16/10/2025 - 10:00h |
| **Tipo** | Obrigatória |
| **Ponderação** | Não ponderada |
| **Duração Total** | 2 horas |
| **Daily Inicial** | 15 minutos |
| **Tempo Efetivo** | 1h 45min |

## 🎯 Objetivo da Aula
Apresentar conceitos fundamentais de IoT e arquitetura básica, aplicando no caso LogiTrack para estabelecer base técnica do Projeto Atlas.

## 📋 Caso de Estudo: LogiTrack

| **Aspecto** | **Descrição** |
|-------------|---------------|
| **Empresa** | LogiTrack (Transportadora fictícia) |
| **Problema** | Falhas no monitoramento de caminhões |
| **Solução** | Sistema IoT para rastreamento |
| **Dados** | Temperatura, localização, vibração |
| **Papel do Aluno** | Engenheiro de sistemas |
| **Entregável** | Diagrama de arquitetura IoT |

## 🔗 Assuntos Relacionados

| **Tópico** | **Relevância** |
|------------|----------------|
| Arquitetura de sistemas distribuídos | Base conceitual |
| Computação em nuvem | Plataforma de processamento |
| Tecnologia Industrial | Aplicação prática |

---

## 🕐 Agenda da Aula

| **Horário** | **Atividade** | **Duração** | **Tipo** | **Objetivo** |
|-------------|---------------|-------------|----------|--------------|
| 0:00-0:15 | Daily dos Grupos | 15 min | Reunião | Alinhamento |
| 0:15-0:30 | Introdução | 15 min | Teórica | Contextualização |
| 0:30-1:00 | Conteúdo Teórico | 30 min | Teórica | Fundamentos IoT |
| 1:00-1:30 | Atividade Prática | 30 min | Prática | Diagrama LogiTrack |
| 1:30-1:45 | Discussão | 15 min | Interativa | Dúvidas |
| 1:45-2:00 | Fechamento | 15 min | Síntese | Orientações |

## 📚 Conteúdo Teórico

### Definição IoT

| **Aspecto** | **Descrição** |
|-------------|---------------|
| **Definição** | Rede de objetos físicos com sensores, software e conectividade |
| **Características** | Conectividade, Sensoriamento, Processamento, Automação, Interoperabilidade |
| **Evolução** | RFID → Dispositivos Inteligentes → IoT Massivo |
| **Impacto** | Transformação digital das indústrias |

### Arquitetura IoT - 4 Camadas

| **Camada** | **Componentes** | **Função** | **Exemplos** |
|------------|-----------------|------------|--------------|
| **4. Aplicação** | Dashboards, APIs, ML | Visualização e análise | Metabase, Grafana |
| **3. Processamento** | Edge, Cloud, Fog | Análise e transformação | AWS, Azure, Edge |
| **2. Comunicação** | WiFi, Bluetooth, LoRa | Conectividade | Gateways, Redes |
| **1. Periféricos** | Sensores, Atuadores | Coleta e ação | Arduino, ESP32 |

### Componentes por Camada

| **Camada** | **Sensores** | **Atuadores** | **Protocolos** | **Plataformas** |
|------------|--------------|---------------|----------------|-----------------|
| **Periféricos** | GPS, Temperatura, Vibração | Motores, LEDs, Alarmes | - | Arduino, Raspberry Pi |
| **Comunicação** | - | - | WiFi, Bluetooth, LoRa | Gateways, Routers |
| **Processamento** | - | - | HTTP, MQTT | AWS, Azure, Edge |
| **Aplicação** | - | - | REST, GraphQL | Dashboards, Apps |

### Fluxo de Dados IoT

| **Etapa** | **Processo** | **Tecnologia** | **Resultado** |
|-----------|--------------|----------------|---------------|
| **1. Coleta** | Sensoriamento → Pré-processamento → Transmissão | Sensores → Microcontroladores → Protocolos | Dados brutos |
| **2. Processamento** | Armazenamento → Análise → Insights | Bancos de dados → Algoritmos → ML | Informações |
| **3. Ação** | Decisões → Atuação → Feedback | APIs → Atuadores → Monitoramento | Controle |

---

## 🏢 Caso de Estudo: LogiTrack

### Contexto da Empresa

| **Aspecto** | **Situação Atual** | **Objetivo IoT** |
|-------------|-------------------|------------------|
| **Empresa** | Transportadora de médio porte | Sistema IoT integrado |
| **Monitoramento** | Falhas no rastreamento | Localização GPS em tempo real |
| **Carga** | Perda por falta de controle | Monitoramento de temperatura |
| **Operação** | Rotas não otimizadas | Análise de vibração e otimização |
| **Custos** | Manutenção reativa | Redução de custos operacionais |

### Requisitos Técnicos

| **Categoria** | **Componente** | **Função** | **Tecnologia** |
|---------------|-----------------|------------|----------------|
| **Sensores** | GPS | Localização | Satélite |
| | Temperatura | Carga refrigerada | Termistor |
| | Acelerômetro | Vibrações/Impactos | MEMS |
| | Giroscópio | Orientação | MEMS |
| | Pressão | Pneus | Sensor de pressão |
| **Comunicação** | Cellular | Conectividade principal | 4G/5G |
| | WiFi | Depósitos | 802.11 |
| | LoRa | Áreas remotas | Long Range |
| **Processamento** | Edge | Alertas críticos | Local |
| | Cloud | Análise histórica | AWS/Azure |
| | Dashboard | Visualização | Web/Mobile |

---

## 🛠️ Atividade Prática

### Objetivo
Desenvolver diagrama de arquitetura IoT para LogiTrack com 4 camadas e fluxos de dados.

### Cronograma da Atividade

| **Fase** | **Tempo** | **Atividade** | **Entregável** |
|----------|-----------|---------------|----------------|
| **Análise** | 10 min | Identificar sensores e requisitos | Lista de componentes |
| **Desenho** | 15 min | Criar diagrama com 4 camadas | Diagrama de arquitetura |
| **Validação** | 5 min | Revisar e refinar | Diagrama final |

### Template de Arquitetura

| **Camada** | **Componentes LogiTrack** | **Tecnologia** |
|------------|----------------------------|----------------|
| **Aplicação** | Dashboard Operacional, Mobile App, Analytics | Web, Mobile, ML |
| **Processamento** | Edge Computing, Cloud Processing, Database | Local, AWS/Azure, Time Series |
| **Comunicação** | Cellular (4G/5G), WiFi, LoRa | 4G/5G, 802.11, Long Range |
| **Dispositivos** | GPS, Temperatura, Acelerômetro, Giroscópio | Satélite, Termistor, MEMS |

### Critérios de Avaliação

| **Critério** | **Peso** | **Descrição** |
|------------|----------|---------------|
| **Completude** | 30% | Todos os componentes necessários |
| **Clareza** | 25% | Diagrama fácil de entender |
| **Técnica** | 25% | Uso correto dos conceitos IoT |
| **Aplicabilidade** | 20% | Solução viável para LogiTrack |

---

## 📚 Autoestudos

### Materiais de Estudo Obrigatórios

| **Material** | **Tipo** | **Link** | **Duração** | **Objetivo** |
|---------------|----------|----------|-------------|--------------|
| **O Despertar da LogiTrack: Introdução à IoT e Arquitetura Básica** | Notion | [Acessar Material](https://cobalt-blarney-8b3.notion.site/O-Despertar-da-LogiTrack-Introdu-o-IoT-e-Arquitetura-B-sica-285256ceaea7801ea9cad5cf8102eb15) | 45 min | Conceitos fundamentais IoT |
| **Internet of Things (IoT) Architecture \| IoT Tutorial for Beginners** | YouTube | [Assistir Vídeo](https://www.youtube.com/watch?v=FRxRT0DjE7A) | 30 min | Arquitetura IoT para iniciantes |
| **Unpacking IoT Architecture: Layers and Components Explained** | Artigo | [Ler Artigo](https://deviceauthority.com/unpacking-iot-architecture-layers-and-components-explained/) | 30 min | Camadas e componentes IoT |
| **Fundamentos Básicos de IoT** | Livro Digital | [Acessar Livro](https://integrada.minhabiblioteca.com.br/reader/books/9786556901947/pageid/28) | 1h | Fundamentos teóricos |

### Cronograma de Autoestudos

| **Período** | **Atividade** | **Material** | **Tempo** |
|-------------|---------------|--------------|-----------|
| **Pré-aula** | Leitura conceitual | O Despertar da LogiTrack | 45 min |
| **Pré-aula** | Vídeo tutorial | IoT Architecture Tutorial | 30 min |
| **Pós-aula** | Aprofundamento | Unpacking IoT Architecture | 30 min |
| **Pós-aula** | Estudo teórico | Fundamentos Básicos de IoT | 1h |

### Atividades Complementares

| **Atividade** | **Tempo** | **Status** | **Entregável** |
|----------------|-----------|------------|----------------|
| Exercício prático | 1 hora | ⏳ Pendente | Diagrama final |
| Projeto Atlas | 1.5 horas | ⏳ Pendente | Documento técnico |
| Pesquisa | 30 min | ⏳ Pendente | Relatório pesquisa |
| Reflexão | 30 min | ⏳ Pendente | Relatório reflexão |

## 📋 Materiais

| **Categoria** | **Recurso** | **Tipo** |
|----------------|-------------|----------|
| **Obrigatórios** | Slides da aula | PDF |
| | Documentação técnica | Web |
| | Ferramentas desenho | Software |
| | Caso LogiTrack | Documento |
| **Complementares** | Artigos técnicos | Web |
| | Vídeos demonstração | YouTube |
| | Templates diagramas | Download |
| | Fóruns discussão | Online |

## 🎯 Objetivos de Aprendizagem

| **Categoria** | **Objetivo** | **Status** |
|----------------|--------------|------------|
| **Conhecimentos** | Compreender conceitos IoT | ⏳ |
| | Entender arquitetura camadas | ⏳ |
| | Conhecer componentes | ⏳ |
| | Identificar protocolos | ⏳ |
| **Habilidades** | Desenhar diagramas | ⏳ |
| | Analisar requisitos | ⏳ |
| | Selecionar componentes | ⏳ |
| | Aplicar conceitos | ⏳ |
| **Atitudes** | Trabalhar em equipe | ⏳ |
| | Pensar criticamente | ⏳ |
| | Comunicar ideias | ⏳ |
| | Adaptar-se | ⏳ |

## 📝 Entregáveis

| **Entregável** | **Formato** | **Prazo** | **Peso** |
|-----------------|-------------|-----------|----------|
| Diagrama Arquitetura | PNG/PDF | Final aula | 40% |
| Documentação Técnica | Markdown/Word | 1 semana | 30% |
| Reflexão Crítica | Texto | 1 semana | 30% |

## 🔄 Próximos Passos

| **Aula** | **Tema** | **Foco** | **Preparação** |
|----------|----------|----------|----------------|
| **Semana 2** | Precificação IoT | Análise custos/ROI | Modelos precificação |
| **Semana 3** | Componentes IoT | Seleção dispositivos | Protocolos comunicação |
| **Semana 4** | Segurança IoT | Implementação segurança | Frameworks segurança |

## 📞 Suporte

| **Canal** | **Contato** | **Horário** | **Local** |
|-----------|-------------|-------------|-----------|
| **Professor** | Afonso Cesar | Seg-Sex 14h-16h | Sala 205 |
| **Email** | afonso.cesar@inteli.edu.br | 24h | Online |
| **Slack** | #projeto-atlas-iot | 24h | Online |
| **Teams** | Canal do curso | 24h | Online |

---

**Esta aula estabelece a base técnica para todo o Projeto Atlas. 🚀**
