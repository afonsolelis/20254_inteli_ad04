# Plano de Aula 07 - Introdução ao Metabase e Criação de Dashboards

## 📋 Informações Gerais

| **Propriedade** | **Valor** |
|-----------------|-----------|
| **Professor** | Afonso Cesar |
| **Unidade** | Semana 07 |
| **Data** | 28/11/2025 - 10:00h |
| **Duração Total** | 2 horas |
| **Modalidade** | Presencial |
| **Turma** | Computação - IoT |

## 🎯 Objetivos de Aprendizagem

### Objetivos Gerais
- Introduzir a plataforma Metabase para visualização de dados
- Configurar conexões com bancos de dados IoT
- Criar dashboards básicos para LogiTrack

### Objetivos Específicos
Ao final desta aula, os alunos serão capazes de:
- Configurar conexões com bancos de dados
- Criar consultas (queries) no Metabase
- Desenvolver dashboards básicos
- Implementar visualizações de dados IoT
- Aplicar filtros e interatividade

## 📚 Materiais e Recursos

### Materiais de Estudo Obrigatórios (Pré-aula)
| **Material** | **Tipo** | **Duração** | **Objetivo** |
|---------------|----------|-------------|--------------|
| **Introdução ao Metabase** | Tutorial | 30 min | Plataforma e funcionalidades |
| **Conexões com Bancos de Dados** | Guia | 25 min | PostgreSQL, MySQL, InfluxDB |
| **Criação de Consultas** | Tutorial | 25 min | SQL, visualizações |
| **Dashboards Básicos** | Exemplo | 20 min | Layout, componentes |

### Recursos da Aula
- Instância do Metabase (Docker)
- Banco de dados com dados IoT (InfluxDB)
- Dados de exemplo LogiTrack
- Computadores para acesso ao Metabase
- Projetor para demonstrações

## ⏰ Cronograma Detalhado

### **Fase 1: Abertura e Contextualização (15 min)**
- **10:00 - 10:15** | Daily inicial e revisão do pipeline de dados

### **Fase 2: Introdução ao Metabase (30 min)**
- **10:15 - 10:45** | Plataforma, interface e funcionalidades

### **Fase 3: Configuração de Conexões (30 min)**
- **10:45 - 11:15** | Conexão com bancos de dados IoT

### **Fase 4: Criação de Dashboards (30 min)**
- **11:15 - 11:45** | Desenvolvimento de dashboards básicos

### **Fase 5: Aplicação LogiTrack (15 min)**
- **11:45 - 12:00** | Dashboard para o projeto

## 📖 Conteúdo Programático

### 1. **Contextualização da Visualização (15 min)**

#### 1.1 Importância da Visualização
- **Cenário LogiTrack:** Dados complexos de transporte
- **Usuários:** Operadores, gerentes, executivos
- **Necessidades:** Monitoramento em tempo real, relatórios
- **Desafios:** Volume de dados, diferentes perspectivas

#### 1.2 Benefícios do Metabase
- **Simplicidade:** Interface intuitiva
- **Flexibilidade:** Múltiplas fontes de dados
- **Colaboração:** Compartilhamento de dashboards
- **Open Source:** Sem custos de licença

### 2. **Introdução ao Metabase (30 min)**

#### 2.1 Plataforma Metabase
1. **Características**
   - **Open Source:** Código aberto
   - **Multi-database:** Suporte a múltiplos bancos
   - **Self-hosted:** Instalação própria
   - **Cloud:** Versão hospedada

2. **Interface Principal**
   - **Home:** Dashboards e consultas recentes
   - **Browse Data:** Navegação pelos dados
   - **Ask Question:** Criação de consultas
   - **Admin:** Configurações e usuários

3. **Funcionalidades**
   - **Consultas:** SQL e interface visual
   - **Dashboards:** Agrupamento de visualizações
   - **Alerts:** Notificações automáticas
   - **Pulses:** Relatórios por email

#### 2.2 Tipos de Visualizações
1. **Gráficos**
   - **Linha:** Séries temporais
   - **Barras:** Comparações
   - **Pizza:** Proporções
   - **Área:** Acumulação

2. **Tabelas**
   - **Dados tabulares:** Listas detalhadas
   - **Métricas:** Números importantes
   - **KPIs:** Indicadores-chave

3. **Mapas**
   - **Geográficos:** Localização
   - **Heatmaps:** Densidade
   - **Trajetos:** Rotas

### 3. **Configuração de Conexões (30 min)**

#### 3.1 Conexão com InfluxDB (15 min)
- **Objetivo:** Conectar Metabase ao InfluxDB
- **Atividade:** Configurar conexão
- **Passos:**
  1. Acessar Admin > Databases
  2. Adicionar nova conexão
  3. Selecionar InfluxDB
  4. Configurar parâmetros:
     - Host: localhost
     - Port: 8086
     - Database: logitrack
     - Username/Password

