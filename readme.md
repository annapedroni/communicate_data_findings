# PISA 2012 Data Exploration
## by Anna Pedroni


## Dataset

### PISA:

- is an age-based survey, assessing 15-year-old students in school in grade 7 or higher. These students are approaching the end of compulsory schooling in most participating countries, and school enrolment at this level is close to universal in almost all OECD countries;
- take a literacy perspective, which focuses on the extent to which students can apply the knowledge and skills they have learned and practised at school when confronted with situations and challenges for which that knowledge may be relevant;
- allows for the assessment of additional cross-curricular competencies [...]. For 2012 a computer-delivered assessment of mathematics and problem solving was added, along with an assessment of financial literacy;
- uses Student Questionnaires to collect information from students on various aspects of their home, family and school background;
- uses School Questionnaires to collect information from schools about various aspects of organisation and educational provision in schools;
- uses Parent Questionnaires administered to the parents of the students participating in PISA (in 11 countries for the 2012 survey);

- test were administered in the language of instruction of mathematics

### Focus and Partecipation

PISA 2012, the fifth PISA survey covered **reading, mathematics, science, problem solving and financial literacy** with a primary focus on mathematics.

It was conducted in 34 OECD countries and 31 partner countries/economies.
All 65 countries/economies completed the paper-based tests, with assessments lasting a total of two hours for each student.

### What is the structure of your dataset?

The main dataset contains 485490 rows, each one representing one student, and 636 columns with coded names.

A second files provide the dictionary for the criptic column names. There we see that each row of the main dataset
- starts with 6 columns about the location of the school attended by the student (e.g. country code, subregion, school ID)
- follows with the sudent ID column and a lot of personal information about the student and their family, their economic situation and experience in school (both emotional and with the school teaching), and a lot more.
- ends with their PLAUSIBLE results at the PISA tests (math and math subscales, science and reading; NO financial literacy) and the weight of the entry within their country, and
- the data on which the entry was created.

### Main feature(s) of interest in your dataset?

The description given above is a very summary one, and the dataset is truly fascinating for the possibilities of analysis it offers, even if it contains only the results for the main survey (the one used in all the countries).

As a matter of fact, here I need to cut on the information I handle, because of scarcity of resources (time and computer memory).

As said PISA 2012 focussed on mathematics, so in the dataset there are plausible scores about subset of mathematic competencies.

Moreover, Countries that participated in the survey have different languages, but also different cultures and writing systems.

