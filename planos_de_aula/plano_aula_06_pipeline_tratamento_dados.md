# Plano de Aula 06 - Pipeline e Tratamento de Dados

## 📋 Informações Gerais

| **Propriedade** | **Valor** |
|-----------------|-----------|
| **Professor** | Afonso Cesar |
| **Unidade** | Semana 06 |
| **Data** | 18/11/2025 - 10:00h |
| **Duração Total** | 2 horas |
| **Modalidade** | Presencial |
| **Turma** | Computação - IoT |

## 🎯 Objetivos de Aprendizagem

### Objetivos Gerais
- Desenvolver pipelines de dados para IoT
- Implementar processamento e transformação de dados
- Aplicar técnicas de limpeza e validação no Projeto Atlas

### Objetivos Específicos
Ao final desta aula, os alunos serão capazes de:
- Entender conceitos de pipeline de dados
- Implementar ETL para dados IoT
- Aplicar técnicas de limpeza e validação
- Desenvolver estratégias de armazenamento
- Implementar processamento em tempo real e batch

## 📚 Materiais e Recursos

### Materiais de Estudo Obrigatórios (Pré-aula)
| **Material** | **Tipo** | **Duração** | **Objetivo** |
|---------------|----------|-------------|--------------|
| **Conceitos de Pipeline de Dados** | Artigo | 25 min | ETL, streaming, batch processing |
| **Ferramentas de Pipeline IoT** | Tutorial | 30 min | Apache Kafka, Apache Spark |
| **Técnicas de Limpeza de Dados** | Guia | 20 min | Validação, normalização, filtragem |
| **Armazenamento de Dados IoT** | Whitepaper | 25 min | Bancos de dados, data lakes |

### Recursos da Aula
- Apache Kafka (confluent platform)
- Apache Spark (databricks community)
- InfluxDB (banco de dados temporal)
- Jupyter Notebooks
- Dados de exemplo IoT
- Computadores para programação

## ⏰ Cronograma Detalhado

### **Fase 1: Abertura e Contextualização (15 min)**
- **10:00 - 10:15** | Daily inicial e revisão da coleta de dados

### **Fase 2: Conceitos de Pipeline (30 min)**
- **10:15 - 10:45** | ETL, streaming, batch processing

### **Fase 3: Laboratório Kafka (30 min)**
- **10:45 - 11:15** | Implementação de streaming de dados

### **Fase 4: Laboratório Spark (30 min)**
- **11:15 - 11:45** | Processamento e transformação de dados

### **Fase 5: Aplicação LogiTrack (15 min)**
- **11:45 - 12:00** | Pipeline completo para o projeto

## 📖 Conteúdo Programático

### 1. **Contextualização do Pipeline de Dados (15 min)**

#### 1.1 Importância do Pipeline
- **Cenário LogiTrack:** Milhares de dispositivos gerando dados
- **Volume:** Milhões de mensagens por dia
- **Variedade:** GPS, temperatura, vibração, status
- **Velocidade:** Tempo real vs. processamento batch

#### 1.2 Desafios do Pipeline IoT
- **Volume:** Big data em tempo real
- **Variedade:** Diferentes tipos de dados
- **Velocidade:** Processamento em tempo real
- **Qualidade:** Dados incompletos ou incorretos

### 2. **Conceitos de Pipeline (30 min)**

#### 2.1 ETL (Extract, Transform, Load)
1. **Extract (Extrair)**
   - **Fonte:** Dispositivos IoT, APIs, arquivos
   - **Métodos:** Streaming, batch, real-time
   - **Aplicação LogiTrack:** Dados de sensores

2. **Transform (Transformar)**
   - **Limpeza:** Remover dados inválidos
   - **Normalização:** Padronizar formatos
   - **Enriquecimento:** Adicionar contexto
   - **Aplicação LogiTrack:** Processar dados GPS

3. **Load (Carregar)**
   - **Destino:** Bancos de dados, data lakes
   - **Métodos:** Append, upsert, replace
   - **Aplicação LogiTrack:** InfluxDB, PostgreSQL

#### 2.2 Processamento em Tempo Real vs Batch
1. **Streaming (Tempo Real)**
   - **Características:** Baixa latência, alta throughput
   - **Ferramentas:** Apache Kafka, Apache Flink
   - **Aplicação LogiTrack:** Alertas em tempo real

