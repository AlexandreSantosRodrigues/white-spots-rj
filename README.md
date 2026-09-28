# 📍 Inteligência Geográfica & Expansão Territorial: Identificação de "White Spots"

[![Visualizar Dashboard](https://img.shields.io/badge/Looker_Studio-Dashboard_Executivo-blue?style=for-the-badge&logo=looker)](https://datastudio.google.com/s/rZ7pUd7whek)
[![Visualizar Mapa](https://img.shields.io/badge/GitHub_Pages-Mapa_Interativo-darkred?style=for-the-badge&logo=github)](([SEU_LINK_DO_GITHUB_PAGES_AQUI](https://datastudio.google.com/s/kd9D8B9h6Pc)))

## 🎯 O Contexto do Case
A **ICONIC**, como líder absoluta no mercado brasileiro de lubrificantes (joint venture Ipiranga e Chevron), opera com uma capilaridade massiva. Em operações dessa magnitude, a decisão de onde abrir novas franquias, alocar distribuidores B2B ou expandir centros de serviços não pode depender de *feeling* comercial. 

Este projeto foi desenvolvido como uma **Prova de Conceito (PoC)** analítica para demonstrar a aplicação de **Geomarketing Avançado** na resolução de problemas de expansão territorial. 

Para ilustrar a metodologia, o algoritmo foi aplicado ao setor de Varejo de Moda no Rio de Janeiro. **A mesma arquitetura de dados, no entanto, é 100% escalável para a realidade da ICONIC**, permitindo cruzar dados de frota circulante, renda e saturação de oficinas/concorrentes para otimizar a malha logística e comercial da companhia.

## 📊 O Desafio Analítico
O objetivo do modelo é identificar **White Spots**: zonas territoriais que combinam altíssima densidade de público-alvo com um forte vazio competitivo (baixa pressão de concorrência num raio de influência predeterminado).

O script varreu 162 bairros do Rio de Janeiro cruzando dados demográficos oficiais com o mapeamento de polos comerciais, gerando um ranking automatizado de atratividade.

## ⚙️ Metodologia: Market Potential Index (MPI)
A solução foi construída utilizando geoprocessamento em Python, criando um Score padronizado que varia de 0 a 100.

**A Fórmula do MPI (O Motor do Modelo):**
`Score White Spot = (Densidade de Público-Alvo Normalizada * 60%) + (Ausência de Concorrência Normalizada * 40%)`

*   **Público-Alvo Estimado:** Habitantes da faixa economicamente ativa (20 a 49 anos) mapeados por setor censitário.
*   **Catchment Area (Raio de Influência):** Foi calculado um *buffer* espacial de 2 km a partir do centro de cada bairro (técnica fundamental para prever áreas de canibalização entre franquias).
*   **Heatmap de Concorrência:** Criação de clusters de concorrência atribuindo pesos maiores para grandes polos (Shoppings) e pesos menores para unidades de rua isoladas.

## 💡 Principais Insights da Aplicação
A aplicação do modelo revelou que a expansão baseada puramente no "senso comum" (foco em bairros nobres como Zona Sul e Barra da Tijuca) ignora as áreas de maior rentabilidade por m²:

1. **Megacomunidades Adensadas (Rocinha, Maré, Jacarezinho):** Dominam o ranking de *White Spots*. Apresentam uma densidade habitacional esmagadora (ex: Rocinha com mais de 26.000 hab/km²) e saturação competitiva formal igual a zero. Um verdadeiro oceano azul para formatos de microfranquias ou distribuição direta.
2. **Centro e Bairros de Passagem (Estácio, Catete, Catumbi):** Regiões de altíssimo fluxo pendular diário que sofrem um "apagão" de oferta, oferecendo oportunidades táticas de posicionamento de marca e alta conversão rápida.

## 🛠️ Stack Tecnológica & Engenharia de Dados
O pipeline foi estruturado focado em eficiência, consumindo APIs gratuitas e processamento em nuvem.

*   **Linguagem & Geoprocessamento:** Python (`Geopandas`, `Shapely`, `Folium`, `Scikit-learn`).
*   **Visualização e BI:** Looker Studio (Dashboard Executivo) e GitHub Pages (Visualização HTML Interativa via Folium).
*   **Dados Demográficos e Espaciais:** IBGE (Malha Municipal Shapefile e Censo 2022 via API Sidra).
*   **Extração de POIs (Points of Interest):** OpenStreetMap (Overpass API) para mapeamento de polígonos comerciais.
