# Intro  

 - It is hard to analize multi-class data. But actually, There are so many multi-class data in daylife.
 - This data is **multi-class data.** so I'm gonna use various models before applying these models to another data.  
 - At the end, I will compare models through **AUC and F1 score.**
     
   - RandomForest  
   - SOM  
   - nnet  
   - multinom  
   - xgboost  

```python
# Libraries
library(dplyr)
library(ggplot2)
library(gridExtra)
library(corrplot)
library(randomForest)
library(kohonen)
library(xgboost)
library(nnet)
library(devtools)
library(RSNNS)
library(pROC)
source('https://gist.githubusercontent.com/fawda123/7471137/raw/466c1474d0a505ff044412703516c34f1a4684a5/nnet_plot_update.r')
# This source will be used to visualize neural-network
```

```python
# Visualizing code in pairs
panel.cor <- function(x, y, digits = 2, prefix = "", cex.cor, ...){
  usr <- par("usr"); on.exit(par(usr))
  par(usr = c(0, 1, 0, 1))
  r <- abs(cor(x ,y))
  txt <- format(c(r, 0.123456789), digits = digits)[1]
  txt <- paste0(prefix, txt)
  if(missing(cex.cor)) cex.cor <- 0.8/strwidth(txt)
  text(0.5, 0.5, txt, cex = cex.cor * r)
}
```

```python
data = read.csv(file = "../input/glass/glass.csv")
summary(data)
cat('There are', sum(is.na(data)), 'NA values')
```

-> All variables are numeric except for target variable

-> There is no NA value in data

