# Plano de Aula 04 - Segurança em IoT

## 📋 Informações Gerais

| **Propriedade** | **Valor** |
|-----------------|-----------|
| **Professor** | Afonso Cesar |
| **Unidade** | Semana 04 |
| **Data** | 05/11/2025 - 10:00h |
| **Duração Total** | 2 horas |
| **Modalidade** | Presencial |
| **Turma** | Computação - IoT |

## 🎯 Objetivos de Aprendizagem

### Objetivos Gerais
- Compreender fundamentos de segurança em sistemas IoT
- Identificar ameaças e vulnerabilidades específicas
- Implementar estratégias de proteção para LogiTrack

### Objetivos Específicos
Ao final desta aula, os alunos serão capazes de:
- Identificar principais ameaças de segurança em IoT
- Compreender vulnerabilidades de dispositivos IoT
- Implementar estratégias de autenticação e autorização
- Aplicar criptografia e proteção de dados
- Desenvolver plano de segurança para o Projeto Atlas

## 📚 Materiais e Recursos

### Materiais de Estudo Obrigatórios (Pré-aula)
| **Material** | **Tipo** | **Duração** | **Objetivo** |
|---------------|----------|-------------|--------------|
| **Ameaças de Segurança IoT** | Artigo | 25 min | Principais ameaças e ataques |
| **Vulnerabilidades IoT** | Relatório | 30 min | Vulnerabilidades específicas |
| **Estratégias de Segurança IoT** | Whitepaper | 25 min | Autenticação, autorização, criptografia |
| **Frameworks de Segurança** | Guia | 20 min | OWASP IoT Top 10, NIST |

### Recursos da Aula
- Ferramentas de análise de vulnerabilidades
- Exemplos de dispositivos IoT vulneráveis
- Software de criptografia
- Simuladores de ataques
- Computadores para laboratório

## ⏰ Cronograma Detalhado

### **Fase 1: Abertura e Contextualização (15 min)**
- **10:00 - 10:15** | Daily inicial e revisão da seleção de componentes

### **Fase 2: Ameaças e Vulnerabilidades (30 min)**
- **10:15 - 10:45** | Principais ameaças de segurança IoT

### **Fase 3: Estratégias de Segurança (30 min)**
- **10:45 - 11:15** | Autenticação, autorização e criptografia

### **Fase 4: Laboratório de Segurança (30 min)**
- **11:15 - 11:45** | Implementação de medidas de segurança

### **Fase 5: Plano de Segurança LogiTrack (15 min)**
- **11:45 - 12:00** | Desenvolvimento do plano de segurança

## 📖 Conteúdo Programático

### 1. **Contextualização da Segurança IoT (15 min)**

#### 1.1 Importância da Segurança
- **Cenário LogiTrack:** Dados sensíveis de transporte
- **Riscos:** Interrupção de serviços, vazamento de dados
- **Consequências:** Perdas financeiras, danos à reputação
- **Regulamentações:** LGPD, GDPR, compliance

#### 1.2 Desafios Específicos IoT
- **Dispositivos limitados:** Recursos computacionais restritos
- **Conectividade:** Múltiplos pontos de ataque
- **Longevidade:** Dispositivos em campo por anos
- **Diversidade:** Diferentes fabricantes e protocolos

### 2. **Ameaças e Vulnerabilidades (30 min)**

#### 2.1 Principais Ameaças IoT
1. **Ataques de DDoS**
   - **Método:** Botnets de dispositivos IoT
   - **Impacto:** Interrupção de serviços
   - **Exemplo:** Mirai botnet (2016)
   - **Prevenção:** Atualizações, monitoramento

2. **Ataques de Man-in-the-Middle**
   - **Método:** Interceptação de comunicações
   - **Impacto:** Roubo de dados, espionagem
   - **Exemplo:** Interceptação de dados GPS
   - **Prevenção:** Criptografia, certificados

