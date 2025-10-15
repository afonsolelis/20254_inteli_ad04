# Plano de Aula 09 - Integração Completa e Aplicação Prática

## 📋 Informações Gerais

| **Propriedade** | **Valor** |
|-----------------|-----------|
| **Professor** | Afonso Cesar |
| **Unidade** | Semana 10 |
| **Data** | 18/12/2025 - 10:00h |
| **Duração Total** | 2 horas |
| **Modalidade** | Presencial |
| **Turma** | Computação - IoT |

## 🎯 Objetivos de Aprendizagem

### Objetivos Gerais
- Integrar todos os componentes de uma solução IoT
- Desenvolver aplicação IoT completa
- Aplicar boas práticas de segurança e performance

### Objetivos Específicos
Ao final desta aula, os alunos serão capazes de:
- Integrar arquitetura completa de solução IoT
- Implementar coleta, processamento e visualização
- Aplicar testes e validação da solução
- Documentar e apresentar resultados
- Analisar resultados e insights obtidos

## 📚 Materiais e Recursos

### Materiais de Estudo Obrigatórios (Pré-aula)
| **Material** | **Tipo** | **Duração** | **Objetivo** |
|---------------|----------|-------------|--------------|
| **Arquitetura IoT Completa** | Artigo | 30 min | Integração de todos os componentes |
| **Boas Práticas IoT** | Guia | 25 min | Segurança, performance, escalabilidade |
| **Testes e Validação** | Tutorial | 20 min | Testes de integração, performance |
| **Documentação de Projetos** | Template | 15 min | Estrutura e conteúdo |

### Recursos da Aula
- Hardware IoT completo (sensores, microcontroladores)
- Plataforma de desenvolvimento (Kafka, Spark, Metabase)
- Ferramentas de monitoramento (Grafana, Prometheus)
- Templates de documentação
- Computadores para desenvolvimento

## ⏰ Cronograma Detalhado

### **Fase 1: Abertura e Contextualização (15 min)**
- **10:00 - 10:15** | Daily inicial e revisão de todos os componentes

### **Fase 2: Arquitetura Completa (30 min)**
- **10:15 - 10:45** | Integração de todos os componentes

### **Fase 3: Implementação Prática (45 min)**
- **10:45 - 11:30** | Desenvolvimento da aplicação completa

### **Fase 4: Testes e Validação (30 min)**
- **11:30 - 12:00** | Testes, documentação e apresentação

## 📖 Conteúdo Programático

### 1. **Contextualização da Integração (15 min)**

#### 1.1 Projeto Atlas Completo
- **Cenário LogiTrack:** Solução IoT completa
- **Componentes:** Sensores, comunicação, processamento, visualização
- **Desafios:** Integração, performance, escalabilidade
- **Objetivo:** Sistema funcionando end-to-end

#### 1.2 Arquitetura Final
- **Camada 1:** Sensores (GPS, temperatura, vibração)
- **Camada 2:** Comunicação (4G/5G, WiFi, LoRa)
- **Camada 3:** Processamento (Kafka, Spark, InfluxDB)
- **Camada 4:** Aplicação (Metabase, alertas, APIs)

### 2. **Arquitetura Completa (30 min)**

#### 2.1 Integração de Componentes
1. **Sensores → Comunicação**
   - **GPS:** Localização em tempo real
   - **Temperatura:** Monitoramento térmico
   - **Vibração:** Detecção de anomalias
   - **Status:** Estado do veículo

2. **Comunicação → Processamento**
   - **MQTT:** Dados em tempo real
   - **HTTP:** Dados batch
   - **Kafka:** Streaming de dados
   - **Segurança:** Criptografia, autenticação

3. **Processamento → Visualização**
   - **Spark:** Transformação de dados
   - **InfluxDB:** Armazenamento temporal
   - **Metabase:** Dashboards e relatórios
   - **APIs:** Integração com sistemas

#### 2.2 Fluxo de Dados Completo
1. **Coleta**
   - Sensores coletam dados
   - Dados são transmitidos via MQTT/HTTP
   - Dados chegam ao Kafka

2. **Processamento**
   - Kafka distribui dados
   - Spark processa e transforma
   - InfluxDB armazena dados

3. **Visualização**
   - Metabase consulta dados
   - Dashboards são atualizados
   - Alertas são disparados

### 3. **Implementação Prática (45 min)**

#### 3.1 Configuração do Ambiente (15 min)
- **Objetivo:** Preparar ambiente completo
- **Atividade:** Configurar todos os componentes
- **Componentes:**
  - Kafka cluster
  - Spark cluster
  - InfluxDB
  - Metabase
  - Sensores IoT

#### 3.2 Implementação da Coleta (15 min)
- **Objetivo:** Implementar coleta de dados
- **Atividade:** Programar sensores e transmissão
- **Código exemplo:**
```cpp
// ESP32 - Coleta e transmissão
#include <WiFi.h>
#include <PubSubClient.h>
#include <ArduinoJson.h>

void setup() {
  // Configurar WiFi
  WiFi.begin(ssid, password);
  
  // Configurar MQTT
  client.setServer(mqtt_server, 1883);
  client.setCallback(callback);
}

void loop() {
  // Coletar dados dos sensores
  float temperature = readTemperature();
  float humidity = readHumidity();
  String gps = readGPS();
  
  // Criar payload JSON
  DynamicJsonDocument doc(1024);
  doc["timestamp"] = millis();
  doc["device_id"] = "truck_001";
  doc["temperature"] = temperature;
  doc["humidity"] = humidity;
  doc["gps"] = gps;
  
  // Enviar via MQTT
  String payload;
  serializeJson(doc, payload);
  client.publish("logitrack/sensor/data", payload.c_str());
  
  delay(5000);
}
```

