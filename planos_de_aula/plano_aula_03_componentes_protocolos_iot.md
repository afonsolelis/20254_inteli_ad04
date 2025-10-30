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
- Acompanhar o capítulo "Conectando Pontos" da jornada da LogiTrack
- Traduzir decisões narrativas em escolhas técnicas de componentes IoT
- Comparar protocolos e estratégias de integração OT/IT por meio de tabelas de decisão

### Objetivos Específicos
Ao final desta aula, os alunos serão capazes de:
- Relacionar arranjos físicos de produção com o fluxo de dados do Projeto Atlas
- Analisar trade-offs entre diferentes tecnologias de conectividade (LoRa, Wi-Fi, 4G/LTE)
- Justificar escolhas de protocolos baseados em cenários operacionais reais
- Projetar arquiteturas híbridas de comunicação para ambientes heterogêneos
- Planejar estratégias de contingência para falhas de conectividade

## 📚 Materiais e Recursos

### Materiais de Estudo Obrigatórios (Pré-aula)
| **Material** | **Tipo** | **Duração** | **Objetivo** |
|---------------|----------|-------------|--------------|
| **Arquitetura IoT em Camadas** | Revisão Aula 01 | 15 min | Relembrar camadas (Percepção, Edge, Middleware, Aplicações) |
| **Análise Econômica do Projeto Atlas** | Revisão Aula 02 | 15 min | Contexto de viabilidade e orçamento aprovado |
| **Protocolos de Comunicação IoT** | Artigo | 30 min | Comparativo MQTT, HTTP/REST, TCP |
| **Integração OT/IT** | Whitepaper | 20 min | Conceitos de convergência operacional |

### Recursos da Aula
- Apresentação narrativa "Conectando Pontos" (slides com storytelling)
- Figuras técnicas do Projeto Atlas:
  - Figura 1: Arquitetura IoT completa
  - Figura 2: Requisitos técnicos mínimos (FIS-IoT)
  - Figura 3: Integração com antenas RFID
  - Figura 4: Integração com PLCs
- Tabelas de decisão impressas para grupos
- Kits de demonstração: LoRa, Wi-Fi e 4G/LTE (se disponível)
- Material para mapeamento físico (papel, post-its, marcadores)

## ⏰ Cronograma Detalhado

### **Fase 1: Abertura e Contextualização (10 min)**
- **10:00 - 10:10** | Daily inicial e recap das aulas anteriores (arquitetura IoT + viabilidade econômica)

### **Fase 2: Ato 1 - Reunião na Base Atlas (15 min)**
- **10:10 - 10:25** | Storytelling da reunião e apresentação da tabela de conectividade

### **Fase 3: Ato 2 - Escolha dos Componentes por Camada (20 min)**
- **10:25 - 10:45** | Figura 1 (Arquitetura IoT) e tabela de decisões por camada

### **Fase 4: Ato 3 e 4 - Conectividade e Protocolos (25 min)**
- **10:45 - 11:10** | Tabelas comparativas (LoRa, Wi-Fi, 4G) e debate sobre MQTT vs HTTP

### **Fase 5: Ato 5 - Testes de Campo (15 min)**
- **11:10 - 11:25** | Evidências da rota SP-Campinas e estratégia de buffer local

### **Fase 6: Ato 6 - Layout Logístico e Trabalho em Grupo (35 min)**
- **11:25 - 12:00** | Tabela de layouts e início da atividade ponderada em grupo

## 📖 Conteúdo Programático

### 1. **Abertura e Contextualização (10 min)**

#### 1.1 Onde Paramos na História
- **Aula 01:** LogiTrack descobriu arquitetura IoT e mapeou camadas críticas
- **Aula 02:** Time financeiro provou viabilidade do Projeto Atlas e garantiu orçamento
- **Aula 03:** Marina e equipe entram na Base Atlas para transformar números em dispositivos conectados

