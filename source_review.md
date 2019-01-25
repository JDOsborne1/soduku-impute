# Source Review

1. https://www.rdocumentation.org/packages/Hmisc/versions/4.1-1/topics/aregImpute
2. https://stats.idre.ucla.edu/r/faq/how-do-i-perform-multiple-imputation-using-predictive-mean-matching-in-r/
3. https://www.analyticsvidhya.com/blog/2016/03/tutorial-powerful-packages-imputing-missing-values/
4. https://datascienceplus.com/imputing-missing-data-with-r-mice-package/
5. https://www.omicsonline.org/open-access/a-comparison-of-six-methods-for-missing-data-imputation-2155-6180-1000224.php?aid=54590
6. https://www.statisticssolutions.com/multiple-imputation-for-missing-data/
7. https://www.theanalysisfactor.com/seven-ways-to-make-up-data-common-methods-to-imputing-missing-data/
8. http://www.stat.columbia.edu/~gelman/arm/missing.pdf
9. https://www.bmj.com/content/338/bmj.b2393
10. https://arxiv.org/abs/1203.5181
11. http://www.inference.org.uk/mackay/itila/
12. https://cse.buffalo.edu/faculty/mbeal/papers/bal03.pdf
13. http://www.seanborman.com/publications/EM_algorithm.pdf
14. http://pages.cs.wisc.edu/~jerryzhu/cs838/EM.pdf
15. https://arxiv.org/pdf/1105.1476.pdf
16. https://webarchive.nationalarchives.gov.uk/20160113083211/http://www.ons.gov.uk/ons/guide-method/method-quality/general-methodology/data-editing-and-imputation/index.html
17. http://www.iaeng.org/publication/WCE2012/WCE2012_pp391-394.pdf
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
      *  Ie, you may only need to understand that for your problem, the sensitivity is the most important metric, and the method with the best sensitivity is the best for your system. 
      *  Therefore, for the evaluation of the different models against each other and against the sodoku impute, we should use representations of the accuracy with multiple metric
    *  The Summary of the paper indicates that the FURIA method produces a high quality cleaned data set at the expense of a high computational cost
    *  Low power conclusion: "Machine Learning may be the best approach"
18. https://www.amstat.org/ASA/Membership/Sections-and-Interest-Groups.aspx
19. https://statistics.stanford.edu/sites/g/files/sbiybj6031/f/BIO%2083.pdf
20. https://web.archive.org/web/20060215221403/http://bcs.whfreeman.com/ips5e/content/cat_080/pdf/moore14.pdf
21. https://planetmath.org/empiricaldistributionfunction
22. https://www.boost.org/doc/libs/1_69_0/libs/math/doc/html/math_toolkit/cubic_b.html
23. https://www.boost.org/doc/libs/1_69_0/libs/math/doc/html/math_toolkit/sf_poly/chebyshev.html
24. https://arxiv.org/pdf/1203.2295.pdf
25. https://docs.python-guide.org/scenarios/ml/
26. https://blog.dominodatalab.com/ab-testing-with-hierarchical-models-in-python/
27. https://machinelearningmastery.com/metrics-evaluate-machine-learning-algorithms-python/
28. https://python.libhunt.com/sixpack-alternatives
29. https://python.libhunt.com/hypothesis-alternatives
30. https://python.libhunt.com/pytest-alternatives
31. https://python.libhunt.com/robotframework-alternatives




