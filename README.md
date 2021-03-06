---
title: "Analise Variantes Covid 19"
author: "Cleyton Junior da Silva Cardoso e Wemerson José Vieira da Silva"
date: "`r Sys.Date()`"
output_dir: "."
output:
  prettydoc::html_pretty:
    theme: cayman
    highlight: github
---
# Análise de dados das variantes da Covid 19 relacionado a país

Os Dados extraídos do Kaggle através do  link: https://www.kaggle.com/yamqwe/omicron-covid19-variant-daily-cases 

O arquivo possui dados sobre os casos diário das variantes da covid 19 e seus respectivos países 
e possui 100.416 linhas e 6 colunas.

### carregando os pacotes:

```{r}
require(ggplot2)
require(DescTools)
require(datasets)
require(dplyr)
```

### Lendo o arquivo base de dados e Analisando a estrutura da tabela:

```{r}
cepas <- read.csv("/Users/cleytoncardoso/Desktop//covid-variants.csv")
head(cepas)
summary(cepas)
```

### Atribuindo a um data frame e lendo as primeiras linhas:

```{r}
variantesCovid <- as.data.frame(cepas)
typeof(variantesCovid)
head(variantesCovid)

```

### Renomeando o cabeçalho das colunas:

```{r}
names(variantesCovid) <- c("Pais", "Data", "Variante", "NumeroCasos", "PercentualCasos", "TotalCasos")
head(variantesCovid)
```

### Filtrando apenas as linhas com valores:

```{r}
variantesCovid <- variantesCovid %>% 
  filter(NumeroCasos != 0)
```

### Filtrando apenas as variantes mais conhecidas:

```{r}
variant_filt <- variantesCovid %>% 
  filter(Variante == "Alpha" | Variante == "Delta" | Variante == "Beta" | Variante == "Gamma" | Variante == "Omicron")
```

### Plotando grafico para saber quais as variantes com mais casos:

```{r}
ggplot(variant_filt,aes(Variante)) +
  geom_bar() +
  ylab("Quantidade") +
  xlab("Variante")
```

### filtrando apenas a variante  Omicron:

```{r}
variant_omicron <- variantesCovid %>% 
  filter(Variante == "Omicron")
```

### Verificando em como os casos de Omicron estão distribuídos por data:

```{r}
ggplot(variant_omicron, aes(x= Data, y=NumeroCasos)) +
  geom_point() +
  xlab("") +
  ylab("Casos")
```

### Verificando as datas que possuem mais casos da variante Omicron:

```{r}
ggplot(variant_omicron,aes(Data)) +
  geom_bar() +
  ylab("Quantidade") +
  xlab("Datas")
```
head(variantesCovid)

```

### Renomeando o cabeçalho das colunas:

```{r}
names(variantesCovid) <- c("Pais", "Data", "Variante", "NumeroCasos", "PercentualCasos", "TotalCasos")
head(variantesCovid)
```

### Filtrando apenas as linhas com valores:

```{r}
variantesCovid <- variantesCovid %>% 
  filter(NumeroCasos != 0)
```

### Filtrando apenas as variantes mais conhecidas:

```{r}
variant_filt <- variantesCovid %>% 
  filter(Variante == "Alpha" | Variante == "Delta" | Variante == "Beta" | Variante == "Gamma" | Variante == "Omicron")
```

### Plotando grafico para saber quais as variantes com mais casos:

```{r}
ggplot(variant_filt,aes(Variante)) +
  geom_bar() +
  ylab("Quantidade") +
  xlab("Variante")
```

### filtrando apenas a variante  Omicron:

```{r}
variant_omicron <- variantesCovid %>% 
  filter(Variante == "Omicron")
```

### Verificando em como os casos de Omicron estão distribuídos por data:

```{r}
ggplot(variant_omicron, aes(x= Data, y=NumeroCasos)) +
  geom_point() +
  xlab("") +
  ylab("Casos")
```

### Verificando as datas que possuem mais casos da variante Omicron:

```{r}
ggplot(variant_omicron,aes(Data)) +
  geom_bar() +
  ylab("Quantidade") +
  xlab("Datas")
```
