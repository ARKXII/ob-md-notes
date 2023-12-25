## Does posing more reviews correlate with more fans?

Please explain your findings and interpretation of the results:
- how do we typically find correlations like this?
- using python/pandas, we plot all review count for each user against the fan count for each user
- how do we do it in sql

*sample query*
```
SELECT range AS fans_range, 
       COUNT(*) AS num_user, 
       AVG(review_count) AS avg_num_review,     
       AVG(fans) AS avg_num_fans
FROM (SELECT CASE  
             WHEN fans BETWEEN 0 AND 9 THEN '0 - 9'
             WHEN fans BETWEEN 10 AND 99 THEN '10 - 99'
             ELSE '100-1000' END AS range,
             review_count, 
             fans
      FROM user) AS subtable
GROUP BY subtable.range
```

*output*
![[Pasted image 20230601113328.png]]

---
### 1. For this last part of your analysis, you are going to choose the type of analysis you want to conduct on the Yelp dataset and are going to prepare the data for analysis.

i. Indicate the type of analysis you chose to do:

- Analyzing the distribution of star ratings for restaurants in the Yelp dataset.

ii. Write 1-2 brief paragraphs on the type of data you will need for your analysis and why you chose that data:
	- business categories
	- average stars for each city
	- average review count

I will need the category from CATEGORY table, avg(stars) and review_count from the BUSINESS table. This will be my basis for analyzing the star distributions for the restaurants. It's easier to find the correlation between the review count and the star rating for cities themselves, since we're only looking at one category. From these, we can infer if the restaurants in one city will be high-rated statistically. I also included the review count to lend credibility to its rating (i.e. *if a lot of people say the restaurants are good, then it must be good*). We can forgive any bias this leads to since we're looking at the data in bulk.

iii. Output of your finished dataset:

iv. Provide the SQL code you used to create your final dataset: