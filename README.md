INTRODUCTION:<br/>
This project aims to estimate the human population of high-altitude villages using satellite remote sensing and modeling techniques. Human population estimation is a critical aspect of socioeconomic planning and development. However, this task is particularly challenging in high-altitude villages, where the rugged terrain and harsh climate make traditional methods of data collection difficult. In recent years, remote sensing and modeling techniques have emerged as powerful tools for estimating population density in remote and inaccessible areas. In this project, Iaim to use satellite remote sensing and modeling to estimate the human population of high-altitude villages. The results of this study will not only improve our understanding of the demographic patterns in these areas but will also provide critical information for planning and development initiatives.
The analysis was conducted in four stages -
  -In the first stage, Icollected data on villages located above 2500 meters. This involved identifying and mapping the location of these villages using various sources of satellite imagery and geographic information systems (GIS) data.
  -In the second stage, Icalculated the slope and aspect of each village using digital elevation models (DEMs) to understand the topographic characteristics of the area.
  -In the third stage, Iused Dynamic World software to extract village features such as building footprints, roads, and water bodies from high-resolution satellite imagery.
  -Finally, in the fourth stage, Iused this data to build a machine learning model that could accurately estimate the population density of each village based on the extracted features, topographic characteristics, and other relevant data.
By following these stages, Iwere able to develop a comprehensive methodology for estimating the human population of high-altitude villages using satellite remote sensing and modeling techniques.
<br/>
STUDY AREA:<br/>
The high-altitude regions of India, such as Ladakh, Himachal Pradesh, Uttarakhand, Sikkim, and other regions with an altitude above 2500m, are characterized by rugged terrain, harsh climate, and unique flora and fauna. Ladakh is a high-altitude desert region located in the northernmost part of India, with an average elevation of 3500 meters. The region is arid, and vegetation is sparse, mainly consisting of shrubs and grasses. Himachal Pradesh, located in the western Himalayas, is known for its picturesque mountain ranges, lush forests, and alpine meadows. Uttarakhand, situated in the central Himalayas, is home to some of India's most sacred rivers, including the Ganges and Yamuna. The region has diverse vegetation, including oak, deodar, and rhododendron forests. Sikkim, located in the eastern Himalayas, is known for its biodiversity and unique mountain ecosystems. The region has a diverse range of vegetation, including alpine meadows, temperate forests, and sub-tropical forests. In all of these regions, remote sensing and modeling techniques can provide critical insights into population density and distribution, which can inform planning and development initiatives in these remote areas.<br/>

DATASET:<br/>
<br/>
<img width="575" alt="Screenshot 2024-02-19 at 8 46 25 PM" src="https://github.com/sachita15/Human-population-estimation-of-high-altitude-Himalayan-villages-using-satellite-remote-sensing-and-m/assets/105349293/002bfdcc-4858-4ea6-966b-9634b9a150fe"><br/>

STAGE 1:Village List & Population Dataset<br/>
● The first stage of the project "Human Population Estimation of High-Altitude Villages Using Satellite Remote Sensing and Modelling" involved the collection of data on 40 villages located above 2500 meters.
● All four of us collected data on 10 villages each.
● To identify these villages, we used the floodmap.net website, which provided
information on the elevation of different locations. We then cross-checked this information with other sources to ensure that the selected villages met our criteria of elevation greater than 2500m.
● To estimate the population density of these villages, we used census data to find the total population and the number of households in each village using data.gov.in and censusindia.gov.in
● This data was essential for developing our statistical model, which relied on population density as a key input parameter. By carefully selecting and collecting data on these 40 villages, we were able to create a reliable dataset that formed the foundation for the subsequent stages of the project.
<br/>
<img width="486" alt="image" src="https://github.com/sachita15/Human-population-estimation-of-high-altitude-Himalayan-villages-using-satellite-remote-sensing-and-m/assets/105349293/b661fdf9-2dcf-465d-80ed-b030b0116b4f"><br/>

STAGE 2:Slope and Aspect<br/>
Using google code editor, I found out slope and aspect of the villages I was dealing with.<br/>
<img width="486" alt="image" src="https://github.com/sachita15/Human-population-estimation-of-high-altitude-Himalayan-villages-using-satellite-remote-sensing-and-m/assets/105349293/761d5112-bc82-4c66-8eca-75edf8dddf2d"><br/>

STAGE 3:Finding Land Use using Dynamic World<br/>
Using Dynamic world and google earth code engine, I found out area under trees,grass,flooded vegetation,crops,shrub and scrub,built area ,i.e urban area ,bare area and snow and ice for these villages respectively. <br/>
<img width="525" alt="image" src="https://github.com/sachita15/Human-population-estimation-of-high-altitude-Himalayan-villages-using-satellite-remote-sensing-and-m/assets/105349293/2fbda97f-77f3-4abf-9e60-3aa271170dc9"> <br/>