#### 3.3 Implementação do Processamento (15 min)
- **Objetivo:** Implementar pipeline de dados
- **Atividade:** Programar processamento com Spark
- **Código exemplo:**
```python
from pyspark.sql import SparkSession
from pyspark.sql.functions import *

# Configurar Spark
spark = SparkSession.builder.appName("LogiTrackProcessing").getOrCreate()

# Ler dados do Kafka
df = spark \
    .readStream \
    .format("kafka") \
    .option("kafka.bootstrap.servers", "localhost:9092") \
    .option("subscribe", "logitrack-sensor-data") \
    .load()

# Processar dados
processed_df = df \
    .select(from_json(col("value").cast("string"), schema).alias("data")) \
    .select("data.*") \
    .filter(col("temperature").isNotNull()) \
    .withColumn("timestamp", current_timestamp()) \
    .withColumn("alert", when(col("temperature") > 30, "HIGH_TEMP").otherwise("NORMAL"))

# Escrever para InfluxDB
query = processed_df \
    .writeStream \
    .outputMode("append") \
    .format("console") \
    .start()

query.awaitTermination()
```

### 4. **Testes e Validação (30 min)**

#### 4.1 Testes de Integração (10 min)
- **Objetivo:** Validar integração completa
- **Atividade:** Testar fluxo end-to-end
- **Testes:**
  - Dados dos sensores chegam ao Kafka
  - Spark processa dados corretamente
  - InfluxDB armazena dados
  - Metabase exibe dados

#### 4.2 Testes de Performance (10 min)
- **Objetivo:** Validar performance do sistema
- **Atividade:** Testar com volume de dados
- **Métricas:**
  - Latência de processamento
  - Throughput de dados
  - Uso de recursos
  - Tempo de resposta

#### 4.3 Documentação e Apresentação (10 min)
- **Objetivo:** Documentar e apresentar solução
- **Atividade:** Criar documentação e apresentar
- **Conteúdo:**
  - Arquitetura da solução
  - Componentes implementados
  - Resultados obtidos
  - Insights e melhorias

## 🎭 Metodologia Pedagógica

### **Projeto Final Integrado**
- **Hands-on:** Implementação completa da solução
- **Aprendizagem ativa:** Descoberta através da prática
- **Integração:** Conectar todos os componentes
- **Aplicação:** Solução real funcionando

### **Aprendizagem Baseada em Projetos**
- **Projeto real:** Solução completa para LogiTrack
- **Investigação:** Análise de requisitos e soluções
- **Implementação:** Desenvolvimento de solução
- **Avaliação:** Testes e validação

### **Apresentação e Colaboração**
- **Trabalho em equipe:** Desenvolvimento conjunto
- **Apresentação:** Demonstração da solução
- **Debate:** Discussão de resultados
- **Aplicação:** Solução para o projeto

## 📊 Avaliação e Acompanhamento

### **Avaliação Formativa**
- **Implementação técnica:** 40%
- **Integração de componentes:** 30%
- **Apresentação e documentação:** 30%

### **Critérios de Avaliação**
- **Compreensão técnica:** Conhecimento de todos os componentes
- **Implementação prática:** Capacidade de integrar solução
- **Análise crítica:** Identificação de problemas e soluções
- **Colaboração:** Trabalho em equipe eficaz

### **Feedback Imediato**
- **Durante a implementação:** Orientação técnica
- **Nos testes:** Comentários sobre performance
- **Fechamento:** Síntese dos aprendizados

## 🚀 Próximos Passos

### **Para o Projeto Atlas**
- **Status:** Solução completa implementada
- **Próximo passo:** Deploy em produção
- **Entregas:** Sistema funcionando end-to-end

### **Para o Curso**
- **Status:** Curso concluído
- **Próximo passo:** Aplicação em projetos reais
- **Entregas:** Conhecimento aplicado

## 📝 Observações e Adaptações

### **Possíveis Adaptações**
- **Sem hardware:** Usar simuladores e emuladores
- **Turma maior:** Rotacionar uso dos recursos
- **Tempo reduzido:** Focar em integração essencial

### **Recursos Alternativos**
- **Ambiente online:** Cloud platforms
- **Hardware limitado:** Simulações
- **Conexão limitada:** Trabalhar offline

### **Indicadores de Sucesso**
- **Engajamento:** Alunos participam ativamente
- **Compreensão:** Conseguem integrar solução completa
- **Aplicação:** Desenvolvem solução funcional
- **Colaboração:** Trabalham bem em equipe

## 📚 Referências e Materiais Complementares

### **Para Aprofundamento**
- Livro: "IoT Architecture Patterns"
- Artigo: "Building Production IoT Systems"
- Tutorial: "IoT Deployment Best Practices"

### **Para Aplicação**
- Preparar para deploy em produção
- Revisar solução para melhorias
- Identificar oportunidades de otimização

---

**Preparado por:** Afonso Cesar  
**Data de criação:** 18/12/2025  
**Versão:** 1.0  
**Status:** Aprovado para execução
