# DDS#001

## Overview

### What we will do ?

We will do a small project that imports Amazon S3 public data and runs a machine learning algorithm called random forest to classify whether a high school is public or private based on multiple variables. The set is then encapsulated in a wrapper to transform any script and thus idea into a microservice that can be dockerizer and put into production on any existing cloud. 

<p align="center">
<b> <i> The aims of this meetup is to turn your R script as an experimental microservice. </i> </b>
</p>

### Things to remember after the meetup <i> #doublequote </i>

> Thanks to space-time of Poincaré-Minkowski it exist people that can do fast prototyping.  
> Each click on the keyboard must have an immediate impact in reality.

## Requirements

### Install R-cran and RStudio

R-Cran : https://cran.r-project.org/  
RStudio : https://www.rstudio.com/products/rstudio/download/  

### Packages to install

```R
install.packages("randomForest", dependencies = TRUE)
install.packages("plumber", dependencies = TRUE)
install.packages("dplyr", dependencies = TRUE)
```

## 

### This meetup is made for :

- [x] Farmer.
- [x] Programmer.
- [x] Student.
- [x] Baker, mostly baker.

### Understand pdg_structure variables ?

```R
A- High school with only L, ES and S;
B- High school with only L, ES, S and STMG;
C- High school with L, ES, S, STMG and other series;
D- High school with L, ES, S and other non-STMG series;
E- Hotel school;
F- Other high school with no more than three series;
G- Other high school with at least four sets.
```

### You will certainly put that on your terminal at the end of the meetup

```bash
curl --data '{"ntree":500, "na_default":"na.roughfix"}' "http://localhost:8000/meetup"
curl --data '{"ntree":500, "na_default":"na.omit"}' "http://localhost:8000/meetup"
```

## Docker

_... only for motivated people ..._

You have to run this commands inside the working repository

### Build Image

```bash
docker build -t microservice . 
```

### Run Container

```bash
docker run --rm -p 8000:80 microservice
```

### Test Microservice

```bash
curl --data '{"ntree":500, "na_default":"na.roughfix"}' "http://localhost:8000/meetup"
curl --data '{"ntree":500, "na_default":"na.omit"}' "http://localhost:8000/meetup"
```

**Note:** please be aware that on Windows it will require additional steps in order to expose the microservice port.

Now you just have to push your images on your desired cloud inside a docker containers.
