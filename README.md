# Implement-Medication-Analyze-in-Python-for-MRI

Background:
----
Around the world the proportion of older adults in our population is rapidly increasing. This is partly due to advances in public health that have lengthened the human lifespan. Longer life is unfortunately associated with cognitive decline, although not for everyone. A major current challenge is the limited understanding of the neural mechanisms of cognitive decline and of preserved cognitive abilities throughout a long lifespan.


It is likely that older adults demonstrating minimal cognitive decline, compared to young adults, are either experiencing minimal age related neural changes or employing successful functional adaptations to age-related neural changes. It is therefore possible that cognitive impairment is the result of adaptive mechanisms no longer functioning or due to some other functional alteration. Successful and unsuccessful functional adaptations can be explored with measures of the neural dynamics of the brain’s response to increases in cognitive load. 


The current work tests how measures of neural dynamics serve as the mechanisms of cognitive decline and cognitive reserve. Results will compare the neural mechanisms utilized by healthy young and old adults for successful completion of two working memory tasks using individualized levels of cognitive load. This will identify neural mechanisms of successful functional adaptations. Comparison between healthy old adults having high and low cognitive task performance will explore whether the poor performance is due to unsuccessful functional adaptations.


The overall aim of this project is to understand the neural underpinnings of variability in cognitive abilities in healthy young and old adults. This will be done by integrating multiple physiological brain measures and measures of neural dynamics of brain activity using two working memory tasks with individualized levels of task demands.


## The practical aspects are:
This project collects multiple imaging modalities of the brains of young and old adutls. The different modalities include measures of greay matter thickness volume throughout the brain, cerebral blood flow throughout the brain, strength of white matter connections throughout the brain and brain function during performance of short term memory tasks. One of the largest challenges of integrating multiple imaging modalities to understand the human brain is the analysis. Software needs to process multiple images per person each containing over 100,000 data points. The images are integrated into statistical models of age related differences in cogntivie performance incorporating lifestyle factors and task performance. Accomplishing such analyses provides views of the the interconnections of brain structure, blood flow and function in predicting someone's cognitive performance. 

Functionalities:
----
## This project contains the methods to bootstrap, jackknife, finding the confidence interval, and calculating standard deviation (z score) of the given size of dataset.
### Data description 
N = number of participants
		N = 100
P = number of data points in the brain
		P = 100,000
	B = number of bootstrap resamples
		B = 5000

### Steps
Fit two regression models
#### Model1:
Mi = b0 + Age*b1
M: brain data, size (NxP)
Age: vector of ages, size (Nx1)
i: cycle over all brain locations: P
b0 : parameter estimate of the constant term in the regression model, size (1xP)
b1: parameter estimate for the predictor Age, size (1xP)
#### Model 2:
C = c0 + Age*c1 + Mi*c2
C: cognitive scores, size (Nx1)
M: brain data, size (NxP)
Age: vector of ages, size (Nx1)
i: cycle over all brain locations: P
c0 : parameter estimate of the constant term in the regression model, size (1x1)
c1: parameter estimate for the predictor Age, size (1x1)
c2: parameter estimate for the predictor brain (Mi) at location i, size (1xP)
Combine parameters
### Calculate: 
b1*c2
Bootstrap these parameters:
b1 
You will end up with PxB values
A b1 value for every data point in the brain (P)
A b1 for every resample (B)
c1 
c2 
b1*c2
Jackknife these parameters
b1 
c1 
c2 
b1*c2
Calculate confidence intervals for these parameters using the bias corrected, accelerated method. Make sure to return the confidence intervals and the Z values. You will want to have a function that takes the bootstrap resamples, jackknife resamples and the point estimates. It returns CI and Z.
b1 
c1 
c2 
b1*c2

Note Step 1c. Mediation and moderated-mediation analyses that I am doing perform a series of regression analyses and then combine the parameters through multiplication. As models become more complicated Models 1 and 2 will become more complicated and additional combinations of parameters will be calculated in step 1c.  To get started feel free to generate random noise for each piece of data to test analyses.
