# Bulk_generator

*Bulk_generator()* function returns a list containing two data.frame : 
- **T** the *Num.mixtures* mixtures
- **P** the proportions used to build T

## Instalation

```{r, eval = FALSE}
if(!require(devtools)){install.packages("devtools")}
devtools::install_github("adrien0598/bulkfakr")
```

## Quick use
```{r, eval = FALSE}
# sc_counts a single cell dataset
# phenoData a data.frame with information about matching cellType and cellID

pseudoBulk <- Bulk_generator(sc_counts, phenoData)
pseudoBulk$T #mixtures
pseudoBulk$P #proportions
```
Cells in sc_counts that did not match with phenoData cellID will not be used.
If no match or only one cellType, execution will be stopped.

## Remove cells from phenoData
```{r, eval = FALSE}
pseudoBulk <- Bulk_generator(sc_counts, phenoData, forbidden_CT = c("cell_type1","cell_type2"))

pseudoBulk$T #mixtures
pseudoBulk$P #proportions, cell_type1 and cell_types2 will be 0 for all mixtures
```

## Force all cell types in all mixtures
```{r, eval = FALSE}
pseudoBulk <- Bulk_generator(sc_counts, phenoData, nb_CT_random = FALSE)

pseudoBulk$T #mixtures
pseudoBulk$P #proportions, no 0 (except rounded ones)
```

## Other parameters

- Num.mixtures = 1000
- pool.size = 100
- min.percentage = 1
- max.percentage = 99
- seed = 24
