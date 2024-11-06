# chocolate

library(tidyverse)
require(data.table)
require(dplyr)
require(tidyr)
install.packages("R.utils")
library(R.utils)
art_moma <- fread('dados rstudio/Dados/Art_Moma.csv.gz')
art <- fread('dados rstudio/Dados/Art.csv.gz')
chocolate <- fread('dados rstudio/Dados/chocolate.csv.gz')

ingredientes <- chocolate$ingredientes
origem_cacau <- chocolate$origem_cacau


#Quantos países produzem chocotale?

nrow(table(origem_cacau))

# b. Quantos chocolates existem com pelo menos 3 ingredientes?
#transformar ingredientes em lista
ingredientes <- strsplit(ingredientes, ",")

## b. Quantos chocolates existem com pelo menos 3 ingredientes?
#transformar ingredientes em lista
#verificar quantos chocolates tem pelo menos 3 ingredientes
sum(ingredientes >= 3)

#Quantos chocolates existem com 5 ingredientes? 
sum(ingredientes >=5)

#Quantos chocolates existem com pelo menos
#4 características memoráveis
class(memoraveis)
memoraveis <- chocolate$caracteristicas
memoraveis <- strsplit(memoraveis, ",")
# Calcular o número de ingredientes em cada item
num_ingredientes <- sapply(memoraveis, length)

# Contar quantos têm 4 ou mais ingredientes
total_com_pelo_menos_4 <- sum(num_ingredientes >= 4)
total_com_pelo_menos_4

library(dplyr)
library(stringr)

# Converter ingredientes para um data frame
ingredientes_df <- data.frame(ingredientes = ingredientes)

# Filtrar os elementos que contêm 'Sa' e contar
sal <- ingredientes_df %>% 
  filter(str_detect(ingredientes, "Sa")) %>% 
  summarise(contem_sal = n())

sal

# Quantos chocolates existem com Baunilha em sua composição
baunilha <- ingredientes_df %>% 
  filter(str_detect(ingredientes, 'V')) %>% 
  summarise(
    contem_baunilha = n()
  )
baunilha

# Quantos chocolates existem com Lecitina e Baunilha em sua composição?
baunilha_lecitina <- ingredientes_df %>% 
  filter(str_detect(ingredientes, 'V') & str_detect(ingredientes, 'L'))  %>% 
  summarise(
    contem_baunilha_lecitina = n()
  )
baunilha_lecitina


