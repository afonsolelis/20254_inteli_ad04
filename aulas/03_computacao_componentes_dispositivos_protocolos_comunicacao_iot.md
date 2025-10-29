# [3] Computação - Componentes de Dispositivos e Protocolos de Comunicação IoT

**Unidade:** Semana 03  
**Data:** 31/10/2025

## Tempo estimado
- Daily inicial
- Aula narrativa/prática
- Atividade avaliativa em sala após a instrução formativa

## Objetivos de aprendizagem
- Acompanhar o capítulo “Conectando Pontos” da jornada da LogiTrack.
- Traduzir decisões narrativas em escolhas técnicas de componentes IoT.
- Comparar protocolos e estratégias de integração OT/IT por meio de tabelas de decisão.
- Relacionar arranjos físicos de produção com o fluxo de dados do Projeto Atlas.

---

## Onde paramos na história
- **Aula 01:** a LogiTrack descobriu a arquitetura IoT e mapeou camadas críticas.
- **Aula 02:** o time financeiro provou a viabilidade do Projeto Atlas e garantiu orçamento.
- **Aula 03:** Marina e a equipe entram na Base Atlas para transformar números em dispositivos conectados.

---

## Conectando Pontos — Storytelling da Aula

### Ato 1 — Reunião na Base Atlas
*"O que definirmos aqui vai determinar a confiabilidade do sistema", alerta Marina Costa enquanto liga o projetor. Na mesa estão três kits: LoRa, Wi-Fi e 4G/LTE. Pedro Nascimento defende 4G nos caminhões; Marina propõe LoRa nos depósitos. Juliana Prado lembra que a operação é heterogênea — a arquitetura terá de ser híbrida.*

| Elemento em debate | Insight narrativo | Dado técnico para discussão |
| --- | --- | --- |
| Conectividade em campo | Frota cruzando áreas urbanas e rurais | Alcance, consumo e custo comparados abaixo |
| Continuidade do serviço | Falhas de rede simuladas no teste | Estratégia com buffer local + reenvio |
| Escalabilidade | Crescimento para 120 caminhões | Requisitos mínimos de plataforma (Figura 2) |

### Ato 2 — Escolha dos componentes de cada camada

