# Plano de Aula 08 - Dashboards Avançados no Metabase

## 📋 Informações Gerais

| **Propriedade** | **Valor** |
|-----------------|-----------|
| **Professor** | Afonso Cesar |
| **Unidade** | Semana 08 |
| **Data** | 01/12/2025 - 10:00h |
| **Duração Total** | 2 horas |
| **Modalidade** | Presencial |
| **Turma** | Computação - IoT |

## 🎯 Objetivos de Aprendizagem

### Objetivos Gerais
- Desenvolver dashboards avançados e interativos
- Implementar visualizações complexas
- Integrar dashboards com sistemas IoT

### Objetivos Específicos
Ao final desta aula, os alunos serão capazes de:
- Criar dashboards interativos e dinâmicos
- Implementar visualizações avançadas
- Configurar alertas e notificações
- Integrar com APIs e webhooks
- Otimizar performance e usabilidade

## 📚 Materiais e Recursos

### Materiais de Estudo Obrigatórios (Pré-aula)
| **Material** | **Tipo** | **Duração** | **Objetivo** |
|---------------|----------|-------------|--------------|
| **Dashboards Interativos** | Tutorial | 30 min | Filtros, parâmetros, drill-down |
| **Visualizações Avançadas** | Guia | 25 min | Heatmaps, treemaps, funnels |
| **Alertas e Notificações** | Documentação | 20 min | Configuração de alertas |
| **Integração com APIs** | Tutorial | 25 min | Webhooks, APIs externas |

### Recursos da Aula
- Metabase com dados IoT reais
- APIs de integração (REST, GraphQL)
- Templates de dashboards avançados
- Computadores para desenvolvimento
- Projetor para demonstrações

## ⏰ Cronograma Detalhado

### **Fase 1: Abertura e Contextualização (15 min)**
- **10:00 - 10:15** | Daily inicial e revisão dos dashboards básicos

### **Fase 2: Dashboards Interativos (30 min)**
- **10:15 - 10:45** | Filtros, parâmetros e drill-down

### **Fase 3: Visualizações Avançadas (30 min)**
- **10:45 - 11:15** | Heatmaps, treemaps, funnels

### **Fase 4: Alertas e Integração (30 min)**
- **11:15 - 11:45** | Configuração de alertas e APIs

### **Fase 5: Aplicação LogiTrack (15 min)**
- **11:45 - 12:00** | Dashboard avançado para o projeto

## 📖 Conteúdo Programático

### 1. **Contextualização dos Dashboards Avançados (15 min)**

#### 1.1 Necessidades Avançadas
- **Cenário LogiTrack:** Operações complexas de transporte
- **Usuários:** Operadores, gerentes, executivos
- **Requisitos:** Interatividade, alertas, integração
- **Desafios:** Performance, usabilidade, escalabilidade

#### 1.2 Benefícios dos Dashboards Avançados
- **Interatividade:** Exploração de dados
- **Automação:** Alertas e notificações
- **Integração:** Sistemas externos
- **Performance:** Otimização de consultas

### 2. **Dashboards Interativos (30 min)**

#### 2.1 Filtros e Parâmetros
1. **Filtros Globais**
   - **Função:** Aplicar a todo o dashboard
   - **Tipos:** Data, texto, numérico, categórico
   - **Aplicação LogiTrack:** Filtrar por período, caminhão, rota

2. **Parâmetros de Consulta**
   - **Função:** Personalizar consultas
   - **Tipos:** Variáveis, condições
   - **Aplicação LogiTrack:** Parâmetros dinâmicos

3. **Drill-down**
   - **Função:** Navegar entre níveis de detalhe
   - **Implementação:** Links entre visualizações
   - **Aplicação LogiTrack:** Caminhão → Viagem → Detalhes

#### 2.2 Interatividade Avançada
1. **Ações Personalizadas**
   - **Função:** Executar ações customizadas
   - **Tipos:** URLs, scripts, integrações
   - **Aplicação LogiTrack:** Abrir sistema de rastreamento

2. **Compartilhamento**
   - **Função:** Compartilhar dashboards
   - **Tipos:** Público, privado, por email
   - **Aplicação LogiTrack:** Relatórios automáticos

### 3. **Visualizações Avançadas (30 min)**

#### 3.1 Heatmaps
1. **Mapas de Calor**
   - **Função:** Visualizar densidade de dados
   - **Aplicação LogiTrack:** Densidade de rotas
   - **Implementação:** Coordenadas geográficas

2. **Matriz de Correlação**
   - **Função:** Correlações entre variáveis
   - **Aplicação LogiTrack:** Correlação temperatura vs. consumo
   - **Implementação:** Dados numéricos

#### 3.2 Treemaps
1. **Hierarquia de Dados**
   - **Função:** Visualizar hierarquias
   - **Aplicação LogiTrack:** Caminhões → Rotas → Viagens
   - **Implementação:** Dados hierárquicos

2. **Proporções**
   - **Função:** Comparar proporções
   - **Aplicação LogiTrack:** Distribuição de carga
   - **Implementação:** Dados categóricos

#### 3.3 Funnels
1. **Funil de Conversão**
   - **Função:** Visualizar processo
   - **Aplicação LogiTrack:** Processo de entrega
   - **Implementação:** Etapas sequenciais