#### 1.2 Daily Inicial
- Revisão rápida dos grupos sobre andamento do projeto
- Dúvidas sobre conceitos anteriores
- Expectativas para a aula de hoje

### 2. **Ato 1 - Reunião na Base Atlas (15 min)**

#### 2.1 Storytelling da Reunião
- Marina Costa liga o projetor e apresenta três kits: LoRa, Wi-Fi e 4G/LTE
- Pedro defende 4G nos caminhões; Marina propõe LoRa nos depósitos
- Juliana lembra: operação heterogênea exige arquitetura híbrida

#### 2.2 Elementos em Debate (Tabela 1)
| Elemento em debate | Insight narrativo | Dado técnico |
| --- | --- | --- |
| Conectividade em campo | Frota cruzando áreas urbanas e rurais | Alcance, consumo e custo comparados |
| Continuidade do serviço | Falhas de rede simuladas no teste | Estratégia com buffer local + reenvio |
| Escalabilidade | Crescimento para 120 caminhões | Requisitos mínimos de plataforma |

### 3. **Ato 2 - Escolha dos Componentes por Camada (20 min)**

#### 3.1 Figura 1 - Arquitetura IoT da Base Atlas
- Apresentação da imagem completa da arquitetura
- Discussão das 4 camadas: Percepção, Edge & Gateways, Middleware, Aplicações

#### 3.2 Tabela de Decisões por Camada
| Camada | Dispositivos selecionados | Decisão da equipe | Pergunta norteadora |
| --- | --- | --- | --- |
| Percepção | Sensores temperatura, vibração, GPS, RFID | Mix de fabricantes; baixo consumo | Como garantir manutenção fácil? |
| Edge & Gateways | Gateways veiculares com cache, PLCs | Gateways determinam protocolo por cobertura | Onde posicionar redundâncias? |
| Middleware | FIS-IoT (Node-RED + REST/MQTT) | Combina MQTT para telemetria e REST para integrações | Qual camada recebe alertas primeiro? |
| Aplicações | KERN + dashboards operacionais | Dados com carimbo e contexto logístico | Quem valida exceções antes de alertar? |

### 4. **Ato 3 - Tabela de Decisão de Conectividade (15 min)**

#### 4.1 Comparação de Tecnologias
| Tecnologia | Alcance | Consumo | Custo recorrente | Uso definido |
| --- | --- | --- | --- | --- |
| LoRa | 1-15 km | Muito baixo | Gateway próprio | Depósitos e pátios |
| Wi-Fi | 50-100 m | Médio | Infraestrutura local | Centros de distribuição |
| 4G/LTE | Nacional | Alto | Plano por SIM | Caminhões em rota longa |

#### 4.2 Discussão em Grupo
- Marina propõe firmware que alterna entre mídias
- Carlos questiona complexidade
- Juliana: "Ambiente é heterogêneo; arquitetura precisa se adaptar"

### 5. **Ato 4 - Protocolos na Mesa de Debate (10 min)**

#### 5.1 Figura 2 - Requisitos Técnicos Mínimos
- Checklist que Marina usa para mostrar que AIX suportará FIS-IoT

#### 5.2 Tabela de Protocolos
| Protocolo | Papel no Projeto Atlas | Por que foi escolhido | Trade-off aceito |
| --- | --- | --- | --- |
| MQTT | Telemetria contínua | Leve, pub/sub, tolera perda | Precisa broker estável |
| HTTP/REST | Sincronização KERN e dashboards | Facilita auditorias | Overhead maior |
| TCP direto | Interface RFID e PLCs | Baixa latência, legado | Requer tuning firewall |
| Buffers locais | Edge cache nos gateways | Resiliência durante quedas | Política de descarte |

#### 5.3 Diálogo-chave
- Carlos: "Por que não só HTTP?"
- Juliana: "Dados críticos não podem esperar reconexão. Usamos camadas adaptativas."

