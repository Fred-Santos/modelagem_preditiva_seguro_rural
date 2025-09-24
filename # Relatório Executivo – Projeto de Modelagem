# Relatório Executivo – Projeto de Modelagem Preditiva no Programa de Subvenção ao Prêmio do Seguro Rural (PSR)

## 1. Introdução (Business Understanding)

O Programa de Subvenção ao Prêmio do Seguro Rural (PSR) é um instrumento de política pública voltado à mitigação de riscos climáticos e de produção na agropecuária.  
Este projeto buscou avaliar a viabilidade de construir um **modelo preditivo atuarial**, inspirado na lógica de **frequência × severidade**, para estimar **valores esperados de indenização** a partir dos dados públicos do **SISSER (2006–2025)**.  

O objetivo principal foi testar **abordagens de calibração e previsão** que possam ser aplicadas em análises de risco e subscrição de seguro rural, servindo como prova de conceito.

---

## 2. Dados Utilizados (Data Understanding)

- **Fonte:** [SISSER — dados abertos](https://dados.gov.br/dataset/sisser3)  
- **Abrangência:** 2006–2025, em nível de proposta/apólice.  
- **Variável-alvo:** `VALOR_INDENIZAÇÃO`  

**Principais grupos de variáveis usadas no modelo:**
- **Cadastrais:** seguradora, UF, município, cultura agrícola.  
- **Cobertura:** área segurada, nível de cobertura, produtividade estimada/segurada.  
- **Financeiras:** prêmio líquido, subvenção, limite de garantia.  
- **Derivadas:** razão e diferença de produtividades, métricas temporais (vigência, ano, mês).  

---

## 3. Abordagem Metodológica (Modeling)

A modelagem foi estruturada em duas etapas:

1. **Modelo de Frequência (`P_FREQ`)**  
   - Objetivo: estimar a probabilidade de ocorrência de sinistro (indenização > 0).  
   - Técnica: **CatBoostClassifier**, com validação cruzada estratificada por segurado.  
   - Métricas: AUC, Average Precision (AP), Brier Score.  

2. **Modelo de Severidade / Expectativa de Valor (`EV_CAP` → `EV_FINAL`)**  
   - Baseline: valor esperado calculado a partir da severidade média (EV_CAP).  
   - Ajuste: calibração isotônica com **piso variável**, garantindo estabilidade em faixas de risco.  
   - Resultado final: `EV_FINAL`, valor esperado calibrado para cada apólice.  
   - Métricas: MAE, RMSE, comparação por decis e por grupos (UF × Cultura).  

---

## 4. Métricas de Avaliação

As seguintes métricas foram utilizadas:

### Frequência (classificação)
- **AUC (Area Under ROC Curve):** mede a capacidade discriminativa do modelo.  
- **AP (Average Precision):** avalia a qualidade da ordenação probabilística.  
- **Brier Score:** avalia calibração das probabilidades previstas.  

### Severidade / Valor esperado (regressão)
- **MAE (Erro Absoluto Médio):** média das diferenças absolutas entre observado e previsto.  
- **RMSE (Raiz do Erro Quadrático Médio):** sensível a grandes erros.  
- **Comparação por decis:** razão entre soma prevista e soma observada em grupos de risco.  
- **Comparação por UF × Cultura:** análise de desempenho em segmentos de maior exposição.  

---

## 5. Resultados Principais

- **Modelo de Frequência:**  
  - Obteve **AUC satisfatória** e Brier Score em linha com modelos de classificação de risco.  
  - As probabilidades calibradas (`P_FREQ`) foram integradas ao cálculo atuarial.  

- **Modelo de Severidade:**  
  - O baseline (`EV_CAP`) apresentava erros elevados.  
  - A calibração com isotonia e piso variável (`EV_FINAL`) reduziu MAE e RMSE em relação ao baseline.  
  - Melhora de calibração observada em quase todos os decis (previsão/observado mais próxima de 1).  

- **Análises por segmento:**  
  - Identificação dos principais **UF × Cultura** em exposição e ganho de acurácia.  
  - Exportação de rankings e tabelas para monitoramento futuro.  

---

## 6. Discussão e Limitações

- O modelo demonstra **ganhos de calibração e redução de erro**, mas ainda não é suficientemente robusto para uso operacional.  
- Principais limitações:
  - Dados do SISSER não trazem variáveis de clima, solo ou safra.  
  - Inconsistências históricas em prêmios, garantias e produtividades.  
  - Forte concentração em poucas regiões e culturas.  

---

## 7. Conclusão e Próximos Passos

O projeto mostrou que é possível estruturar um **pipeline de modelagem atuarial híbrida (frequência × severidade)** com dados públicos do PSR, produzindo estimativas calibradas de valor esperado de indenização.  

**Próximos passos recomendados:**
1. Enriquecimento dos dados com variáveis externas (clima, zoneamento agrícola, preços).  
2. Uso de técnicas de aprendizado não linear e modelos espaço-temporais.  
3. Exploração de dashboards para monitoramento de performance por UF e cultura.  
4. Estudos de fidelização e recorrência de segurados, utilizando a chave única.  

---
