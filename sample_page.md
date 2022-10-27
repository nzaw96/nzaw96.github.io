## Predicting Grain and Seed Oil Production in Ukraine

**Project description:** The goal of this project is to build a Machine Learning model that is capable of predicting the amount of grain, specifically barley, wheat and corn, and sunflowerseed oil being produced in a calendar year, in Ukraine. The two sources of the data used in this project were United States Department of Agriculture (USDA) and World Bank. Three linear models (Multi-variable Linear Regression, Ridge Regression, Lasso Regression) and three non-linear models (Decision Tree Regression, Random Forest Regression and k-Nearest Neighbors Regression) were trained, tested and compared. Root Mean-Squared Error (RMSE) was used as a metric to compare the models. In the end, the model with the smallest RMSE on the test dataset is identified as the most suitable model for use as a tool to predict amount of grain and seed oil production in Ukraine.
<br><br>
This project was presented at the IBDAP 2022 Big Data Anatlytics Conference, which was held in Bangkok, Thailand. The paper has been published recently by IEEE, which can be accessed at https://ieeexplore.ieee.org/document/9907513. The code for this project can be found in my github repo: github.com/nzaw96. 

### 1. Project Motivation: The recent invasion of Ukraine by Russia can have global consequences.
In 2021, Ukraine was one of the top grain and seed oil producers in the world. Four of its primary commodities, which brought in over 1 billion dollars each in export sales in 2021, were wheat, barley, corn, and sunflower oil seed (also simply referred to as sunflower seed or sunflower oil). The February 24th invasion by Russia could negatively impact Ukraine’s ability to keep the same production (and export) level for its
primary products. With countries such as Egypt, Indonesia, and the Philippines being heavily dependent on grains and seed oil from Ukraine, the impact of this war could extend the borders of Ukraine. It could disrupt the global economic trends and even cause food shortages. Therefore, it is important to learn which factors affect the amount of grain and seed oil being produced in Ukraine, more than others. Additionally, it would be beneficial to have a Machine Learning model that is capable of predicting amount of grain/seed oil production in Ukraine based on these factors. The data that were primarily used for the analysis were yearly agricultural statistics (import, export, production, etc.) between 1987 and 2021 (USDA) and the population data for the corresponding years (World Bank).


<img src="images/csis_russia_damages_ukraine_food_warehouse.jpeg?raw=true"/>
<figcaption><em>Image shows the damage caused by Russian attach on a food warehouse in Ukraine (Source: <a href=https://www.csis.org/analysis/spotlight-damage-ukraines-agricultural-infrastructure-russias-invasion>CSIS</a>).</em></figcaption>
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

### 4. Model Development

The features left in the dataset after the feature selection were Commodity, Area Harvested, Beginning Stocks,Exports, Domestic Consumption, Yield and Rural Population. Using these 7 features, the six models (multilinear, ridge, lasso, decision tree, random forest, kNN) were trained to predict the production amount.

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).