![Arquitetura IoT da Base Atlas](https://res.cloudinary.com/dyhjjms8y/image/upload/v1761734211/project_atlas/iot_architecture.png)
*Figura 1 – Blueprint usado por Marina para explicar as camadas do Projeto Atlas.*

| Camada | Dispositivos selecionados | Decisão da equipe | Pergunta norteadora para a aula |
| --- | --- | --- | --- |
| Percepção | Sensores de temperatura, vibração, GPS, antenas RFID | Mix de fabricantes homologados; prioridade para baixo consumo | Como garantir manutenção fácil nos caminhões? |
| Edge & Gateways | Gateways veiculares com armazenamento local, PLCs nos hubs | Gateways fazem cache e determinam o protocolo conforme cobertura | Onde posicionar redundâncias físicas? |
| Middleware | FIS-IoT (Node-RED + serviços REST/MQTT) | Combina MQTT para telemetria e REST para integrações corporativas | Qual camada recebe alertas críticos primeiro? |
| Aplicações | KERN (process chain), dashboards operacionais | Dados chegam com carimbo e contexto logístico | Quem valida as exceções antes de gerar alertas? |

### Ato 3 — Tabela de decisão de conectividade

| Tecnologia | Alcance típico | Consumo de energia | Custo recorrente | Uso definido pela equipe |
| --- | --- | --- | --- | --- |
| LoRa | 1–15 km | Muito baixo | Gateway próprio | Depósitos regionais e pátios com baixa infraestrutura |
| Wi-Fi | 50–100 m | Médio | Infraestrutura local | Centros de distribuição e manutenção preventiva |
| 4G/LTE | Cobertura nacional | Alto | Plano por SIM | Caminhões em rota longa e contingência para sensores críticos |

Marina propõe um firmware que permite alternar entre essas mídias. Carlos questiona a complexidade. Juliana responde: *“Nosso ambiente é heterogêneo; a arquitetura precisa se adaptar, não o contrário.”*

### Ato 4 — Protocolos na mesa de debate

![Requisitos técnicos mínimos](https://res.cloudinary.com/dyhjjms8y/image/upload/v1761734221/project_atlas/fis_tech_requirements.png)
*Figura 2 – Checklist que Marina usa para mostrar que a infraestrutura AIX suportará o FIS-IoT.*

| Protocolo | Papel no Projeto Atlas | Por que foi escolhido | Trade-off aceito |
| --- | --- | --- | --- |
| MQTT | Telemetria contínua (sensores → broker) | Leve, publish/subscribe, tolera perda momentânea | Precisa de broker estável e controle de tópicos |
| HTTP/REST | Sincronização com KERN e dashboards | Facilita auditorias e APIs corporativas | Overhead maior em conexões persistentes |
| TCP (captura direta) | Interface com antenas RFID e PLCs | Baixa latência, integração legada | Requer tuning de firewall e roteamento dedicado |
| Buffers locais | Edge cache nos gateways | Garantia de resiliência durante quedas | Exige política de descarte e validade de dados |

**Diálogo-chave:**  
> Carlos: “Por que não simplificar e usar só HTTP?”  
> Juliana: “Porque dados críticos não podem esperar uma rede reconectar. Trabalhamos com camadas adaptativas: MQTT quando há cobertura, armazenamento local quando cai, HTTP para reenviar logs.”  

![Integração com antenas](https://res.cloudinary.com/dyhjjms8y/image/upload/v1761734229/project_atlas/ot_integration_antennas.png)  
*Figura 3 – Caminho de dados de etiquetas RFID lidas nos centros de distribuição.*

![Integração com PLCs](https://res.cloudinary.com/dyhjjms8y/image/upload/v1761734240/project_atlas/ot_integration_data_capture.png)  
*Figura 4 – Integração com PLCs e módulos FIS para consolidar leitura de sensores veiculares.*

### Ato 5 — Testes de campo na rota São Paulo–Campinas

| Métrica observada | MQTT | HTTP | Comentário da equipe |
| --- | --- | --- | --- |
| Largura de banda consumida | Redução de 83% vs HTTP | Base de comparação | Permitiu manter custo do plano 4G dentro do orçamento |
| Latência média | 1,3 s | 3,8 s | MQTT entrega alertas quase em tempo real |
| Recuperação pós-falha | Reenvio automático via buffer | Manual | Estratégia híbrida aprovada pelo conselho |

Quando a equipe derruba propositalmente o sinal 4G durante 10 minutos, o gateway armazena as leituras. Ao reconectar, o lote completo é enviado via HTTP para o FIS, preservando a trilha de auditoria.

### Ato 6 — Layout logístico e posicionamento dos ativos

| Ambiente LogiTrack | Layout predominante | Ponto IoT crítico | Lição para a operação |
| --- | --- | --- | --- |
| Linha de expedição nos depósitos | Layout linear | Antenas RFID alinhadas às docas para fechamento automático de carga | Sincronizar PLCs com leitura de etiquetas evita erros de embarque |
| Oficina de manutenção | Arranjo por processo | Gateways móveis e Wi-Fi industrial para diagnósticos | Flexibilidade exige redes mesh e dados locais |
| Hub metropolitano | Layout em U | Checkpoints IoT no início e fim da célula | Permite comparar entrada/saída de carga com dados MQTT |
| Rotas de longa distância | Fluxo distribuído | Gateways veiculares com fallback 4G | Planejar janelas de reconexão para uploads pesados |

## Atividade ponderada pós-aula
**Desafio:** cada grupo assume um trecho da operação da LogiTrack (expedição, oficina, hub metropolitano ou rota longa).  
**Entregáveis:**
- Mapa físico (pode ser desenhado) com sensores, gateways e pontos de protocolo.
- Tabela justificando a escolha de conectividade (baseada nas tabelas da aula).
- Plano de contingência: o que acontece se o MQTT cair? e se o HTTP ficar indisponível?
- Checklist de requisitos mínimos reaproveitando a Figura 2.

**Critérios de avaliação (0–10):**
- Adequação técnica das escolhas (0–3).
- Clareza do arranjo físico e cobertura de dados (0–3).
- Uso das evidências dos testes de campo (0–2).
- Criatividade na contingência e ligação com storytelling (0–2).

---

## Ganchos para a próxima aula — Segurança em IoT
- Dados híbridos exigem políticas de criptografia e atualização OTA (tema da Aula 04).
- O buffer local virou ponto crítico: como protegê-lo contra adulteração?
- Quem garante que antenas e PLCs não serão vetores de ataque?
> Henrique Duarte encerra a reunião: *“Pela primeira vez vejo dados viajando da estrada para a nuvem. Agora precisamos garantir que ninguém intercepte essa rota.”*
