# Series
```{r packages, include = F}
packages <- c("data.table","ggplot2","zoo","astsa","xtable")
for(i in 1:length(packages)){
  if(!(packages[i] %in% installed.packages()))
    install.packages(packages[i])
  library(packages[i],character.only=TRUE)
}
```
