# Plano de Aula 05 - Coleta de Dados MQTT/HTTP

## 📋 Informações Gerais

| **Propriedade** | **Valor** |
|-----------------|-----------|
| **Professor** | Afonso Cesar |
| **Unidade** | Semana 05 |
| **Data** | 11/11/2025 - 10:00h |
| **Duração Total** | 2 horas |
| **Modalidade** | Presencial |
| **Turma** | Computação - IoT |

## 🎯 Objetivos de Aprendizagem

### Objetivos Gerais
- Implementar coleta de dados em sistemas IoT
- Compreender protocolos MQTT e HTTP para IoT
- Aplicar coleta segura de dados no Projeto Atlas

### Objetivos Específicos
Ao final desta aula, os alunos serão capazes de:
- Entender características dos protocolos MQTT e HTTP
- Implementar coleta de dados usando MQTT
- Implementar coleta de dados usando HTTP
- Comparar vantagens e desvantagens de cada protocolo
- Desenvolver sistema de coleta para LogiTrack

## 📚 Materiais e Recursos

### Materiais de Estudo Obrigatórios (Pré-aula)
| **Material** | **Tipo** | **Duração** | **Objetivo** |
|---------------|----------|-------------|--------------|
| **Protocolo MQTT** | Tutorial | 30 min | Message Queuing Telemetry Transport |
| **HTTP para IoT** | Guia | 25 min | HTTP REST APIs para IoT |
| **Brokers MQTT** | Documentação | 20 min | Mosquitto, HiveMQ, AWS IoT |
| **Implementação Prática** | Código | 25 min | Exemplos de clientes e servidores |

### Recursos da Aula
- Broker MQTT (Mosquitto)
- Servidor HTTP (Node.js/Python)
- Sensores IoT (ESP32, Arduino)
- Ferramentas de monitoramento (Wireshark, MQTT Explorer)
- Computadores para programação
- Rede local para testes

## ⏰ Cronograma Detalhado

### **Fase 1: Abertura e Contextualização (15 min)**
- **10:00 - 10:15** | Daily inicial e revisão do plano de segurança

### **Fase 2: Protocolos MQTT e HTTP (30 min)**
- **10:15 - 10:45** | Características e diferenças dos protocolos

### **Fase 3: Laboratório MQTT (30 min)**
- **10:45 - 11:15** | Implementação de coleta via MQTT

### **Fase 4: Laboratório HTTP (30 min)**
- **11:15 - 11:45** | Implementação de coleta via HTTP

### **Fase 5: Comparação e Aplicação (15 min)**
- **11:45 - 12:00** | Análise comparativa e aplicação no projeto

## 📖 Conteúdo Programático

### 1. **Contextualização da Coleta de Dados (15 min)**

#### 1.1 Importância da Coleta
- **Cenário LogiTrack:** Dados críticos de transporte
- **Tipos de dados:** GPS, temperatura, vibração, status
- **Frequência:** Tempo real, batch, sob demanda
- **Volume:** Milhares de dispositivos, milhões de mensagens

#### 1.2 Desafios da Coleta IoT
- **Conectividade:** Dispositivos móveis, áreas remotas
- **Latência:** Tempo real vs. tolerância a atrasos
- **Confiabilidade:** Garantia de entrega, retry
- **Segurança:** Criptografia, autenticação

### 2. **Protocolos MQTT e HTTP (30 min)**

#### 2.1 Protocolo MQTT
1. **Características**
   - **Tipo:** Publish/Subscribe
   - **Transporte:** TCP/IP
   - **QoS:** 0, 1, 2 (Quality of Service)
   - **Retenção:** Mensagens retidas no broker

2. **Vantagens**
   - **Eficiência:** Baixo overhead
   - **Escalabilidade:** Milhares de clientes
   - **Confiabilidade:** QoS garantido
   - **Simplicidade:** Fácil implementação

3. **Desvantagens**
   - **Complexidade:** Broker necessário
   - **Latência:** Dependência do broker
   - **Segurança:** Configuração adicional

#### 2.2 Protocolo HTTP
1. **Características**
   - **Tipo:** Request/Response
   - **Transporte:** TCP/IP
   - **Métodos:** GET, POST, PUT, DELETE
   - **Formato:** JSON, XML, texto

2. **Vantagens**
   - **Simplicidade:** Fácil de entender
   - **Compatibilidade:** Amplo suporte
   - **Debugging:** Ferramentas disponíveis
   - **Caching:** HTTP caching

3. **Desvantagens**
   - **Overhead:** Headers grandes
   - **Latência:** Request/Response
   - **Escalabilidade:** Limitações de conexão

#### 2.3 Comparação MQTT vs HTTP
| **Aspecto** | **MQTT** | **HTTP** |
|-------------|----------|----------|
| **Overhead** | Baixo | Alto |
| **Latência** | Baixa | Média |
| **Escalabilidade** | Alta | Limitada |
| **Simplicidade** | Média | Alta |
| **Caching** | Não | Sim |
| **QoS** | Sim | Não |

### 3. **Laboratório MQTT (30 min)**

#### 3.1 Configuração do Broker (10 min)
- **Objetivo:** Configurar broker MQTT
- **Atividade:** Instalar e configurar Mosquitto
- **Comandos:**
```bash
# Instalar Mosquitto
sudo apt-get install mosquitto mosquitto-clients

# Iniciar broker
mosquitto -v

# Testar conexão
mosquitto_pub -h localhost -t "test/topic" -m "Hello MQTT"
```

#### 3.2 Cliente Publisher (10 min)
- **Objetivo:** Implementar cliente que publica dados
- **Atividade:** Programar ESP32 para publicar dados de sensores
- **Código exemplo:**
```cpp
#include <WiFi.h>
#include <PubSubClient.h>

const char* ssid = "LogiTrack_WiFi";
const char* password = "password123";
const char* mqtt_server = "broker.hivemq.com";

WiFiClient espClient;
PubSubClient client(espClient);

void setup() {
  client.setServer(mqtt_server, 1883);
  client.setCallback(callback);
}

void loop() {
  if (!client.connected()) {
    reconnect();
  }
  client.loop();
  
  // Publicar dados do sensor
  String payload = "{\"temperature\":25.5,\"humidity\":60}";
  client.publish("logitrack/sensor/data", payload.c_str());
  delay(5000);
}
```

#### 3.3 Cliente Subscriber (10 min)
- **Objetivo:** Implementar cliente que recebe dados
- **Atividade:** Programar cliente para receber e processar dados
- **Código exemplo:**
```python
import paho.mqtt.client as mqtt
import json

def on_connect(client, userdata, flags, rc):
    print("Connected with result code "+str(rc))
    client.subscribe("logitrack/sensor/data")

def on_message(client, userdata, msg):
    data = json.loads(msg.payload.decode())
    print(f"Temperature: {data['temperature']}°C")
    print(f"Humidity: {data['humidity']}%")

client = mqtt.Client()
client.on_connect = on_connect
client.on_message = on_message
client.connect("broker.hivemq.com", 1883, 60)
client.loop_forever()
```

### 4. **Laboratório HTTP (30 min)**

#### 4.1 Servidor HTTP (10 min)
- **Objetivo:** Implementar servidor HTTP para receber dados
- **Atividade:** Criar API REST com Node.js
- **Código exemplo:**
```javascript
const express = require('express');
const app = express();
app.use(express.json());

app.post('/api/sensor/data', (req, res) => {
    const { temperature, humidity, gps } = req.body;
    console.log(`Received: ${temperature}°C, ${humidity}%, ${gps}`);
    
    // Processar dados
    processSensorData({ temperature, humidity, gps });
    
    res.json({ status: 'success', message: 'Data received' });
});

app.listen(3000, () => {
    console.log('Server running on port 3000');
});
```

#### 4.2 Cliente HTTP (10 min)
- **Objetivo:** Implementar cliente HTTP para enviar dados
- **Atividade:** Programar ESP32 para enviar dados via HTTP
- **Código exemplo:**
```cpp
#include <WiFi.h>
#include <HTTPClient.h>
#include <ArduinoJson.h>

void sendSensorData() {
    HTTPClient http;
    http.begin("http://192.168.1.100:3000/api/sensor/data");
    http.addHeader("Content-Type", "application/json");
    
    DynamicJsonDocument doc(1024);
    doc["temperature"] = 25.5;
    doc["humidity"] = 60;
    doc["gps"] = "lat:40.7128,lon:-74.0060";
    
    String payload;
    serializeJson(doc, payload);
    
    int httpResponseCode = http.POST(payload);
    if (httpResponseCode > 0) {
        String response = http.getString();
        Serial.println(response);
    }
    http.end();
}
```