#### 3.2 Conexão com PostgreSQL (15 min)
- **Objetivo:** Conectar Metabase ao PostgreSQL
- **Atividade:** Configurar conexão
- **Passos:**
  1. Adicionar nova conexão
  2. Selecionar PostgreSQL
  3. Configurar parâmetros:
     - Host: localhost
     - Port: 5432
     - Database: logitrack
     - Username/Password

### 4. **Criação de Dashboards (30 min)**

#### 4.1 Consultas Básicas (10 min)
- **Objetivo:** Criar consultas simples
- **Atividade:** Usar interface visual
- **Exemplos:**
  - Temperatura média por caminhão
  - Número de viagens por dia
  - Distância percorrida por rota

#### 4.2 Visualizações (10 min)
- **Objetivo:** Criar gráficos e tabelas
- **Atividade:** Configurar visualizações
- **Tipos:**
  - Gráfico de linha para temperatura
  - Tabela de status dos caminhões
  - Mapa de localizações

#### 4.3 Dashboard (10 min)
- **Objetivo:** Agrupar visualizações
- **Atividade:** Criar dashboard
- **Componentes:**
  - Layout responsivo
  - Filtros globais
  - Títulos e descrições

### 5. **Aplicação LogiTrack (15 min)**

#### 5.1 Requisitos do Dashboard (5 min)
- **Objetivo:** Definir necessidades da LogiTrack
- **Atividade:** Grupos analisam requisitos
- **Componentes:**
  - Monitoramento em tempo real
  - Alertas de temperatura
  - Rastreamento de rotas
  - Métricas de performance

#### 5.2 Implementação (5 min)
- **Objetivo:** Criar dashboard LogiTrack
- **Atividade:** Grupos implementam componentes
- **Resultado:** Dashboard funcionando

#### 5.3 Apresentação (5 min)
- **Objetivo:** Apresentar dashboards
- **Atividade:** Grupos apresentam resultados
- **Avaliação:** Funcionalidade e usabilidade

## 🎭 Metodologia Pedagógica

### **Laboratório Prático**
- **Hands-on:** Criação real de dashboards
- **Aprendizagem ativa:** Descoberta através da prática
- **Experimentação:** Testes com diferentes visualizações
- **Aplicação:** Implementação em projeto real

### **Aprendizagem Baseada em Projetos**
- **Projeto real:** Dashboard para LogiTrack
- **Investigação:** Análise de requisitos
- **Implementação:** Desenvolvimento de soluções
- **Avaliação:** Testes e validação

### **Discussão Colaborativa**
- **Trabalho em equipe:** Análise conjunta de requisitos
- **Debate:** Comparação de visualizações
- **Consenso:** Decisões baseadas em usabilidade
- **Aplicação:** Soluções para o projeto

## 📊 Avaliação e Acompanhamento

### **Avaliação Formativa**
- **Participação no laboratório:** 40%
- **Implementação técnica:** 30%
- **Qualidade do dashboard:** 30%

### **Critérios de Avaliação**
- **Compreensão técnica:** Conhecimento do Metabase
- **Implementação prática:** Capacidade de criar dashboards
- **Análise crítica:** Usabilidade e funcionalidade
- **Colaboração:** Trabalho em equipe eficaz

### **Feedback Imediato**
- **Durante o laboratório:** Orientação técnica
- **Na implementação:** Comentários sobre design
- **Fechamento:** Síntese dos aprendizados

## 🚀 Próximos Passos

### **Para a Próxima Aula**
- **Tema:** Dashboards Avançados no Metabase
- **Preparação:** Pesquisar recursos avançados
- **Objetivo:** Desenvolver dashboards complexos

### **Projeto Atlas**
- **Status:** Dashboard básico criado
- **Próximo passo:** Dashboards avançados
- **Deliverables:** Dashboard funcionando com dados

## 📝 Observações e Adaptações

### **Possíveis Adaptações**
- **Sem Metabase:** Usar versão online ou demo
- **Turma maior:** Rotacionar acesso ao sistema
- **Tempo reduzido:** Focar em funcionalidades essenciais

### **Recursos Alternativos**
- **Ambiente online:** Metabase Cloud
- **Dados limitados:** Usar datasets de exemplo
- **Conexão limitada:** Trabalhar offline

### **Indicadores de Sucesso**
- **Engajamento:** Alunos participam ativamente do laboratório
- **Compreensão:** Conseguem criar dashboards
- **Aplicação:** Desenvolvem soluções relevantes
- **Colaboração:** Trabalham bem em equipe

## 📚 Referências e Materiais Complementares

### **Para Aprofundamento**
- Livro: "Metabase User Guide"
- Artigo: "Creating Effective Dashboards"
- Tutorial: "Advanced Metabase Features"

### **Para Próxima Aula**
- Preparar pesquisa sobre recursos avançados
- Revisar dashboard básico para melhorias
- Identificar requisitos de dashboards avançados

---

**Preparado por:** Afonso Cesar  
**Data de criação:** 28/11/2025  
**Versão:** 1.0  
**Status:** Aprovado para execução
