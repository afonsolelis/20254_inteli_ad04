# Plano de Aula 03 - Componentes de Dispositivos e Protocolos de Comunicação IoT

## 📋 Informações Gerais

| **Propriedade** | **Valor** |
|-----------------|-----------|
| **Professor** | Afonso Cesar |
| **Unidade** | Semana 03 |
| **Data** | 31/10/2025 - 10:00h |
| **Duração Total** | 2 horas |
| **Modalidade** | Presencial |
| **Turma** | Computação - IoT |

## 🎯 Objetivos de Aprendizagem

### Objetivos Gerais
- Estudar componentes físicos de dispositivos IoT
- Compreender protocolos de comunicação IoT
- Aplicar seleção de componentes no caso LogiTrack

### Objetivos Específicos
Ao final desta aula, os alunos serão capazes de:
- Identificar componentes principais de dispositivos IoT
- Compreender características de diferentes protocolos
- Selecionar protocolos baseados em requisitos
- Aplicar critérios de seleção no Projeto Atlas
- Implementar comunicação básica entre dispositivos

## 📚 Materiais e Recursos

### Materiais de Estudo Obrigatórios (Pré-aula)
| **Material** | **Tipo** | **Duração** | **Objetivo** |
|---------------|----------|-------------|--------------|
| **Componentes IoT Essenciais** | Artigo | 25 min | Sensores, microcontroladores, módulos |
| **Protocolos de Comunicação IoT** | Whitepaper | 30 min | WiFi, Bluetooth, LoRa, Zigbee |
| **Seleção de Protocolos IoT** | Guia | 20 min | Critérios de seleção |
| **Implementação Prática** | Tutorial | 25 min | Exemplos de código |

### Recursos da Aula
- Dispositivos IoT para demonstração
- Sensores diversos (temperatura, GPS, vibração)
- Microcontroladores (Arduino, ESP32)
- Módulos de comunicação (WiFi, Bluetooth, LoRa)
- Osciloscópio e multímetro
- Computadores para programação

## ⏰ Cronograma Detalhado

### **Fase 1: Abertura e Contextualização (15 min)**
- **10:00 - 10:15** | Daily inicial e revisão da análise econômica

### **Fase 2: Componentes IoT (30 min)**
- **10:15 - 10:45** | Sensores, microcontroladores e módulos

### **Fase 3: Protocolos de Comunicação (30 min)**
- **10:45 - 11:15** | WiFi, Bluetooth, LoRa, Zigbee, Z-Wave

### **Fase 4: Laboratório Prático (30 min)**
- **11:15 - 11:45** | Implementação de comunicação básica

### **Fase 5: Seleção para LogiTrack (15 min)**
- **11:45 - 12:00** | Aplicação dos conceitos no projeto

## 📖 Conteúdo Programático

### 1. **Revisão do Projeto Atlas (15 min)**

#### 1.1 Contextualização Técnica
- **Análise econômica:** Viabilidade confirmada
- **Próximo passo:** Seleção de componentes e protocolos
- **Requisitos LogiTrack:**
  - Rastreamento GPS em tempo real
  - Monitoramento de temperatura
  - Detecção de vibração/anomalias
  - Conectividade em movimento
  - Baixo consumo de energia

#### 1.2 Desafios Técnicos
- **Conectividade:** 4G/5G na estrada, WiFi nos depósitos
- **Energia:** Baterias de longa duração
- **Ambiente:** Resistência a vibração e temperatura
- **Custo:** Componentes economicamente viáveis

### 2. **Componentes de Dispositivos IoT (30 min)**

#### 2.1 Sensores
1. **GPS (Global Positioning System)**
   - Função: Localização geográfica
   - Precisão: 3-5 metros
   - Consumo: Médio
   - Aplicação LogiTrack: Rastreamento de caminhões

2. **Sensores de Temperatura**
   - Função: Monitoramento térmico
   - Precisão: ±0.5°C
   - Consumo: Baixo
   - Aplicação LogiTrack: Carga refrigerada

