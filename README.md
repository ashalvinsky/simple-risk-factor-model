# simple-risk-factor-model 

Used Jupyter Notebook.

Simple risk factor model to explain the risk attribution of return series.

Steps used to generate results:

1. Some data preprocessing joining excel sheets on date filtering out empty records.

2. Statistical OLS model to check t values. For a two-tailed test of t, with df=533 and p=.05, t must equal or exceed 1.960 
   From simple regression we can conclude that all factors are statistically significant with |t| stat > 1.96 given the small sample size. 
   Factors explain 55.8% of risk. OLS has major drawbacks. First, OLS has no mechanism to filter out noise variables. 
   Second, it assumes that factor loadings are constant over time.
3. ML Ridge regression and Lasso regressions performed to check R^2 and compare results.

4. The value of R2 is the percent of total risk explained by systematic risk. 
   Total risk could be derived in multiple ways, one is standard deviation multiplied by returns annualized. 
   I call 2 ML regression Ridge, Lasso models with different combinationns of factors and take mean between the two results. 
   The models are called with deifferent factors / feutures and R^2 results are recoded in the dataframe called final_results. 
   I also calculate R^2 value with all the factors / feutures. Next step i subtract calculate R^2 mean for the two models with 
   one factor excluded from the total.
   
5. Results:
   
Total risk % 4.817834833924939
DBC factor % of total risk     0.311112%
HYG factor % of total risk     4.817835%
IEF factor % of total risk     1.798403%
SPY factor % of total risk     0.004667%
united-states-ig-oas-all-sector factor % of total risk     0.610083%
united-states-hy-oas-all-sector factor % of total risk     0.004874%
united-states-cmt10y     0.576809%
