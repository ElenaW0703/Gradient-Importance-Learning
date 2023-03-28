### Gradient-Importance-Learning
Please see the final reports in *FinalReport_ElenaW* and *FinalPoster_ElenaW* \
Investigating automated algorithms to detect sepsis labels more precisely by 2 major methods for over 70% incomplete observations: \
     i) Logistic Regression w/o Missing Values \
     ii) Gradient Importance Learning w/n Missing Values      

Naïve Way for Brief View:
* Basic Logistic Regression after various time-series rearrangements of each patients’ recordings and subsets attempting to adjust significant 2:98 imbalance problems and relative missing values imputation
* AUC could achieve≈0.65
* Question: Could we achieve better result or try more sophisticated method to execute within NA values?

#### Method1-Logistic Regression by Gradient Descent Update
* Built Logistic Regression with Gradient Descent update to decrease log loss in each iterations and computed a weighted cross entropy to trade off recall and precision by up- or down-weighting the cost of a positive error relative to a negative error
* Parameters for better performance: positive weight=50, batch size=12800, epochs=300, and learning rate=0.01
* Converged best results: 
  Low log loss (≈1.3) \
  Relatively high AUC score (≈0.65)

#### Method2-Gradient Importance Learning for Incomplete Observations
![image](https://user-images.githubusercontent.com/120523258/207774057-7aff10ea-a615-42bc-8006-9efad6507fd6.png)

* Gradient Importance Learning (GIL) method to train multilayer perceptrons (MLPs) and long short-term memories (LSTMs) to directly perform inference from inputs containing missing values
* Reinforcement learning (RL) to adjust gradients used to train these models back-propagation, which allows the model to exploit the underlying information behind missingness patterns
* Tabular analysis is designated: training and testing sets separated by normal (all non-sepsis) and abnormal (all sepsis)

#### Conclusion 
* System Satisfactory: Good fitness of assumptions and comprehensive algorithms for Logistic Regression
* Limitations: 
  1. Missing entries leads poor performance by simply generation of estimation as the assumptions may do not satisfy the real-world applications, such as, patient time-series characteristics and a huge proportion of missingness rate or a small sample size
  2. Imputation error could limit the model capabilities
* Future Improvements: Simplify and tune GIL model to solve overfitting drawbacks