3. **Sensores de Vibração**
   - Função: Detecção de anomalias
   - Precisão: Acelerômetro 3D
   - Consumo: Baixo
   - Aplicação LogiTrack: Manutenção preditiva

#### 2.2 Microcontroladores
1. **Arduino Uno/Nano**
   - Processador: ATmega328P
   - Memória: 32KB Flash, 2KB RAM
   - Conectividade: Limitada
   - Aplicação: Prototipagem

2. **ESP32**
   - Processador: Dual-core 240MHz
   - Memória: 4MB Flash, 520KB RAM
   - Conectividade: WiFi + Bluetooth
   - Aplicação: Dispositivos finais

3. **Raspberry Pi**
   - Processador: Quad-core ARM
   - Memória: 1-8GB RAM
   - Conectividade: WiFi + Bluetooth + Ethernet
   - Aplicação: Gateways

#### 2.3 Módulos de Comunicação
1. **WiFi (ESP32, ESP8266)**
   - Alcance: 50-100m
   - Velocidade: 54-150 Mbps
   - Consumo: Médio
   - Aplicação: Conectividade local

2. **Bluetooth (HC-05, ESP32)**
   - Alcance: 10-100m
   - Velocidade: 1-3 Mbps
   - Consumo: Baixo
   - Aplicação: Comunicação próxima

3. **LoRa (SX1276, SX1278)**
   - Alcance: 2-15km
   - Velocidade: 0.3-50 kbps
   - Consumo: Muito baixo
   - Aplicação: Longa distância

### 3. **Protocolos de Comunicação (30 min)**

#### 3.1 WiFi (IEEE 802.11)
- **Características:** Alta velocidade, baixo alcance
- **Vantagens:** Velocidade, disponibilidade
- **Desvantagens:** Consumo, alcance limitado
- **Aplicação LogiTrack:** Depósitos e centros

#### 3.2 Bluetooth (IEEE 802.15.1)
- **Características:** Baixo consumo, curto alcance
- **Vantagens:** Baixo consumo, fácil implementação
- **Desvantagens:** Alcance limitado, velocidade
- **Aplicação LogiTrack:** Comunicação local

#### 3.3 LoRa (Long Range)
- **Características:** Longo alcance, baixa velocidade
- **Vantagens:** Alcance, baixo consumo
- **Desvantagens:** Velocidade, latência
- **Aplicação LogiTrack:** Áreas remotas

#### 3.4 Zigbee (IEEE 802.15.4)
- **Características:** Rede mesh, baixo consumo
- **Vantagens:** Rede mesh, baixo consumo
- **Desvantagens:** Complexidade, alcance
- **Aplicação LogiTrack:** Redes de sensores

#### 3.5 Z-Wave
- **Características:** Rede mesh, frequência específica
- **Vantagens:** Confiabilidade, rede mesh
- **Desvantagens:** Custo, frequência
- **Aplicação LogiTrack:** Automação residencial

### 4. **Laboratório Prático (30 min)**

#### 4.1 Configuração do Ambiente (5 min)
- **Objetivo:** Preparar dispositivos para experimentação
- **Atividade:** Configurar ESP32 e sensores
- **Resultado:** Ambiente pronto para testes

#### 4.2 Implementação WiFi (10 min)
- **Objetivo:** Conectar ESP32 à rede WiFi
- **Atividade:** Programar conexão e envio de dados
- **Código exemplo:**
```cpp
#include <WiFi.h>
#include <HTTPClient.h>

const char* ssid = "LogiTrack_WiFi";
const char* password = "password123";

void setup() {
  WiFi.begin(ssid, password);
  while (WiFi.status() != WL_CONNECTED) {
    delay(1000);
  }
}
```

#### 4.3 Implementação Bluetooth (10 min)
- **Objetivo:** Comunicação Bluetooth entre dispositivos
- **Atividade:** Configurar servidor e cliente Bluetooth
- **Resultado:** Transmissão de dados via Bluetooth

#### 4.4 Teste de Sensores (5 min)
- **Objetivo:** Coletar dados de sensores
- **Atividade:** Leitura de GPS, temperatura e vibração
- **Resultado:** Dados sendo coletados e transmitidos

