# Tech Challenge - Arquitetura Medalhão para Indicadores de Alfabetização

## Objetivo do Projeto

Este projeto tem como objetivo construir uma arquitetura moderna de dados utilizando o conceito de Medalion Architecture (Bronze, Silver e Gold) aplicada aos dados de alfabetização do INEP.

O projeto contempla processamento batch e streaming utilizando serviços da Google Cloud Platform (GCP), com foco em Engenharia de Dados, Analytics e visualização de indicadores educacionais.

---

## Arquitetura do Projeto

A solução foi estruturada utilizando:

* Google Cloud Storage
* BigQuery
* Pub/Sub
* Dataflow
* Looker Studio

Além de uma prova de conceito inicial realizada no Databricks para validação da arquitetura medalhão.

---

## Fluxo Batch

CSV → Cloud Storage → BigQuery Bronze → Silver → Gold → Dashboard

---

## Fluxo Streaming

Simulador Python → Pub/Sub → Dataflow → BigQuery → Dashboard

---

## Camadas Medalhão

### Bronze

Armazena os dados brutos provenientes da origem.

### Silver

Realiza limpeza, padronização, tratamento de tipos e validação dos dados.

### Gold

Contém tabelas analíticas e indicadores para consumo em dashboards e análises.

---

## Tecnologias Utilizadas

* Python
* PySpark
* SQL
* Databricks
* Google Cloud Platform (GCP)
* BigQuery
* Pub/Sub
* Dataflow
* Looker Studio

---

## Principais Indicadores

* Taxa de alfabetização por UF
* Gap para meta de alfabetização 2030
* Ranking de UFs
* Ranking de municípios
* Status de atingimento de metas

---

## Estrutura do Projeto

```text
arquitetura/
dashboard/
data/
docs/
notebooks/
sql/
src/
streaming/
```

---

## Próximos Passos

* Implementação da arquitetura no GCP
* Construção do pipeline streaming
* Criação do dashboard analítico
* Publicação dos resultados
