# Pewlett Hackard Analysis

## Overview
Withing the larger task of organizing Pewlett Hackard's database systems, we're focusing on two specific challenges: determining the number of retiring employees per job title and identifying employees who are eligible to participate in a mentorship program. With the results in hand, we'll write a report that summarizes the analysis makes recommendations on how to prepare for the “silver tsunami” as many current employees reach retirement age.

## Results

Working from the basis that employees born between the years 1952 and 1955 are at prime retirement age, we'll use postgres queries to identify employees born between January 1, 1952 and December 31, 1955. Our first query collected every employee born within that range but was inaccurate because it contained several thousand duplicate entries. As several employees changed roles within the company throughout their tenure, they existed as separate entries within the DB for each job title they accumulated. 

![duplicates](https://github.com/watsonlarry/Pewlett_Hackard_Analysis/blob/main/Resources/Duplicates.png)

To eliminate the duplicates, we used the DISTINCT ON function to retrieve only the first occurrence of an employee number and separated them into a new table "unique_titles".

![unique](https://github.com/watsonlarry/Pewlett_Hackard_Analysis/blob/main/Resources/Unique.png)

With the duplicates pruned, we could analyze the correct number of employees who existed in our retirement range:

![table](https://github.com/watsonlarry/Pewlett_Hackard_Analysis/blob/main/Resources/Retiring.png)

To identify employees that were most fit for Pewlett Hackard's mentorship program, we decided we'd look for employees in the year 1965 (a limited range in my opinion, but hey what are you going to do...). The search revealed 1549 employees eligible to become mentors.

## Conclusion

The results of the analysis reveal that there is a large section of employees, 90,398, leaving the company over the next few years to retire, and only a fraction of the number are eligible to mentor newer employees, 1549. The number of mentors is too few to stymie the lost labor cost of the "silver tsunami" given the current parameters of eligibility. If we expand the eligibility search to encompass more than just one birth year, maybe from 1963-1965, the company may have enough mentors to weather the wave of retirements. Results from the expanded search:

![expanded](https://github.com/watsonlarry/Pewlett_Hackard_Analysis/blob/main/Resources/expanded_mentorship_eligibilty.png)

A pool of nearly 40,000 eligible mentors is a much better result than the previous query. And this query's results include 3 managers to assist in management training, considering 2 will be lost to retirement.
