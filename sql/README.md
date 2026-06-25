# Scripts SQL

Esta pasta contém os scripts SQL utilizados na construção das camadas analíticas do projeto no BigQuery.

Os scripts representam a implementação da arquitetura medalhão no ambiente cloud da Google Cloud Platform (GCP).

---

# Organização da Pasta

```text
sql/
├── bronze/
├── silver/
└── gold/
```

---

# bronze/

Contém scripts responsáveis pela ingestão inicial dos dados brutos.

Nesta etapa:
- os dados são carregados no BigQuery;
- poucas transformações são realizadas;
- os dados permanecem próximos da origem original.

## Objetivos

- ingestão de dados;
- rastreabilidade;
- preservação dos arquivos originais.

---

# silver/

Contém scripts responsáveis pelo tratamento e padronização dos dados.

Nesta camada são aplicadas:
- conversões de tipos;
- padronização textual;
- remoção de duplicidades;
- validações estruturais;
- limpeza de dados.

## Objetivos

- melhoria da qualidade dos dados;
- padronização;
- preparação para análises.

---

# gold/

Contém scripts responsáveis pela construção das tabelas analíticas e indicadores utilizados nos dashboards.

Nesta etapa são gerados:
- KPIs;
- rankings;
- métricas;
- agregações;
- análises comparativas.

## Principais indicadores

- ranking de UFs;
- gap para meta 2030;
- indicadores municipais;
- análise temporal;
- status das metas.

---

# Objetivo dos Scripts SQL

Os scripts SQL permitem reproduzir o pipeline analítico diretamente no BigQuery, facilitando:
- escalabilidade;
- governança;
- manutenção;
- processamento cloud;
- integração com dashboards.

---

# Tecnologias Utilizadas

- SQL
- BigQuery
- Google Cloud Platform (GCP)
```