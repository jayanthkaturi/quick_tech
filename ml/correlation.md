## Correlation Coefficients

```
Pearson coefficient:

Draw a straight line fit in scatter plot. The line is the one that minimizes the square distances between
the line and the points. The slope (up + or down -) will be sign of the correlation.
Compare scatter along yaxis and along the scatter line.
If yaxis > scatter line: strong correlation coefficient else: weak.

pearson coeff = (SP(cross product of deviation)) / (sqrt(ssx)*sqrt(ssy))
ssx -> sum of squares of deviations

Point Biserial:
Dichotomous variable categrical (one hot encode) and continous, calc pearson coeff


Analysis of variance (ANOVA): 
F = sum_var(between grps)/sum_var(with in grps), p -> confidence
## F, p = stats.f_oneway(...)

F(b,w) -> b,w are degrees of freedom across and within groups
b = num grps - 1
w = total observations - num grps
```
