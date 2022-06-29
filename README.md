## PakWheels Used Cars Analysis and Price Prediction Model
## Table of Contents
* [Introduction to Project](#introduction-to-project)
* [Technologies Used](#technologies-used)
* [Project Explanation through CRISP Methodology](#project-explanation-through-crisp-methodology)                
    * [1.Business Understanding/Motivation/Questions](#1business-understandingmotivationquestions)      
    * [2.Data Understanding](#2data-understanding)      
    * [3.Data Preparation/EDA/Questions Answered](#3data-preparationedaquestions-answered)        
    * [4.Data Modeling/Price Prediction](#4data-modelingprice-prediction)     
    * [5.Evaluation](#5evaluation)     
    * [6.Deployment/Feedback](#6deploymentfeedback)
* [Conclusion/Final Impact of the Project](#conclusionfinal-impact-of-the-project)  

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
![alt text](https://github.com/WaheedAhmad-DS/PakWheels-Used-Cars-Analysis/blob/main/Images/Popular-fuel.png)                     

Most of the cars listed have Petrol driven engine.                              

**Q2. What are the top fifteen used cars listed?**                      
![alt text](https://github.com/WaheedAhmad-DS/PakWheels-Used-Cars-Analysis/blob/main/Images/Top-15-Listed-Cars.png)                     

Honda Civic, Toyota corollas and Suzuki Wagon Rs are the market dominating cars.  
   
**Q3. What transmission type occurs more in used cars listed?**                      
![alt text](https://github.com/WaheedAhmad-DS/PakWheels-Used-Cars-Analysis/blob/main/Images/Transmission%20Type.png)                     

Manual type occurs more, although it is not clear here wether the price of manual is more than automatic. This will be revealed in Q. 5.         
   
**Q4. What effect engine size has on the price of used cars listed?**                      
![alt text](https://github.com/WaheedAhmad-DS/PakWheels-Used-Cars-Analysis/blob/main/Images/Price%20Based%20on%20Engine%20size.png)                     

There is an overall increasing trend in the price with the increase of engine power.        
   
**Q5. Does the body type has any effect on the price of used cars?**                      
![alt text](https://github.com/WaheedAhmad-DS/PakWheels-Used-Cars-Analysis/blob/main/Images/Body-Type%20effect%20on%20price.png)                     

The price of Crossover > SUV > Sedan > Hatchback.                               
   * Side note: > means gretaer than.                                                                 
   
As I will buying a sedan, we can see below from the groupby function that automatic sedan is much more expensive than manual sedan.  
![alt text](https://github.com/WaheedAhmad-DS/PakWheels-Used-Cars-Analysis/blob/main/Images/Automatic%20vs.%20manual.png)                        
   
   
**Q6. Does the Model Year and Mileage have any effect on the price of used cars?**                      
![alt text](https://github.com/WaheedAhmad-DS/PakWheels-Used-Cars-Analysis/blob/main/Images/Year%20and%20Price.png)                              
   
![alt text](https://github.com/WaheedAhmad-DS/PakWheels-Used-Cars-Analysis/blob/main/Images/Mileage%20and%20price.png) 
   
The price of a car tends to increase with the recent model years and it tends to decrease with the increase in Mileage.    

**Q7. Does the Black color have any effect on the price of used cars?**                      
![alt text](https://github.com/WaheedAhmad-DS/PakWheels-Used-Cars-Analysis/blob/main/Images/No%20of%20cars%20listes%20colorwise.png)                     
![alt text](https://github.com/WaheedAhmad-DS/PakWheels-Used-Cars-Analysis/blob/main/Images/Price%20based%20on%20Color.png)                 
   
In the first plot, it can be seen that more white colored cars are listed, although the price is usually more for the black colored cars as it can be seen from the above 2nd plot.          

**Q8. Hybrids should be expensive because they give more mileage per litre, is it so?**                      
![alt text](https://github.com/WaheedAhmad-DS/PakWheels-Used-Cars-Analysis/blob/main/Images/Price%20based%20on%20Engine%20type.png)                     

Although from Q1. it can be seen that petrol driven cars outnumber hybrids, but from the figure it is visible that hybrids are much more expensive than petrol or diesel based cars.          
   
**Q9. What maximum price I can set for my Honda Civic 1.8 i-VTEC CVT 2016, automatic, black color car?**                      
![alt text](https://github.com/WaheedAhmad-DS/PakWheels-Used-Cars-Analysis/blob/main/Images/Maximum%20price.png)                     

So the maximum price i can set is 3 Million PKR.                     
   
***Now let's see what can i buy in that price.*** 

**Q10. What other cars can I buy in this price range, and can i afford a hybrid one?**                      
![alt text](https://github.com/WaheedAhmad-DS/PakWheels-Used-Cars-Analysis/blob/main/Images/Cars%20to%20buy.png)                     

So what hybrids can i buy?                   

I can buy a comparatively newer and less driven model of Toyota Aqua; a hatchback, or an older version of Honda Vezel (crossover) and Toyota Prius (sedan). 
   
I will probably buy Honda Vezel 🤫. 

### 4.Data Modeling/Price Prediction  
I wanted to train a model which, when given with some specifications, will give us the estimated price of car. For modelling the data was normalized by using one hot encoding. I trained three models; Linear Regression, Polynomial regression,and Ridge regression.               

The modelling phase can be summarized in the following steps:                        
* **Model Selection:** It onvolves different ML algorithms. I tried three different models.                         
* **Test Design:** Model test design was designed by splitting the data into training, test, validation sets, and cross-validation.                                
* **Model Development:** The model was fitted using the data we cleaned. 
* **Model Assessment:**  Models were assessed using various statistical techniques.                                              

**1) Linear Regression**                                            
![alt text](https://github.com/WaheedAhmad-DS/PakWheels-Used-Cars-Analysis/blob/main/Images/LinearRegression.png)                                   

The linear regression model gives 82% and 81.8% accuracy on training and testing data respectively.                                  

**2) PolynomialFeatures**                                                               
![alt text](https://github.com/WaheedAhmad-DS/PakWheels-Used-Cars-Analysis/blob/main/Images/PolynomialFeatures.png)                                     

The polynomial regression model with degree of 2 gives 88.9% and 86.06% accuracy on training and testing data respectively.  
   
**3) Ridge Regression**                                                                                   
![alt text](https://github.com/WaheedAhmad-DS/PakWheels-Used-Cars-Analysis/blob/main/Images/RidgeRegression.png)                                          
   
The ridge regression model with alpha value of 0.1 gives 81.8% and 82.03% accuracy on testing and training data respectively.               

***Therefore, Polynomial Linear regression with degree of 2 is a better model because of its statistical accuracy.***
   
### 5.Evaluation
**Technical Evaluation**                        

Technical evaluation of the models have been done above where we found the accuracy measurements regarding all the three models.                         

**Non-technical Evalution**                                                                                               

***This is of utmost importnace. It can be described as below.***                                      

* **Evaluating Results:** This involves evaluating the model concerning the buisness indicator. The data minig results should be rigorously assessed, probabaly in a controlled laboratory setting. Why? To gain confidence that they are reliable before moving to deployment phase.                                   

* **Review Process:** From this phase we can go back to First phase and start the overall process again for better results and decision-making. What if we need more data? May be, all phases were not executed as they should have been, etc.                                                                                                                      

*  **Next Steps:** The model may well be ready for deployment or may be iteration of the CRISP-DM methodolgy is required. Depending on the previous phases different decisions could be taken.                                                     

**Evaluation of our project**                                      

Technical evaluation of our Ridge regression model is near to accurate. But evaluation in the actual buisness context may reveal some failures. May be, we could scrape more data from the PakWheels website or anyother relevant source and try to iterate the whole process and then compare the results.                               

### 6.Deployment/Feedback                                                           

* It involves implementing a predictive model in some information system or buisness process.                                 

* In our used car analysis example, price predicting model could be integrated with the buisness process on the PakWheels website. Visitors on the website or app could enter the specifications of the car and would get back the estimated price.                                                 

***Note: The process often returns to the first phase of Buisness Understanding regardless of the success of deployment. A second iteration may produce improved solutions to the problems***                                                             

***
## Conclusion/Final Impact of the Project                                                    
* I found the best maximum price i could set for my car. Also I found the best options available in hybrid version.                     

* Price prediction model was also developed with more than 85 % accuracy, and the model can be deployed on the PakWheels site.                          
  

