# Arquitetura Medalhão (Batch)

## Objetivo

A arquitetura medalhão foi utilizada neste projeto para organizar o processamento dos dados educacionais em diferentes camadas de qualidade e refinamento.

O principal objetivo é garantir:

- organização dos dados;
- rastreabilidade;
- escalabilidade;
- qualidade analítica;
- separação entre dados brutos e dados analíticos.

A arquitetura foi estruturada utilizando serviços da Google Cloud Platform (GCP).

---

# Visão Geral da Arquitetura

```text
CSV → Cloud Storage → Bronze → Silver → Gold → Dashboard
```

---

# Fluxo Completo do Projeto

## 1. Fonte de Dados

Os dados utilizados no projeto são provenientes de arquivos CSV contendo indicadores de alfabetização do INEP.

Os arquivos possuem informações como:

- ano;
- município;
- UF;
- taxa de alfabetização;
- média de português;
- metas educacionais;
- indicadores de participação.

---

# 2. Cloud Storage (Data Lake)

O Google Cloud Storage é utilizado como Data Lake da solução.

Nesta etapa:
- os arquivos CSV são armazenados;
- os dados permanecem brutos;
- não existem transformações;
- os dados originais são preservados.

## Objetivos da camada

- armazenamento centralizado;
- rastreabilidade;
- persistência dos arquivos;
- desacoplamento entre ingestão e processamento.

---

# 3. Camada Bronze

## Objetivo

A camada Bronze realiza a ingestão inicial dos dados no BigQuery.

Nesta etapa:
- os dados são carregados praticamente sem transformação;
- os dados permanecem próximos da origem;
- são adicionadas colunas técnicas de auditoria.

## Principais características

- ingestão dos dados brutos;
- preservação dos dados originais;
- baixa transformação;
- controle de origem dos arquivos;
- rastreabilidade.

## Exemplos de colunas técnicas

- data_ingestao;
- fonte_arquivo;
- timestamp_processamento.

---

# 4. Camada Silver

## Objetivo

A camada Silver é responsável pelo tratamento e padronização dos dados.

Nesta etapa são aplicadas regras de qualidade e transformação.

## Processamentos realizados

- conversão de tipos;
- padronização textual;
- remoção de duplicidades;
- tratamento estrutural;
- validação de chaves;
- normalização de dados.

## Regras aplicadas

### Conversão de tipos

Exemplo:

```sql
CAST(taxa_alfabetizacao AS FLOAT64)
```

### Padronização textual

Exemplo:

```sql
UPPER(sigla_uf)
```

### Remoção de duplicidades

Exemplo:

```sql
SELECT DISTINCT
```

## Tratamento de valores nulos

Os valores nulos provenientes da base oficial foram preservados quando representam ausência legítima de informação.

Exemplo:
- municípios sem indicador informado;
- metas ausentes;
- ausência de participação.

---

# 5. Camada Gold

## Objetivo

A camada Gold contém tabelas analíticas prontas para consumo em dashboards e análises estratégicas.

Nesta camada são gerados:
- KPIs;
- rankings;
- métricas;
- indicadores;
- comparações entre metas e resultados.

## Principais tabelas analíticas

### indicador_uf_meta_2030

Responsável por:
- comparar resultado atual x meta;
- calcular gap da meta;
- identificar status da meta.

### ranking_uf_alfabetizacao

Responsável por:
- ranking de estados;
- média de alfabetização;
- comparação entre UFs.

### indicador_municipio_meta_2030

Responsável por:
- análise granular por município;
- cálculo de gap;
- acompanhamento de metas.

---

# 6. Dashboard Analítico

As tabelas Gold serão consumidas pelo Looker Studio para construção de dashboards interativos.

## Principais visualizações

- ranking de UFs;
- evolução temporal;
- municípios críticos;
- indicadores de metas;
- análise comparativa;
- gráficos analíticos.

---

# Benefícios da Arquitetura Medalhão

## Organização

Separação clara entre:
- dados brutos;
- dados tratados;
- dados analíticos.

## Escalabilidade

A arquitetura permite crescimento futuro do volume de dados.

## Governança

Maior controle sobre:
- qualidade;
- rastreabilidade;
- versionamento lógico.

## Reusabilidade

As tabelas Silver e Gold podem ser reutilizadas por múltiplos consumidores.

---

# Tecnologias Utilizadas

- Python
- PySpark
- SQL
- Databricks
- Google Cloud Platform (GCP)
- Cloud Storage
- BigQuery
- Looker Studio

---

# Conclusão

A arquitetura medalhão permitiu construir um pipeline moderno de dados com separação entre ingestão, tratamento e consumo analítico, garantindo qualidade, organização e escalabilidade para análises educacionais.