STAGE 4:Data Analysis<br/>
1) DATA PROCESSING:<br/>
   Data processing is an essential step in creating and training a machine learning (ML) model. It involves the preparation and cleaning of data to ensure that it is suitable for use      in the model. The main objective of data processing is to transform raw data into a format that can be used by the ML algorithms.
   ➔ 1.1) IMPORTING DATABASE
   ➔ 1.2) CLEANING OF DATA
     I then dropped village name, as it was in strings format and was not necessary for the working of model. I also dropped snow and ice, grass and flooded vegetation column, as they       had same values throughout the dataset and some had missing values.
     Then I encoded the dependent variable Location that was in form of string to int format.<br/>
 2) ANALYSING DATA:<br/>
  I tried to analyse which features are strongly correlated to population of a region, which would help us to identify what factors affect the population density of a region.
  Correlation refers to the statistical relationship between two variables, often denoted as X and Y. It measures the degree to which changes in one variable are associated with          changes in another variable. In other words, it describes how closely the two variables move together.
  Correlation can be positive or negative. A positive correlation means that as one variable increases, the other variable also increases, while a negative correlation means that as      one variable increases, the other variable decreases. A correlation of 0 indicates that there is no relationship between the variables.
  <br/>
  <img width="418" alt="image" src="https://github.com/sachita15/Human-population-estimation-of-high-altitude-Himalayan-villages-using-satellite-remote-sensing-and-m/assets/105349293/fbdb5950-5dfd-4d57-aaea-7bc31645aff8"> <br/>
  From the above input we can conclude that as the area under trees, shrub and scrub and bare ground i.e forest area and inhabitant area increases, the population of that area            decreases.
  However, if the crop area and built area, i.e urban area increases the population of that area increases.
  Also as slope increases and we move towards regions with higher altitude like Ladakh, the population decreases.
  Since the ultimate goal of the project was to build a regression model, so I eliminated the features with very less correlation, like trees, cross and bareground.
  ❏ In order to build an accurate model, the desired ratio of features to data-points is 1:10. But in our case number of features was 16 after applying encoding and the number of data 
  points was 40. So I tried to remove as many features as possible, logically to make an accurate model.
  I also tried to study the relationship between different features, so I created a heatmap.<br/>
  <img width="555" alt="image" src="https://github.com/sachita15/Human-population-estimation-of-high-altitude-Himalayan-villages-using-satellite-remote-sensing-and-m/assets/105349293/2dafd63a-bc1f-46e8-8153-935ff4348d9c"><br/>
  I observed that as slope and aspect of a region increases, the built area of that area decreases and eventually number of households also decreases.
  Also for the region of Ladakh under our study area slope and aspect are negatively correlated to them.
  Also we can see that number of households is positively correlated with Uttrakhand region only.<br/>
  
3) APPLYING REGRESSION MODELS:<br/>
  We can also use our model to predict the Population of a village with help of this dataset. So l applied some machine learning models and compared which model gave better results.

    ➔ 3.1) DECLARING FEATURES AND LABELS:
    Features (x) comprise of independent variables like location,built area,slope,
    aspect ,etc.
    Labels (y) comprise of independent variables, which in our case is Population only.
     divided the data set into two parts- training data and testing data in the ratio 4:1. Here training data is used for building the model and then its accuracy is tested on the          testing data set.<br/>
❏ ACCURACY:
R-squared, also known as the coefficient of determination, is a statistical measure of how well a regression model fits the data. In machine learning, R-squared is used as a metric to evaluate the accuracy of a model's predictions.
R-squared measures the proportion of the variance in the dependent variable (i.e., the target variable that the model is trying to predict) that is explained by the independent variables (i.e., the features used in the model). It ranges from 0 to 1, with higher values indicating a better fit.<br/>

  ➔ 3.a) MULTIPLE LINEAR REGRESSION:<br/>
  Multiple linear regression is a statistical method used to model the relationship between a dependent variable and two or more independent variables. It is an extension of simple linear regression, which models the relationship between a dependent variable and a single independent variable.
  In multiple linear regression, the goal is to find the best-fitting linear equation that describes the relationship between the dependent variable and the independent variables. The equation takes the form:
  y = β0 + β1x1 + β2x2 + ... + βnxn + ε where:
  ● y is the dependent variable
  ● x1, x2, ..., xn are the independent variables
  ● β0, β1, β2, ..., βn are the regression coefficients (also known as the model
  parameters)
  ● ε is the error term (representing the difference between the predicted and actual
  values)
  The regression coefficients represent the change in the dependent variable for a one-unit change in the corresponding independent variable, holding all other independent variables constant.
/*Using this model we were able to achieve 97% accuracy, but it is too high, so there can be chances of overfitting.*/ <br/>

  ➔ 3.b) RANDOM FOREST REGRESSION:<br/>
  Random forest regression is a machine learning algorithm that is used for regression tasks, which involves predicting a continuous numerical value. This algorithm is a variant of the random forest algorithm, which is widely used for both regression and classification tasks.
  The random forest regression algorithm builds an ensemble of decision trees that are trained on different subsets of the training data and a random subset of the features. Each tree in the ensemble independently makes a prediction for the target variable based on the input features.
  During the training process, the algorithm selects a subset of the training data and features at random, and grows a decision tree on this subset. The process is repeated several times, each time with a different random subset of the data and features. This creates multiple decision trees that are different from each other and may have different strengths and weaknesses in their predictions.
  The final prediction from the random forest regression model is obtained by aggregating the predictions from all the trees in the forest. The most common method for aggregation is to take the mean of the predicted values, which reduces the variance and produces a more stable prediction.
  One of the key advantages of random forest regression is that it can handle high-dimensional feature spaces, which is a common problem in many real-world applications. The random forest algorithm is also robust to noise and outliers, which can improve its performance on noisy datasets.

  
