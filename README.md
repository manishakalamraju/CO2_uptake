## CO2_uptake_R code
It contains dataset regarding CO2 uptake of two types of grassplants Qubec and Missisipi under different treatments like chilled and non-chilled. The dataset is present in the 'datasets' package of R.
### package installation
```{r installing packages,echo=TRUE}
install.packages("tidyverse")
install.packages("ggplot2")
install.packages("magrittr")         -- for pipe operators
```
### loading packages
Once packages are installed we can load them by using library() function with package name inside parentheses as shown

```{r loading packages,echo=TRUE}
library(tidyverse)
library(ggplot2)
library(magrittr)
```
### loading dataset
```{r loading dataset,echo=TRUE}
data("CO2")
plants <- CO2
glimpse(plants)
```
### Data analysis
We can find the average CO2_uptake for each plant type under different treatments by using summarize() and group_by() functions.
```{r analysis,echo=TRUE}
plants %>% group_by(Type,Treatment) %>% drop_na() %>% summarise(avg_uptake=mean(uptake))
```
The output will be displayed in the console as
Type        Treatment  avg_uptake
  <fct>       <fct>           <dbl>
1 Quebec      nonchilled       35.3
2 Quebec      chilled          31.8
3 Mississippi nonchilled       26.0
4 Mississippi chilled          15.8
## Data visualization
The visualization can also be done in R using ggplot by giving aesthetics and bar graph type using geom_bar() function. The position="dodge" arranges the bars for each group side-by-side within each category.
```{r analysis,echo=TRUE}
ggplot(plants, aes(x =Type , y = uptake, fill = Treatment)) +geom_bar(stat = "identity", position = "dodge") +
  labs(title = "CO2 uptake for different plant types",x = "Type",y = "uptake") +theme_minimal()
```
The output will be displayed in the plots as follows
<img width="513" height="273" alt="image" src="https://github.com/user-attachments/assets/6e33fa44-ef0e-4628-bf36-c92c3c87f3aa" />
