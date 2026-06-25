# Dashboard Analítico

Esta pasta contém a documentação relacionada ao dashboard analítico do projeto.

O dashboard será desenvolvido utilizando Looker Studio conectado ao BigQuery para visualização dos indicadores educacionais processados na camada Gold.

---

# Objetivo do Dashboard

O principal objetivo do dashboard é permitir análise visual dos indicadores de alfabetização, metas educacionais e desempenho por UF e município.

A solução busca transformar os dados processados em informações analíticas para apoio à tomada de decisão.

---

# Fonte dos Dados

O dashboard consumirá tabelas analíticas da camada Gold geradas no BigQuery.

Principais tabelas:
- indicador_uf_meta_2030
- ranking_uf_alfabetizacao
- indicador_municipio_meta_2030
- ranking_municipios_maior_gap_meta_2030