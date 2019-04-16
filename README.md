# gender_autism
Looking at how the DSM-5 criteria of autism may be biased for female participants because base cases used to create the model criteria had more male autistic participants. 


## Implemented using R.


Original dataset taken from: 
https://archive.ics.uci.edu/ml/datasets/Autistic+Spectrum+Disorder+Screening+Data+for+Children++
https://archive.ics.uci.edu/ml/datasets/Autistic+Spectrum+Disorder+Screening+Data+for+Adolescent+++ 
https://archive.ics.uci.edu/ml/datasets/Autism+Screening+Adult


## A Brief Overview of the Documentation attached to the file:

### Introduction

Autistic Spectrum Disorder (ASD) is a mental illness that limits an individual’s linguistic,
cognitive and social skills (Johnson & Myers, 2007). Behavioral and neuroimaging studies
has consistently shown that ASD usually manifests differently in females, because
females may have better social abilities than typical boys with ASD (Lai et al., 2015;
Mandy et al., 2012). Because DSM metrics have been based mostly from data derived
from male studies, current diagnostic methods (DSM-5) may overlook females with ASD
(Kopp & Gillberg, 2011). There may also be a higher likelihood that females are
diagnosed at a greater age, as symptoms become more pronounced at later life stage or
as females become more self-aware of their characteristic symptoms (Howlin &
Asgharian, 1999). Previous studies have not conducted an epidemiological analysis on
gender-related autism regarding the new DSM-5 criteria (Newschaffer et al., 2007;
Worley & Matson, 2012). To understand how females, respond differently to males, an
analysis of how both genders respond to the questions in the new DSM-5 will be
conducted.

The dataset is taken from the UCI website for the Centre of Machine Learning and
Intelligent Systems. Originally, it was used for two main papers (Thabtah, 2017; Thabtah,
2018). In both studies, the data was mainly used to conduct analyses on how fulfilling
current diagnostic methods are at determining the presence of ASD, in relation to the
DSM-5. Machine learning was at the core of their analysis and was used to improve,
precision, timing and quality of the diagnosis procedure, as well as to ensure all criteria
(e.g. place of birth, presence of Jaundice) were significant for diagnosis purposes.
Overall, they found that some of the diagnostic methods used previously in relation to
the DSM-4 were not as relevant to the DSM-5.

The current investigation will focus on implementing a complex exploratory and
predictive model to identify the influence gender may play in ASD diagnosis.

#### The aims are to:

(1) Determine whether fewer females than males have been diagnosed with
ASD.

(2) To understand whether females score differently on the DSM-5
diagnostic criteria.


#### The hypotheses are:

(1) Females are more likely to be diagnosed as having ASD at a later age
compared to males.

(2) Questions related to social deficit in the DSM-5 diagnostic criteria
(namely Q1, Q2, Q3, Q8, Q9, as shown at the end of the document), will
be more relevant to males diagnosed with ASD compared to females.

Questions naming Q1 to Q10 comprises as follows:

- Q1, Q2, Q3, Q8 and Q9 are questions related to social deficit. All these
questions addressed autistic impairments such as non-verbal
communication skills, emotions reciprocity, social relationships and
expression in communication.

- Q4, Q5, Q6, Q7 and Q10 are those that are not related to social deficit.


### Data Structure:

Datasets were originally in .arff format. The file was saved in “csv”" format and
each dataset (child, adolescent and adult) were transferred to R Studio. The “rbind”
function was then used to combine the datasets together into one large dataset
called “autism”. An additional column was added to the large dataset to signify
which life stages (adult, adolescent, child) everyone corresponded to. This helped
to ease the process of sub-setting individuals into various age groups for further
analysis.

The data has a total of 948 people along with 22 variables. Data comprises of binary
responses to 10 Questions, with 1 representing “yes”, and 0 representing “no”.
Age, Gender, Race, Place of Residence, Age Range are also included, as character
values. ASD column show categorical data on whether the individual had autism or
not. Participants are only shown to have autism if they score seven or higher in
Screening Score (they answered yes to at least 7 out of 10 questions within the
DSM-5).


### Data Cleaning and Wrangling:

As the original dataset contained more males than females, approximately 150
males were randomly deleted from the dataset, making sure to maintain a similar
proportional distribution of children, adolescents and adults to the female dataset.
After that, the dataset was split based on gender, into two separate datasets.
The characteristics of this dataset are shown using the describe function. With the
use of this function, missing values can be identified and deleted if necessary. Two
outliers were also deleted from dataset. Additionally, the age variable that was
originally a character value is subsequently set to an integer value. The binary
response from those 10 Questions were changed into ‘yes’ and ‘no’ for ease of
analysis and interpretation. They were also subsequently changed to a factor
variable to enable random forest analysis.


### Predictive Analysis:

Decision trees and confusion matrix comprised the bulk of the analysis. This was
also accompanied with a barplot for hypothesis 1 using the ggplot function. Other
methods were applied (such as KNN and logistic regression) however both did not
apply well to the binomial dataset that we had. In particular, KNN required the use
of dummy variables and there was not sufficient time for such an analysis to be
constructed.


### Summary of Results:

The diagnosis of ASD through the current DSM-5 criteria seems to be quite
accurate, as can be seen from the confusion matrix where number of
misdiagnosis for both genders are very small in both number and probability.
However, the difference of 4% in correct diagnosis probability between males
and females, may indicate that the DSM-5 is still slightly more relevant in
diagnosing males with ASD than it is for females.

As stated in the decision tree, Q9 is the most important question (or variable) in diagnosis
of both genders. This characteristic can also be seen in this plot because Q9 has the
highest Gini Index.

For females, Q4, Q5, Q6, Q7 and Q10, which are not related to social deficit seems to
hold greater significance in diagnosing a female ASD patient (due to the larger Gini
index for those questions in females, compared to males). In relation to that,
questions, which are social deficit related (Q1, 2, 3, 8) have the lowest Gini Index. This
might imply that questions related to social deficit are not so important compared to
non-social deficit questions.

The plot for males suggest the similar condition as females. However, social deficit
related question, Q3, has relatively larger importance in diagnosing males compared to
females.


### Evaluation:


The first hypothesis that females are more likely to be diagnosed as having ASD at a later
age compared to males, was validated. This may be because females tend to be
misdiagnosed as not having ASD during childhood, where they are less aware of their
characteristic symptoms (Howlin & Asgharian, 1999). It may also be because current
DSM-5 criteria are more relevant to adult females than younger females, although further
research is required to confirm such an inference. Another possible factor may be
because females are better at “blending in” and their characteristic symptoms may be
hidden from the outside (Lai et al., 2015; Mandy et al., 2012).
The plot will be much more relevant to the hypothesis if proportion is taken in to account.
It will also be interesting to reproduce this analysis with a likert scale (ranging from 1 to 7)
for each question, so variance in responses can be compared through the ages.


The second hypothesis was only partially validated. This is because most questions not
related to social deficit played a large role in diagnosing both females and males with
ASD, apart from Q9. It cannot be concretely accepted also because Q9 is still the most
important question for diagnosis of both genders. Q9 is related to symptoms regarding
social and occupational impairment. Nonetheless, greater weighting was still placed on
questions unrelated to social deficit for female diagnosis because those questions were
slightly more significant to their diagnosis (larger mean decrease in Gini). It was also the
case that questions related to social deficit (Q1, 2, 3, 8) had the lowest importance in
females, whereas for males, Q1, 2, 8 but not 3 had the lowest importance. There is thus
some reason to suspect that perhaps questions unrelated to social deficit may play a large
role in not only diagnosing females, but also males with ASD. If this were indeed the case,
further analysis on how social deficit questions (relevant questions except Q9), play a role
in diagnosis should be of critical interest.

Furthermore, the large difference in Gini Index of Q6 and Q7 for females should be
investigated further to understand the drastic drop in average decrease of Gini index.


### Difficulties encountered while obtaining results:

Logistic regression was attempted, but the prediction error seems to be too
inaccurate for our results. The range of threshold for the roc plot resulted in an
absurd accuracy and shape of the graph.

K-nearest neighbour (KNN) algorithm was attempted as well. However, knowledge on
implementation of categorical variables using KNN were lacking. According to
research, categorical variables are compatible with KNN, but dummy variables need
to be implemented beforehand, for it to work. Therefore, more learning and
understanding of dummy variables is required for KNN to work with our dataset.