2. **Batch (Lote)**
   - **Características:** Alta latência, processamento completo
   - **Ferramentas:** Apache Spark, Hadoop
   - **Aplicação LogiTrack:** Relatórios diários

#### 2.3 Técnicas de Limpeza de Dados
1. **Validação**
   - **Range checking:** Valores dentro do esperado
   - **Format validation:** Formato correto dos dados
   - **Completeness:** Dados obrigatórios presentes

2. **Normalização**
   - **Unidades:** Padronizar unidades de medida
   - **Formato:** Padronizar formatos de data/hora
   - **Encoding:** Padronizar codificação de caracteres

3. **Filtragem**
   - **Outliers:** Remover valores extremos
   - **Duplicatas:** Remover dados duplicados
   - **Ruído:** Filtrar ruído dos sensores

### 3. **Laboratório Apache Kafka (30 min)**

#### 3.1 Configuração do Kafka (10 min)
- **Objetivo:** Configurar cluster Kafka
- **Atividade:** Instalar e configurar Kafka
- **Comandos:**
```bash
# Download Kafka
wget https://downloads.apache.org/kafka/2.8.0/kafka_2.13-2.8.0.tgz
tar -xzf kafka_2.13-2.8.0.tgz

# Iniciar Zookeeper
bin/zookeeper-server-start.sh config/zookeeper.properties

# Iniciar Kafka
bin/kafka-server-start.sh config/server.properties
```

#### 3.2 Producer (10 min)
- **Objetivo:** Implementar producer para enviar dados
- **Atividade:** Programar producer em Python
- **Código exemplo:**
```python
from kafka import KafkaProducer
import json
import time

producer = KafkaProducer(
    bootstrap_servers=['localhost:9092'],
    value_serializer=lambda x: json.dumps(x).encode('utf-8')
)

def send_sensor_data():
    data = {
        'timestamp': int(time.time()),
        'device_id': 'truck_001',
        'temperature': 25.5,
        'humidity': 60,
        'gps': {'lat': 40.7128, 'lon': -74.0060}
    }
    producer.send('logitrack-sensor-data', value=data)
    producer.flush()

while True:
    send_sensor_data()
    time.sleep(5)
```

#### 3.3 Consumer (10 min)
- **Objetivo:** Implementar consumer para receber dados
- **Atividade:** Programar consumer em Python
- **Código exemplo:**
```python
from kafka import KafkaConsumer
import json

consumer = KafkaConsumer(
    'logitrack-sensor-data',
    bootstrap_servers=['localhost:9092'],
    value_deserializer=lambda m: json.loads(m.decode('utf-8'))
)

for message in consumer:
    data = message.value
    print(f"Received: {data}")
    
    # Processar dados
    process_sensor_data(data)
```

### 4. **Laboratório Apache Spark (30 min)**

#### 4.1 Configuração do Spark (10 min)
- **Objetivo:** Configurar ambiente Spark
- **Atividade:** Instalar e configurar Spark
- **Comandos:**
```bash
# Download Spark
wget https://archive.apache.org/dist/spark/spark-3.2.0/spark-3.2.0-bin-hadoop3.2.tgz
tar -xzf spark-3.2.0-bin-hadoop3.2.tgz

# Iniciar Spark
./bin/spark-shell
```

#### 4.2 Processamento de Dados (10 min)
- **Objetivo:** Implementar processamento com Spark
- **Atividade:** Programar transformações de dados
- **Código exemplo:**
```python
from pyspark.sql import SparkSession
from pyspark.sql.functions import *

spark = SparkSession.builder.appName("LogiTrackDataProcessing").getOrCreate()

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
    .filter(col("temperature") > 0) \
    .withColumn("timestamp", current_timestamp())

# Escrever para InfluxDB
query = processed_df \
    .writeStream \
    .outputMode("append") \
    .format("console") \
    .start()
```

