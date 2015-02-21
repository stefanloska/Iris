---
title       : Iris classifier
subtitle    : course project
author      : Stefan Loska
job         : Developing Data Products @ Coursera
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## Intro
These 3 irises look quite similar:

Iris setosa | Iris virginica | Iris versicolor
------------- | ------------- | -------------
![""](assets/img/setosa.jpg)  | ![""](assets/img/versicolor.jpg) | ![""](assets/img/virginica.jpg)

* However, they are indeed 3 different species.
* They differ in lengths and widths of petals and sepals.
* Combination of these measurements allows to distinguish them.

---

## Model
To develop a tool for determining the Iris species, a random forest model was built using `iris` data from the `datasets` package.


```r
inTrain=createDataPartition(iris$Species, p=0.75, list=FALSE)
training=iris[inTrain,]
testing=iris[-inTrain,]
model = train(Species ~ ., data=training, method="rf")
```

Achieved out of sample accuracy was:


```r
pred = predict(model, newdata=testing)
confusionMatrix(pred, testing$Species)$overall[1]
```

```
##  Accuracy 
## 0.9166667
```

---

## Application

The model was saved as an .RData file and used to build an online application:

![""](assets/img/screen.png)

---

## Where to find it

The application is available at:

[https://stefanloska.shinyapps.io/Iris/](https://stefanloska.shinyapps.io/Iris/)

Have fun!




