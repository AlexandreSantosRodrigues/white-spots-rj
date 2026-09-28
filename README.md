# 📍 White Spots: Mapa de Oportunidade de Expansão para Varejo de Moda (RJ)

[![Visualizar Dashboard](https://img.shields.io/badge/Looker_Studio-Dashboard_Executivo-blue?style=for-the-badge&logo=looker)]((INSERIR_SEU_LINK_DO_LOOKER_STUDIO))
[![Visualizar Mapa](https://img.shields.io/badge/GitHub_Pages-Mapa_Interativo-darkred?style=for-the-badge&logo=github)]((INSERIR_SEU_LINK_DO_GITHUB_PAGES))

## 📊 O Desafio de Negócio
A ICONIC (marca fictícia de varejo de moda) planeja abrir novas lojas físicas e expandir sua rede de franquias no Rio de Janeiro. Tradicionalmente, decisões territoriais no varejo dependem de intuição comercial ou da disponibilidade imobiliária. 

O objetivo deste projeto é substituir o *feeling* por **Inteligência Geográfica**. Foi desenvolvido um modelo analítico para mapear a cidade e responder à pergunta executiva: **"Onde está o nosso próximo melhor ponto de venda?"** 

A estratégia focou em encontrar **White Spots**: regiões com altíssima concentração de público-alvo (20 a 49 anos) e um forte vazio competitivo (baixa presença de concorrentes diretos e grandes centros comerciais num raio de 2km).

## 💡 Principais Insights & Resultados
O algoritmo varreu 162 bairros do Rio de Janeiro. Contrariando a lógica comum de expansão — que foca excessivamente na Zona Sul e na Barra da Tijuca —, o modelo revelou que as maiores oportunidades estão em áreas densamente povoadas, mas negligenciadas pelas grandes âncoras varejistas.

**Top Oportunidades Identificadas:**
1. **Megacomunidades Adensadas (Rocinha, Maré, Jacarezinho):** Dominam o ranking de *White Spots*. Apresentam uma densidade habitacional esmagadora (ex: Rocinha com 26.000 hab/km²) e saturação competitiva formal igual a zero. Representam um oceano azul para formatos de loja compactos ou operações de microfranquia.
2. **Centro e Bairros de Passagem (Estácio, Catete, Catumbi):** Regiões de altíssimo fluxo diário e alta concentração residencial que sofrem um "apagão varejista", pois as marcas tendem a se aglomerar no eixo comercial primário do Centro (Uruguaiana/Carioca) ou nos shoppings de Botafogo.

## ⚙️ Metodologia e Market Potential Index (MPI)
A solução foi construída utilizando Python para a extração e manipulação espacial, criando um Score que varia de 0 a 100.

**A Fórmula do MPI:**
`Score White Spot = (Densidade de Público-Alvo Normalizada * 60%) + (Ausência de Concorrência Normalizada * 40%)`

*   **Público-Alvo:** Habitantes de 20 a 49 anos.
*   **Catchment Area (Raio de Influência):** Foi calculado um *buffer* espacial de 2 km a partir do centro de cada bairro.
*   **Heatmap de Concorrência:** Shoppings relevantes e lojas isoladas (Renner, Riachuelo, C&A, Farm) receberam pesos competitivos. A pressão concorrencial foi somada caso interceptasse o raio de 2 km do bairro analisado.

## 🛠️ Stack Tecnológica & Origem dos Dados
O projeto foi estruturado com uso de fontes de dados 100% abertas e arquitetura em nuvem gratuita.

*   **Linguagem & Geoprocessamento:** Python (`Geopandas`, `Shapely`, `Folium`, `Pandas`).
*   **Visualização:** Looker Studio (Dashboard Executivo) e GitHub Pages (HTML Interativo).
*   **Dados Demográficos:** IBGE (Malha Municipal e Censo 2022 via API).
*   **Dados de Concorrência:** OpenStreetMap (Overpass API) para mapeamento de polígonos comerciais.
