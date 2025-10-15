# Plano de Aula 01 - Introdução à IoT e Arquitetura Básica

## 📋 Informações Gerais

| **Propriedade** | **Valor** |
|-----------------|-----------|
| **Professor** | Afonso Cesar |
| **Unidade** | Semana 01 |
| **Data** | 16/10/2025 - 10:00h |
| **Duração Total** | 2 horas |
| **Modalidade** | Presencial |
| **Turma** | Computação - IoT |

## 🎯 Objetivos de Aprendizagem

### Objetivos Gerais
- Apresentar conceitos fundamentais de IoT e arquitetura básica
- Aplicar conceitos no caso LogiTrack para estabelecer base técnica do Projeto Atlas

### Objetivos Específicos
Ao final desta aula, os alunos serão capazes de:
- Compreender os conceitos fundamentais de IoT
- Identificar as 4 camadas da arquitetura IoT
- Desenhar diagramas de arquitetura básica
- Aplicar conceitos em cenários reais
- Trabalhar colaborativamente em equipe

## 📚 Materiais e Recursos

### Materiais de Estudo Obrigatórios (Pré-aula)
| **Material** | **Tipo** | **Link** | **Duração** | **Objetivo** |
|---------------|----------|----------|-------------|--------------|
| **O Despertar da LogiTrack: Introdução à IoT e Arquitetura Básica** | Notion | [Acessar Material](https://cobalt-blarney-8b3.notion.site/O-Despertar-da-LogiTrack-Introdu-o-IoT-e-Arquitetura-B-sica-285256ceaea7801ea9cad5cf8102eb15) | 45 min | Conceitos fundamentais IoT |
| **Internet of Things (IoT) Architecture \| IoT Tutorial for Beginners** | YouTube | [Assistir Vídeo](https://www.youtube.com/watch?v=FRxRT0DjE7A) | 30 min | Arquitetura IoT para iniciantes |
| **Unpacking IoT Architecture: Layers and Components Explained** | Artigo | [Ler Artigo](https://deviceauthority.com/unpacking-iot-architecture-layers-and-components-explained/) | 30 min | Camadas e componentes IoT |
| **Fundamentos Básicos de IoT** | Livro Digital | [Acessar Livro](https://integrada.minhabiblioteca.com.br/reader/books/9786556901947/pageid/28) | 1h | Fundamentos teóricos |

### Recursos da Aula
- Quadro branco ou projetor
- Material para desenho (papel, canetas)
- Cronômetro
- Slides de apresentação
- Template de arquitetura IoT

## ⏰ Cronograma Detalhado

### **Fase 1: Abertura e Contextualização (15 min)**
- **10:00 - 10:15** | Daily inicial e apresentação do cenário LogiTrack

### **Fase 2: Conceitos Fundamentais (30 min)**
- **10:15 - 10:45** | Apresentação dos conceitos de IoT e arquitetura

### **Fase 3: Atividade Prática (60 min)**
- **10:45 - 11:45** | War Room IoT - Construindo a Arquitetura da LogiTrack

### **Fase 4: Discussão e Fechamento (15 min)**
- **11:45 - 12:00** | Discussão coletiva e fechamento

## 📖 Conteúdo Programático

### 1. **Introdução ao Cenário LogiTrack (15 min)**

#### 1.1 Apresentação do Problema
- **Situação:** LogiTrack, transportadora com 120 caminhões
- **Crise:** 6% de perdas anuais, falta de rastreabilidade
- **Desafio:** Transformar caminhões em unidades inteligentes

#### 1.2 Personagens e Stakeholders
- **Marina Costa** (Engenheira de Software)
- **Carlos Menezes** (Gerente de Operações)
- **Juliana Prado** (Analista de Dados)
- **Pedro Nascimento** (Coordenador de TI)

### 2. **Conceitos Fundamentais de IoT (30 min)**

#### 2.1 Definição de IoT
- **Conceito:** Rede de objetos físicos com sensores, software e conectividade
- **Características:** Conectividade, Sensoriamento, Processamento, Automação, Interoperabilidade

#### 2.2 Arquitetura IoT - 4 Camadas
1. **Camada 1: Percepção (Sensores e Atuadores)**
   - Função: Coleta de dados do mundo físico
   - Componentes: GPS, temperatura, vibração, motores, LEDs
   - Exemplo LogiTrack: Sensores nos caminhões

2. **Camada 2: Comunicação (Rede)**
   - Função: Transmissão de dados entre dispositivos
   - Componentes: Gateways, WiFi, Bluetooth, LoRa, 4G/5G
   - Exemplo LogiTrack: 4G/5G para estrada, WiFi para depósitos

3. **Camada 3: Processamento**
   - Função: Análise e transformação de dados
   - Componentes: Edge Computing, Cloud Computing, bancos de dados
   - Exemplo LogiTrack: Processamento local + análise na nuvem

4. **Camada 4: Aplicação**
   - Função: Interface com usuários e tomada de decisões
   - Componentes: Dashboards, APIs, aplicações móveis
   - Exemplo LogiTrack: Dashboard operacional, alertas

#### 2.3 Fluxo de Dados IoT
- **Coleta:** Sensores → Pré-processamento → Transmissão
- **Processamento:** Armazenamento → Análise → Insights
- **Ação:** Decisões → Comandos → Feedback

### 3. **Atividade Prática: War Room IoT (60 min)**

#### 3.1 Organização dos Grupos (5 min)
- Dividir turma em grupos de 4-5 pessoas
- Distribuir material para desenho
- Explicar instruções da atividade

#### 3.2 Análise do Problema (15 min)
- **Objetivo:** Entender o problema da LogiTrack
- **Atividade:** Grupos analisam o cenário e identificam necessidades
- **Resultado:** Lista de requisitos para a solução IoT

#### 3.3 Desenho da Arquitetura (30 min)
- **Objetivo:** Desenhar arquitetura IoT com 4 camadas
- **Template fornecido:**
  ```
  Camada 4 - Aplicação: Dashboard, Alertas, Relatórios
  Camada 3 - Processamento: Edge + Cloud + Database
  Camada 2 - Comunicação: 4G/5G + WiFi + LoRa
  Camada 1 - Percepção: GPS + Temperatura + Vibração
  ```
- **Resultado:** Diagrama de arquitetura por grupo

#### 3.4 Apresentações (10 min)
- **Formato:** 3 minutos por grupo
- **Conteúdo:** Arquitetura proposta e justificativas
- **Avaliação:** Clareza, completude, aplicabilidade

### 4. **Discussão Coletiva (15 min)**

#### 4.1 Conceitos-Chave (10 min)
- **Sensores:** Dispositivos de coleta de dados
- **Atuadores:** Dispositivos de execução de ações
- **Gateways:** Conectores entre sensores e internet
- **Edge Computing:** Processamento próximo aos sensores
- **Dashboards:** Interfaces visuais de monitoramento

#### 4.2 Dilema da Conectividade (5 min)
- **Problema:** "E se a conexão cair na estrada?"
- **Discussão:** Soluções para conectividade intermitente
- **Soluções:** Armazenamento local, sincronização, redundância

## 🎭 Metodologia Pedagógica

### **Storytelling e Gamificação**
- **Narrativa:** LogiTrack em crise, equipe técnica salvando o dia
- **Personagens:** Stakeholders com diferentes perspectivas
- **Drama:** Pressão do CEO, prazo de 90 dias

### **Aprendizagem Ativa**
- **War Room:** Ambiente de alta pressão para tomada de decisões
- **Colaboração:** Trabalho em equipe para resolver problemas reais
- **Aplicação:** Conceitos teóricos aplicados em cenário prático

### **Discussão Socrática**
- **Perguntas-chave:** Estimulam reflexão e debate
- **Múltiplas perspectivas:** Diferentes visões sobre o mesmo problema
- **Descoberta guiada:** Alunos chegam às conclusões através de perguntas

## 📊 Avaliação e Acompanhamento

### **Avaliação Formativa**
- **Participação na atividade prática:** 40%
- **Qualidade da apresentação:** 30%
- **Participação na discussão:** 30%

### **Critérios de Avaliação**
- **Compreensão dos conceitos:** Clareza na explicação dos conceitos IoT
- **Aplicação prática:** Capacidade de aplicar conceitos no cenário LogiTrack
- **Colaboração:** Trabalho em equipe e comunicação
- **Pensamento crítico:** Análise e questionamento das soluções

### **Feedback Imediato**
- **Durante as apresentações:** Comentários sobre clareza e completude
- **Na discussão:** Validação de conceitos e correção de equívocos
- **Fechamento:** Síntese dos aprendizados e próximos passos

## 🚀 Próximos Passos

### **Para a Próxima Aula**
- **Tema:** Precificação e Impactos Econômicos IoT
- **Preparação:** Análise de custos da solução proposta
- **Objetivo:** Entender viabilidade econômica do Projeto Atlas

### **Projeto Atlas**
- **Status:** Iniciado nesta aula
- **Desenvolvimento:** Contínuo ao longo do semestre
- **Entregas:** Incrementais a cada aula

## 📝 Observações e Adaptações

### **Possíveis Adaptações**
- **Turma menor:** Reduzir tempo de apresentações, aumentar discussão
- **Turma maior:** Dividir em mais grupos, usar rotação de apresentações
- **Tempo reduzido:** Focar em conceitos essenciais, reduzir atividade prática

### **Recursos Alternativos**
- **Sem projetor:** Usar quadro branco para desenhos
- **Ambiente online:** Adaptar atividade para ferramentas digitais
- **Material limitado:** Usar papel e caneta para diagramas

### **Indicadores de Sucesso**
- **Engajamento:** Alunos participam ativamente da atividade
- **Compreensão:** Conseguem explicar conceitos IoT
- **Aplicação:** Propõem soluções relevantes para o cenário
- **Colaboração:** Trabalham bem em equipe

## 📚 Referências e Materiais Complementares

### **Para Aprofundamento**
- Livro: "Fundamentos Básicos de IoT" (Biblioteca Digital)
- Artigo: "Unpacking IoT Architecture: Layers and Components Explained"
- Vídeo: "Internet of Things (IoT) Architecture | IoT Tutorial for Beginners"

### **Para Próxima Aula**
- Preparar análise de custos da solução IoT
- Pesquisar tecnologias específicas mencionadas
- Revisar conceitos de arquitetura para aplicação em precificação

---

**Preparado por:** Afonso Cesar  
**Data de criação:** 16/10/2025  
**Versão:** 1.0  
**Status:** Aprovado para execução
