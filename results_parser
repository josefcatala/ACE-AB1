# José F Català \ 21/04/2025 
library(tidyverse)
library(writexl)

# Fichero de origen generado por https://github.com/IngDiegoSosa/ACE-AB1/tree/main
input_file <- "/home/jfcatala/ownCloud/Bacplant/Secuenciación 16S UV/2025-04-16_E_Gonzalez/Resultados/BLAST_Results.txt"
output_file <- "/home/jfcatala/ownCloud/Bacplant/Secuenciación 16S UV/2025-04-16_E_Gonzalez/Resultados/BLAST_Results_Resumidos.xlsx"

# Creo un dataframe vacío con 3 columnas
df <- setNames(data.frame(matrix(ncol = 3, nrow = 0)), c("Fichero", "Especie", "Identidad"))

# Parseado linea a linea buscando palabras clave (optimizable)
lines <- readLines(input_file, warn = FALSE)

for (i in 0:length(lines)){
  if (length(lines[i]) > 0){
    if(startsWith(lines[i], "Analizando:")){
    seq <- stringr::str_split(lines[i], pattern = " ", simplify = TRUE)
    # print(seq[2])
    especie <- stringr::str_split(lines[i+1], pattern = "\\| ", simplify = TRUE)
    # print(especie[2])
    id <- stringr::str_split(lines[i+2], pattern = ": ", simplify = TRUE)
    # print(id[2])
    df[nrow(df)+1,] <- c(seq[2], especie[2], id[2])
  }}
}

# Guardo el resultado en un excel
write_xlsx(df %>% dplyr::arrange(Fichero), output_file)