#### 5.4 Figuras 3 e 4
- Figura 3: Caminho de dados de etiquetas RFID
- Figura 4: Integração com PLCs e módulos FIS

### 6. **Ato 5 - Testes de Campo na Rota SP-Campinas (15 min)**

#### 6.1 Tabela de Métricas Observadas
| Métrica | MQTT | HTTP | Comentário |
| --- | --- | --- | --- |
| Largura de banda | 83% redução vs HTTP | Base | Mantém custo 4G no orçamento |
| Latência média | 1,3 s | 3,8 s | MQTT entrega alertas quase real-time |
| Recuperação pós-falha | Reenvio automático | Manual | Estratégia híbrida aprovada |

#### 6.2 Experimento de Falha
- Equipe derruba sinal 4G por 10 minutos
- Gateway armazena leituras
- Ao reconectar: lote enviado via HTTP preservando auditoria

### 7. **Ato 6 - Layout Logístico e Posicionamento dos Ativos (35 min)**

#### 7.1 Tabela de Ambientes LogiTrack
| Ambiente | Layout | Ponto IoT crítico | Lição operacional |
| --- | --- | --- | --- |
| Linha expedição | Linear | Antenas RFID nas docas | Sincronizar PLCs evita erros |
| Oficina manutenção | Por processo | Gateways móveis Wi-Fi | Flexibilidade exige redes mesh |
| Hub metropolitano | Layout em U | Checkpoints início/fim | Comparar entrada/saída com MQTT |
| Rotas longa distância | Fluxo distribuído | Gateways com fallback 4G | Planejar janelas de reconexão |

#### 7.2 Trabalho em Grupo (início)
- Grupos assumem um trecho da operação
- Começam a elaborar mapa físico e tabela de justificativa
- Discussão orientada pelo professor

## 🎭 Metodologia Pedagógica

### **Storytelling Técnico**
- **Narrativa imersiva:** Alunos acompanham personagens tomando decisões reais
- **Contextualização:** Conceitos técnicos apresentados como soluções para problemas concretos
- **Engajamento:** História da LogiTrack mantém interesse e relevância
- **Identificação:** Alunos se veem nos papéis de Marina, Juliana, Pedro e Carlos

### **Aprendizagem Baseada em Decisões**
- **Tabelas comparativas:** Estruturas visuais facilitam análise de trade-offs
- **Discussão de cenários:** Alunos debatem as mesmas questões que os personagens
- **Justificativa técnica:** Cada escolha precisa ser fundamentada em dados
- **Pensamento crítico:** Não há resposta única; depende do contexto

### **Trabalho Colaborativo em Grupo**
- **Divisão por ambientes:** Cada grupo assume um trecho operacional
- **Co-criação:** Grupos elaboram mapas e tabelas de decisão
- **Apresentação:** Compartilhamento de soluções entre grupos
- **Aprendizado peer-to-peer:** Grupos aprendem com escolhas uns dos outros

## 📊 Avaliação e Acompanhamento

### **Atividade Ponderada Pós-Aula (0-10 pontos)**

#### Desafio
Cada grupo assume um trecho da operação LogiTrack (expedição, oficina, hub metropolitano ou rota longa)

#### Entregáveis
1. **Mapa físico** com sensores, gateways e pontos de protocolo (pode ser desenhado)
2. **Tabela justificando** a escolha de conectividade (baseada nas tabelas da aula)
3. **Plano de contingência:** O que acontece se MQTT cair? E se HTTP ficar indisponível?
4. **Checklist de requisitos mínimos** reaproveitando a Figura 2

#### Critérios de Avaliação
- **Adequação técnica das escolhas (0-3 pontos):** Escolhas fazem sentido para o ambiente?
- **Clareza do arranjo físico e cobertura de dados (0-3 pontos):** Mapa está bem estruturado?
- **Uso das evidências dos testes de campo (0-2 pontos):** Aplicaram os aprendizados da rota SP-Campinas?
- **Criatividade na contingência e ligação com storytelling (0-2 pontos):** Soluções inovadoras e conectadas à narrativa?

