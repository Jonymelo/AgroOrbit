# AgroÓrbit
Plataforma de monitoramento espacial de queimadas e risco climático no Bioma Caatinga, desenvolvida para ajudar pequenos agricultores do Semiárido brasileiro que não têm acesso a tecnologia de monitoramento.

**Dashboard:** https://jonymelo.github.io/AgroOrbit/  
**Repositório:** https://github.com/Jonymelo/AgroOrbit

---

## O problema
Milhões de pequenos produtores rurais do Semiárido enfrentam grandes perdas nas safras sem conseguir se preparar com antecedência. No Bioma Caatinga, nos três anos analisados (2022, 2023 e 2024), setembro e outubro concentram os maiores volumes de focos de queimadas: mais de 80 mil focos em setembro e 127 mil em outubro (médias dos 3 anos). A precipitação cai a menos de 15mm nesses meses, criando condições extremas para incêndios e perdas agrícolas.

Em 2024, a Caatinga registrou aumento de 38% nos focos de calor em relação ao ano anterior, em meio à seca prolongada do Sertão. (Fonte: INPE BDQueimadas, 2024)

## O que o AgroÓrbit faz
Cruza dados do INPE, CHIRPS e INMET com um modelo preditivo de Machine Learning para gerar alertas simples e acessíveis sobre risco climático em 130 microrregiões do Bioma Caatinga, permitindo que o agricultor se prepare antes que o problema vire prejuízo.

Funcionalidades principais:
- Mapa interativo com 130 microrregiões coloridas por nível de risco (baixo, médio, alto, crítico)
- Alertas mensais de queimadas e condições climáticas
- Calendário de plantio com recomendações por microrregião para cada mês
- Modelo preditivo Random Forest com acurácia de 86,1%
- Análise comparativa de 2022, 2023 e 2024
- Projeção de tendência para 2025

---

## Fontes de dados
- **INPE BDQueimadas:** focos de calor detectados por satélite, 1,85 milhão de focos nos 9 estados
- **CHIRPS UCSB:** precipitação por satélite (resolução 0.05°, mensal), 36 meses (2022-2024)
- **INMET:** temperatura e umidade via rede de 1.026 estações de superfície
- **TerraBrasilis (INPE):** portal de download dos dados de focos
- **IBGE 2024:** Bioma Predominante por Município, lista oficial de 1.095 municípios da Caatinga
- **GOV.BR:** delimitação territorial oficial do Bioma Caatinga

**Período analisado:** 2022, 2023 e 2024  
**Nota:** O projeto foi desenvolvido em 2026. Os dados de 2025 não estavam consolidados nas fontes no período de coleta, o que é comum para dados científicos que passam por validação antes da publicação.  
**Bioma:** Caatinga, AL, BA, CE, MG, PB, PE, PI, RN e SE  
**Cobertura:** 130 microrregiões, 1.073 municípios  
**Nota sobre municípios:** Os 1.095 são o total oficial do IBGE para o Bioma Caatinga. Os 1.073 são os municípios efetivamente cobertos pelo monitoramento após filtragem das microrregiões disponíveis nas fontes.

---

## Metodologia do índice de risco
Cada microrregião recebe um índice de risco mensal entre 0 e 1:

| Variável | Peso | Lógica |
|---|---|---|
| Focos de queimada (INPE) | 30% | Mais focos = maior risco |
| Déficit de chuva (CHIRPS) | 30% | Menos chuva = maior risco |
| Umidade do ar (INMET) | 25% | Baixa umidade = maior risco |
| Temperatura (INMET) | 15% | Alta temperatura = maior risco |

Classificação: Baixo (< 0,30), Médio (0,30-0,50), Alto (0,50-0,70), Crítico (maior ou igual a 0,70)

---

## Tecnologias Aplicadas
| Categoria | Tecnologias |
|---|---|
| Back-end e Dados | Python, Pandas, NumPy, Scikit-Learn (Random Forest, K-Means), Matplotlib, SciPy |
| Front-end e Visualização | HTML, CSS, JavaScript (Vanilla), Chart.js |
| Infraestrutura e Ferramentas | VS Code, GitHub Pages |
| Inteligência Artificial | Suporte técnico via Google Gemini, ChatGPT e Claude (Anthropic) |

---

## Estrutura do projeto
```
AgroOrbit/
├── index.html
├── mapa_caatinga.html
├── README.md
├── notebooks/
│   ├── 01_exploracao_dados.ipynb
│   ├── 02_pipeline_dados.ipynb
│   ├── 03_modelo_risco.ipynb
│   ├── 04_tendencia_projecao.ipynb
│   └── 05_clustering_meses.ipynb
└── data/
    ├── icons/
    ├── images/
    ├── logo.png
    ├── dados_caatinga_filtrado.json
    ├── dados_finais_3anos.csv
    ├── dados_por_uf.csv
    ├── dados_por_microrregiao.csv
    └── recomendacoes_plantio.csv
```

---

## ODS relacionados
- **ODS 2:** Fome Zero e Agricultura Sustentável
- **ODS 9:** Indústria, Inovação e Infraestrutura
- **ODS 13:** Ação Contra a Mudança Global do Clima
- **ODS 15:** Vida Terrestre, proteção do Bioma Caatinga

---

## Global Solution FIAP 2026
Faculdade de Informática e Administração Paulista  
Tecnologia em Data Science, Big Data, BI e Data Engineering  
Global Solution 1º Semestre 2026, Turma 1TSC
