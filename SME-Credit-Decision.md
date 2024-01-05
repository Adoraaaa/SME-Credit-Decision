

## BACKGROUND

In practice, due to the smaller scale and limited mortgage assets of micro, small, and medium-sized enterprises, banks typically provide loans based on credit policies, transaction history, and the influence of upstream and downstream entities. They may offer interest rate concessions to enterprises with high reputation and low credit risk. Banks evaluate credit risk, considering financial strength and reputation, before determining lending decisions and credit terms.

A certain bank sets the loan amount for eligible borrowing enterprises between 1 to 10 million RMB, with an annual interest rate ranging from 4% to 15%, and a loan term of 1 year. The materials provide relevant data for 123 enterprises with credit records, 302 enterprises without credit records, and statistical data for the relationship between loan interest rates and customer churn rates in 2019. The bank has invited your team to, based on the actual data and information in the attachments, conduct a study and establish a mathematical model to analyze credit strategies for small and medium-sized enterprises and address related issues.

## CATALOGUE

* [Problems](#Problems)
  * [The Credit Strategy for 123 Enterprises with Credit Records](#The Credit Strategy for 123 Enterprises with Credit Records )
* [Issue Analysis](#Issue Analysis)
  * Problem 1

### Problems

#### The Credit Strategy for 123 Enterprises with Credit Records

Conducting Quantitative Analysis of Credit Risks for 123 Enterprises, Providing the Bank's Credit Strategy for These Companies When the Annual Credit Limit is Fixed.

Among the 123 enterprises, the credit rating of the enterprise is divided into four grades: A,B,C and D. The higher the grade, the better the credit rating of the enterprise in the bank, that is, the enterprise with the credit rating of A has the best credit in the bank and is most likely to lend to this type of enterprise.



### Issue Analysis

#### Problem 1

This section begins by establishing an indicator system for evaluating enterprise credit risks, resulting in seven credit risk assessment indicators. Subsequently, Fisher Linear Discriminant Analysis is applied to conduct a quantitative analysis of credit risks for 123 enterprises. The credit risks of these enterprises are then quantified into default rates, where lower default rates indicate lower credit risks. The bank's credit strategy for enterprises is transformed into a multi-objective optimization problem, solving it through relevant information such as the average default rates and quantities for enterprises of different credit levels. This approach provides insights into the bank's credit strategy for these enterprises when determining the annual credit limit.

###### Enterprise Credit Risk Evaluation Indicator System

According to the topic, the assessment of enterprise credit risk can be conducted based on three aspects: the invoice void ratio, the enterprise's credit rating, and the overall strength of the enterprise. To address these three aspects, this paper establishes seven credit risk assessment indicators, namely: the void ratio of input invoices, the void ratio of output invoices, the total amount of transaction revenue, profit margin, growth rate, enterprise credit rating, and the quantity of invoices.

* The void ratio of input invoices

* The void ratio of output invoices

  The following figure shows the proportion of invalidated invoices of enterprises with credit rating C and D compared with those with credit rating A and B Therefore, the selection of this index is objective, reasonable and necessary.

  

![image-20240105162223089](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20240105162223089.png)

* Total transaction income

  As seen in the graph below, with the decrease in credit rating, the total transaction revenue of the enterprise shows a declining trend. It can be observed that this indicator can to some extent reflect the credit risk of the enterprise. Therefore, the total transaction revenue of each enterprise is selected as an indicator for evaluating the credit risk of the enterprise.

  Total transaction income = total amount of enterprise output invoice + total amount of input invoice

  ![image-20240105163337528](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20240105163337528.png)

* profit margin

  ![image-20240105163812609](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20240105163812609.png)

* rate of increase

* Credit rating

* Invoice quantity

  The quantity of invoices can reflect the supply and demand relationships of a company and is also one of the indicators for evaluating the strength of the enterprise. The larger the value of this indicator, the more products the company sells or purchases, indicating a better supply and demand relationship. As seen in the graph below, companies with credit ratings A and B have a larger quantity of invoices compared to those with credit ratings C and D. The former's higher supply and demand indicate a stronger ability to repay credit, resulting in lower credit risk.

  ![image-20240105164738977](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20240105164738977.png)

* Determination of compliance rate of each enterprise

  By selecting seven credit risk evaluation indicators and relevant data, we constructed a Fisher discriminant model. We used the "Classification-Discriminant" function in SPSS software to perform Fisher discriminant analysis on the samples, classifying enterprises based on "default" or "non-default." This function provides the probability that an enterprise belongs to the category of "non-defaulting enterprise." The output probability $P_j$ from the Fisher discriminant analysis model is taken as the compliance rate, where the closer the value of $P_j$ is to 1, the higher the compliance rate of the enterprise. A higher $P_j$ value indicates better credit, and consequently, lower credit risk for the enterprise. Conversely, the closer $P_j$ is to 0, the lower the compliance rate, indicating poorer credit and higher credit risk for the enterprise. This quantification of credit risk facilitates subsequent loan decisions by different banks for various enterprises. 

  Inputting the seven selected credit risk evaluation indicators from the previous section into the SPSS software, we classified the 123 enterprises based on whether they 'violated regulations.' The classification results and the default probability for each enterprise are shown in the table below.

  ![image-20240105170352438](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20240105170352438.png)

  

* Credit Strategy Objective Functions

  We have devised a strategy where the bank extends loans to enterprises with credit ratings A, B, and C, while refraining from lending to those with a credit rating of D. Additionally, the bank assigns equal loan amounts and interest rates to enterprises with the same credit rating. Based on these assumptions and considering the bank's overall revenue and risk, this paper proposes using a multi-objective optimization approach to determine the bank's credit strategy. Since we assume that the bank employs the same credit strategy for enterprises with identical credit ratings, the compliance rate $\overline{P}_j$ in each objective function is taken as the average of the compliance rates for enterprises in each credit rating category $\overline{P}_j$.

  * Risk Objective: 

    Quantitative analysis of credit risk for enterprises with credit records by assessing the compliance rates of enterprises under each credit rating to quantify their credit risk. One of the bank's credit strategies is to minimize risk losses. The risk objective is as follows:
    $$
    \min \left\{C_{j} \cdot\left(1-\overline{P}_{j}\right) x_{j}\right\}, j=1,2,3
    $$

  * Revenue Objective: 

    One of the bank's credit strategies is to maximize overall revenue, specifically interest income. The revenue objective is as follows:
    $$
    \sum_{j=1}^{3} C_{j} \cdot r_{j} \cdot x_{j}
    $$
    
* Customer Churn Rate Objective: 
  
  With the increase in bank loan interest rates, the customer churn rate also rises. Hence, we construct the customer churn rate function $Y(r_j)$. For the bank, a decrease in the number of loan customers represents a loss. Therefore, one of the bank's credit strategies is to minimize the customer churn rate.
    $$
    \min \left\{C_{j} \cdot r_{j} \cdot x_{j} \cdot Y\left(r_{j}\right)\right\}
    $$
    Here, $r_1$, $r_2$, and $r_3$ represent the loan interest rates for the three categories A, B, and C among the 123 enterprises.
  
  The customer churn rate function $Y(r_j)$ can be fitted using the MATLAB fitting toolbox to the data provided in the question. After consulting literature and practical experimentation, we found that using the natural logarithm (base *e*) function for fitting yields the best results. The functions  $Y(r_j)$for enterprises in categories A, B, and C are as follows:

$$
\begin{array}{l}
Y(r)=2.239+0.669 \cdot \ln r_{1}\\
\begin{array}{l}
Y(r)=2.158+0.6506 \cdot \ln r_{2} \\
Y(r)=2.168+0.6586 \cdot \ln r_{3}
\end{array}
\end{array}
$$

​		In conclusion, to maximize net revenue, minimize customer churn rate, and minimize credit risk, the following three 		objective functions are determined:

​		
$$
\left\{\begin{array}{l}
\max \left\{\sum_{j=1}^{3} C_{j} \cdot r_{j} \cdot x_{j}\right\} \\
\min \left\{C_{j} \cdot\left(1-\bar{P}_{J}\right) x_{j}\right\} \\
\min \left\{C_{j} \cdot r_{j} \cdot x_{j} \cdot Y\left(r_{j}\right)\right\}
\end{array} \quad, j=1,2,3\right.
$$


* Constraints

  * Constraint 1: 

    The bank imposes restrictions on loans to each enterprise, with loan amounts ranging from 10 to 100 million yuan.
    $$
    100000 \leq x_{j} \leq 1000000, j=1,2,3
    $$
    

  * Constraint 2: 

    The bank imposes constraints on the annual interest rates for each enterprise, ranging from 4% to 15%.
    $$
    0.04 \leq r_{j} \leq 0.15, j=1,2,3
    $$
    

  * Constraint 3: 

    The bank imposes a fixed amount constraint, assuming a fixed amount of 50 million yuan.
    $$
    \sum_{j=1}^{3} C_{j} \cdot x_{j}=50000000, j=1,2,3
    $$
    

  * Constraint 4: 

    Upon reviewing the bank's information regarding loans to enterprises, it is found that enterprises with different credit ratings have different upper limits on loan amounts. Therefore, an additional constraint on the upper limit of loan amounts is added:
    $$
    \left\{\begin{array}{c}
    100000 \leq x_{1} \leq 1000000 \\
    100000 \leq x_{2} \leq 700000 \\
    100000 \leq x_{2} \leq 200000
    \end{array}\right.
    $$
    

  * Constraint 5: 

    Upon reviewing the bank's information regarding loans to enterprises, it is found that enterprises with different credit ratings have different upper limits on loan interest rates. Therefore, constraints on the upper limit of loan interest rates are added for enterprises with A and B credit ratings:
    $$
    \left\{\begin{array}{l}
    0.04 \leq r_{1} \leq 0.08 \\
    0.04 \leq r_{2} \leq 0.10
    \end{array}\right.
    $$
    In summary, to solve the multi-objective optimization problem, the three objectives are combined into a single objective. The final optimization problem is as follows:
    $$
    \begin{array}{l}
    \min \left\{C_{j} \cdot r_{j} \cdot x_{j} \cdot Y\left(r_{j}\right)+C_{j} \cdot\left(1-\bar{P}_{J}\right) x_{j}-\sum_{j=1}^{3} C_{j} \cdot r_{j} \cdot x_{j}\right\}, j=1,2,3\\
    \text { s.t. }\left\{\begin{array}{c}
    100000 \leq x_{j} \leq 1000000 \\
    0.04 \leq r_{j} \leq 0.15 \\
    \sum_{j=1}^{3} C_{j} \cdot x_{j}=50000000 \\
    100000 \leq x_{1} \leq 1000000^{\prime} \\
    100000 \leq x_{2} \leq 700000 \\
    100000 \leq x_{3} \leq 200000 \\
    0.04 \leq r_{1} \leq 0.08 \\
    0.04 \leq r_{2} \leq 0.10
    \end{array}\right.
    \end{array}
    $$

  * solution method for model

    This problem is a nonlinear multi-objective optimization problem. After linearizing the objective functions and using the `solve` function in MATLAB, the solution is obtained.
    $$
    \begin{array}{c}
    x_{1}=927680, x_{2}=522640, x_{3}=104060 \\
    r_{1}=5.93 \%, \quad r_{2}=8.18 \%, \quad r_{3}=8.01 \%
    \end{array}
    $$
    Hence, the credit strategy for the 123 enterprises in Attachment One is as follows: For enterprises with credit rating A, the loan amount is 927,680 yuan, and the interest rate is 5.93%. For those with credit rating B, the loan amount is 522,640 yuan, and the interest rate is 8.18%. For those with credit rating C, the loan amount is 104,060 yuan, and the interest rate is 8.01%. For enterprises with credit rating D, no loans are provided.