### **Avaliação Formativa Durante a Aula**
- **Participação nos debates:** Contribuição nas discussões dos atos narrativos
- **Qualidade das perguntas:** Questionamentos técnicos relevantes
- **Colaboração:** Trabalho em equipe durante o início da atividade

### **Feedback**
- **Durante os atos:** Professor orienta debates e esclarece dúvidas técnicas
- **No trabalho em grupo:** Feedback sobre direcionamento das escolhas
- **Pós-entrega:** Comentários detalhados sobre cada critério de avaliação

## 🚀 Próximos Passos

### **Ganchos para a Próxima Aula - Segurança em IoT**
- Dados híbridos exigem políticas de criptografia e atualização OTA (tema da Aula 04)
- O buffer local virou ponto crítico: como protegê-lo contra adulteração?
- Quem garante que antenas e PLCs não serão vetores de ataque?
- **Frase de fechamento de Henrique Duarte:** "Pela primeira vez vejo dados viajando da estrada para a nuvem. Agora precisamos garantir que ninguém intercepte essa rota."

### **Projeto Atlas - Status Atual**
- **Avanço:** Componentes e protocolos selecionados por ambiente operacional
- **Próximo desafio:** Implementar segurança em toda a cadeia de dados
- **Deliverables desta aula:** Mapa físico + tabela de decisão + plano de contingência

## 📝 Observações e Adaptações

### **Possíveis Adaptações**
- **Sem kits físicos:** Usar apenas imagens e especificações técnicas nas tabelas
- **Turma maior:** Aumentar número de ambientes operacionais (criar sub-divisões)
- **Tempo reduzido:** Condensar Atos 1-2 em apresentação única, focar nos Atos 3-6
- **Aula remota:** Usar Miro ou Figma para co-criação dos mapas físicos

### **Recursos Alternativos**
- **Sem projetor:** Imprimir figuras técnicas em formato A3 para grupos
- **Conexão limitada:** Preparar materiais offline (PDFs com figuras e tabelas)
- **Materiais de desenho limitados:** Usar ferramentas digitais colaborativas

### **Indicadores de Sucesso**
- **Engajamento:** Alunos fazem perguntas sobre os dilemas dos personagens
- **Compreensão:** Conseguem justificar escolhas com base em trade-offs técnicos
- **Aplicação:** Mapas físicos demonstram entendimento da arquitetura híbrida
- **Pensamento crítico:** Planos de contingência são realistas e fundamentados

## 📚 Referências e Materiais Complementares

### **Imagens Técnicas Utilizadas na Aula**
- Figura 1: Arquitetura IoT da Base Atlas (Blueprint completo)
- Figura 2: Requisitos técnicos mínimos FIS-IoT (Checklist da Marina)
- Figura 3: Integração com antenas RFID nos centros de distribuição
- Figura 4: Integração com PLCs e módulos FIS para sensores veiculares

### **Para Aprofundamento**
- Whitepaper: "MQTT vs HTTP: Choosing the Right Protocol for IoT"
- Artigo: "OT/IT Convergence in Industrial IoT Systems"
- Case study: "Hybrid Connectivity in Fleet Management"
- Documentação: "LoRa, Wi-Fi and 4G/LTE Trade-offs"

### **Para Próxima Aula (Segurança em IoT)**
- Pesquisar vulnerabilidades em protocolos MQTT e HTTP
- Ler sobre criptografia de dados em trânsito e em repouso
- Estudar técnicas de atualização OTA (Over-The-Air)
- Identificar vetores de ataque em gateways e buffers locais

---

**Preparado por:** Afonso Cesar  
**Data de criação:** 31/10/2025  
**Versão:** 1.0  
**Status:** Aprovado para execução
