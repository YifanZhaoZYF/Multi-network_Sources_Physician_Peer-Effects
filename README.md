# Combining multiple sources of relationships in a network to advance understanding of physicians’ beliefs regarding peer-effects
This repository stores simulated data sets and corresponding R code for performing the main analyses included in the manuscript of 'Combining multiple sources of relationships in a
network to advance understanding of physicians’ beliefs regarding peer-effects'.

Load the needed R packages:
```
library(lme4)
library(lmerMultiMember)
```

An example model for analyzing the associations between measures from different network sources:
```
lmerMultiMember::glmer(Nominated ~ Strength + Fellowship + StartPractice35 + Age + Sex + Race + (1|hosp), family = "binomial", memberships = list(hosp = t(W1)), data = MultiSource_Sim)
```

An example model for analyzing the associations between survey responses to physician outcome questions and multiple-source network measures:
```
lmerMultiMember::glmer(Q1 ~ Nominated + NominationSum + Strength + Betweenness + Eigenvector + Fellowship + StartPractice35 + Age + Sex + Race + (1|hosp), family = "binomial", memberships = list(hosp = t(W1)), data = MultiSource_Sim)
```
