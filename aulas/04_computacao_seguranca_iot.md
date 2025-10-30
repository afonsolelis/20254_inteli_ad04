# [4] Computação - Segurança em IoT

**Unidade:** Semana 04
**Data:** 05/11/2025

## Tempo estimado
- Daily inicial (15 min)
- Aula narrativa expositiva (55 min) — 7 atos com storytelling
- Atividade de grupo em sala (35 min) — elaboração de apresentação em markdown
- Apresentações dos grupos (35 min) — 5 grupos × 7 min cada

## Objetivos de aprendizagem
- Acompanhar o capítulo "Quebra de Sigilo" da jornada da LogiTrack.
- Identificar ameaças típicas em sistemas IoT usando threat modeling (STRIDE).
- Projetar contramedidas de segurança por camada da arquitetura IoT.
- Avaliar trade-offs entre segurança, custo e operacionalidade.

---

## Onde paramos na história
- **Aula 01:** LogiTrack descobriu a arquitetura IoT e mapeou camadas críticas.
- **Aula 02:** Time financeiro provou a viabilidade do Projeto Atlas e garantiu orçamento.
- **Aula 03:** Marina e equipe definiram componentes, protocolos e arquitetura híbrida de conectividade.
- **Aula 04:** Fase piloto entra em operação — e um incidente de segurança expõe vulnerabilidades críticas.

---

## Quebra de Sigilo — Storytelling da Aula

### Ato 1 — O incidente: terça-feira, 08:47h

*A fase piloto do Projeto Atlas está rodando há duas semanas. Três caminhões equipados, telemetria fluindo para a nuvem. No NOC da LogiTrack, um alerta vermelho pisca: **"Risco de perda de carga — temperatura crítica em SPC-023 e SPC-041"**.*

**Pedro Nascimento (TI):** "Dois veículos ao mesmo tempo? Isso não é normal."
**Operador do NOC:** "Eles ainda nem saíram do pátio. Compressores estáveis."
**Marina Costa (Engenharia):** "Se não é físico, é digital. Alguém mexeu nos nossos dados."

| Sintoma observado | Comportamento esperado | Hipótese inicial |
| --- | --- | --- |
| Temperatura reportada: 28°C (acima do limite) | Temperatura real: 4°C (medida local) | Telemetria adulterada |
| Dois caminhões afetados simultaneamente | Eventos independentes | Ataque coordenado ou credenciais vazadas |
| Alertas disparados antes da partida | Sensores só reportam em movimento | Publicação externa no broker MQTT |

**Decisão imediata:** Isolar os caminhões da rede, abrir investigação técnica e convocar reunião de emergência na Base Atlas.

---

### Ato 2 — Investigação: rastreando o intruso

Marina projeta o diagrama da arquitetura atual no quadro:

```
[Sensores] → [Gateway 4G] → [Broker MQTT gerenciado] → [Pipeline de ingestão] → [Banco analítico] → [Metabase]
```

Pedro abre os **logs do broker MQTT**. Em 5 minutos, a equipe identifica:

| Evidência técnica | O que revela | Gravidade |
| --- | --- | --- |
| Duas conexões de IPs desconhecidos | Acesso não autorizado | 🔴 Crítica |
| Mesmo `clientId` usado por gateway legítimo | Spoofing de identidade | 🔴 Crítica |
| Conexão aceita com TLS unilateral | Broker não valida cliente | 🟡 Alta |
| Credenciais de teste em produção | Falta de rotacionamento | 🟡 Alta |
| Tópico `/lt/frota/SPC-023/telemetria` sem ACL | Qualquer cliente pode publicar | 🔴 Crítica |

**Carlos Mendes (Operações):** "Como isso passou nos nossos testes?"
**Juliana Prado (Arquitetura):** "Porque testamos funcionalidade, não segurança. Agora vamos corrigir."

---

### Ato 3 — Threat modeling: mapeando as ameaças com STRIDE

