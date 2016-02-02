---
layout: page
title: Proje
---



# Marka Başvurularının İllere Göre Dağılımı
## R Paadysavdya

* adasda
* asdasd
   +add 
   +asdada
   +asdasfa

```{r}
require(caret)
evveri$price=as.factor(evveri$price)
ctrl <- trainControl(method = "cv", 
                     number = 10, 
                     savePredictions = TRUE)

lojistikcv<- train(price~lotsize+stories,  data=evveri, 
              method="glm", family="binomial",
                 trControl = ctrl)
```

[TPE](http://www.tpe.gov.tr/TurkPatentEnstitusu/statistics/)		

![AB2016](C:\Users\burak\Documents\prometheus-ab16/logo.png)		 