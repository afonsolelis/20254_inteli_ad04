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

## 📚 Autoestudos

### Materiais de Estudo Obrigatórios

| **Material** | **Tipo** | **Link** | **Duração** | **Objetivo** |
|---------------|----------|----------|-------------|--------------|
| **O Despertar da LogiTrack: Introdução à IoT e Arquitetura Básica** | Notion | [Acessar Material](https://cobalt-blarney-8b3.notion.site/O-Despertar-da-LogiTrack-Introdu-o-IoT-e-Arquitetura-B-sica-285256ceaea7801ea9cad5cf8102eb15) | 45 min | Conceitos fundamentais IoT |
| **Internet of Things (IoT) Architecture \| IoT Tutorial for Beginners** | YouTube | [Assistir Vídeo](https://www.youtube.com/watch?v=FRxRT0DjE7A) | 30 min | Arquitetura IoT para iniciantes |
| **Unpacking IoT Architecture: Layers and Components Explained** | Artigo | [Ler Artigo](https://deviceauthority.com/unpacking-iot-architecture-layers-and-components-explained/) | 30 min | Camadas e componentes IoT |
| **Fundamentos Básicos de IoT** | Livro Digital | [Acessar Livro](https://integrada.minhabiblioteca.com.br/reader/books/9786556901947/pageid/28) | 1h | Fundamentos teóricos |

---

## 🎭 Aula: "O Despertar da LogiTrack - War Room IoT"

### 📖 Storytelling da Aula (30 minutos)

#### **Cenário: A LogiTrack em Crise**
*"É 8h da manhã de uma segunda-feira chuvosa em São Paulo. Na sala de reuniões da LogiTrack, o CEO Henrique Duarte olha para os números do último trimestre: 6% de perdas anuais, clientes insatisfeitos, concorrência digital avançando. Ele precisa de uma solução - e precisa dela agora."*

#### **Os Personagens Entram em Cena**
- **Marina Costa** (Engenheira de Software) - "Precisamos pensar em arquitetura, não em gadgets"
- **Carlos Menezes** (Gerente de Operações) - "E se a conexão cair na estrada?"
- **Juliana Prado** (Analista de Dados) - "Dados estruturados e rastreáveis"
- **Pedro Nascimento** (Coordenador de TI) - "Gerenciamento e autenticação são essenciais"

#### **O Desafio É Lançado**
*"O conselho aprovou o Projeto Atlas. Vocês têm 90 dias para transformar nossa frota de 120 caminhões em unidades inteligentes. Mas primeiro, precisamos entender: o que é IoT? Como funciona? Qual a arquitetura que nos salvará?"*

### 🎯 Metodologia Ativa: "War Room IoT"

#### **Fase 1: Apresentação Teórica (30 min)**
**Professor como "Henrique Duarte"** - Apresenta o problema da LogiTrack:

1. **Contexto Empresarial** (10 min)
   - LogiTrack: 120 caminhões, 3 centros de distribuição
   - Problema: 6% de perdas, falta de rastreabilidade
   - Solução: Projeto Atlas - IoT para monitoramento

2. **Conceitos IoT Fundamentais** (15 min)
   - **Definição:** Rede de objetos físicos conectados
   - **Arquitetura 4 Camadas:** Percepção → Rede → Processamento → Aplicação
   - **Fluxo de Dados:** Sensor → Gateway → Servidor → Dashboard

3. **O Dilema da LogiTrack** (5 min)
   - "E se a conexão cair na estrada?"
   - Robustez vem do desenho, não do improviso
   - Arquitetura define comportamento sob falhas

#### **Fase 2: Atividade Prática - "War Room IoT" (1h 15min)**

### 🏗️ **Atividade: Construindo a Arquitetura IoT da LogiTrack**

#### **Setup da Atividade**
- **5 grupos** já formados
- **Cada grupo** representa uma "equipe técnica" da LogiTrack
- **Material:** Quadros brancos, post-its, canetas, templates de arquitetura

#### **Cronograma Detalhado da Atividade**

| **Tempo** | **Atividade** | **Descrição** | **Entregável** |
|-----------|---------------|---------------|----------------|
| **0-15 min** | **Análise do Problema** | Grupos analisam o caso LogiTrack | Lista de requisitos |
| **15-45 min** | **Desenho da Arquitetura** | Criar diagrama IoT 4 camadas | Diagrama no quadro |
| **45-60 min** | **Apresentação Rápida** | Cada grupo apresenta (3 min) | Pitch da solução |
| **60-75 min** | **Feedback e Refinamento** | Discussão coletiva e melhorias | Arquitetura final |

#### **Instruções Detalhadas para os Grupos**

### 📋 **Roteiro da Atividade**

#### **1. Análise do Problema (15 min)**
**Perguntas para os grupos:**
- Quais dados a LogiTrack precisa coletar?
- Quais sensores são necessários?
- Como garantir conectividade na estrada?
- Onde processar e armazenar os dados?

**Template de Análise:**
```
PROBLEMA: Falta de rastreabilidade da LogiTrack
DADOS NECESSÁRIOS: [Listar]
SENSORES: [Listar]
CONECTIVIDADE: [Definir]
PROCESSAMENTO: [Onde e como]
```

#### **2. Desenho da Arquitetura (30 min)**
**Cada grupo deve criar um diagrama com:**

**Camada 1 - Percepção (Sensores)**
- GPS, Temperatura, Vibração, Umidade
- Localização: Caminhões, cargas, motoristas

**Camada 2 - Rede (Comunicação)**
- 4G/5G para estrada
- WiFi para depósitos
- LoRa para áreas remotas

**Camada 3 - Processamento**
- Edge Computing (local)
- Cloud Computing (central)
- Banco de dados

**Camada 4 - Aplicação**
- Dashboard operacional
- Alertas em tempo real
- Relatórios gerenciais

#### **3. Apresentação Rápida (15 min)**
**Cada grupo tem 3 minutos para:**
- Explicar sua arquitetura
- Justificar escolhas técnicas
- Responder uma pergunta do "CEO"

#### **4. Feedback e Refinamento (15 min)**
**Discussão coletiva:**
- Quais soluções foram mais criativas?
- Como resolver o problema da conectividade?
- Qual arquitetura é mais robusta?

### 🎭 **Dinâmicas Especiais**

#### **Role-Playing**
- **Professor:** CEO Henrique Duarte
- **Alunos:** Equipe técnica da LogiTrack
- **Cenário:** War room com pressão de tempo

#### **Gamificação**
- **Pontos por:** Criatividade, Viabilidade técnica, Robustez
- **Desafio:** "E se a conexão cair?" - Como sua arquitetura resolve?
- **Prêmio:** Melhor arquitetura vira referência da LogiTrack

#### **Storytelling Contínuo**
- **Início:** "A LogiTrack está em crise..."
- **Meio:** "Vocês são a última esperança..."
- **Fim:** "O Projeto Atlas começa aqui..."

### 📊 **Critérios de Avaliação**

| **Critério** | **Peso** | **Descrição** |
|------------|----------|---------------|
| **Completude** | 25% | Todas as 4 camadas presentes |
| **Criatividade** | 25% | Soluções inovadoras para problemas |
| **Viabilidade** | 25% | Solução tecnicamente possível |
| **Robustez** | 25% | Como lidar com falhas e limitações |

### 🎯 **Objetivos de Aprendizagem**

**Ao final da aula, os alunos serão capazes de:**
- ✅ Compreender arquitetura IoT em múltiplas camadas
- ✅ Identificar componentes físicos e lógicos
- ✅ Desenhar diagramas de arquitetura básica
- ✅ Reconhecer decisões que impactam escalabilidade
- ✅ Trabalhar em equipe sob pressão
- ✅ Apresentar soluções técnicas de forma clara

### 🚀 **Fechamento da Aula**

**Professor como "Henrique Duarte":**
*"Excelente trabalho, equipe! Vocês transformaram um problema em uma oportunidade. O Projeto Atlas começa aqui, mas não termina. Nas próximas semanas, vamos descobrir quanto tudo isso vai custar e como implementar. A LogiTrack está nas mãos de vocês!"*

**Juliana Prado (narradora):**
*"Hoje deixamos de falar em problemas isolados e passamos a falar em sistema. O Atlas começa aqui."*

---

## 📚 Conteúdo Teórico

