# Wastewater-Treatment Operation Cost (kWh) Prediction Using Energy billed and Treated Flow (MGD)
Predicting Electricity Consumption at Dillman Road Wastewater Treatment Plant



#Project: Multiple linear regression exercise

#Author: Ahmed Ibrahim Yunus

#PhD student at Georgia Institute of Technology
```
- This section provides metadata about the project and the author.

```R
# Install necessary packages
install.packages("psych")
install.packages("lm.beta")
install.packages("lmtest")
install.packages("sandwich")
install.packages("car")
```
- These lines install the required R packages if they are not already installed. The packages are necessary for conducting various statistical analyses and visualization.

```R
# Load necessary packages
library(psych)
library(lm.beta)
library(lmtest)
library(sandwich)
library(car)
```
- After installing the packages, these lines load them into the current R session, allowing the functions from these packages to be used in subsequent code chunks.

```R
# Import dataset (dillman_wwtp_daily_electricity_and_influent_data.csv)
View(dillman_wwtp_daily_electricity_and_influent_data)
DF <- data.frame(dillman_wwtp_daily_electricity_and_influent_data)
```
- This section imports the dataset named "dillman_wwtp_daily_electricity_and_influent_data.csv" and assigns it to the variable `DF`. The `View()` function is used to visually inspect the dataset.

```R
# Structure of Data frame DF
str(DF)
```
- This line displays the structure of the DataFrame `DF`, including the data types of each variable.

```R
# Description of Data frame DF
describe(DF)
```
- This line provides a summary of the DataFrame `DF`, including descriptive statistics for each variable.

```R
# Correlation test of Data frame DF
corr.test(DF, use = "complete.obs", method = "pearson", adjust = "bonferroni")
```
- This line conducts a correlation test between variables in the DataFrame `DF` using Pearson's correlation coefficient. The Bonferroni adjustment is applied to correct for multiple comparisons.

```R
# Pearsons panel test of Data frame DF's variables
pairs.panels(DF, methods = "pearson", density = TRUE)
```
- This line generates a panel of scatterplots with histograms for each variable in the DataFrame `DF`, using Pearson's correlation coefficient to assess the relationships between variables.

```R
# Linear Regression model of selected variables
fit <- lm(Operation_bill ~ MG + kW + billed_kWh + total_kWh, data = DF)
```
- This line fits a linear regression model to predict `Operation_bill` using the variables `MG`, `kW`, `billed_kWh`, and `total_kWh` in the DataFrame `DF`.

```R
# Display of Fit
fit
```
- This line displays the fitted linear regression model.

```R
# Summary of Fit
summary(fit)
```
- This line provides a summary of the fitted linear regression model, including coefficients, standard errors, t-values, p-values, and R-squared.

```R
# Beta Test of Fit
lm.beta(fit, complete.standardization = TRUE)
```
- This line computes standardized coefficients (beta coefficients) of the variables in the fitted regression model.

The remaining code sections involve statistical analyses, diagnostic tests, and predictions using the fitted regression model. Each line or block of code performs a specific statistical operation or visualization, as indicated by the comments provided. These include:

- Confidence intervals calculation (`confint()`),
- Heteroskedasticity-robust standard errors computation (`vcovHC()`),
- Variance inflation factor calculation (`vif()`),
- Partial regression plots generation (`avPlots()`),
- Residual plots generation (`residualPlots()`),
- Breusch-Pagan test for heteroskedasticity (`bptest()`),
- Influence index plots generation (`infIndexPlot()`), and
- Predictions using the fitted regression model (`predict()`).
