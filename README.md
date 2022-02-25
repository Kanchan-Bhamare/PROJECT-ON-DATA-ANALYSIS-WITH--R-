# "PROJECT ON MEDICAL DEVICES CASE STUDY USING R CODE"
## 1. Problem Statement

![enter image description here](https://github.com/Kanchan-Bhamare/PROJECT-ON-DATA-ANALYSIS-WITH--R-/blob/main/image1.png?raw=true)

## 1.1 Background Information
Operating in the Edinburgh office of **GluMet**, a leading European medical devices company that provides technological solutions for the healthcare industry. One of the products GluMet manufactures is a **Blood-Glucose Meter**. A glucose meter is a medical device for determining the approximate concentration of glucose in the blood. It is essentially used for **Home Blood Glucose Monitoring (HBGM)** by people with diabetes. Leonard, the CEO, was continuing a long series of discussions with his partners Sebastian, COO, and Alfredo, Director of Sales, deliberating a market entry strategy for its gluco-meter devices in **Buckingham**, a town in England, and in **Louisa**.

## 1.2 Challenges at hand

As GluMet’s senior management had anticipated, entering the propsed market posed a wide variety of  **challenges**.

-   The lack of  **brand awareness**  for gluco-meter product.
    
-   The  **disjointed**  customer  **support services**  and technical services.
    
-   Rolling out the  **updates**  and  **upgrade features**  for the devices.
    

Sebastian said, “I knew it would not be easy. But I still believe we can provide value to customers.” Leonard agreed: “Considering our long-term growth goals, entering the proposed market is a necessary step for GluMet. But, in light of the challenges ahead, is it the step we should take now?”

## 1.3 Current Scenario

The management has decided to use diabetes data to double down this decision, instead of going with gut feeling. Diabetes data from the hospitals and clinics of the two places has been made available which contains patient information like age, gender, height, and weight. In addition to this, we also have anamnesis of the patients. We have diagnosis and results of the patients to see whether the patient is diabetic or not.

## 1.4 Plan of Action

Using this, the management plans to carry out  **market research**  and develop a statistical model which, given this information, predicts whether patient in question will buy the product or not. A successful model which is able to do this, will make the launch efficiently targeted.

## 1.5 End Result

Once the gluco-meter  **awareness**  and  **acceptance**  in these regions is matured, Glumet might have an easier time selling in these countries by leveraging its experiences and reputation. While these markets were small compared to the previous ones, they could offer a means for  **GluMet to grow**  in the short term.

# 2. Study Questions

-   **What are the factors that will make the launch successful?**
    
-   **How is the current market different from the previous ones?**
    
-   **What are the strategies that we are going to opt in?**
    
-   **What are the operational decisions need to be made?**
    

# 3. Product Launch Process

The product launch process starts with the following steps:

1.  We are going to collect  **patient information**  from various hospitals and clinics.
    
2.  Then we will carryout the  **market research**  on the data we have.
    
3.  Once it’s all blended together, we will take that data and then try and come up with a  **marketing analysis**.
    
4.  Finally, we will come up with a  **strategy**  to enter the market.

# 4. Case Study

----------

## 4.1 Introduction

**HbA1c**  or  **Glycated Hemoglobin**  is most reliable test for confirming diabetes. HbA1c measurement has a central role in management of diabetes. People with diabetes need to check their glucose levels often, hence they are more likely to buy  **glucometers**  for regular monitoring of their HbA1c levels. Also, it would help pre-diabetic patients to take preventive measures as well

## 4.2 What is Hemoglobin A1c (HbA1c) ?

A hemoglobin A1c (HbA1c) test reflects the  **average concentration of glucose in blood**  over the past 2-3 months. The test measures the amount of glucose attached to hemoglobin and is reported as a percentage of total hemoglobin.

![enter image description here](https://github.com/Kanchan-Bhamare/PROJECT-ON-DATA-ANALYSIS-WITH--R-/blob/main/image2.png?raw=true)

## 4.3 Why measure Hemoglobin A1c?

Having a consistently high HbA1c levels indicates either  **Type 2 Diabetes**  or a heightened risk for developing diabetes (**Pre-Diabetes**).


![enter image description here](https://github.com/Kanchan-Bhamare/PROJECT-ON-DATA-ANALYSIS-WITH--R-/blob/main/image3.png?raw=true)


## 4.4 Why HbA1c (Glycated Hemoglobin) is most reliable test for Diabetes?

HbA1c (Glycated Hb) serves as a retrospective indicator of the average glucose concentration over the previous 6-8 weeks. HbA1c offers a potentially  **easier**,  **non-fasting**, and therefore more acceptable test.

## 4.5 How HbA1c is interpreted?

![enter image description here](https://github.com/Kanchan-Bhamare/PROJECT-ON-DATA-ANALYSIS-WITH--R-/blob/main/image4.png?raw=true)

Results of HbA1c can be interpreted for diagnosis of diabetes as:

-   5.6 % and below =  **Normal**
    
-   5.7% - 6.4% =  **Pre-Diabetes**
    
-   6.5% and Above =  **Diabetes**
    

----------

# 5. Loading Packages and Libraries

Alright! lets begin our marketing research by installing some packages and loading all the libraries.
```
library(dplyr)
library(psych)
library(vtree)
library(DataExplorer)
```
# 6. Market Research Process

**Market research**  is an organized effort to gather data about  **target markets**  or  **potential customers**  and then analyzing it to better understand what that group of people needs. It is a very important component of  **business strategy**. The results of market research, which are usually summarized in a report, are then used to help business owners make more  **informed decisions**  about the company’s  **strategies**,  **operations**, and potential customer base.

## 6.1 Importing Data

Lets import our data first.

```
dataset = read.csv("https://raw.githubusercontent.com/insaid2018/R/master/Data/diabetes.csv")
```
## 6.2 Reading Data

Lets have a complete view of our dataset.
```
View(dataset)
```
Lets have a look at the head of the data.
```
View(head(dataset))
```
To know how the structure of the data is, we will **str** function.
```
str(dataset)


```
**glimpse** gives you a better organized structure of the data.
glimpse (dataset)

glimpse (dataset)


Using the **describe()** function, we can compute descriptive statistics for numerical data. The descriptive statistics help determine the distribution of numerical variables.

describe (dataset)

``

## 6.3 Data Cleaning

dim(dataset)

#1.a Count the columns
numColumns = dim(dataset)[2]

##count missing values in each column

vector_NAS = rep(0,numColumns)

#True -1- value is missing
#False -0 - value is not missing

for (i in 1:numColumns) {
  vector_NAS[i] = sum(is.na(dataset[,i]))
}

print("The missing values in each column:")
print(vector_NAS)


dataset =dataset[,-c(15, 16)]
print(dim(dataset))
      

#It appears that columns **15** and **16** has maximum number of 
missing values which accumaltes to more than 50 percent of the data 
points.

#**262** missing values are really high in number. Therefore, it is essential to delete these columns as they dont contribute much to our analysis.

deleting those columns
Now, lets remove all the rows containing missing values.

row.has.na <- apply(dataset, 1, function(x){any(is.na(x))})
dataset = dataset[!row.has.na,]

print(dim(dataset))


Again, lets have a look at the head of the dataset.
head(dataset)


## 6.4 Analyzing the Data

Lets use the **plot** function to do **univariate analysis** of some variables.

## 6.4.1 Which variable turns out to be significant for the analysis?

 - Lets begin with a very important variable **glyhb**.
 
  plot(dataset$glyhb)
  
  ![enter image description here](https://github.com/Kanchan-Bhamare/PROJECT-ON-DATA-ANALYSIS-WITH--R-/blob/main/Picture1.png?raw=true)


 Majority of patients have normal levels of **glycated hemoglobin**. However, higher levels of **glyhb** seems to be evenly spread across the sample size.

plot(dataset$age)

![enter image description here](https://github.com/Kanchan-Bhamare/PROJECT-ON-DATA-ANALYSIS-WITH--R-/blob/main/Picture3.png?raw=true)

We get from this chart patients from different **age groups** and the sample distribution seems to be evenly spread.


## Bar plot :


barplot(table(dataset$gender))
or we can use ggplot for same 
ggplot(dataset, aes(x=gender))+geom_bar()

![enter image description here](https://github.com/Kanchan-Bhamare/PROJECT-ON-DATA-ANALYSIS-WITH--R-/blob/main/Picture4.png?raw=true)

**Female** patients are more as compared to the **Male** patients. Here, we can conclude that the prevalence of diabetes is more in women in comparison to men.

But, wait a minute, dont jump to conclusions in such an early stage of analysis. What I'll suggest is to lookout for some metrics or statistics before you draw some conclusion.



barplot(table(dataset$frame))

or we can use ggplot for the same

ggplot(dataset, aes(x=frame)) + geom_bar()


![enter image description here](https://github.com/Kanchan-Bhamare/PROJECT-ON-DATA-ANALYSIS-WITH--R-/blob/main/Picture5.png?raw=true)

**Frame** variable basically talks about the body frames of the patients. Here, maximum number of pateints belong to **meduim** body frame


barplot(table(dataset$location))
or
ggplot(dataset, aes(x=location)) + geom_bar()

![enter image description here](https://github.com/Kanchan-Bhamare/PROJECT-ON-DATA-ANALYSIS-WITH--R-/blob/main/Picture6.png?raw=true)

These are the two **locations** where Glumet is planning to launch the product. Apparemtly, Louisa seems to have more number of target customers.

 

## BI-VARIATE ANALYSIS

plot(dataset$glyhb, dataset$stab.glu)

![enter image description here](https://github.com/Kanchan-Bhamare/PROJECT-ON-DATA-ANALYSIS-WITH--R-/blob/main/Picture7.png?raw=true)

Although, these two variables seem highly correlated but however, it is important to understand the scales of glucose levels we are looking at.


 To have a better picture, lets see who our **target customers** are in colorful visualization.

## SCATTER PLOT WITH COLOURS

ggplot(dataset, aes(x=stab.glu, y=glyhb, color=diagnosis)) +
  geom_point() + geom_smooth(method="lm")



![enter image description here](https://github.com/Kanchan-Bhamare/PROJECT-ON-DATA-ANALYSIS-WITH--R-/blob/main/Picture8.png?raw=true)



## 6.4.2 How the distribution of data is?

Lets see how the data is distributed using the **box plots**, **histograms**, and **density plots**

#Picking the numeric variables

dataset_numeric = dataset[,-c(7, 9, 12, 18)]
View(dataset_numeric)
dim(dataset_numeric)

## Box And Whisker Plots

par(mfrow = c(2,2))     #break the chart in rows and columns
for(i in 2:14) {
  boxplot(dataset_numeric[,i], main=names(dataset_numeric)[i])
}

![enter image description here](https://github.com/Kanchan-Bhamare/PROJECT-ON-DATA-ANALYSIS-WITH--R-/blob/main/Picture9.png?raw=true)



## Histograms

par(mfrow = c(1,1))  # Put four figures in a row

for (i in 2:13) {
	hist(dataset_numeric[,i],main=names(dataset_numeric)[i])
}


## 6.4.3 Which age group does our target customers fall into?

Lets bin our customers into different **age groups**.


ggplot(dataset, aes(y = glyhb, x = age)) +
  geom_point()+ geom_smooth(method="lm")

![enter image description here](https://github.com/Kanchan-Bhamare/PROJECT-ON-DATA-ANALYSIS-WITH--R-/blob/main/Picture10.png?raw=true)

 According to the scatter plot, we can categorize our customers into 
different age groups.
# 
20 - 35 yrs : **Group 1**
36 - 70 yrs : **Group 2**
 71 - 100 yrs : **Group 3**

Although, the spread of our potential customers is across different age groups but, primarily we need to focus on **Diabetic** and **Pre-Diabetes** patients.



Here we can clearly see our target customers with respect to the age groups we are looking at.

p = ggplot(dataset, aes(x = age, y = glyhb, color = diagnosis))
p+geom_jitter() + geom_boxplot()

![enter image description here](https://github.com/Kanchan-Bhamare/PROJECT-ON-DATA-ANALYSIS-WITH--R-/blob/main/Picture11.png?raw=true)

p = ggplot(dataset, aes(x = age, y = glyhb, color = factor(result)))
p+geom_point() + stat_smooth()

![enter image description here](https://github.com/Kanchan-Bhamare/PROJECT-ON-DATA-ANALYSIS-WITH--R-/blob/main/Picture12.png?raw=true)


## 6.4.4 Which gender should we focus on?

ggplot(dataset, aes(x = gender, fill=diagnosis)) + geom_bar()

![enter image description here](https://github.com/Kanchan-Bhamare/PROJECT-ON-DATA-ANALYSIS-WITH--R-/blob/main/Picture13.png?raw=true)


From the above bar plot, we can say that females are more prone to diabetes in comparision to males.



ggplot(dataset, aes(x=gender, fill=frame)) + geom_bar()

![enter image description here](https://github.com/Kanchan-Bhamare/PROJECT-ON-DATA-ANALYSIS-WITH--R-/blob/main/Picture15.png?raw=true)


However, It seems there are more number of **males** with **large** body **frame**

## Variable tree
We know that there are more number of female patients than male. But, lets just see those numbers in percentages.

install.packages("vtree")   #Variable Tree
library(vtree)

vtree(dataset, "gender",horiz = FALSE)

![enter image description here](https://github.com/Kanchan-Bhamare/PROJECT-ON-DATA-ANALYSIS-WITH--R-/blob/main/Picture17.png?raw=true)

**59%** is a good number which tells us on which gender we should keep our focus. 

Based on gender, lets see what are the percentages in different **locations**.

vtree(dataset, "gender diagnosis")

![enter image description here](https://github.com/Kanchan-Bhamare/PROJECT-ON-DATA-ANALYSIS-WITH--R-/blob/main/Picture18.png?raw=true)

I think we have very good infromation here, our primary focus in gender **male** should primarily be in **Buckingham** because the glyhb levels are really high there.  



## 6.4.5 Which body frame should be targeted in a specific location?


ggplot(dataset, aes(x = location, fill=frame)) + geom_bar()

vtree(dataset, "frame",horiz=FALSE, height=250, width=850)

  ![enter image description here](https://github.com/Kanchan-Bhamare/PROJECT-ON-DATA-ANALYSIS-WITH--R-/blob/main/Picture19.png?raw=true)
 
We have a very good share of **large** body frame i.e. **26%** 
which tend to be more diabetic than the other body frames.  



vtree(dataset,"frame location")



**Buckingham** is the place where we should **focus** more on the **large** body frame as it holds **60%** share. Moreover, we have **56%** of **medium** body frame people to look in **Louisa*


Now, lets see what are the percentages of body frames in different locations. 

vtree(dataset,"frame location",horiz=FALSE,height=250,width=850,showlevels=FALSE)


![enter image description here](https://github.com/Kanchan-Bhamare/PROJECT-ON-DATA-ANALYSIS-WITH--R-/blob/main/Picture20.png?raw=true)

For **large** and **medium** body frames **Buckingham** should be our priority as per the **mean** glyhb levels, whereas, 
for **small** body frame we can focus more on **Louisa**


## 6.4.6 Correlation Analysis

install.packages("DataExplorer")
library(DataExplorer)
plot_correlation(dataset[,1:5])
plot_correlation(dummy_dataset)


![enter image description here](https://github.com/Kanchan-Bhamare/PROJECT-ON-DATA-ANALYSIS-WITH--R-/blob/main/Picture21.png?raw=true)
dummy_dataset<- dataset[,1:5]


#As per my observation, glyhb, stab.glu, and age 
#correlated with the variable result.

To check out my R program please click [here](https://github.com/Kanchan-Bhamare/PROJECT-ON-DATA-ANALYSIS-WITH--R-/blob/main/PROJECT%20ON%20DATA%20ANALYSIS%20WITH%20%E2%80%98R%E2%80%99.R)