Juliana propõe um **threat modeling estruturado** usando o framework STRIDE sobre o fluxo crítico `sensor → broker → processamento`.

![Framework STRIDE aplicado ao Projeto Atlas](https://www.practical-devsecops.com/wp-content/uploads/2022/12/STRIDE-Threat-Model-identify-threats-980x540.webp)
*Figura 1 – Mapa de ameaças STRIDE sobre a arquitetura atual do Projeto Atlas.*

| Categoria STRIDE | Ameaça identificada | Impacto no Projeto Atlas | Probabilidade |
| --- | --- | --- | --- |
| **S**poofing | Reutilização de credenciais e clientId | Telemetria falsa aceita como legítima | 🔴 Alta |
| **T**ampering | Alteração de payload em trânsito (TLS fraco) | Dados corrompidos antes de armazenar | 🟡 Média |
| **R**epudiation | Ausência de trilhas criptograficamente verificáveis | Impossível provar origem da mensagem | 🟡 Média |
| **I**nformation disclosure | Tópicos legíveis se houver downgrade de cifra | Exposição de rotas e cargas | 🟡 Média |
| **D**enial of service | Floods de publish/subscribe | Broker sobrecarregado, telemetria perdida | 🟢 Baixa |
| **E**levation of privilege | Credenciais de teste com acesso amplo | Invasor publica em qualquer tópico | 🔴 Alta |

**Juliana:** "Temos três ameaças críticas. Vamos priorizá-las por camada."

---

### Ato 4 — Contramedidas por camada: endurecendo a arquitetura

A equipe define um plano de mitigação estruturado por camada da arquitetura IoT.

#### 4.1 — Camada de Dispositivo

| Vulnerabilidade | Contramedida | Implementação no Atlas | Trade-off |
| --- | --- | --- | --- |
| Credenciais compartilhadas | Identidade única por hardware (UUID + X.509) | Cada gateway recebe certificado único | Custo de PKI gerenciada |
| Firmware adulterado | Secure boot + assinatura de firmware | OTA só aceita imagens assinadas | Processo de build mais complexo |
| Replay de mensagens | Carimbo de tempo + nonce por mensagem | Backend valida timestamp e rejeita nonce repetido | Overhead de processamento |
| Perda de dados offline | Fila persistente local com backoff exponencial | Gateway armazena até reconectar | Custo de storage local |

**Marina:** "Nenhum gateway entra em campo sem certificado único. Zero exceções."

---

#### 4.2 — Camada de Comunicação (Gateway ↔ Broker)

| Vulnerabilidade | Contramedida | Implementação no Atlas | Trade-off |
| --- | --- | --- | --- |
| TLS unilateral | **mTLS** obrigatório (mutual TLS) | Broker valida certificado do cliente | Complexidade de gestão de certificados |
| Senhas compartilhadas | Autenticação via certificado X.509 | Elimina usuário/senha | Dependência de CA (Certificate Authority) |
| Certificados eternos | Rotacionamento automático (janela de 90 dias) | Renovação via ACME/Let's Encrypt | Janelas de manutenção |
| Rede pública 4G | APN privada para frota | Reduz exposição da internet pública | Custo adicional por SIM |
| Tópicos abertos | Namespace por dispositivo + ACL fina | `lt/{deviceId}/telemetria` (publish), `lt/{deviceId}/cmd` (subscribe) | Configuração manual por dispositivo |
| QoS inadequado | Telemetria QoS 1, comandos QoS 2 | Balanceio entre confiabilidade e latência | Overhead de rede |

**Tabela de QoS recomendado:**

| Tipo de mensagem | QoS | Justificativa |
| --- | --- | --- |
| Telemetria (temperatura, GPS) | 1 (at least once) | Perda ocasional tolerável, latência importa |
| Comandos remotos (desligar motor) | 2 (exactly once) | Não pode ser executado duas vezes |
| Heartbeat | 0 (at most once) | Apenas para monitoramento, não crítico |

---

#### 4.3 — Camada de Broker MQTT

| Vulnerabilidade | Contramedida | Implementação no Atlas | Trade-off |
| --- | --- | --- | --- |
| Broker "aberto" | Instância dedicada com ACL fina | Regra: publish apenas em `lt/{CN do cert}/telemetria` | Custo de instância gerenciada |
| Flood de mensagens | Rate limiting por cliente + max inflight | 10 msg/s por cliente, 5 inflight | Possível perda em picos legítimos |
| Sessões eternas | Session expiry curto (5 min) | Cliente desconectado precisa reautenticar | Overhead de reconexão |
| AuthN fraca | mTLS como método único de autenticação | CN do certificado mapeia para deviceId | — |
| AuthZ genérica | Políticas por CN (Common Name do certificado) | `CN=SPC-023` só publica em `lt/SPC-023/*` | Gestão granular de políticas |
| Logs não auditáveis | Logs assinados e exportados para SIEM | Integração com Splunk/ELK | Custo de SIEM |
| Bridge inseguro | Conector com assinatura HMAC de mensagens | Pipeline valida HMAC antes de processar | Overhead criptográfico |

**Pedro:** "Vou provisionar a nova instância hoje. Migração no fim de semana."

---

#### 4.4 — Camada de Backend (Processamento e Armazenamento)

| Vulnerabilidade | Contramedida | Implementação no Atlas | Trade-off |
| --- | --- | --- | --- |
| Payload não verificado | Validação de HMAC na entrada do pipeline | Rejeita mensagens sem assinatura válida | Latência adicional |
| Schema frouxo | Esquemas rígidos (JSON Schema) | Rejeita campos desconhecidos ou inválidos | Menor flexibilidade |
| Outliers físicos aceitos | Validação de contexto (temp impossível) | Rejeita temperatura fora de -20°C a +50°C | Pode descartar leituras válidas em edge cases |
| Redes misturadas | Segmentação: rede de ingestão ≠ analytics | VPC isolada para pipeline | Complexidade de rede |
| Secrets em env vars | Secret management centralizado (AWS Secrets Manager) | Rotação automática de credenciais | Custo de serviço gerenciado |
| RBAC inexistente | Princípio do menor privilégio + KMS | Lambda só lê do tópico, não escreve no banco diretamente | Mais permissões a gerenciar |

**Juliana:** "Backend não confia em ninguém. Valida tudo."

---

#### 4.5 — Princípios de Arquitetura: Tolerância a Falhas e Atributos de Qualidade

Com as contramedidas por camada definidas, Marina propõe uma discussão mais profunda sobre **princípios arquiteturais** que garantem resiliência.

**Marina:** "Não basta resolver este incidente. Precisamos de uma arquitetura que **previna** problemas semelhantes. Vou apresentar dois frameworks que usaremos daqui pra frente."

##### 4.5.1 — ISO/IEC 25010: Framework de Atributos de Qualidade

Juliana projeta um diagrama no quadro mostrando a **ISO/IEC 25010**, padrão internacional de qualidade de software:

| Grupo de Qualidade | Atributos Relevantes para IoT | Como aplicamos no Atlas |
| --- | --- | --- |
| **Reliability** | Availability, Fault Tolerance, Recoverability | Arquitetura em 3 níveis, buffer local, retry automático |
| **Security** | Confidentiality, Integrity, Authenticity | mTLS, HMAC, certificados únicos |
| **Performance Efficiency** | Time behavior, Resource utilization | QoS otimizado, rate limiting |
| **Maintainability** | Modularity, Testability | Componentes independentes, logs estruturados |
| **Usability** | Operability, Accessibility | Múltiplas interfaces (app, switch, RF) |

**Juliana:** "A ISO 25010 define **31 atributos de qualidade**. Para IoT, os mais críticos são Reliability e Security. Mas há um desafio: **sensores são FRACOS, cloud é FORTE**. Como equilibrar?"

##### 4.5.2 — O Desafio Arquitetural: Componentes Fracos + Componentes Fortes

| Componente | Nível de Qualidade | Limitações | Impacto no Sistema |
| --- | --- | --- | --- |
| **Sensores/Atuadores** | 🔴 POBRE (2/10) | Processamento limitado, falhas frequentes, sem criptografia nativa | Ponto único de falha |
| **Gateways** | 🟡 REGULAR (4/10) | Conectividade instável, energia limitada | Perda de dados offline |
| **Cloud Infrastructure** | 🟢 EXCELENTE (9/10) | Alta disponibilidade, segurança robusta, escalável | Dependência de rede |
| **Sistema IoT Final** | 🟢 MUITO BOM (8/10) | **Apenas com arquitetura híbrida** | Meta: 99,9% disponibilidade |

**Pedro:** "Como chegamos de 2/10 nos sensores para 8/10 no sistema final?"
**Marina:** "Com **táticas arquiteturais**. Deixa eu mostrar um exemplo prático."

##### 4.5.3 — Táticas Arquiteturais para Confiabilidade de Sensores

Marina desenha o diagrama de **Táticas Arquiteturais** aplicado ao controle de temperatura dos caminhões:

```
┌─────────────────────────────────────────────────────────────────┐
│  OBJETIVO: Medições confiáveis de temperatura (evitar falsos    │
│  positivos como no incidente de terça-feira)                     │
└─────────────────────────────────────────────────────────────────┘
                              │
                 ┌────────────┴────────────┐
                 │   TÁTICAS APLICADAS      │
                 └────────────┬────────────┘
                              │
        ┌─────────────────────┼─────────────────────┐
        │                     │                     │
        ▼                     ▼                     ▼
┌────────────────┐  ┌──────────────────┐  ┌──────────────────┐
│ 1. INTEGRIDADE │  │ 2. DETECÇÃO DE   │  │ 3. RECUPERAÇÃO   │
│    DE LEITURA  │  │    INCONSISTÊNCIA│  │    DE FALHAS     │
└────────────────┘  └──────────────────┘  └──────────────────┘
        │                     │                     │
        ▼                     ▼                     ▼
```

**Tabela de Táticas e Mecanismos:**

| Tática Arquitetural | Mecanismos Técnicos | Implementação no Atlas |
| --- | --- | --- |
| **1. Reading Integrity** (Integridade de Leitura) | • Múltiplos sensores por caminhão<br>• Leitura redundante (3x por minuto)<br>• Algoritmo de consolidação (mediana) | 3 sensores de temperatura por baú refrigerado; se 1 falhar, sistema usa os outros 2 |
| **2. Inconsistency Detection** (Detecção de Inconsistências) | • Validação de padrões históricos<br>• Predição baseada em contexto<br>• Detecção de falso positivo/negativo | Se temperatura variar >10°C em <1min, sistema rejeita e solicita nova leitura |
| **3. Consistency Recovery** (Recuperação de Consistência) | • Registro de alertas e eventos<br>• Snapshot do estado anterior<br>• Rollback automático | Se leitura inválida for detectada, sistema reverte para último estado consistente e marca sensor para manutenção |

**Carlos:** "Isso explica por que o ataque funcionou: tínhamos **1 sensor, 1 caminho, 0 validação**."
**Marina:** "Exatamente. Agora teremos **redundância em hardware E software**."

##### 4.5.4 — Arquitetura em 3 Níveis de Operação

Juliana apresenta a arquitetura final do Projeto Atlas, inspirada em padrões de **Fault-Tolerant Systems**:

| Nível | Modo de Operação | Disponibilidade | Funcionalidades Ativas | Cenário de Uso |
| --- | --- | --- | --- | --- |
| **Nível 0: Offline** | Gateway desconectado | 🟢 99,99% | Switch físico, leitura local de sensores | Falha total de rede; manutenção preventiva |
| **Nível 1: Local** | Gateway conectado à rede local (WiFi/Ethernet) | 🟢 99,5% | Monitoramento via app local, controle manual | Internet indisponível; operação em depósito |
| **Nível 2: Internet** | Gateway conectado à nuvem via 4G/LTE | 🟢 99,9% | Telemetria em tempo real, alertas automáticos, dashboards | Operação normal em rota |

**Diagrama de Contingência:**

```
Internet disponível? ──► SIM ──► Nível 2 (Cloud)
         │
         NÃO
         │
         ▼
Rede local disponível? ──► SIM ──► Nível 1 (Local)
         │
         NÃO
         │
         ▼
    Nível 0 (Offline) ──► Armazena dados localmente até reconectar
```

**Pedro:** "Com essa arquitetura, mesmo se o 4G cair, o motorista consegue monitorar a temperatura pelo app?"
**Marina:** "Sim. E quando reconectar, o gateway envia todos os dados armazenados via HTTP batch."

##### 4.5.5 — Trade-offs de Qualidade: Segurança vs. Usabilidade

Juliana alerta sobre um princípio fundamental de arquitetura:

> **"Toda decisão arquitetural envolve trade-offs. Aumentar um atributo pode degradar outro."**

**Exemplos de Trade-offs no Projeto Atlas:**

| Decisão Arquitetural | Atributo que Melhora | Atributo que Pode Degradar | Como Balanceamos |
| --- | --- | --- | --- |
| mTLS obrigatório | 🔒 **Security** +3 pontos | 🎨 **Usability** -1 ponto (complexidade de setup) | Provisionamento automático de certificados |
| Manutenção preventiva a cada 6h | 🔧 **Maintainability** +2 | ⚡ **Availability** -1 (sistema fica offline) | ❌ Rejeitado. Manutenção a cada 24h é o ótimo |
| Buffer local de 7 dias | ⚡ **Availability** +3 | 💾 **Storage** -1 (custo de memória) | Aceitável: custo de R$15/gateway |
| Validação tripla de sensores | 🎯 **Reliability** +3 | ⏱️ **Performance** -0,5s latência | Aceitável: alertas críticos toleram 0,5s |

**Juliana:** "No incidente de terça, priorizamos **velocidade** sobre **validação**. Agora invertemos: preferimos 0,5s de latência a mais do que um falso positivo que custa R$180 mil."

##### 4.5.6 — Meta de Disponibilidade: 99,9% (Three Nines)

Com as táticas implementadas, a equipe estabelece métricas de qualidade:

| Métrica de Qualidade | Meta do Projeto Atlas | Como Medimos |
| --- | --- | --- |
| **Disponibilidade** | 99,9% (8,76h downtime/ano) | Uptime monitoring com PingDom |
| **MTTR** (Mean Time to Recovery) | < 10 min | Tempo entre detecção e contenção de falhas |
| **MTTD** (Mean Time to Detect) | < 2 min | Tempo entre falha e alerta no NOC |
| **Taxa de Falsos Positivos** | < 0,1% | Alertas inválidos / total de alertas |
| **Cobertura de Testes de Segurança** | > 90% | Cenários STRIDE testados vs. total |

**Henrique Duarte (Diretoria):** "99,9% significa que podemos ter até 8 horas de falha por ano. Isso é aceitável?"
**Marina:** "Para a fase piloto, sim. Quando escalarmos para 120 caminhões, subiremos para 99,99% (four nines = 52min/ano)."

---

#### 4.6 — Camada de Operações (Runbooks e Playbooks)

| Cenário | Ação de contenção | Ação de erradicação | Ação de recuperação |
| --- | --- | --- | --- |
| Telemetria falsa detectada | Revogar certificado do dispositivo suspeito | Rotacionar todas as credenciais de teste | Validação cruzada com sensores redundantes |
| Flood de mensagens | Bloquear clientId no broker | Revisar rate limits | Restaurar QoS normal |
| Replay de mensagens antigas | Limpar retained messages | Forçar nonce único por mensagem | Recalcular dashboards afetados |
| Downgrade de cifra | Forçar TLS 1.3 mínimo | Auditar configurações de broker | Testar reconexão de todos os gateways |

**Runbook de incidente — Falsificação de telemetria:**

1. **Detecção:** Alerta automático no NOC (temperatura fora do padrão físico esperado)
2. **Contenção:** Revogar certificado do cliente suspeito (< 2 min)
3. **Investigação:** Analisar logs do broker para identificar IP e clientId
4. **Erradicação:** Rotacionar credenciais de teste, forçar mTLS
5. **Recuperação:** Validar dados limpos, recalcular métricas afetadas
6. **Pós-incidente:** Documentar lições aprendidas, atualizar playbook

**Carlos:** "Vou treinar o time do NOC com este runbook amanhã."

---

### Ato 6 — Prova de correção: testando as defesas

Com as contramedidas implementadas, a equipe executa **testes de intrusão controlados**:

| Teste de segurança | Método | Resultado esperado | Resultado obtido |
| --- | --- | --- | --- |
| **Replay de credenciais antigas** | Tentar conectar com certificado revogado | Broker recusa na camada TLS | ✅ Conexão negada (TLS handshake falhou) |
| **Replay de mensagem válida** | Reenviar payload capturado com mesmo nonce | Backend rejeita por nonce duplicado | ✅ Mensagem descartada (nonce já visto) |
| **Flood de publish** | Enviar 50 msg/s de um único cliente | Rate limiting ativa, cliente isolado | ✅ Cliente bloqueado após 10 msg/s |
| **Publicação em tópico de outro dispositivo** | Tentar publicar em `lt/SPC-041/telemetria` com certificado de SPC-023 | ACL bloqueia (CN não corresponde ao tópico) | ✅ Publish rejeitado (ACL violation) |
| **Downgrade de TLS** | Forçar TLS 1.1 | Broker rejeita conexão (TLS 1.3 mínimo) | ✅ Conexão negada (protocol version) |

**Marina:** "Todas as defesas operacionais. Dashboard voltou ao normal."

---

### Ato 7 — Apresentação executiva: custo vs. risco evitado

A diretoria é informada em linguagem executiva. Henrique Duarte questiona o investimento adicional.

**Pedro:** "Incremento mensal de infraestrutura segura: R$ 12 mil (mTLS gerenciado, PKI, SIEM)."
**Marina:** "Custo evitado de uma **única carga de fármacos perdida**: R$ 180 mil. Payback em 45 dias."
**Juliana:** "Métricas de resiliência após endurecimento:"

| Métrica | Antes do incidente | Depois das correções |
| --- | --- | --- |
| **Falso-positivo por telemetria adulterada** | 2 eventos/semana | 0 eventos (últimas 4 semanas) |
| **Mean Time to Detect (MTTD)** | 14 min | 2 min |
| **Mean Time to Contain (MTTC)** | N/A (sem runbook) | 9 min |
| **Certificados únicos em campo** | 0% (credenciais compartilhadas) | 100% (3/3 gateways) |
| **mTLS ativo** | Não | Sim (TLS 1.3) |

**Henrique:** "A conta fecha. Aprovado. Mas quero isso documentado para auditoria."

**Juliana fecha a reunião com um compromisso:**

> "Pacto de disciplina técnica: nenhuma feature nova entra sem **revisão de ameaças** (STRIDE), e todo componente passa por **checklist de segurança** antes de produção."

---

## Atividade de grupo em sala

**Desafio:** Cada grupo recebe um **cenário de ataque** diferente e deve elaborar uma apresentação em markdown destrinchando o cenário e propondo um plano de mitigação completo baseado na arquitetura IoT que definiram na Aula 03.

### Cenários de ataque (1 por grupo - 5 grupos):

1. **Ataque de Man-in-the-Middle:** Invasor intercepta comunicação entre gateway e broker, tenta ler e alterar mensagens.
2. **Ataque de Denial of Service:** Invasor envia flood de 1000 mensagens/segundo no broker MQTT.
3. **Ataque de Firmware Malicioso:** Invasor tenta instalar firmware adulterado em gateway via OTA.
4. **Ataque de Credential Stuffing:** Invasor obtém lista de credenciais vazadas e tenta acessar múltiplos dispositivos.
5. **Ataque de Spoofing de Dispositivo:** Invasor clona identidade de gateway legítimo e publica telemetria falsa.

### Entregável (por grupo):

**Apresentação em markdown** contendo:

1. **Descrição do cenário de ataque:** Como o ataque acontece passo a passo na arquitetura da LogiTrack.
2. **Análise STRIDE:** Tabela com 6 categorias identificando ameaças específicas do cenário.
3. **Contramedidas por camada:** Tabela com mitigações para dispositivo, comunicação, broker, backend e operações.
4. **Runbook de incidente:** Etapas de detecção, contenção, erradicação e recuperação.
5. **Justificativa executiva:** Argumento de custo vs. risco evitado para convencer a diretoria.

### Formato da apresentação:

- **Arquivo markdown** (.md) com tabelas e estrutura clara
- **Sem slides** - apresentação direta do markdown
- **Tempo de apresentação:** 5-7 minutos por grupo
- **Discussão em sala:** Após cada apresentação, turma debate as soluções propostas

### Pontos para discussão:

- As contramedidas são realistas para a LogiTrack?
- Há trade-offs que não foram considerados?
- O runbook é executável pela equipe do NOC?
- Outras soluções possíveis que o grupo não mencionou?

---

## Ganchos para a próxima aula — Coleta de Dados com MQTT e HTTP

- A arquitetura está segura. Agora é hora de escalar: como **coletar dados de forma robusta** em produção?
- MQTT é ideal para telemetria, mas **quando usar HTTP**? E como **integrar ambos**?
- Como garantir que dados não se percam durante quedas de rede? **Buffer local, QoS e persistência**.
- **Marina anuncia:** "Na próxima semana, ampliamos o piloto de 3 para 15 caminhões. Precisamos de um pipeline de coleta que aguente."

---

## Referências Técnicas desta Aula

Esta aula foi baseada em pesquisas científicas de arquitetura de sistemas IoT:

1. **Hayashi, V. T., Garcia, V., Andrade, R. M., & Arakaki, R. (2020).** "OKIoT Open Knowledge IoT Project: Smart Home Case Studies of Short-term Course and Software Residency Capstone Project". *IoTBDS 2020 - 5th International Conference on Internet of Things, Big Data and Security*.
   - **Conceitos aplicados:** Arquitetura em 3 níveis de operação (offline, local, internet), fault-tolerant design, redundâncias de comunicação.

2. **Arakaki, R., Hayashi, V. T., & Ruggiero, W. V. (2020).** "Available and Fault Tolerant IoT System: Applying Quality Engineering Method". *ICECCE 2020 - 2nd International Conference on Electrical, Communication and Computer Engineering*.
   - **Conceitos aplicados:** ISO/IEC 25010 (atributos de qualidade), táticas arquiteturais (Reading Integrity, Inconsistency Detection, Consistency Recovery), análise de trade-offs, métricas de disponibilidade (MTTR, MTTD).

3. **ISO/IEC 25010:2011.** "Systems and software engineering — Systems and software Quality Requirements and Evaluation (SQuaRE) — System and software quality models".
   - **Conceitos aplicados:** 8 grupos de atributos de qualidade (Reliability, Security, Performance, Maintainability, Usability, Compatibility, Portability, Functional Suitability).

---

**Preparado para a Aula 05:**
- Revisar conceitos de MQTT (pub/sub, QoS, retained messages)
- Pesquisar padrões de integração HTTP/REST em IoT
- Estudar estratégias de buffer local e retry
- Entender diferenças entre push (MQTT) e pull (HTTP polling)
- Revisar princípios de arquitetura tolerante a falhas (Aula 04)
