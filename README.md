# A Country GDP Vs. Its Fertility and Mortality Rates

I want to see whether there is a relationship between a country GDP and its fertility and mortality rates. I recreated this project from my CMSE class but improved it by apply a fundamental data science project's outline.

## Background and Motivation

I stumbled across this question when I was studying in my social science class about the prosperity of different countries. Especially, we looked at three types of nation: core nations, semi-periphery nations, and periphery nations. 

To summarize, a core nation is one that has strong power, both politically and economically (GDP > 1.5 trillions). While the periphery nation is a complete opposite (GDP < 250 billions). Hence, the semi-periphery nation is the one in between the two groups (1.5 trillions >= GDP > 250 billions). 

I finished this project once ([CMSE201_FinalProject.ipynb](https://github.com/chilam27/P01_GDP_Fertility_Mortality_Relation/blob/master/CMSE201_FinalProject.ipynb), original project file, can be found in this repository). I redid it with added step, such as: data cleaning and exploratory data analysis. I also practiced using `sklearn` package for statistical interpretation and building polynomial regression model.

## Prerequisites
Python Version: 3.7.4

Packages: pandas, numpy, sklearn, matplotlib, random

## Project Outline
1. Project planning: determine the necessary variables to compute statistical analysis to answer our question
    - List of variables: _GDP_ (Gross Domestic Product), _fertility rate_ (average number of children that would be born to a woman over her lifetime), _mortality rate_ (can be called death rate; is a measure of the number of deaths in a particular population)
2. Data cleaning: read the dataset in to get farmiliar with columns and values, modify the dataframes, delete null and unnecessary data values, extracting data from original to cleaned csv files
3. Exploratory data analysis: observe the cleaned data set and understand the general trend of the data
4. Regression model: perform polynomial regression and caculate mean squared error (MSE) and coefficient of determination (R**2)

As I am doing my research for the data source, I find the page [World Bank Group](https://www.worldbank.org/). Based on my findings, they have a very accountable data bank that I can use for my project. I also do some checking to see if the data is clean and whether there is an empty/ incomplete data point. Although there are incomplete data, I does not seem to affect my analysis too much. Here are the sources for data I collected:

* [The World Bank Group: GDP (current US$)](https://data.worldbank.org/indicator/NY.GDP.MKTP.CD?most_recent_year_desc=false&view=map&year=2018)

* [The World Bank Group: Fertility rate, total (births per woman)](https://data.worldbank.org/indicator/SP.DYN.TFRT.IN/)

* [The World Bank Group: Death rate, crude (per 1,000 people)](https://data.worldbank.org/indicator/sp.dyn.cdrt.in)

### Data Cleaning

* Modify the dataframe: rename columns' names, delete unnecessary rows and columns
* Remove unrelated values: ex: 'World', 'Arab World', 'Caribbean small states', etc.
* Remove countries with incomplete data (complete: has data from 1960 to 2018)
* Make sure all three dataset (GDP, fertility, and mortality) have the same countries; if not, take countries that all three have in common
* Extracting cleaned data to new csv files: _gdp_data_cleaned.csv_, _fer_data_cleaned.csv_, _mor_data_cleaned.csv_

### Exploratory Data Analysis

In this stage, I want to specifcially look at United States and analyze its data and trend before applying the math and algorithm to other countries.

* Observe data: using methods, such as: `pandas.DataFrame.columns`, `pandas.DataFrame.describe`, etc.
* Check for null value or incomplete data
* Evalutae United States' GDP, fertility and mortality rates trend based on the data given
* Perform polynomial regression model
* Caculate the MSE and R**2 of the two graphs

<p align="center">
  <img width="460" height="300" src="https://github.com/chilam27/P01_GDP_Fertility_Mortality_Relation/blob/master/readme_image/us_gdp.png">
</p>

![alt text](https://github.com/chilam27/P01_GDP_Fertility_Mortality_Relation/blob/master/readme_image/us_gdp_fer.png "United States GDP vs. Fertility")
![alt text](https://github.com/chilam27/P01_GDP_Fertility_Mortality_Relation/blob/master/readme_image/us_gdp_mor.png "United States GDP vs. Mortality")

### Polynomial Regression Model (extended)

* Separate countries into three groups: core, semi-periphery, and periphery
* Randomly choose three countries from each group
* Creating a polynomial regression loop function to graph and caculate MSE and R**2

Core Nations             |  Semi-periphery Nations
:-------------------------:|:-------------------------:
![alt text](https://github.com/chilam27/P01_GDP_Fertility_Mortality_Relation/blob/master/readme_image/china_poly.png "China")  |  ![alt text](https://github.com/chilam27/P01_GDP_Fertility_Mortality_Relation/blob/master/readme_image/bel_poly.png "Belgium")
![alt text](https://github.com/chilam27/P01_GDP_Fertility_Mortality_Relation/blob/master/readme_image/can_poly.png "Canada")   |   ![alt text](https://github.com/chilam27/P01_GDP_Fertility_Mortality_Relation/blob/master/readme_image/pak_poly.png "Pakistan")
![alt text](https://github.com/chilam27/P01_GDP_Fertility_Mortality_Relation/blob/master/readme_image/in__poly.png "India")    |   ![alt text](https://github.com/chilam27/P01_GDP_Fertility_Mortality_Relation/blob/master/readme_image/nor_poly.png "Norway")

Periphery Nations             | 
:-------------------------:|
![alt text](https://github.com/chilam27/P01_GDP_Fertility_Mortality_Relation/blob/master/readme_image/mada_poly.png "Madagascar") |
![alt text](https://github.com/chilam27/P01_GDP_Fertility_Mortality_Relation/blob/master/readme_image/por_poly.png "Portugal")   |
![alt text](https://github.com/chilam27/P01_GDP_Fertility_Mortality_Relation/blob/master/readme_image/hati_poly.png "Hati")  |

### Overall Model Performance

I use MSE and R**2 to track the overall performance of the polynomial regression to see how good the fit or the estimation is. After collecting data from 3 countries of each group, I find the mean of the statistical analysis:
| ___                                           |   Mean Squared Error    |   Coefficient of Determination   |
| --------------------------------------------- |:-----------------------:|:--------------------------------:|
| Mean of statistics for GDP vs. Fertility      | 0.299                   | 0.734                            |
| Mean of statistics for GDP vs. Mortality      | 2.197                   | 0.615                            |


## Conclusion

After having my cleaned data files that are ready to be analyzed, in the EDA stage, I applied the polynomial regression onto United States data. The trend of data shows that, as the GDP increases and the rates of fertility and mortality decrease over time, there seems to be a relationship between GDP and the rates. After running 2nd degree polynomial regression, the fitted line fitted the data quite well: with MDE of GDP vs. Fertility being 0.157 and GDP vs. Mortality being 0.054; with R**2 of GDP vs. Fertility being 0.285 and GDP vs. Mortality being 0.752. 

Although I cound not find out the reason for metrics for the first relationship to be low, I also analyzed nine more countries from the three groups: core, semi-periphery and periphery. The reason I picked three countries was that I wanted to eliminate bias. After applying the regression model and applying the metrics (can be found in the _Overall Model Performance_), most values proof the trend strongly. Except for MSE of GDP vs. Mortality: China and Portugal have large outliers that raise the mean.

It is clear to us that the statement "The higher the GDP is, the lower rates of fertility and mortality are for that country" is true.

_If I would redo this project again, there are two things I would change. First, I want to be more apply one more layer of selection to decrease the bias in data. I have only eliminated bias by picking countries from each group. I can add another layer by picking countries from each continent. Second, I want to apply the regression model to more countries than just three. This is to strengthen the conclusion of proofing the statement above is true._

## Author

* **Chi Lam**, _student_ at Michigan State University - [chilam27](https://github.com/chilam27)

## Acknowledgments

* [Pritchard, Adam. "Markdown Cheatsheet."](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)
* [Thompson, Billie. "A template to make good README.md"](https://gist.github.com/PurpleBooth/109311bb0361f32d87a2)
* [Wells, David. "aligning-images.md"](https://gist.github.com/DavidWells/7d2e0e1bc78f4ac59a123ddf8b74932d)
* [Wikipedia contributors. "List of countries by GDP (nominal)." Wikipedia, The Free Encyclopedia. Wikipedia, The Free Encyclopedia, 9 Jun. 2020. Web. 13 Jun. 2020.](https://en.wikipedia.org/wiki/List_of_countries_by_GDP_%28nominal%29)
* [World Population Review. "GDP Ranked by Country 2020."](https://worldpopulationreview.com/countries/countries-by-gdp/)
* [“machine learning with python video 14 Polynomial Regression.” YouTube, uploaded by 
I know python, 3 Apr. 2020, www.youtube.com/watch?v=2wzxzHoW-sg&t=381s.](https://www.youtube.com/watch?v=2wzxzHoW-sg&t=381s)
