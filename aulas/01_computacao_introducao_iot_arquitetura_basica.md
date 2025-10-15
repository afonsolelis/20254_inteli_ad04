# Aula 01 - Introdução à IoT e Arquitetura Básica

## 📊 Informações da Aula

| **Propriedade** | **Valor** |
|-----------------|-----------|
| **Professor** | Afonso Cesar |
| **Unidade** | Semana 01 |
| **Data** | 16/10/2025 - 10:00h |
| **Duração Total** | 2 horas |
| **Daily Inicial** | 15 minutos |
| **Tempo Efetivo** | 1h 45min |

## 🎯 Objetivo da Aula
Apresentar conceitos fundamentais de IoT e arquitetura básica, aplicando no caso LogiTrack para estabelecer base técnica do Projeto Atlas.

## 📚 Autoestudos

### Materiais de Estudo Obrigatórios

| **Material** | **Tipo** | **Link** | **Duração** | **Objetivo** |
|---------------|----------|----------|-------------|--------------|
| **O Despertar da LogiTrack: Introdução à IoT e Arquitetura Básica** | Notion | [Acessar Material](https://cobalt-blarney-8b3.notion.site/O-Despertar-da-LogiTrack-Introdu-o-IoT-e-Arquitetura-B-sica-285256ceaea7801ea9cad5cf8102eb15) | 45 min | Conceitos fundamentais IoT |
| **Internet of Things (IoT) Architecture \| IoT Tutorial for Beginners** | YouTube | [Assistir Vídeo](https://www.youtube.com/watch?v=FRxRT0DjE7A) | 30 min | Arquitetura IoT para iniciantes |
| **Unpacking IoT Architecture: Layers and Components Explained** | Artigo | [Ler Artigo](https://deviceauthority.com/unpacking-iot-architecture-layers-and-components-explained/) | 30 min | Camadas e componentes IoT |
| **Fundamentos Básicos de IoT** | Livro Digital | [Acessar Livro](https://integrada.minhabiblioteca.com.br/reader/books/9786556901947/pageid/28) | 1h | Fundamentos teóricos |

---

## 🎭 A LogiTrack em Crise: O Despertar do IoT

### 📖 O Cenário: A LogiTrack em Crise

*"É 8h da manhã de uma segunda-feira chuvosa em São Paulo. Na sala de reuniões da LogiTrack, o CEO Henrique Duarte olha para os números do último trimestre: 6% de perdas anuais, clientes insatisfeitos, concorrência digital avançando. Ele precisa de uma solução - e precisa dela agora."*

**A Situação:** LogiTrack, transportadora de médio porte com 120 caminhões e 3 centros de distribuição, enfrenta uma crise operacional. A empresa perde 6% do faturamento anual devido a:
- Falta de rastreabilidade confiável
- Controle inadequado das condições das cargas
- Atrasos e produtos danificados
- Concorrência digital avançando

### 🎭 Os Personagens Entram em Cena

- **Marina Costa** (Engenheira de Software) - *"Precisamos pensar em arquitetura, não em gadgets"*
- **Carlos Menezes** (Gerente de Operações) - *"E se a conexão cair na estrada?"*
- **Juliana Prado** (Analista de Dados) - *"Dados estruturados e rastreáveis"*
- **Pedro Nascimento** (Coordenador de TI) - *"Gerenciamento e autenticação são essenciais"*

### 🚨 O Desafio É Lançado

*"O conselho aprovou o Projeto Atlas. Vocês têm 90 dias para transformar nossa frota de 120 caminhões em unidades inteligentes. Mas primeiro, precisamos entender: o que é IoT? Como funciona? Qual a arquitetura que nos salvará?"*

**O Desafio:** O CEO Henrique Duarte precisa de uma solução IoT para transformar caminhões comuns em unidades inteligentes, capazes de monitorar temperatura, vibração e localização em tempo real.

### 🎯 O Que É IoT? Conceitos Fundamentais

**Definição:** Internet das Coisas é uma rede de objetos físicos incorporados com sensores, software e conectividade para trocar dados com outros dispositivos e sistemas.

**Características Principais:**
- **Conectividade:** Dispositivos conectados à internet
- **Sensoriamento:** Coleta de dados do ambiente físico
- **Processamento:** Análise e transformação de dados
- **Automação:** Ações baseadas em dados coletados
- **Interoperabilidade:** Comunicação entre diferentes sistemas

### 🏗️ Arquitetura IoT: As 4 Camadas Fundamentais

#### **Camada 1: Percepção (Sensores e Atuadores)**
- **Função:** Coleta de dados do mundo físico
- **Componentes:** Sensores (GPS, temperatura, vibração), atuadores (motores, LEDs)
- **Exemplo LogiTrack:** Sensores de temperatura, GPS, acelerômetro nos caminhões

#### **Camada 2: Comunicação (Rede)**
- **Função:** Transmissão de dados entre dispositivos
- **Componentes:** Gateways, protocolos (WiFi, Bluetooth, LoRa, 4G/5G)
- **Exemplo LogiTrack:** 4G/5G para estrada, WiFi para depósitos, LoRa para áreas remotas

#### **Camada 3: Processamento**
- **Função:** Análise e transformação de dados
- **Componentes:** Edge Computing, Cloud Computing, bancos de dados
- **Exemplo LogiTrack:** Processamento local para alertas, análise histórica na nuvem

#### **Camada 4: Aplicação**
- **Função:** Interface com usuários e tomada de decisões
- **Componentes:** Dashboards, APIs, aplicações móveis
- **Exemplo LogiTrack:** Dashboard operacional, alertas em tempo real, relatórios

### 🔄 Fluxo de Dados IoT

**1. Coleta:** Sensores coletam dados → Pré-processamento local → Transmissão
**2. Processamento:** Armazenamento → Análise → Geração de insights
**3. Ação:** Decisões baseadas em dados → Comandos para atuadores → Feedback

### 🚨 O Dilema da LogiTrack: "E se a conexão cair na estrada?"

**Problema Real:** Conectividade não é garantida em todas as áreas

**Solução:** Arquitetura robusta com:
- Armazenamento local (Edge Computing)
- Sincronização quando conectividade retorna
- Redundância de comunicação
- Processamento distribuído

### 🏗️ Atividade Prática: War Room IoT - Construindo a Arquitetura da LogiTrack

**Cenário:** Vocês são a equipe técnica da LogiTrack. O CEO Henrique Duarte está esperando uma solução. É hora de entrar em ação!

**Instruções para os Grupos:**
1. **Analisem o problema** da LogiTrack (15 min)
2. **Desenhem a arquitetura como vocês acham que está hoje** com 4 camadas (30 min)
3. **Apresentem a solução** (3 min por grupo)
4. **Discussão coletiva** com perguntas-chave (15 min)

**Template de Arquitetura:**
```
Camada 4 - Aplicação: Dashboard, Alertas, Relatórios
Camada 3 - Processamento: Edge + Cloud + Database
Camada 2 - Comunicação: 4G/5G + WiFi + LoRa
Camada 1 - Percepção: GPS + Temperatura + Vibração
```

### 🎯 Discussão Coletiva: Perguntas-Chave sobre IoT

**Após as apresentações, vamos discutir os conceitos fundamentais:**

#### **🤔 O que são Sensores?**
- **Definição:** Dispositivos que coletam dados do ambiente físico
- **Exemplos na LogiTrack:** GPS (localização), termômetro (temperatura), acelerômetro (vibração)
- **Pergunta:** Que outros sensores vocês incluiriam na solução?

#### **⚡ O que são Atuadores?**
- **Definição:** Dispositivos que executam ações baseadas em comandos
- **Exemplos na LogiTrack:** Alarme de temperatura, sistema de refrigeração, notificações
- **Pergunta:** Que ações automáticas vocês implementariam?

#### **🌐 O que são Gateways?**
- **Definição:** Dispositivos que conectam sensores à internet
- **Função:** Traduzir protocolos, agregar dados, gerenciar conectividade
- **Pergunta:** Como garantir que os dados cheguem mesmo com falhas de rede?

#### **☁️ O que é Edge Computing?**
- **Definição:** Processamento de dados próximo aos sensores
- **Vantagem:** Resposta rápida, funciona offline
- **Pergunta:** Que dados processariam localmente vs na nuvem?

#### **📊 O que é um Dashboard?**
- **Definição:** Interface visual para monitoramento em tempo real
- **Função:** Transformar dados em informações acionáveis
- **Pergunta:** Que informações seriam mais importantes para o CEO?

### 🚨 O Dilema da Conectividade

**Carlos Menezes pergunta:** *"E se a conexão cair na estrada?"*

**Discussão:**
- Como sua arquitetura resolve esse problema?
- Que dados armazenariam localmente?
- Como sincronizariam quando a conexão voltar?
- Que redundâncias implementariam?

### 🎭 Fechamento: O Projeto Atlas Começa Aqui

**Henrique Duarte (CEO):** *"Excelente trabalho, equipe! Vocês transformaram um problema em uma oportunidade. O Projeto Atlas começa aqui, mas não termina. Nas próximas semanas, vamos descobrir quanto tudo isso vai custar e como implementar. A LogiTrack está nas mãos de vocês!"*

**Juliana Prado (narradora):** *"Hoje deixamos de falar em problemas isolados e passamos a falar em sistema. O Atlas começa aqui."*

### 🎯 Objetivos de Aprendizagem

**Ao final desta aula, vocês serão capazes de:**
- Compreender os conceitos fundamentais de IoT
- Identificar as 4 camadas da arquitetura IoT
- Desenhar diagramas de arquitetura básica
- Aplicar conceitos em cenários reais
- Trabalhar colaborativamente em equipe

### 🚀 Próximos Passos

**Hoje:** Entendemos o que é IoT e sua arquitetura básica

**Próxima aula:** Descobriremos quanto tudo isso vai custar - precificação e impactos econômicos

**Projeto Atlas:** Começa aqui, mas não termina aqui