---
layout: post
title: descriptive lab
#subtitle: 
#gh-repo: daattali/beautiful-jekyll
#gh-badge: [star, fork, follow]
#tags: [test]
#comments: true
---
for this lab i worked with the "new coder survey" dataset
the first variable i looked at was the age of the participants
~~~
pd.DataFrame.describe(survey)
~~~
when i looked at the summary statistics of the dataset, i saw that the mean age was around 28 years old

~~~
ages = survey['Age']
sns.histplot(data = survey, x = ages)
~~~
then i generated a histogram showing the distribution of ages, and saw that the graph was skewed to the right

~~~
CityPopulations = survey['CityPopulation']

sns.boxplot(x = CityPopulations, y = ages, data = survey, order = ("less than 100,000", "between 100,000 and 1 million", "more than 1 million"), palette=(sns.color_palette(n_colors=1)))
~~~
then, i looked at the relationship between age and city population
i generated a bar plot that showed that older people tended to live in less populated areas than younger people, this makes sense because older people would probably live in more rural areas.