### 5. **Seleção para LogiTrack (15 min)**

#### 5.1 Análise de Requisitos (5 min)
- **Objetivo:** Definir requisitos técnicos específicos
- **Atividade:** Grupos analisam necessidades da LogiTrack
- **Resultado:** Lista de requisitos técnicos

#### 5.2 Seleção de Componentes (5 min)
- **Objetivo:** Escolher componentes baseados em requisitos
- **Atividade:** Grupos selecionam sensores e microcontroladores
- **Critérios:** Custo, consumo, precisão, durabilidade

#### 5.3 Seleção de Protocolos (5 min)
- **Objetivo:** Escolher protocolos de comunicação
- **Atividade:** Grupos selecionam protocolos por cenário
- **Cenários:** Estrada (4G/5G), depósito (WiFi), área remota (LoRa)

## 🎭 Metodologia Pedagógica

### **Laboratório Prático**
- **Hands-on:** Experimentação com dispositivos reais
- **Aprendizagem ativa:** Construção de conhecimento através da prática
- **Descoberta:** Alunos descobrem características dos componentes
- **Aplicação:** Conceitos aplicados em cenário real

### **Aprendizagem Baseada em Projetos**
- **Projeto real:** Seleção para LogiTrack
- **Investigação:** Análise de requisitos e soluções
- **Implementação:** Testes práticos com componentes
- **Avaliação:** Comparação de soluções

### **Discussão Colaborativa**
- **Trabalho em equipe:** Análise conjunta de requisitos
- **Debate:** Comparação de diferentes soluções
- **Consenso:** Decisões baseadas em critérios técnicos
- **Aplicação:** Soluções para o projeto real

## 📊 Avaliação e Acompanhamento

### **Avaliação Formativa**
- **Participação no laboratório:** 40%
- **Qualidade da implementação:** 30%
- **Análise de requisitos:** 30%

### **Critérios de Avaliação**
- **Compreensão técnica:** Conhecimento dos componentes
- **Implementação prática:** Capacidade de programar dispositivos
- **Análise crítica:** Seleção baseada em requisitos
- **Colaboração:** Trabalho em equipe eficaz

### **Feedback Imediato**
- **Durante o laboratório:** Orientação técnica
- **Na seleção:** Comentários sobre critérios
- **Fechamento:** Síntese dos aprendizados

## 🚀 Próximos Passos

### **Para a Próxima Aula**
- **Tema:** Segurança em IoT
- **Preparação:** Pesquisar vulnerabilidades de segurança
- **Objetivo:** Implementar segurança na solução LogiTrack

### **Projeto Atlas**
- **Status:** Componentes e protocolos selecionados
- **Próximo passo:** Implementação de segurança
- **Entregas:** Lista de componentes e protocolos selecionados

## 📝 Observações e Adaptações

### **Possíveis Adaptações**
- **Sem dispositivos:** Usar simuladores e demonstrações
- **Turma maior:** Rotacionar uso dos dispositivos
- **Tempo reduzido:** Focar em conceitos essenciais

### **Recursos Alternativos**
- **Ambiente online:** Simuladores de IoT
- **Dispositivos limitados:** Demonstrações em grupo
- **Conexão limitada:** Trabalhar offline

### **Indicadores de Sucesso**
- **Engajamento:** Alunos participam ativamente do laboratório
- **Compreensão:** Conseguem explicar características dos componentes
- **Aplicação:** Selecionam componentes apropriados para o projeto
- **Colaboração:** Trabalham bem em equipe

## 📚 Referências e Materiais Complementares

### **Para Aprofundamento**
- Livro: "IoT Components and Protocols Guide"
- Artigo: "Selecting IoT Communication Protocols"
- Tutorial: "ESP32 Programming for IoT"

### **Para Próxima Aula**
- Preparar pesquisa sobre segurança IoT
- Revisar componentes selecionados para análise de segurança
- Identificar vulnerabilidades específicas dos componentes

---

**Preparado por:** Afonso Cesar  
**Data de criação:** 31/10/2025  
**Versão:** 1.0  
**Status:** Aprovado para execução
