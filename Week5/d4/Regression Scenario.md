Billy Beane, with his colleague Paul DePodesta, followed an analytical, sabermetric approach to assembling a competitive baseball team, despite Oakland’s disadvantaged revenue situation. Their analysis suggested that some skills were undervalued and some skills were overvalued. If they could detect the undervalued skills, they could find players at a bargain.

They analyzed that a team needs to win at least 95 games to make the playoffs. Based on this, the A’s calculated that they must score 135 more runs than they allow during the regular season to expect to win 95 games.

The A’s also discovered that two baseball statistics were significantly more important than others:

On-Base percentage (OBP): Percentage of time a player gets on base (including walks) and Sluggish percentage (SLG): How far a player gets around the bases on his turn (measures power). And, Batting Average was overvalued. To verify this, they ran a linear regression model, similar to the one below:

```python
# Regression model to predict runs scored:
RunsScored = lm(RS ~ OBP + SLG, data=moneyball)
```

And they have obtained the following results:

```python
summary(RunsScored)
lm(formula = RS ~ OBP + SLG, data = moneyball)

Coefficients:
            Estimate Std. Error t value Pr(>|t|)    
(Intercept)  -804.63      18.92  -42.53   <2e-16 ***
OBP          2737.77      90.68   30.19   <2e-16 ***
SLG          1584.91      42.16   37.60   <2e-16 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1


Multiple R-squared:  0.9296,    Adjusted R-squared:  0.9294 
```

Instruction

Read more about this analysis in the article [**How Linear Regression Changed Baseball**](https://kharshit.github.io/blog/2017/07/28/moneyball-how-linear-regression-changed-baseball).

