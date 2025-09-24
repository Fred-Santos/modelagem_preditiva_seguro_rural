# Modelo Preditivo de Seguro Rural (PSR)

Este repositório contém o desenvolvimento de um **modelo de Machine Learning** aplicado ao **Programa de Subvenção ao Prêmio do Seguro Rural (PSR)**, no Brasil.  
O objetivo é explorar a viabilidade de **previsão de valores de indenização e comportamento de sinistros**, a partir da base pública do **SISSER** (2006–2025).  

## 🎯 Objetivo

- Investigar o potencial preditivo dos dados do PSR.  
- Testar diferentes abordagens de modelagem (regressão, árvores de decisão, ensembles).  
- Comparar métricas de desempenho (MAE, RMSE, R², MAPE).  
- Documentar limitações e próximos passos para modelos mais robustos.  

## 📂 Estrutura

```
modelo_seguro_rural/
├─ data/
│  ├─ raw/        # Dados originais do SISSER (2006–2025)
│  ├─ processed/  # Dados tratados e enriquecidos (métricas derivadas, flags)
├─ notebooks/
│  ├─ modelo_seguro_rural.ipynb  # Desenvolvimento do modelo
├─ reports/
│  ├─ figuras/    # Gráficos gerados pelo notebook
│  └─ resultados/ # Saídas de avaliação do modelo
├─ docs/          # Documentação de apoio
```

## 🧭 Metodologia

O projeto segue a lógica **CRISP-DM**, em continuidade ao repositório da análise exploratória:

1. **Business Understanding**  
   - Motivação: avaliar se os dados públicos do PSR permitem modelagem preditiva confiável.  
2. **Data Understanding**  
   - Fonte: [SISSER — dados abertos](https://dados.gov.br/dataset/sisser3).  
   - Abrangência: apólices de 2006 a 2025, nível de proposta/apólice.  
3. **Data Preparation**  
   - Limpeza, padronização e derivação de métricas (sinistralidade, eficiência da subvenção, etc.).  
4. **Modeling**  
   - Testes com modelos de regressão para previsão de valores indenizados.  
5. **Evaluation**  
   - Comparação de métricas (MAE, RMSE, R²).  
   - Discussão sobre limitações e erros.  
6. **Deployment / Reporting**  
   - Resultados documentados em relatório executivo e visualizações.  

## ⚙️ Instalação

```bash
git clone https://github.com/seu-usuario/modelo_seguro_rural.git
cd modelo_seguro_rural
pip install -r requirements.txt
```

## **Tabela** base https://drive.google.com/file/d/17CsmT8jP62Y9xILO7zamlc21xm9G39LG/view?usp=drive_link

## 📊 Resultados (parciais)

- Primeiros modelos testados apresentaram **baixa acurácia** (R² próximo de zero).  
- Indicativo de que os dados do PSR, isoladamente, não são suficientes para boa previsão de sinistros.  
- Próximos passos incluem enriquecer o dataset com variáveis externas (clima, safra, geoespaciais).  

## 📜 Licença

[MIT](LICENSE)  
