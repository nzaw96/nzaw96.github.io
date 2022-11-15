## Predicting Grain and Seed Oil Production in Ukraine

**Project description:** The goal of this project is to analyze changes in linguistic patterns of the Reddit users before and during the COVID-19 pandemic.

<br><br>
This project was presented at the ICWSM 2022 Conference, which was held in Atlanta, Georgia, USA. The code for this project can be found in <a href="https://github.com/nzaw96/Reddit-Addiction-Study">my Github repo</a> .

### 1. Project Motivation: The recent invasion of Ukraine by Russia can have global consequences.
The outbreak of the COVID-19 pandemic created global social distancing restrictions, which forced millions of people to stay at home. The imposed seclusion could cause further marginalization of the 


<img src="images/csis_russia_damages_ukraine_food_warehouse.jpeg?raw=true"/>
<figcaption><em>Image shows the damage caused by Russian attack on a food warehouse in Ukraine (Source: <a href="https://www.csis.org/analysis/spotlight-damage-ukraines-agricultural-infrastructure-russias-invasion">CSIS</a>).</em></figcaption>
<br><br>
<br><br>

### 2. Project Workflow Chart
<img src="images/Ukraine_project_workflow.png?raw=true"/>

### 3. Exploratory Data Analysis (EDA)

Boxplots were created using Plotly to observe the spread/skew of the independent variables. The most skewed variables were Beginning Stocks, Imports, Exports, Feed Dom. Consumption and Fsi. Consumption. However, since the size of the dataset is small, the skewed variables/columns were not dropped.
(Note: 'Fsi' stand for 'Feed, Seed and Indsutrial' and virtually refers to consumption by humans and pets while Feed Dom. (Domestic) Consumption refers to consumption by farm animals.)
<img src="images/Ukraine_project_boxplots.png?raw=true"/>
<br><br>
The following plot shows how the production levels of the four primary commodities of Ukraine (barley, corn, wheat and sunflowerseed oil) have changed over the years since 1987. Notice that corn has emerged as Ukraine's most produced commodity in the last few years.
<img src="images/Ukraine_project_commodityVsYear.png?raw=true"/>
<br><br>
An important step before training ML models is the feature selection. Seaborn's correlation heatmap allows one to see how strongly the independent variables are correlated with one another and with the dependent variable. For example, Total Supply has the (pearson) correlation value of 0.99 with Production but it also has 0.85 correlation with Area Harvested, which is another feature. With the interest of keeping the number of features in the dataset small, one can drop Total Supply or Area Harvested. Similarly, Population and Rural Population have a strong correlation of 0.95 between them and one can drop one of those features from the dataset. The criteria and full thought processes involved in the feature selection step of the project can be in the paper, linked at the top of this page.  
<img src="images/Ukraine_project_heatmap.png?raw=true"/>
<br><br>

### 4. Model Development and Results

The features left in the dataset after the feature selection were Commodity, Area Harvested, Beginning Stocks,Exports, Domestic Consumption, Yield and Rural Population. Using these 7 features, the six models (multilinear, ridge, lasso, decision tree, random forest, kNN) were trained to predict the production amount.
Comprehensive hyperparameter search was done using LassoCV (for Lasso Regression), RidgeCV (for Ridge Regression) and GridSearchCV (for Decision Tree, Random Forest and kNN). After getting the optimal values for the hyperparameters, each model was trained and test 1000 times, using 1000 different train-test splits of the dataset. At the end, average training and testing RMSE was calculated and tabulated for each model.
<br><br>
The table below shows the training and testing RMSEs for the six models. Note that all the values inside the table are in 1000 MT (Megatonnes), which is the same unit as Production in the data.
<body>

<table style="width:100%">
  <tr>
    <th>Model</th>
    <th>Train Error</th>
    <th>Test Error</th>
  </tr>
  <tr>
    <td>Multi-linear</td>
    <td>948.480</td>
    <td>1030.839</td>
  </tr>
  <tr>
    <td>Ridge</td>
    <td>948.888</td>
    <td>1030.053</td>
  </tr>
  <tr>
    <td>Lasso</td>
    <td>948.916</td>
    <td>1030.042</td>
  </tr>
  <tr>
    <td>Decision Tree</td>
    <td>8.523</td>
    <td>2327.817</td>
  </tr>
  <tr>
    <td>Random Forest</td>
    <td>676.098</td>
    <td>1701.885</td>
  </tr>
  <tr>
    <td>kNN</td>
    <td>1424.678</td>
    <td>2151.700</td>
  </tr>
</table>

<p>Even with hyper-parameter tuning using GridsearchCV module, one can see that the decision tree model has a testing error of 2327.817, which is the highest of all six models. On the other hand, the training error for the decision tree is 8.523. This suggests that the model is highly over-fitting, which decision trees are known for, especially for the smaller data sets. Over-fitting is also observed in the random forest model, albeit to a lesser degree, where training and testing errors were 676.098 and 1701.853, respectively.
<br><br>
On the other hand, the linear models were more accurate, with slight differences in RMSEs between the three. Lasso has smallest testing error among the three models.
<br><br>
Even though Lasso has been identified as the best performing model out of the six, it is still difficult to gauge its usefulness. Without much context, the RMSE error values inside the results table above may either seem too large or too small. Therefore, another metric called RMSPE (Root Mean-Squared Percentage Error) was calculated in order to put context in the testing RMSE value of Lasso model, shown in the results table above. The <b>RMSPE</b> value of the <b>lasso regression model</b> was <b>9.09%</b>. 
<br><br>
While this project was coming to an end, the USDA published the data for 2022. Therefore, this next calculation was not included in the paper itself. The table below shows the actual production values of corn, wheat, barley and sunfloweroil seed, alongside the production values predicted by the Lasso model.
</p>
</body>

<table style="width:100%">
  <tr>
    <th>Commodity</th>
    <th>Actual Production Values for 2022 (in 1000 MT)</th>
    <th>Predicted Values (in 1000 MT)</th>
  </tr>
  <tr>
    <td>Barley</td>
    <td>6400</td>
    <td>6864.80</td>
  </tr>
  <tr>
    <td>Corn</td>
    <td>31500</td>
    <td>25668.70</td>
  </tr>
  <tr>
    <td>Wheat</td>
    <td>20500</td>
    <td>19959.90</td>
  </tr>
  <tr>
    <td>Sunfloweroil Seed</td>
    <td>10500</td>
    <td>10701.89</td>
  </tr>
</table>

The <b>RMSPE</b> was calculated again for the Lasso Model on this new 2022 test dataset. It came out to be <b>10.08%</b>.



<br><br>
For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).