#### 4.3 Armazenamento (10 min)
- **Objetivo:** Armazenar dados processados
- **Atividade:** Configurar InfluxDB
- **Código exemplo:**
```python
# Configurar InfluxDB
from influxdb import InfluxDBClient

client = InfluxDBClient(host='localhost', port=8086)
client.create_database('logitrack')

# Escrever dados
json_body = [{
    "measurement": "sensor_data",
    "tags": {
        "device_id": "truck_001"
    },
    "fields": {
        "temperature": 25.5,
        "humidity": 60
    },
    "time": "2023-01-01T00:00:00Z"
}]

client.write_points(json_body)
```

### 5. **Aplicação LogiTrack (15 min)**

#### 5.1 Arquitetura do Pipeline (5 min)
- **Objetivo:** Definir arquitetura completa
- **Atividade:** Grupos desenham arquitetura
- **Componentes:** Kafka, Spark, InfluxDB, dashboards

#### 5.2 Implementação (5 min)
- **Objetivo:** Implementar pipeline completo
- **Atividade:** Grupos implementam componentes
- **Resultado:** Pipeline funcionando

#### 5.3 Monitoramento (5 min)
- **Objetivo:** Configurar monitoramento
- **Atividade:** Implementar métricas e alertas
- **Resultado:** Sistema monitorado

## 🎭 Metodologia Pedagógica

### **Laboratório Prático**
- **Hands-on:** Implementação real de pipelines
- **Aprendizagem ativa:** Descoberta através da prática
- **Experimentação:** Testes com diferentes cenários
- **Aplicação:** Implementação em projeto real

### **Aprendizagem Baseada em Projetos**
- **Projeto real:** Pipeline para LogiTrack
- **Investigação:** Análise de requisitos e soluções
- **Implementação:** Desenvolvimento de soluções
- **Avaliação:** Testes e validação

### **Discussão Colaborativa**
- **Trabalho em equipe:** Análise conjunta de arquiteturas
- **Debate:** Comparação de ferramentas
- **Consenso:** Decisões baseadas em evidências
- **Aplicação:** Soluções para o projeto

## 📊 Avaliação e Acompanhamento

### **Avaliação Formativa**
- **Participação no laboratório:** 40%
- **Implementação técnica:** 30%
- **Arquitetura do pipeline:** 30%

### **Critérios de Avaliação**
- **Compreensão técnica:** Conhecimento de pipelines
- **Implementação prática:** Capacidade de programar
- **Análise crítica:** Arquitetura de soluções
- **Colaboração:** Trabalho em equipe eficaz

### **Feedback Imediato**
- **Durante o laboratório:** Orientação técnica
- **Na implementação:** Comentários sobre código
- **Fechamento:** Síntese dos aprendizados

## 🚀 Próximos Passos

### **Para a Próxima Aula**
- **Tema:** Introdução ao Metabase
- **Preparação:** Pesquisar ferramentas de visualização
- **Objetivo:** Criar dashboards para LogiTrack

### **Projeto Atlas**
- **Status:** Pipeline de dados implementado
- **Próximo passo:** Criação de dashboards
- **Deliverables:** Pipeline funcionando com dados

## 📝 Observações e Adaptações

### **Possíveis Adaptações**
- **Sem ferramentas:** Usar simuladores e emuladores
- **Turma maior:** Rotacionar uso das ferramentas
- **Tempo reduzido:** Focar em implementação essencial

### **Recursos Alternativos**
- **Ambiente online:** Databricks Community, Confluent Cloud
- **Ferramentas limitadas:** Demonstrações em grupo
- **Conexão limitada:** Trabalhar offline

### **Indicadores de Sucesso**
- **Engajamento:** Alunos participam ativamente do laboratório
- **Compreensão:** Conseguem implementar pipelines
- **Aplicação:** Desenvolvem arquiteturas relevantes
- **Colaboração:** Trabalham bem em equipe

## 📚 Referências e Materiais Complementares

### **Para Aprofundamento**
- Livro: "Building Real-Time Data Pipelines"
- Artigo: "Apache Kafka vs Apache Spark"
- Tutorial: "Data Processing with Apache Spark"

### **Para Próxima Aula**
- Preparar pesquisa sobre Metabase
- Revisar dados processados para visualização
- Identificar requisitos de dashboards para LogiTrack

---

**Preparado por:** Afonso Cesar  
**Data de criação:** 18/11/2025  
**Versão:** 1.0  
**Status:** Aprovado para execução
