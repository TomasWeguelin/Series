# Series
```{r packages, include = F}
packages <- c("data.table","ggplot2","zoo","astsa","xtable")
for(i in 1:length(packages)){
  if(!(packages[i] %in% installed.packages()))
    install.packages(packages[i])
  library(packages[i],character.only=TRUE)
}
```

```{r month_function}
add.months= function(date,n) seq(date, by = paste (n, "months"), length = 2)[2]

```


```{r read_data_serie1, include = F}
serie1 <- fread("monthly-new-york-city-average-te.csv")
names(serie1) <- c("Month","Temperature")
serie1$Month <- as.yearmon(serie1$Month)
serie1$Month <- as.Date(serie1$Month)
serie1$T <- c(1:nrow(serie1))
serie1 <- serie1[-which(year(serie1$Month)==last(year(serie1$Month))),]
```

```{r plot_serie1, echo = F}
ggplot(data = serie1, aes(x = Month, y = Temperature))+
  geom_line()+
  theme_minimal()+
  ggtitle("Monthly Temperature in New York")+
  theme(plot.title = element_text(hjust = 0.5))

```
