## PakWheels Used Cars Analysis and Price Prediction Model
## Table of Contents
* [Introduction to Project](https://github.com/WaheedAhmad-DS/PakWheels-Used-Cars-Analysis/edit/main/README.md#introduction-to-project)
* [Technologies Used](https://github.com/WaheedAhmad-DS/PakWheels-Used-Cars-Analysis/edit/main/README.md#technologies-used)
* [Project Explanation through CRISP Methodology](https://github.com/WaheedAhmad-DS/PakWheels-Used-Cars-Analysis/edit/main/README.md#project-explanation-through-crisp-methodology)                
    * [1.Business Understanding/Motivation/Questions](https://github.com/WaheedAhmad-DS/PakWheels-Used-Cars-Analysis/edit/main/README.md#1business-understandingmotivationquestions)      
    * [2.Data Understanding](https://github.com/WaheedAhmad-DS/PakWheels-Used-Cars-Analysis/edit/main/README.md#2data-understanding)      
    * [3.Data Preparation/EDA/Questions Answered](https://github.com/WaheedAhmad-DS/PakWheels-Used-Cars-Analysis/edit/main/README.md#3data-preparationedaquestions-answered)        
    * [4.Data Modeling/Price Prediction](https://github.com/WaheedAhmad-DS/PakWheels-Used-Cars-Analysis/edit/main/README.md#4data-modellingprice-prediction)     
    * [5.Evaluation](https://github.com/WaheedAhmad-DS/PakWheels-Used-Cars-Analysis/edit/main/README.md#5evaluation)     
    * [6.Deployment/Feedback](https://github.com/WaheedAhmad-DS/PakWheels-Used-Cars-Analysis/edit/main/README.md#6deploymentfeedback)
* [Conclusion/Final Impact of the Project](https://github.com/WaheedAhmad-DS/PakWheels-Used-Cars-Analysis/edit/main/README.md#conclusionfinal-impact-of-the-project)
* [Contact](https://github.com/WaheedAhmad-DS/PakWheels-Used-Cars-Analysis/edit/main/README.md#contact)  

## Introduction to Project 
PakWheels is one of the biggest online marketplaces in Pakistan for buying and selling used cars.             

***What intrigued my interest in this project?***              

I own a Honda Civic 1.8 iVTEC 2016 model, black color and approximately 80,000 KM driven at the moment of writing this report. I wanted to sell it; thanks to high fuel prices and overall skyrocketing inflation rate. I decided to buy a more fuel-efficient or hybrid car. You might ask why not Electric Vehicle. Because EVs are not common in Pakistan, currently due to energy crisis, rarity of charging stations and high inflation rate (yes inflation again), it was not an option. Therefore, I wanted to analyze some data related to used cars and see insights regarding correlations between price and other factors such as, model year, mileage, transmission type, body type and even may be color (People here love black colored cars, even though in summers it's unbearable).          

I also wanted to see what maximum legitimate price can i set for my car and what other options are available in that price range.       

Side note: I also like black colored cars 🤐.  

***So, which car did i decide to buy?***        

The answer will be revealed gradually in the steps below.
***

## Technologies Used  
A list of technologies used within the project:
* Python
* Pandas
* Numpy
* Matplotlib
* Seaborn
* StandardScaler
* Ridge Regression
* Scikit-Learn
* LinearRegression
* PolynomialFeatures
* Scipy
* train_test_split, cross_val_score
* r2_score, mean_absolute_error, mean_squared_error
***

## Project Explanation through CRISP Methodology
Cross Industry Standard Process for Data Mining (CRISP-DM) is a process, a methodology, or a framework developed by IBM. A data science team, whenever embarking on a new project, can implement this method for better results and ultimately successful decision-making at the end of the project. 

***Why did i choose this methodology?***

Although it is not the only model out there, but i actually believe that it is the best. It gives you a path and understanding of your tasks beforehand. 

So let's dive into the steps but with out project explanation in mind. 

### 1.Business Understanding/Motivation/Questions 
This phase could be summed as in the following questions:    
* **What do i want to accomplish?** 
* **What are the questions, i want to find answers to?**
* **What problem do i want to solve? What is my end goal?**
* **How exactly would i do it? What is my project plan**         

The ***questions*** i want answers to are:                                
* What is the most popular engine type?
* What are the top fifteen used cars listed? 
* What transmission type occurs more in used cars listed?
* What effect engine size has on the price of the car?
* Does the body type have any effect on the price?
* Does the Model Year and Mileage have any effect on the price?
* Does the Black color have any effect on the price?
* Are hybrids expensive because they give more mileage per liter?           

 The ultimate ***goal*** of the project is:                     
 * What maximum price can i set for my Honda Civic 1.8 i-VTEC CVT 2016, automatic, black color car?                
 * What other cars can I buy in that price range, and can i afford a hybrid one?                     
 * Building a price prediction model.                                          

Now we have well-defined problem and we know what we want to solve. But where is the data? Let me answer it in the next phase.                      

### 2.Data Understanding 
**Data Set:**                  
The dataset can be found here.<nav><a href="https://www.kaggle.com/datasets/spideysloth/pakwheels-cars-dataset?resource=download&select=pakwheels-11Jul2020.csv"> PakWheels Used Cars for sale </a>                  

The Data Set before cleaning has 56186 entries with 16 columns.           

**Key Features of the Data Set:**      
![alt text](https://github.com/WaheedAhmad-DS/PakWheels-Used-Cars-Analysis/blob/main/Images/Data-Features.png)

* **Ad No:-**  Unique ID given to every ad and will be set as index. 

* **Name:-**  Name of the car being sold.       

* **Price:-**  Price of the car in PKR.                          

* **Model Year:-**  The year in which the car was manufactured.      

* **Location:-**  The location where the car is being sold at.       

* **Mileage:-**  How many KiloMeters has the car been driven.         

* **Registered City:-**  In which city is the car registered in excise and taxation department.        

* **Engine Type:-**  Petrol, Diesel and Hybrid.                                      

* **Engine Capacity:-**  Engine size in cc e.g. 1800cc.                               

* **Transmission:-**  Automatic or Manual transmission.                       

* **Color:-**  Color of the car, e.g. black.                            

* **Assembly:-**  Imported or locally assembled car.                            

* **Body Type:-**  This feature identifies if a vehicle is a sedan, SUV or a mini-van etc. There are 17 unique values in this column.          

* **Features:-**  For example, sunroof, automatic windows etc.                      

* **Last Updated:-**  The date when the add was updated last time. We will drop this column.                          

* **URL:-**  Link to the add. We will drop this column too.                     

### 3.Data Preparation/EDA/Questions Answered   
**Data Cleaning:**
1) First, 'Ad No' was set as index.                       
2) URL and Last Updated columns were dropped.                               
3) There is 'call for price' in Price column, these values were dropped.                                                     
4) Checked if NaN values could be replaced. NaN values in Features column were replaced with 'Unknown', in Engine Type with 'Petrol' and in Body Type with 'Hatchback'.                           
5) Data types of some columns were changed to make them coherent with their values: Price and Engine Capacity column into float.                               
6) Duplicates were removed using unique function in pandas.                                     
7) Outliers in Price column were removed i.e. imported cars.                                    
8) Rows with NaN values which could not be substituted were dropped.   

**Exploratory Analysis:**                          

**Q1. What is the most popular engine type?**                     
 
![alt text](https://github.com/WaheedAhmad-DS/PakWheels-Used-Cars-Analysis/blob/main/Images/Popular-EngineType.png)                      

Most of the cars listed have Petrol driven engine. 

### 4.Data Modeling/Price Prediction
### 5.Evaluation
### 6.Deployment/Feedback
## Conclusion/Final Impact of the Project
## Contact 