3. **Ataques de Eavesdropping**
   - **Método:** Escuta de comunicações
   - **Impacto:** Vazamento de informações
   - **Exemplo:** Interceptação de dados de sensores
   - **Prevenção:** Criptografia end-to-end

4. **Ataques de Spoofing**
   - **Método:** Falsificação de identidade
   - **Impacto:** Acesso não autorizado
   - **Exemplo:** Falsificação de dados GPS
   - **Prevenção:** Autenticação forte

#### 2.2 Vulnerabilidades Específicas IoT
1. **Senhas Padrão**
   - **Problema:** Senhas padrão não alteradas
   - **Risco:** Acesso não autorizado
   - **Solução:** Política de senhas forte

2. **Firmware Desatualizado**
   - **Problema:** Falta de atualizações
   - **Risco:** Exploração de vulnerabilidades
   - **Solução:** Gerenciamento de atualizações

3. **Comunicações Não Criptografadas**
   - **Problema:** Dados em texto claro
   - **Risco:** Interceptação de dados
   - **Solução:** Criptografia obrigatória

4. **Interfaces de Gerenciamento Inseguras**
   - **Problema:** Interfaces web vulneráveis
   - **Risco:** Acesso administrativo
   - **Solução:** Autenticação e autorização

### 3. **Estratégias de Segurança (30 min)**

#### 3.1 Autenticação e Autorização
1. **Autenticação Multifator (MFA)**
   - **Método:** Múltiplos fatores de autenticação
   - **Implementação:** Senha + token + biometria
   - **Aplicação LogiTrack:** Acesso a sistemas críticos

2. **Certificados Digitais**
   - **Método:** PKI (Public Key Infrastructure)
   - **Implementação:** Certificados X.509
   - **Aplicação LogiTrack:** Comunicação entre dispositivos

3. **OAuth 2.0**
   - **Método:** Autorização baseada em tokens
   - **Implementação:** Tokens de acesso
   - **Aplicação LogiTrack:** APIs e serviços

#### 3.2 Criptografia
1. **Criptografia Simétrica**
   - **Método:** AES-256
   - **Uso:** Dados em repouso
   - **Aplicação LogiTrack:** Armazenamento de dados

2. **Criptografia Assimétrica**
   - **Método:** RSA, ECC
   - **Uso:** Troca de chaves
   - **Aplicação LogiTrack:** Comunicação segura

3. **Criptografia de Transporte**
   - **Método:** TLS 1.3
   - **Uso:** Comunicação em rede
   - **Aplicação LogiTrack:** Transmissão de dados

#### 3.3 Monitoramento e Detecção
1. **SIEM (Security Information and Event Management)**
   - **Função:** Correlação de eventos
   - **Implementação:** Análise de logs
   - **Aplicação LogiTrack:** Detecção de anomalias

2. **IDS/IPS (Intrusion Detection/Prevention)**
   - **Função:** Detecção de intrusões
   - **Implementação:** Análise de tráfego
   - **Aplicação LogiTrack:** Proteção de rede

### 4. **Laboratório de Segurança (30 min)**

#### 4.1 Análise de Vulnerabilidades (10 min)
- **Objetivo:** Identificar vulnerabilidades em dispositivos
- **Atividade:** Usar ferramentas de análise
- **Ferramentas:** Nmap, Nessus, OpenVAS
- **Resultado:** Relatório de vulnerabilidades

#### 4.2 Implementação de Criptografia (10 min)
- **Objetivo:** Implementar criptografia em comunicações
- **Atividade:** Configurar TLS/SSL
- **Código exemplo:**
```python
import ssl
import socket

def create_secure_connection(host, port):
    context = ssl.create_default_context()
    context.check_hostname = False
    context.verify_mode = ssl.CERT_NONE
    
    with socket.create_connection((host, port)) as sock:
        with context.wrap_socket(sock) as ssock:
            return ssock
```

#### 4.3 Configuração de Autenticação (10 min)
- **Objetivo:** Implementar autenticação forte
- **Atividade:** Configurar MFA e certificados
- **Resultado:** Sistema com autenticação robusta