2. **Análise de Abandono**
   - **Função:** Identificar pontos de perda
   - **Aplicação LogiTrack:** Abandono de rotas
   - **Implementação:** Dados de processo

### 4. **Alertas e Integração (30 min)**

#### 4.1 Configuração de Alertas (15 min)
- **Objetivo:** Configurar alertas automáticos
- **Atividade:** Criar alertas baseados em métricas
- **Tipos:**
  - **Threshold:** Valores acima/abaixo do limite
  - **Anomaly:** Detecção de anomalias
  - **Schedule:** Alertas programados

- **Implementação:**
```sql
-- Alerta de temperatura alta
SELECT device_id, temperature, timestamp
FROM sensor_data
WHERE temperature > 30
AND timestamp > NOW() - INTERVAL '1 hour'
```

#### 4.2 Integração com APIs (15 min)
- **Objetivo:** Integrar com sistemas externos
- **Atividade:** Configurar webhooks e APIs
- **Tipos:**
  - **Webhooks:** Notificações em tempo real
  - **APIs REST:** Integração com sistemas
  - **GraphQL:** Consultas flexíveis

- **Implementação:**
```python
# Webhook para alertas
import requests

def send_alert(data):
    webhook_url = "https://hooks.slack.com/services/..."
    payload = {
        "text": f"Alerta LogiTrack: {data['message']}",
        "channel": "#logitrack-alerts"
    }
    requests.post(webhook_url, json=payload)
```

### 5. **Aplicação LogiTrack (15 min)**

#### 5.1 Requisitos Avançados (5 min)
- **Objetivo:** Definir necessidades avançadas
- **Atividade:** Grupos analisam requisitos
- **Componentes:**
  - Dashboard executivo
  - Monitoramento operacional
  - Alertas de emergência
  - Integração com sistemas

#### 5.2 Implementação (5 min)
- **Objetivo:** Criar dashboard avançado
- **Atividade:** Grupos implementam componentes
- **Resultado:** Dashboard avançado funcionando

#### 5.3 Apresentação (5 min)
- **Objetivo:** Apresentar dashboards avançados
- **Atividade:** Grupos apresentam resultados
- **Avaliação:** Funcionalidade e inovação

## 🎭 Metodologia Pedagógica

### **Laboratório Prático**
- **Hands-on:** Criação real de dashboards avançados
- **Aprendizagem ativa:** Descoberta através da prática
- **Experimentação:** Testes com diferentes recursos
- **Aplicação:** Implementação em projeto real

### **Aprendizagem Baseada em Projetos**
- **Projeto real:** Dashboard avançado para LogiTrack
- **Investigação:** Análise de requisitos avançados
- **Implementação:** Desenvolvimento de soluções
- **Avaliação:** Testes e validação

### **Discussão Colaborativa**
- **Trabalho em equipe:** Análise conjunta de requisitos
- **Debate:** Comparação de soluções
- **Consenso:** Decisões baseadas em funcionalidade
- **Aplicação:** Soluções para o projeto

## 📊 Avaliação e Acompanhamento

### **Avaliação Formativa**
- **Participação no laboratório:** 40%
- **Implementação técnica:** 30%
- **Inovação e criatividade:** 30%

### **Critérios de Avaliação**
- **Compreensão técnica:** Conhecimento de recursos avançados
- **Implementação prática:** Capacidade de criar dashboards complexos
- **Análise crítica:** Usabilidade e funcionalidade
- **Colaboração:** Trabalho em equipe eficaz

### **Feedback Imediato**
- **Durante o laboratório:** Orientação técnica
- **Na implementação:** Comentários sobre design
- **Fechamento:** Síntese dos aprendizados

## 🚀 Próximos Passos

### **Para a Próxima Aula**
- **Tema:** Integração Completa e Aplicação Prática
- **Preparação:** Revisar todos os componentes
- **Objetivo:** Integrar solução completa

### **Projeto Atlas**
- **Status:** Dashboards avançados criados
- **Próximo passo:** Integração completa
- **Entregas:** Dashboard avançado funcionando

## 📝 Observações e Adaptações

### **Possíveis Adaptações**
- **Sem recursos avançados:** Usar funcionalidades básicas
- **Turma maior:** Rotacionar acesso ao sistema
- **Tempo reduzido:** Focar em funcionalidades essenciais

### **Recursos Alternativos**
- **Ambiente online:** Metabase Cloud
- **Dados limitados:** Usar datasets de exemplo
- **Conexão limitada:** Trabalhar offline

### **Indicadores de Sucesso**
- **Engajamento:** Alunos participam ativamente do laboratório
- **Compreensão:** Conseguem criar dashboards avançados
- **Aplicação:** Desenvolvem soluções inovadoras
- **Colaboração:** Trabalham bem em equipe

## 📚 Referências e Materiais Complementares

### **Para Aprofundamento**
- Livro: "Advanced Metabase Techniques"
- Artigo: "Creating Interactive Dashboards"
- Tutorial: "Metabase API Integration"

### **Para Próxima Aula**
- Preparar revisão de todos os componentes
- Revisar dashboard avançado para integração
- Identificar requisitos de integração completa

---

**Preparado por:** Afonso Cesar  
**Data de criação:** 01/12/2025  
**Versão:** 1.0  
**Status:** Aprovado para execução
