---
hastex: True
---
## Linear Regression

Question to answer
1. Is there a relationship between predictors and dependent variable?
2. Are there predictors useful to predict the dependent variable
3. Which predictors are associated with the dependent variable?
4. How well does the model fit the data?
5. Ho accurately can we predict future results with our model?
6. Is the relationship linear or do we have to transform our predictors?
7. Are there any interactions between predictors?

Answers
1. Linear regression
The response variable is the linear combination of the predictor variables. i
The regression estimates the factors $\beta_i$.

Simple regression:

$$
\hat{y} = \hat{\beta_0} + \hat{\beta_1} * x
$$

Multiple Regression:

$$
\hat{y} = \hat{\beta_0} + \sum_{i=1}^{p}{\hat{\beta_i} * x_i}
$$

Obs: Categorical variables will be recoded into binary variable. A categorical variable of $n$ levels will be recoded into $n-1$ binary variables.E.g.
the variable quality = ("bad", "medium", "good") would be recoded into quality_bad and quality_quality_medium. Therefore
bad -> quality_bad = 1, quality_medium = 0
medium -> quality_bad = 0, quality_medium = 1
good -> quality_bad = 0, quality_medium = 0

2. 
Simple Regression: Test whether $\beta_1$ is different from 0:

$H_0$  $\beta_1 = 0$ vs $H_1:$ $\beta_1 \ne 0$

t-test  with $t = \frac{\beta_1}{\sigma_{\beta_1}}$

Multiple Regression: Test whether at least one $\beta_i \ne 0$.
F-Test

$H_0$  $\forall i: \beta_i = 0$ vs $H_1:$ $\exists i: \beta_i \ne 0$

F-Test with

 $$
 F = \frac{\frac{TSS - RSS}{p}}{\frac{RSS}{n-p-1}}
 $$
  where $n:$ number of measurments
and $p:$ number of predictors

3. 

Simple Regression: Nothing to do, there is only one variable

Multiple Regression:
Various methods to find the important variables, such as *Forward Selection*, *Backward Selection* or *Mixed Selection*
All based on t-tests for each parameter.

* Forward Selection: Start with null model, do $p$ linear regressions, add factor with lowest p-value, do $p-1$ two parameter regressions, add the parameter with lowest p-value ... until stopping rule.

* Backward Selection: Start with all paramteres and exclude parameter with highest p-value. Rerun with $p-1$ paramenters and exclude parameter with highest p-value ... until stopping rule.

Obs: This step should be done only after step 2 showed there are nozero parameters. An individual p-value could be significant by chance (model with 100 paramters will have 5 paramters below $\alpha$ just by chance)

4.

Error measures:

$$
TSS = \sum_{i=1}^{n}{(y_i - \bar{y})^2}

RSS = \sum_{i=1}^{n}{(y_i - \hat{y_i})^2}

R^2 = \frac{TSS-RSS}{TSS}
RSE = \sqrt{\frac{RSS}{n-p-1}}
$$


### Confidence and predictive intervals

#### Confidence Iterval
Confidence Intervals for Linear regresson (how well do we estimate the regression line (hyperplane)?):

$y_0, \hat{y_0} \in \R,  x_0 \in \R^p, X \in \R^{n x p}$

* Simple Regression

$$
var(\hat{y_0}) = RSE^2 \cdot (\frac{1}{n} + {\frac{(x_0-\bar x)^2}{\sum_{i=1}^{n}{(x_i-\bar x)^2}}}))
$$

* Mutiple Regression

$$
var(\hat{y_0}) = RSE^2 \cdot x_0(X^TX)^{-1}x_0^T
$$

5.
 
#### Prediction Interval
This interval estimates the range where a new prediction will lie.

* Simple Regression

$$
var(y_0 - \hat{y_0}) = RSE^2 \cdot (1+\frac{1}{n} + {\frac{(x_0-\bar x)^2}{\sum_{i=1}^{n}{(x_i-\bar x)^2}}}))
$$

* Mutiple Regression

$$
var(y_0 - \hat{y_0}) = RSE^2 \cdot (1 + x_0(X^TX)^{-1}x_0^T)
$$

6. 

Sometimes the prdictors or the response variable have to be transformed to show a linear relationship in the $\beta_i$ parameters.

7.Interaction between predictor variables: Sometimes there are synergies 
between predictor variables that is the model is not entirely aaditive anymore
 (e.g. money spend on radio adverising increases the effecitvenes of TV 
 adverising). E.g., instead of 

$$
y = \beta_0 + \beta_1 x_1 + \beta_2 x_2
$$

we have 

$$
y = \beta_0 + (\beta_1 x_1 + \beta_12 x_2)x_1 + \beta_2 x_2
$$

If we suspect interaction terms, it might be a good idea to specify the model
all interaction terms and weed out the non-significant ones.

If an interaction term is significant, then the model should contain
the principal terms even if they are not sgnificant.


### Potential Problems with a linear model
1. Non linearity of predictor response relationship
2. Correlation of error terms
3. Non constant variancae of error terms (heteroscedasticity)
4. Outliers
5. High leverage points : Predictor values far from other predictor values. Problems aris if a high leverage point is also an outlier.
Leverage stisitc for simple regression is :

$$h_i = \frac{1}{n} + \frac{(x_i - \bar{x})^2}{\sum_{j=1}^n{(x_j - \bar{x})^2}}
$$

This staistic is always betwwen $\frac{1}{n}$ and $1$ with mean $(p+1)/n$ with 
$p$ the number of predictor variables. Values much bigget than $(p+1)/n$ are
 an indication of high leverage points.

6. Collinearity of predictors:
Check for collinearity by regressing predictor $\beta_j$ on all other 
predictors $\beta_{-j}$ and calulcating the *variance influence factor (VIF)*.

$$VIF(\beta_j) = \frac{1}{1-{R^2}_{x_j|x_{-j}}}
$$