#### 4.3 Monitoramento e Debugging (10 min)
- **Objetivo:** Monitorar tráfego de rede
- **Atividade:** Usar Wireshark para analisar pacotes
- **Ferramentas:** Wireshark, MQTT Explorer, Postman
- **Resultado:** Análise de tráfego e performance

### 5. **Comparação e Aplicação (15 min)**

#### 5.1 Análise Comparativa (10 min)
- **Objetivo:** Comparar MQTT vs HTTP para LogiTrack
- **Atividade:** Grupos analisam cenários de uso
- **Critérios:** Latência, confiabilidade, escalabilidade
- **Resultado:** Recomendação de protocolo

#### 5.2 Aplicação no Projeto (5 min)
- **Objetivo:** Definir protocolo para LogiTrack
- **Atividade:** Grupos justificam escolha
- **Resultado:** Protocolo selecionado e justificativa

## 🎭 Metodologia Pedagógica

### **Laboratório Prático**
- **Hands-on:** Implementação real de protocolos
- **Aprendizagem ativa:** Descoberta através da prática
- **Experimentação:** Testes com diferentes cenários
- **Aplicação:** Implementação em projeto real

### **Aprendizagem Baseada em Problemas**
- **Problema real:** Coleta de dados para LogiTrack
- **Investigação:** Análise de requisitos e soluções
- **Implementação:** Desenvolvimento de soluções
- **Avaliação:** Comparação de alternativas

### **Discussão Colaborativa**
- **Trabalho em equipe:** Análise conjunta de protocolos
- **Debate:** Comparação de vantagens e desvantagens
- **Consenso:** Decisões baseadas em evidências
- **Aplicação:** Soluções para o projeto

## 📊 Avaliação e Acompanhamento

### **Avaliação Formativa**
- **Participação no laboratório:** 40%
- **Implementação técnica:** 30%
- **Análise comparativa:** 30%

### **Critérios de Avaliação**
- **Compreensão técnica:** Conhecimento dos protocolos
- **Implementação prática:** Capacidade de programar
- **Análise crítica:** Comparação de alternativas
- **Colaboração:** Trabalho em equipe eficaz

### **Feedback Imediato**
- **Durante o laboratório:** Orientação técnica
- **Na implementação:** Comentários sobre código
- **Fechamento:** Síntese dos aprendizados

## 🚀 Próximos Passos

### **Para a Próxima Aula**
- **Tema:** Pipeline e Tratamento de Dados
- **Preparação:** Pesquisar ferramentas de processamento
- **Objetivo:** Implementar pipeline de dados para LogiTrack

### **Projeto Atlas**
- **Status:** Protocolo de coleta selecionado
- **Próximo passo:** Implementação de pipeline de dados
- **Entregas:** Sistema de coleta funcionando

## 📝 Observações e Adaptações

### **Possíveis Adaptações**
- **Sem dispositivos:** Usar simuladores e emuladores
- **Turma maior:** Rotacionar uso dos dispositivos
- **Tempo reduzido:** Focar em implementação essencial

### **Recursos Alternativos**
- **Ambiente online:** Simuladores de IoT
- **Dispositivos limitados:** Demonstrações em grupo
- **Conexão limitada:** Trabalhar com broker local

### **Indicadores de Sucesso**
- **Engajamento:** Alunos participam ativamente do laboratório
- **Compreensão:** Conseguem implementar ambos os protocolos
- **Aplicação:** Selecionam protocolo apropriado para o projeto
- **Colaboração:** Trabalham bem em equipe

## 📚 Referências e Materiais Complementares

### **Para Aprofundamento**
- Livro: "MQTT Essentials"
- Artigo: "HTTP vs MQTT for IoT"
- Tutorial: "Building IoT Applications with MQTT"

### **Para Próxima Aula**
- Preparar pesquisa sobre pipelines de dados
- Revisar dados coletados para processamento
- Identificar requisitos de processamento para LogiTrack

---

**Preparado por:** Afonso Cesar  
**Data de criação:** 11/11/2025  
**Versão:** 1.0  
**Status:** Aprovado para execução
