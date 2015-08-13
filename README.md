# rSymPy
---
title: "Five Variables"
output: html_document
---


```{r}
library(rSymPy)


```




```{r, echo=FALSE}

x1 <- Var("x1")
x2 <- Var("x2")


a1 <- Var("x1*x2")#change variables here instead of multiplying them in the matrix below.
a2 <- Var("a2")
a3 <- Var("a3")
a4 <- Var("a4")
a5 <- Var("a5")

A <- Matrix(List(a1, a2, a3,0,0), List(a3, a4, a4,0,0), List(a1, a2, a3,0,0),List(a1, a2, a3,0,0),List(a1, a2, a3,0,0))
V <- Matrix(List(a1), List(a2), List(a3),List(a4),List(a5))
T <- t(V)

T*A*V


f1 <- a1
f2 <- a2
f3 <- a3
f4 <- a4
f5 <- a5

f <- T*A*V*f1*f2*f3*f4*f5

#write f as a function format
f.input <- function(x1,x2,x3,x4,x5){f}

library(cubature)
adaptIntegrate(f.input,lowerLimit = c(0,0,0,0,0), upperLimit = c(1,1,1,1,1))

# inverse
library(rSymPy)
a1 <- Var("a1")
a2 <- Var("a2")
a3 <- Var("a3")
a4 <- Var("a4")
A <- Matrix(List(a1, a2), List(a3, a4))
A <- Matrix(List(a1, a2, a3,0,0), List(a3, a4, a4, a1, a2), List(a1, a3, a5, a2, 0), List(a3, a1, a4, a1, a3), List(a3, a1, a4, a1, a4))
#define inverse and determinant
Inv <- function(x) Sym("(", x, ").inv()")
A
Inv(A)

```