### 5. **Plano de Segurança LogiTrack (15 min)**

#### 5.1 Análise de Riscos (5 min)
- **Objetivo:** Identificar riscos específicos da LogiTrack
- **Atividade:** Grupos analisam cenários de risco
- **Resultado:** Lista de riscos identificados

#### 5.2 Estratégias de Proteção (5 min)
- **Objetivo:** Definir estratégias de proteção
- **Atividade:** Grupos propõem medidas de segurança
- **Resultado:** Plano de proteção

#### 5.3 Implementação (5 min)
- **Objetivo:** Definir cronograma de implementação
- **Atividade:** Grupos criam cronograma
- **Resultado:** Plano de implementação

## 🎭 Metodologia Pedagógica

### **Laboratório de Segurança**
- **Hands-on:** Experimentação com ferramentas reais
- **Aprendizagem ativa:** Descoberta através da prática
- **Análise crítica:** Identificação de vulnerabilidades
- **Aplicação:** Implementação de soluções

### **Aprendizagem Baseada em Casos**
- **Casos reais:** Exemplos de ataques e vulnerabilidades
- **Análise:** Investigação de incidentes
- **Solução:** Desenvolvimento de contramedidas
- **Aplicação:** Implementação em cenário real

### **Discussão Colaborativa**
- **Trabalho em equipe:** Análise conjunta de riscos
- **Debate:** Comparação de estratégias
- **Consenso:** Decisões baseadas em evidências
- **Aplicação:** Soluções para o projeto

## 📊 Avaliação e Acompanhamento

### **Avaliação Formativa**
- **Participação no laboratório:** 40%
- **Análise de riscos:** 30%
- **Plano de segurança:** 30%

### **Critérios de Avaliação**
- **Compreensão técnica:** Conhecimento de ameaças e vulnerabilidades
- **Implementação prática:** Capacidade de implementar segurança
- **Análise crítica:** Identificação de riscos e soluções
- **Colaboração:** Trabalho em equipe eficaz

### **Feedback Imediato**
- **Durante o laboratório:** Orientação técnica
- **Na análise:** Comentários sobre identificação de riscos
- **Fechamento:** Síntese dos aprendizados

## 🚀 Próximos Passos

### **Para a Próxima Aula**
- **Tema:** Coleta de Dados MQTT/HTTP
- **Preparação:** Pesquisar protocolos de coleta
- **Objetivo:** Implementar coleta segura de dados

### **Projeto Atlas**
- **Status:** Plano de segurança desenvolvido
- **Próximo passo:** Implementação de coleta de dados
- **Entregas:** Plano de segurança e medidas implementadas

## 📝 Observações e Adaptações

### **Possíveis Adaptações**
- **Sem ferramentas:** Usar demonstrações e simulações
- **Turma maior:** Rotacionar uso das ferramentas
- **Tempo reduzido:** Focar em conceitos essenciais

### **Recursos Alternativos**
- **Ambiente online:** Simuladores de segurança
- **Ferramentas limitadas:** Demonstrações em grupo
- **Conexão limitada:** Trabalhar offline

### **Indicadores de Sucesso**
- **Engajamento:** Alunos participam ativamente do laboratório
- **Compreensão:** Conseguem identificar ameaças e vulnerabilidades
- **Aplicação:** Desenvolvem planos de segurança relevantes
- **Colaboração:** Trabalham bem em equipe

## 📚 Referências e Materiais Complementares

### **Para Aprofundamento**
- Livro: "IoT Security: A Comprehensive Guide"
- Artigo: "OWASP IoT Top 10"
- Framework: "NIST Cybersecurity Framework"

### **Para Próxima Aula**
- Preparar pesquisa sobre MQTT e HTTP
- Revisar plano de segurança para implementação
- Identificar requisitos de segurança para coleta de dados

---

**Preparado por:** Afonso Cesar  
**Data de criação:** 05/11/2025  
**Versão:** 1.0  
**Status:** Aprovado para execução
