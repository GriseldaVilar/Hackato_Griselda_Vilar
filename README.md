### <span style="color:Aquamarine">PROVA DATA SCIENCE HACKATÓ JUMP2DIGITAL</span>

### Table of contents

#### **1. Introducció: Presentació del conjunt de dades i de les variables seleccionades**
To import libraries and selected dataframes: Rental Price (base) + City Sound of Barcelona in 2017

[2017_Lloguer_preu_trim](https://opendata-ajuntament.barcelona.cat/data/es/dataset/est-mercat-immobiliari-lloguer-mitja-mensual/resource/0a71a12d-55fa-4a76-b816-4ee55f84d327?view_id=89b47b95-78ba-4996-a3de-f9eabb1492c3)

[Poblacio_exposada_barris_Mapa_Estrategic](https://opendata-ajuntament.barcelona.cat/data/es/dataset/poblacio-exposada-mapa-estrategic-soroll/resource/3846500e-72aa-4780-967f-f09aa184eaba#additional-info)


##### **1.1 Data analysis & Quality Original Dataset**
Initial exploration of the dataframes to consult key data such as columns, index, null data and their location and general characteristics and first general operations of the database: maximum, minimum values and len(), to know the database and characteristics. This allows us to identify that the Price column contains null data as well as containing two categories of data (euros monthly and per square meter) and the city's sound range database has good quality and all the data.
One of the main actions is to locate null data since it allows evaluating the quality of the database and allows carrying out averages and actions that allow filling in the missing data. Only if these do not represent more than 5% of the database.
To calculate threshold of lost data, if the percentage is higher than 5% we must evaluate whether to eliminate the data or recover information.
I verify that I need to convert the Value column of the Sound Range dataset from percentage to float in order to generate a Score Index per neighborhood (1-10).
Also I  verify that the price variable is distributed over 4 quarters and is divided into price per month and per square meter, so we can subsequently divide/expand the variable into two columns and calculate the averages and means. In this way we reduce duplicate data.

#### **2 Depuració de dades: Descripció detallada de les tècniques de preprocessat aplicades i els criteris d’avaluació utilitzats**
##### **2.1 Dataset operations and analysis. Final dataset configuration**
I perform operations for the datasets and the configuration of the final dataframe.
In the City Sound Range dataset, a score index adjusted to the value (%) is configured according to the range column value (dB). Likewise, the object variable "Loguer_mitja" is transformed into a string variable to be able to divide/expand the columns in the two categories (e/month and m2)
I have grouped by the value TOTAL_DEN since it contains the sections (day, afternoon and night) and with this a standardized index is generated that represents the noise records by neighborhood in a weighted way.
I create my own index that transforms the percentage (0-100) into a score range of (1-10). This allows you to view the final index and convert the range variable to continuous for correlations and linear regressions.
The dataset Rental Price (base) is divided into two datasets: monthly price and the price per m2 and performed by "merge" between the tables, also deleting the duplicate columns.
To guarantee the quality of the data, the columns with null data in Price are selected and filled with the prime values of the Price by Neighborhood columns.
Afterwards, the annual average is calculated per month and square meter grouped by neighborhoods.

#### **3. Resultats: Presentació dels resultats obtinguts**
##### **3.1 Correlations and linear regressions. Conclusions**
Finally I create the final project dataset uniting final Rental Price (base) and City Sound dataframes ordered, analyzed, cleaned and in a single dataframe.
To visualize the data, I generate:
1)boxplot of the numerical variables (price and dB range) 
2)Subboxplot grouped by colors and the neighborhood code to observe the median and quartiles and compare the distribution of the data 
3)Pearson's Correlation between the numerical variables and represent them using graphs

#### **4. Conclusions: Principals inferències derivades dels resultats aconseguits**
##### **4.1 Linear regression: Noise index score & Average monthly price**
Finally, the linear regression between the related variables is calculated and represented in a graph
A correlation coefficient of 1 is observed between the variables "Index score points" and "Monthly price".
#approximately 1 are the ones that are most related to the index score points