I will select a subset of countries such as their writing system belongs to one of these groups:
  - alphabetic, with a highly phonemic orthography (or shallow orthography): Spanish, Finnish, Italian, German *
  - alphabetic, with a more complex relationship between orthography and pronunciation, a deeper orthography: English, French, Arabic *
  - logographic: Chinese, Japanese ([Korean](https://en.wikipedia.org/wiki/Korean_language#Writing_system), but keeping in mind that Korean logograms, still studied in school, as been long replaced in use by Korean alphabet) *


\* *I wanted to make the distinction between languages "that are written how they are pronunced", languages "that you cannot guess how a word is written just by hearing it" and languages that use ideograms... [Wikipedia](https://en.wikipedia.org/wiki/Writing_system) and the article [Getting to the bottom of orthographic depth](https://link.springer.com/article/10.3758/s13423-015-0835-2#Sec7) helped me putting things down a little more precisely.*

### What features in the dataset will help support the investigation?

I will keep for sure the mathematic and reading scores, as well as the language(s) spoken by the students and the language in which the test was administered.

There is a wealth of information about the students' background as well, and it seems like a good idea to see if there are influential factors there, for instance the *index of economic, social and cultural status (column "ESCS" in the dataset)*.

Proficiency levels
In the Technical Report (from p.296 on) it is possible to find the scales used to record the proficiency for the different areas:

Mathematics: >1, 1, 2, 3, 4, 5, 6 (highest level) *

Reading and Science: I couldn't find the scales in the document. There is, however, indicated that the scales are just one for each discipline and are respectively the same as 2009 and 2006.

Reading: 1a, 1b, 2, 3, 4, 5, 6 (highest level)
Science: 1, 2, 3, 4, 5, 6 (highest level)
All this proficiency levels are provided with a description of the competencies associated with them.

(problem solving and financial literacy are also described, but the relative plausible scores are not in the dataset)

\*NB. this is the main scale for mathematics, and also for all the subscales of different competencies tested (e.g.: "formulating situations mathematically", "employing mathematical concepts, facts, ...")

However, the results are not given by those scales: enter plausible values.

My understanding about these evil PLAUSIBLE SCORES
Reading through the Technical report, I've come up with this layman explanation:

For every student, for every scale and subscale, the results of the tests have been taken and used to compute 5 plausible results that student could have reached if they had taken all the PISA tests, not only the subset contained in the booklet they tackled. This has been done for accuracy in later estimating the parameters of the population (all the students of a Country). Accuracy of those parameters is also the reason it would be better to use the weight of each student and also to repeat the calculations 5 times per scale (one for each plausible score column).

The plausible score is given in a scale that can be converted to the relative proficiency level according to the bands provided in the Technical report:

Main mathematical literacy levels and subscales as well - p. 297 of the Technical report
Level : Score points on the PISA scale

6 : Above 669.3
5 : From 607.0 to less than 669.3
4 : From 544.7 to less than 607.0
3 : From 482.4 to less than 544.7
2 : From 420.1 to less than 482.4
1 : From 357.8 to less than 420.1
Below level 1 : Below 357.8
Reading literacy performance band definitions on the PISA scale - p. 265 of the PISA 2009 Technical report
Level : Score points on the PISA scale

6 : Higher than 698.32
5 : Higher than 625.61 and less than or equal to 698.32
4 : Higher than 552.89 and less than or equal to 625.61
3 : Higher than 480.18 and less than or equal to 552.89
2 : Higher than 407.47 and less than or equal to 480.18
1a : Higher than 334.75 and less than or equal to 407.47
1b : 262.04 to less than or equal to 334.75
Scientific literacy performance band definitions on the PISA scale - p. 293 of the PISA 2006 Technical report
Level : Score points on the PISA scale

6 : Above 707.9
5 : 633.3 to 707.9
4 : 558.7 to 633.3
3 : 484.1 to 558.7
2 : 409.5 to 484.1
1 : 334.9 to 409.5

### About the weights
Every row/student has a weight (more than one, to be precise, but..).

The reason for it resides, if I got it right, in the sampling process of subregions, schools and students done in every Country and the reason to use it (them) is, in the end, to better represent the country parameters.

I'm planning to regroup the students by different parameters (primary first language = language at school = language of the PISA test), so they won't be divided by Country and won't represent country level proficiency.

Therefore I think it would be wrong to use the weights within this project.

## Summary of Findings

I initially kept:

- these 37 Countries/economies: 'United Arab Emirates', 'Argentina', 'Australia', 'Austria', 'Belgium', 'Canada', 'Switzerland', 'Chile', 'Colombia', 'Costa Rica', 'Germany', 'Spain', 'Finland', 'France', 'United Kingdom', 'Hong Kong-China', 'Ireland', 'Italy', 'Japan', 'Korea', 'Liechtenstein', 'Luxembourg', 'Macao-China', 'Mexico', 'New Zealand', 'Peru', 'Qatar', 'China-Shanghai', 'Florida (USA)', 'Connecticut (USA)', 'Massachusetts (USA)', 'Singapore', 'Chinese Taipei', 'Tunisia', 'Uruguay', 'United States of America', 'Vietnam'

- all the plausible values, plus:
- 'Country code 3-character',
- 'OECD country', 'Student ID', 'Gender', 'Mother<Highest Schooling>', 'Mother Current Job Status', 'Father<Highest Schooling>', 'Father Current Job Status', 'Highest educational level of parents', 'Country of Birth International - Self', 'First language learned', 'Age started learning <test language>', 'Language of the test', 'Language spoken - Mother', 'Language spoken - Father', 'Standard or simplified set of booklets', 'Attitude towards School: Learning Outcomes', 'Attitude towards School: Learning Activities', 'Sense of Belonging to School', "Mathematics Teacher's Classroom Management", 'Cognitive Activation in Mathematics Lessons', 'Instrumental Motivation for Mathematics', 'Mathematics Interest', 'Mathematics Work Ethic', "Mathematics Teacher's Support", 'Mathematics Self-Concept', 'Teacher Student Relations', 'Subjective Norms in Mathematics', 'Index of economic, social and cultural status', 'Home educational resources', 'Preference for Heritage Language in Conversations with Family and Friends', 'Language at home (3-digit code)', 'International Language at Home', 'Preference for Heritage Language in Language Reception and Production'

It was too much.
I did a lot of cleaning and found some problems. For instance:
- I considered the use of the variables about the highest level of education of parents (mother, father and both of them), the number of values for each column is similar and the last one is theoretically derived from the first two, but that is not possible: Father and mother's highest schooling level reported is the "ISCED 3A, 4", while for the highest level between the two parents, "ISCED 5B" and "ISCED 5A, 6" contain together around 150k of the 290,593 available data.
- language at home unique values were far too many to be used, and could have done with a bit of cleaning (e.g. Italian is in 'Italian', 'Another EU language (ITA)', 'Another language (ITA) ', 'Another official language (ITA)').


I created a new column, "Language_type", to be able to group the data by these values:
- shallow_ortography =['Spanish', 'Finnish', 'Italian', 'German']
- deep_ortography = ['English', 'French', 'Arabic', 'English_Arabic']
- logographic = ['Chinese', 'Japanese', 'Korean', 'Shanghai dialect', 'Mandarin', 'Cantonese']
The count of rows for the three language types was
```
shallow orthography    152681
deep orthography       114292
logographic             31621
```

Since, the last group was much less numerous than the two alphabetic ones, I sampled the Countries in the other groups to get to a similar number of rows.

 However I included a flaw that became apparent only when I got to the bivariate exploration.

Up to that moment the unimodal distribution of the mathematics scores appeared to be right-skewed, with the majority of student in the levels 2 and 3, followed by 1 and below_1, and lastly 4, 5, 6.

The bimodal distribution "math levels by language type", showed a clear difference between the shape of the two alphabetic group on one side and the shape of the logographic group on the other (with the latter performing a lot better).

I wondered if the many  "too low" ones  could be due to problem with the language (maybe students that moved from a different language area).
Therefore, to clean the data from these "interference" I dropped the rows where the language spoken at home by the student (column "International Language at Home") was not the same as the language of the test.
This, together with the fact that other rows had to be dropped for missing data in columns I was planning to use, left me with a dataset much reduced, that became insufficient when finally I plotted the distributions of math levels by booklet type (the mentioned flaw):
- the distribution of math levels of the students who solved the simplified set of booklets was heavily left-skewed, with the bulk of the data in the lowest levels;
- the distribution of math levels of the students who solved the standard set of booklets tended to be normal, with a much higher mean.

What had happened is that Countries who chose to use the simplified version used ONLY that one. In those countries the results are all right skewed, with very bad results in general. AND this Countries were found only in the two alphabetic groups, strongly influencing the distributions of their math levels.
These Countries resulted to be the South American ones, plus Tunisia and Vietnam.
I had initially kept them, because they had been weighted so that the results of those Countries could be comparable with the rest of the data. It is indeed possible to use the data all together and with the correct weight for each line) to judge the performance of the schooling system of each Country compared to the others. However I am regrouping the data by a different criterion (the language type) and therefore including the Countries whose schooling system has evidently a markedly different effect on the performance of their students (and, in fact, those Countries choose the simplified booklets) was simply adding complexity (and a variable that needed to be highlighted).

So I started the selection again and I better chose my variables:
- 'Country code 3-character',
- 'Student ID',
- 'Gender',
- 'Language of the test',
- 'Standard or simplified set of booklets' (to delete the simplified),
- 'Attitude towards School: Learning Activities',
- 'Cognitive Activation in Mathematics Lessons',
- 'Index of economic, social and cultural status',
- 'Language at home (3-digit code)',
- 'International Language at Home' (to keep only student that spoke at home the same language of the test),
- 'Plausible value 1 in mathematics',
- 'Plausible value 1 in reading',

and I added:
- language type,
- plausible level in mathematics,
- plausible level in reading,
- ESCS levels

The two plausible levels variables were added ALONG the plausible value, this time, so that I had both a numerical and a categorical variable for reading and mathematics scores.

The same goes for the ESCS levels variable: it is the categorical version of the 'Index of economic, social and cultural status' (numerical).

#### An univariate look at my new dataset:

- **Country** : the most represented is Italy (more than 20k students each), followed by Spain and Canada (above 15k each). Between 10k and 15k there are Australia and the UK. All other Countries are under 10k.;
- **Student_ID**
- **Gender** : about 50% females, 50% males
- **Index_of_economic_social_and_cultural_status** : ESCS distribution is left skewed (less than before, probably because of the absence of the Countries that choose the simplified booklets).
  If we take 0 as a neutral point, were students are "OK" (not priviledged, but neither disadvantaged), then there are 17204 more student on the disadvantaged side than in the advantaged one. Before the last cleaning they were 20135
  About the extremes,  for ESCS < -2 now there are 962 students more than for ESCS >+2. Before there were 17777 of them.
- **Language_at_home** : a reasonable number of languages survived the last cleaning (read: many less than before);
- **Language_of_the_test** : English is the most represented, followed by Italian. Then we have Spanish, French and German. All other account for less than 8k rows each;
- **Language_type** : my new variable: three categories "shallow_ortography" (Spanish, Finnish, Italian, German), "deep_ortography" (English, French, Arabic, English_Arabic), "logographic" (Chinese, Japanese, Korean, Shanghai dialect, Mandarin, Cantonese)
- **Plausible_value_in_mathematics** and **Plausible_level_in_math** : with the dataset better cleaned from the start, the math values and levels appear to be normally distributed, with the mode at 3 for the levels, and a mean around 500 for the values
- **Plausible_value_in_reading** and **Plausible_level_in_reading** : The distribution of the reading level has a mode of 3 as well, and the mean of the reading values is around 500, as the one for math values, but these two distributions are slightly left-skewed.

#### Bivariate:
- **Math levels vs reading levels**: There is a clear positive correlation between test result in reading and test results in mathematics.

- **Math levels by ESCS**: If, we plot the math levels by the ESCS index, we see the curve starting slightly right-skewed for math level 'below 1', going normal and then bending on the other side, with an ESCS index mean that increases, as we move up the math levels. When we reach level 6 it is definitely left-skewed.

There looks to be a correlation here, and it is a bit sad: very bad levels in mathematics can be "achieved" by students from every socioeconomic and cultural background (but actually, students in the lowest ESCS level are not the worst achievers). On the other side, students living in the most disadvantaged condition are not presents in the top mathematics scores.

- **reading and ESCS**: The relationship between reading and ESCS is similar to math and ESCS.

- **Math levels by gender (normalized)**: Girls seem to score a bit worst, generally: their mean is slightly lower, and their std is narrower

- Contrary to math levels by gender, **READING levels by gender** suggests that girls are better than boys in this task.

###### The relationship looks NOT to be better performance in reading gives better performance in mathematics, but rather BETTER SOCIOECONOMIC AND CULTURAL BACKGROUND ALLOWS FOR ANY READING AND MATH PERFORMANCE, WORSE SOCIOECONOMIC AND CULTURAL BACKGROUND HINDERS TOP ACHIEVEMENTS IN READING AND MATHEMATICS.

## Key Insights for Presentation

What I wanted to explore, as said in the introduction, is if the type of writing system of a language has an influence on the performance in the mathematics tests.

Therefore I looked for the relationship between **Math values and language type**:
- Using performance levels it seems that their distribution is left skewed.
  Using the values, which are more fine-grained, the distributions of each language group results normal:
- The students using a logographic language perform better.
  The logographic group has an higher mean and a larger std (top of the curve is kind of flattened).
- The deep orthography language group distribution has a similar shape, but with a lower mean (the lowest of the three).
- The shallow orthography group is in the middle, with a mean a little above the one of the deep orthography languages, and the smallest std.

_This plot needs a title and better axix labels_

- so then explaing that ESCS seems to have a big impact on performance (see above)

- and than look at the schooling system:
  - Macao
  - Belgium, Luxemburg, Switzerland
  - English speaking countries and Singapore


## References

### PISA survey 2012
- http://www.oecd.org/pisa/pisaproducts/PISA-2012-technical-report-final.pdf
- https://www.oecd.org/pisa/data/42025182.pdf
- https://www.oecd-ilibrary.org/docserver/9789264167872-en.pdf?expires=1587756729&id=id&accname=guest&checksum=3C4CAAFFDA33331CACE78A9B3A852FA5

### Language and phonetics
- https://en.wikipedia.org/wiki/Korean_language#Writing_system
- https://en.wikipedia.org/wiki/Writing_system
- https://link.springer.com/article/10.3758/s13423-015-0835-2#Sec7

### Code
- https://pandas.pydata.org/
- https://www.geeksforgeeks.org/
- https://stackoverflow.com/
- https://towardsdatascience.com/3-simple-ways-to-handle-large-data-with-pandas-d9164a3c02c1
