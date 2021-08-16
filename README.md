# iterative-proportional-fitting
Iterative Proportional fitting technique to create sample weights such that data is representative of the target dataset or distributions. In statistics, a sample statistic would be biased if sample is not representative of the "population". In ML/AB context, impact of an treatment in an experiment (treatment vs control) or impact of an attribute in an "explainable" model would be biased/incorrect if the distribution of the sample on features is not accurate.


<font color='darkblue' size=4> Often with a design of experiments, the effect of a treatment (vs control) could be measured using randomised control trails. However, it might not always be feasible to divide traffic/users/devices/entities in this manner.  </font>

* The outcome/target/metric could be driven by treatment vs control differences. Besides this, there could be other dimensions which could affect the outcome - exogenous effect variables


* In some cases there might be "endogenous / confounder variables". 


* In such instances, one coule follow a few matching/propensity-scoring techniques such that, the effect of treatment vs difference can be measured, " after accounting for the exogenous effect and endogenous confounder variables/dimensions.


* For many linear problems, the econometric modeling methods such as ANOVA/ANCOVA can be used [linear models] . Or more advancements in recent decade, such as counter factual techniques, conditional average treatment effect (CATE) methods could be applied. 


* In your armour of techniques, add iterative proportional fitting method too. 





**KEY POINTS **
- It is simple, efficient, can be used to match unconventional distributions. 
- It can be used to match non-parameteric, discretised distributions of features in the sample. 
- You may not know the joint distribution of the features. You can try IPF to match "marginal distributions". 
- 
- Note that there might not be a "feasible set" of weights in some scenarios. 
    - For example, assume there are two dimensions which are negatively correlated (~very high). 
    - But user provides target distributions for dimension 1 and 2 such that they seem to be highly +vely correlated.
    - A "feasible set" of weights might not exist. Or the weights could be highly skewed, that a few rows in the data have very large weight and most of the rows have very small (close to zero) weight. 
    - So chose targets wisely. 


**Below notebook does following:**

* Creates targets
* Creates dummy sample

* IPF class
   - train weights 
   - compute standardized mean difference between target and simulated sample distributions [raw distributions]
