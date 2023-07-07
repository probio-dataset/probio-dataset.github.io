---
layout: default
title: ProBio | Dataset
permalink: /dataset.html
mathjax_autonumber: true
---


# ProBio Dataset

## Overview



## Protocol Format


```json
{
    "info": info,

}
```

## Ambiguity

We define ambiguity between two actions with the bidirectional Levenshtein distance ratio, as shown in Equation \eqref{a}. In Equation \eqref{a}, $$P(A)$$ and $$P(B)$$ represent the power set of the given $$A$$ or $$B$$ set of hoi, while ratio denotes the Levenshtein distance ratio. The ambiguity (i.e. $$amb$$) between two practical experiments can exceed 1, which represents a high similarity between the two prc\_exp. Afterward, in order to measure the average ambiguity of each action, we define it by taking the average value (i.e. $$\frac{1}{N} {\sum \limits_{amb\in N} amb_i}$$).


$$amb=\frac{1}{P(A)}*\sum \limits_{x\in P(A)}{\underset{y\in P(B)}{\max}(ratio(x, y))} + \frac{1}{P(B)}*\sum \limits_{y\in P(B)}{\underset{x\in P(A)}{\max}(ratio(y, x))} \label{a}$$


{% include mathjax.html %}



