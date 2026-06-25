# Arquitetura Streaming (Simulação de Dados)

## Objetivo

A arquitetura streaming foi projetada para simular a ingestão contínua de novos registros de alfabetização em tempo quase real.

O objetivo principal é demonstrar:
- processamento streaming;
- ingestão contínua;
- pipelines modernos de dados;
- arquitetura orientada a eventos;
- integração entre serviços cloud.

---

# Visão Geral da Arquitetura

```text
Python Producer → Pub/Sub → Dataflow → BigQuery → Dashboard
```

---

# Fluxo Completo da Arquitetura Streaming

## 1. Simulador de Dados (Producer Python)

Um script Python será responsável por simular o envio contínuo de eventos educacionais.

Os eventos serão gerados em formato JSON.

## Exemplo de evento

```json
{
  "ano": 2025,
  "uf": "SP",
  "municipio": "São Paulo",
  "taxa_alfabetizacao": 97.3,
  "fonte": "Simulador",
  "timestamp": "2025-05-24T12:30:00Z"
}
```

## Objetivos do Producer

- simular dados em tempo real;
- gerar eventos continuamente;
- representar ingestão streaming;
- testar pipelines em tempo quase real.

---

# 2. Pub/Sub

## Objetivo

O Google Pub/Sub será utilizado como serviço de mensageria da arquitetura.

O Pub/Sub recebe os eventos enviados pelo Producer Python.

## Principais características

- alta disponibilidade;
- escalabilidade;
- desacoplamento;
- processamento assíncrono;
- arquitetura orientada a eventos.

## Funcionamento

O Producer publica mensagens em um tópico Pub/Sub.

Exemplo:

```text
topic_alfabetizacao_streaming
```

---

# 3. Dataflow

## Objetivo

O Google Dataflow será responsável pelo processamento streaming dos eventos recebidos via Pub/Sub.

## Processamentos realizados

- leitura das mensagens;
- validação do schema;
- tratamento de campos;
- enriquecimento;
- padronização;
- roteamento para BigQuery.

## Benefícios

- processamento distribuído;
- pipeline escalável;
- integração nativa com GCP;
- suporte a streaming contínuo.

---

# 4. BigQuery Bronze Streaming

## Objetivo

A camada Bronze Streaming armazena os eventos recebidos em tempo quase real.

Nesta etapa:
- os dados permanecem próximos da origem;
- as transformações são mínimas;
- os eventos são preservados.

## Características

- ingestão contínua;
- baixa transformação;
- rastreabilidade;
- armazenamento histórico.

## Exemplo de tabela

```text
bronze.streaming_alfabetizacao
```

---

# 5. Camadas Silver e Gold

Após ingestão na Bronze Streaming, os dados podem ser processados para geração de indicadores analíticos.

## Silver

Responsável por:
- limpeza;
- padronização;
- tratamento de tipos;
- validação de dados.

## Gold

Responsável por:
- indicadores analíticos;
- agregações;
- KPIs;
- dashboards;
- análises em tempo quase real.

---

# 6. Dashboard em Tempo Quase Real

Os dashboards poderão consumir:
- dados históricos;
- dados streaming;
- indicadores atualizados continuamente.

## Principais visualizações

- taxa média atualizada;
- eventos recebidos;
- evolução temporal;
- indicadores por UF;
- municípios críticos;
- monitoramento em tempo quase real.

---

# Benefícios da Arquitetura Streaming

## Tempo Quase Real

Os dados ficam disponíveis rapidamente após ingestão.

## Escalabilidade

A arquitetura suporta crescimento do volume de eventos.

## Flexibilidade

Novos pipelines podem ser adicionados futuramente.

## Modernização

A arquitetura demonstra práticas modernas de engenharia de dados.

---

# Tecnologias Utilizadas

- Python
- Google Cloud Platform (GCP)
- Pub/Sub
- Dataflow
- BigQuery
- Looker Studio

---

# Conclusão

A arquitetura streaming complementa a arquitetura batch do projeto, permitindo simular cenários modernos de ingestão contínua e processamento em tempo quase real utilizando serviços da Google Cloud Platform.