# Source Review

1. [Hmisc R package](https://www.rdocumentation.org/packages/Hmisc/versions/4.1-1/topics/aregImpute)
   * aregImpute:
     * Implementing multiple imputation using
   * gbayes:
2. [Implementing Predictive Mean Mathing in R](https://stats.idre.ucla.edu/r/faq/how-do-i-perform-multiple-imputation-using-predictive-mean-matching-in-r/)
3. [Packages overierview: Analytics Vidhya](https://www.analyticsvidhya.com/blog/2016/03/tutorial-powerful-packages-imputing-missing-values/)
4. [Imputing With Mice](https://datascienceplus.com/imputing-missing-data-with-r-mice-package/)
5. [Comparing 6 methods of imputation](https://www.omicsonline.org/open-access/a-comparison-of-six-methods-for-missing-data-imputation-2155-6180-1000224.php?aid=54590)
6. [Multiple Imputation Methods]( https://www.statisticssolutions.com/multiple-imputation-for-missing-data/)
7. [Seven Common Imputation Methods](https://www.theanalysisfactor.com/seven-ways-to-make-up-data-common-methods-to-imputing-missing-data/)
8. [Missing Data Imputation](http://www.stat.columbia.edu/~gelman/arm/missing.pdf)
9.  [Multiple imputation for missing data in epidemiological and clinical research: potential and pitfalls](https://www.bmj.com/content/338/bmj.b2393)
10. [k-MLE fast statistical mixture models](https://arxiv.org/abs/1203.5181)
11. [Information Theory, Inference, and Learning Algorithms](http://www.inference.org.uk/itprnn/book.pdf)
12. [Cold Link](https://cse.buffalo.edu/faculty/mbeal/papers/bal03.pdf)
13. [Short Tutorial on EM](http://www.seanborman.com/publications/EM_algorithm.pdf)
14. [Advanced NLP with EM Algorithm](http://pages.cs.wisc.edu/~jerryzhu/cs838/EM.pdf)
15. [Paper on the Expectation-Maximisation Algorithm](https://arxiv.org/pdf/1105.1476.pdf)
    * Expectation-Maximisation algorithm
    * Where Y is a random variable with pdf. of p(y|Ó), the goal is to find the maximum of the probability distribution L(θ) = p(y|θ) over a "Search Space"
      * This would represent the value which has the highest probabilty of being the true parameter θ in the random variable distribution
      * These problems only have a "Closed-form" solution in a minority of cases: most of which are quite boring
    * EM is an iterative optimiser tailored for ML
    * The definitive feature of EM as opposed to Newton methods is the underlying philosophy in the approximation scheme, which has a low reliance on calculus 
    * Instead the idea is to introduce another random variable Z, which represents an easier maximisaton problem than Y. This is implemented by imputing/guessing some additional useful informaton.
      * Z can be any variable such that θ -> Y -> Z is a Markov Chain
        * Assuming p(y|z, θ) is independent of θ, that manifests a "Chapman-Kolmogorov" equation
    * Z is a complete data space: If Z were fully observed, estimating θ would be easy
      * The conversion speed is very dependent on the specification of that data space, which has a arbitrary difficulty despite some problems naturally lending themselves to a hidden variable interpretation
    * References Jensen's Inequality in: T. M. Cover and J. A. Thomas. Elements of Information Theory.
    * In section 2.2 it derives an auxilliary function: Q(θ, θ′) which is always less than or equal to the change in the Likelihood function: L between θ' and θ. and always 0 for Q(θ,θ) 
    * As a consequence, when starting from θ', any value θ which has Q(θ,θ') > 0 is guaranteed to also have a higher value of L(θ).
    * The EM algorithm is principially defined by iterating over increases in Q to find maxima in the likelihood function
    * We can develop the function of θ and θ' as a difference of probabilities: Q(θ, θ') = Q(θ|θ') - Q(θ'|θ'). This also explicitly satisfies the condition that Q(θ',θ') = 0.
      * For a fixed value of θ', maximising Q(θ,θ') is the same as maximising Q(θ|θ')
    * Then considering the Residual function, representing the elements of the log-likelihood unaccounted for. This can be ignored because previous parts of the formulation show the residual of the new parameter is greater than the old one.
    * The auxilliary function declines in quality as an approximation to the likelihood as the parameters θ and θ' diverge.
      * Since this error is not constant, true maximisation of the likelihood using EM is not possible. but iterative processes can determine at least a local maximum.
      * These iterative processes are broken up into two key elements:
      1. The E-Step: Forming the auxilliary function, involves computing the "posterior distribution" of the unobserved variable. The Expectation Step
      2. The M-Step: update the estimate of the parameter by maximising the auxilliary function. This does not attempt to maximise the likelihood in one step, and an increase in Q ensures an increase in L, therefore keeping the "monotonicity" property of EM. The Maximisation Step
    * 
16. [ONS methodology on imputation](https://webarchive.nationalarchives.gov.uk/20160113083211/http://www.ons.gov.uk/ons/guide-method/method-quality/general-methodology/data-editing-and-imputation/index.html)
17. [**Complete**: ~~Article on FURIA~~](http://www.iaeng.org/publication/WCE2012/WCE2012_pp391-394.pdf)
    * Focus of paper on __FURIA: Fuzzy Unordered Rule Induction Algorithm__.
    * Focuses on the implementation for medical data, where there is a lot of missing data which needs to be kept around
    * Evaluates various machine learning imputation methods against the performance of a k-mean cluster to classify when trained on the data it has imputed
    * Discussion of MCAR, references: __B. M. Marlin, “Missing Data Problems in Machine Learning__
    * There are merits to the the leastwise deletion method but there are works showing applying it can introduce data bias.
    * Side referece to a machine learning type called Self-Organising Maps
    * An implementation and modification of the rule learner algotithm RIPPER
    * Mathematics in paper too summarised, references: __J. Hühn, and E. Hüllermeier, “Fuzzy Unordered Rules Induction Algorithm,”__
    * The missing value imputation here is trained on the complete rows, where there is no missing data, and then applied to the rest of the data with missing values.
    * The results of the analysis indicate that the FURIA imputation is able to support a better classification of the High risk cases at the cost of a lesser classification of the low risk cases. I.e you catch more high risk patients, but you over-test or over-treat more low risk patients
    * In this instance the systems problem mandates that the better high risk identifier is the better algorithm, but the accuracy of that model was the worst, since it was less accurate at identifying the larger group. The Low risk patients. 
    * There are __more metrics than data accuracy at play__, which will normally be determined by the systems problem, and the domain knowledge, rather than an objective statistic. however there are a series of statistical metrics which can be used as the principle dimensions to judge the efficacy of a model with depending on the situation
      * Ie, you may only need to understand that for your problem, the sensitivity is the most important metric, and the method with the best sensitivity is the best for your system. 
      * Therefore, for the evaluation of the different models against each other and against the sodoku impute, we should use representations of the accuracy with multiple metric
    * The Summary of the paper indicates that the FURIA method produces a high quality cleaned data set at the expense of a high computational cost
    * Low power conclusion: "Machine Learning may be the best approach"
18. [Computer Intensive Methods in Statistics](https://statistics.stanford.edu/sites/g/files/sbiybj6031/f/BIO%2083.pdf)
19. [Bootstrap Methods and Permutation Tests](https://web.archive.org/web/20060215221403/http://bcs.whfreeman.com/ips5e/content/cat_080/pdf/moore14.pdf)
20. [Empirical Distribution Function](https://planetmath.org/empiricaldistributionfunction)
21. [Cubic B-Spline Interpolation](https://www.boost.org/doc/libs/1_69_0/libs/math/doc/html/math_toolkit/cubic_b.html)
22. [Chebyshev Polynomials](https://www.boost.org/doc/libs/1_69_0/libs/math/doc/html/math_toolkit/sf_poly/chebyshev.html)
23. [Techniques for solving sodoku puzzles](https://arxiv.org/pdf/1203.2295.pdf)
24. [Machile Learning basics: Python](https://docs.python-guide.org/scenarios/ml/)
25. [A/B testing with Hierarchical Models: Python](https://blog.dominodatalab.com/ab-testing-with-hierarchical-models-in-python/)
26. [Metrics for Evaluating Machine learning performance: Python](https://machinelearningmastery.com/metrics-evaluate-machine-learning-algorithms-python/)
27. [Python Module Research: sixpack](https://python.libhunt.com/sixpack-alternatives)
28. [Python Module Research: hypothesis](https://python.libhunt.com/hypothesis-alternatives)
29. [Python Module Research: pytest](https://python.libhunt.com/pytest-alternatives)
30. [Python Module Research: robotframework](https://python.libhunt.com/robotframework-alternatives)
31. [Gaussian Processes for Regression: Intro](https://higherlogicdownload.s3.amazonaws.com/AMSTAT/83c090fb-b70c-4699-9d1e-293de567de36/UploadedImages/Learning%20Materials/1505.02965v2.pdf)
32. [Gaussian Processes for model construction](http://www.cs.toronto.edu/~duvenaud/thesis.pdf)
33. [Gaussian Processes for machine learning](http://www.gaussianprocess.org/gpml/chapters/RW4.pdf)