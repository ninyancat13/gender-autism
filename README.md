# gender_autism
Looking at how the DSM-5 criteria of autism may be biased for female participants because base cases used to create the model criteria had more male autistic participants. 


Implemented using R.


Original dataset taken from: 
https://archive.ics.uci.edu/ml/datasets/Autistic+Spectrum+Disorder+Screening+Data+for+Children++
https://archive.ics.uci.edu/ml/datasets/Autistic+Spectrum+Disorder+Screening+Data+for+Adolescent+++ 
https://archive.ics.uci.edu/ml/datasets/Autism+Screening+Adult


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
predictive model to identify the influence gender may play in ASD diagnosis
