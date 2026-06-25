# Estrutura de Dados

Esta pasta contém os dados utilizados no projeto de arquitetura medalhão aplicado aos indicadores de alfabetização do INEP.

---

# Organização da Pasta

```text
data/
└── raw/
    └── alfabetizacao/
```

---

# raw/

A pasta `raw/` armazena os dados brutos utilizados no projeto.

Os arquivos presentes nesta camada representam a origem oficial dos dados e permanecem sem transformações estruturais relevantes.

Nesta etapa:
- os dados são preservados;
- não existe tratamento analítico;
- não ocorre padronização;
- não há remoção de registros.

O objetivo principal é manter a rastreabilidade e integridade da informação original.

---

# Fonte dos Dados

Os dados utilizados foram obtidos a partir de bases públicas relacionadas aos indicadores de alfabetização do INEP.

Os arquivos contêm informações como:
- ano;
- município;
- UF;
- taxa de alfabetização;
- médias educacionais;
- metas de alfabetização;
- indicadores de participação.

---

# Estrutura Utilizada

## alfabetizacao/

Contém os arquivos CSV utilizados no pipeline batch do projeto.

### Arquivos utilizados

- br_inep_avaliacao_alfabetizacao_municipio.csv
- br_inep_avaliacao_alfabetizacao_uf.csv
- br_inep_avaliacao_alfabetizacao_meta_alfabetizacao_brasil.csv
- br_inep_avaliacao_alfabetizacao_meta_alfabetizacao_uf.csv
- br_inep_avaliacao_alfabetizacao_meta_alfabetizacao_municipio.csv

---

# Objetivo da Camada Raw

A camada raw representa a entrada inicial do pipeline de dados e serve como base para as etapas posteriores da arquitetura medalhão:
- Bronze;
- Silver;
- Gold.

Os dados desta camada serão posteriormente processados e refinados para geração de indicadores analíticos e dashboards.