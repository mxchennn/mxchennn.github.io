---
layout: post
title: hospital lab
#subtitle: 
#gh-repo: daattali/beautiful-jekyll
#gh-badge: [star, fork, follow]
#tags: [test]
#comments: true
---

the county in new york state with the most hospital beds per person is new york

to generate the csv file, i used code simmilar to that in the web api worksheet, and printed out the values for the csv file.
to manually clean the data, i copied it into a google sheets file, and used an equation in google sheets to standardize the number of beds per person.

to analyze the csv file, i wrote a function that organized the data by county, ignoring bed type, and then summed the values of any given field (in this case, beds per person)

~~~
def calculate_sum(field_to_sum):
    county_to_values = {}
    county_to_sum = {}
    with open("/Users/mingxingchen/Desktop/ArtOfData/HospitalLab/hospital.csv", "r") as f:
        file_data = csv.DictReader(f)
        for current_row_data in file_data:
            #assigns variables to each county in the data set, and whatever field is to be summed
            current_county = current_row_data["county"]
            current_county_data = current_row_data[field_to_sum]
            #sort all the data by county
            if current_county not in county_to_values:
                county_to_values[current_county] = []
            county_to_values[current_county].append(float(current_county_data))

    for county in county_to_values:
        county_to_sum[county] = sum(county_to_values[county])
~~~

i then wrote appended each value of the dictionary county_to_sum into a list, and used the max function to find the highest value, which ended up being the value associated with the county new york

~~~
summed_values = []
    for county in county_to_sum:
        summed_values.append(county_to_sum[county])
    print(max(summed_values))
~~~