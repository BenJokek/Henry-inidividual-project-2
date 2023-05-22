## Introduction

In the realm of aviation, the occurrence of airplane crashes has left an indelible mark on the history of the past century. Despite significant advancements in technology and the tireless pursuit of safety, these catastrophic events continue to disrupt the lives of individuals and communities worldwide. With the ever-evolving landscape of air travel, one might assume that airplanes have become safer over time. While it is true that consistent improvements in technology have enhanced overall flight safety, the complex dynamics of the modern airline industry present new challenges.

Airline business models have progressively shifted towards maximizing efficiency and accommodating a higher number of passengers per flight. While this approach allows for increased accessibility and convenience, it also amplifies the potential consequences of any mishap. The cost of a crash is no longer measured solely in financial terms; the true toll is reflected in the invaluable loss of human lives.

Throughout this project, we delve into the sobering reality of airplane crashes, exploring their multifaceted nature and the various factors that contribute to their occurrence. By analyzing historical data and studying the patterns, we seek to gain a deeper understanding of these incidents and shed light on the ongoing efforts to mitigate risks in aviation. Join me as we navigate through the annals of aviation history, uncovering lessons learned, and advocating for a safer future in the skies.

## **Analyzing Two Different Datasets**

In order to find meaningful correlations, two different datasets were used. One has the records of major accidents in the past 110 years. The other has the records of flights in the past 50 years.

## **Data Cleaning**

### Explanation of the data cleaning process I performed in the first dataset:

1. First, I imported the necessary libraries, including pandas, numpy, re, matplotlib.pyplot, and seaborn.
2. Next, I read the CSV file 'AccidentesAviones.csv' into a pandas DataFrame.
3. To ensure clarity and consistency, I renamed several columns in the DataFrame using the **`rename()`** function.
4. I reordered the columns in the DataFrame according to the desired sequence.
5. I replaced any occurrences of "?" with None in the DataFrame using the **`replace()`** function.
6. Certain columns that were not relevant to the analysis were dropped from the DataFrame.
7. Rows with missing values in the 'total_aboard' column were dropped from the DataFrame using the **`dropna()`** function.
8. The 'total_aboard' and 'total_fatalities_aboard' columns were converted to integer data type using the **`astype()`** function.
9. For rows where the 'hour' column was null, I assumed the time of the crash as 00:00 (midnight) and filled the null values accordingly.
10. I defined a function to extract the digits from strings in the 'hour' column. This function was applied to the 'hour' column using the **`apply()`** function.
11. Another function was created to format the time in the 'hour' column. This function added a zero at the beginning or end to three-digit values depending the last two digits.
12. The 'date' and 'hour' columns were combined into a single datetime column named 'datetime'. This was achieved by concatenating the 'date' and 'hour' columns using the **`+`** operator and converting the resulting string to datetime format using **`pd.to_datetime()`**. Finally, the 'date' and 'hour' columns were dropped from the DataFrame.

### Explanation of the data cleaning process I performed in the second dataset:

1. Firstly, I imported the necessary libraries and read the CSV file 'total_flights.csv' into a pandas DataFrame named 'Totals'.
2. I specified a list of columns to drop from the 'Totals' DataFrame using the **`drop()`** function and assigned the result back to 'Totals'.
3. I replaced any null values in the 'Totals' DataFrame with 0 using the **`replace()`** function.
4. The 'Totals' DataFrame was modified to compute the sum of each column. This was done by creating a new DataFrame named 'Totals' that consists of the column sums calculated using the **`sum()`** function on the 'Totals' DataFrame.
5. The column in the 'Totals' DataFrame was named 'Sum' using the **`columns`** attribute.
6. The index name of the 'Totals' DataFrame was set to 'Year' using the **`index.name`** attribute.

Result (total flights by year):

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/72b5c5e3-313c-463a-ad6b-5f120b3ea218/Untitled.png)

All the steps helped to clean and preprocess the data, making it ready for further analysis and exploration.

---

# **FINDINGS**

How many plane accidents have occurred since 1908? **Nearly 5,000.** This includes military (15.2%) and non-military (84.8%) flights.

How many lives have been lost in these accidents? **Over 111,000.**

What was the deadliest year for plane crashes? **1972.** This year witnessed 77 plane crashes, which resulted in nearly 2,800 deaths.

## ****Yearly Trend****

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/95643a3b-3570-41f1-8cac-12e383e68c8b/Untitled.png)

We can see a gradual increase in the number of crashes from 1908 (with some lateral trend) and a dramatic decrease in recent years. The year 1972 was the deadliest year with the highest number of fatalities.

## **Monthly, Weekly and Hourly Trend**

There is no definite pattern in the monthly trend, but the number of crashes tends to be a little higher during winter seasons. Respecting the hours, at early hours seem to be less crashes.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/40eaeb8f-8690-4e5d-990c-09fbdc559807/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a98be111-2cc9-4382-b294-41b0c0176d16/Untitled.png)

## Military vs non-military crashes

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9ddb5a35-8cf6-42e8-a5bd-7e15fa2ea8ab/Untitled.png)

Seems to be a high number of military crashes in the 40s, I suppose because the World War 2.

## Number of people involved

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a9fbc630-0e24-4d73-98e3-5241f3b56265/Untitled.png)

This looks scary. The number of fatalities is high compared with the total aboard. 

But the graphs don't consider the accidents by all flights by year. So 1970-1990 look very bad years but there might be also the rise of total amount of people flying by air while actually proportion became lower.

So, the dataset considers "total aboards" from accidents... But what about those where there was no accident?

I'll use a dataset from the World Bank ([https://data.worldbank.org/indicator/IS.AIR.DPRT](https://data.worldbank.org/indicator/IS.AIR.DPRT?end=2016&start=1970&view=chart)) to get to the bottom of the matter.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/04df6485-74d9-45b5-a190-dd55094df03b/Untitled.png)

From this plot we can see that trend actually goes down which was maybe not so obvious from the other plot. Let's put line with ratio and number of deaths on one plot.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/59c08353-7d42-4eab-a7e1-ab0f19668cfd/Untitled.png)

## **Operator**

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/061b6ad3-618b-4f33-ac82-a00594ee1339/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3e75fa74-8ec5-4026-a49c-d87385bb0fd8/Untitled.png)

These plots show that among commercial airlines, Russian Airlines, Aeroflot has a record as the airline with the most crashes, 253 (with 8802 fatalities), followed by 73 crashes from Air France (with 3395 fatalities). Aeroflot is one of the largest air carriers in the world and presents a good example of rapid innovative development. Their innovation program aims at increasing safety. As a result, Aeroflot has significantly improved their flight safety in the past few years. 253 crashes, however, are hard to ignore. One of the reasons why Aeroflot has the highest frequency of crashes was the collapse of the country's aircraft manufacturing industry, which caused the Russian airlines to rely on the old aircraft that they had been using for decades. 

Before the 2022 Russian invasion of Ukraine, the airline flew to 146 destinations in 52 countries. The number of destinations was significantly reduced after many countries banned Russian aircraft.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/aad04d36-912a-4542-84cc-05581d1a5387/Untitled.png)

## TYPES

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0a11e3dc-e421-422a-b1a2-e17eeb542606/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/854b91e1-369b-4d57-9776-a75fbeda21b9/Untitled.png)

In terms of **manufacturers models**, the Douglas DC-3 planes have been involved in 330 crashes. Most of these crashes were concentrated in the 15–20 years following World War II. However, DC-3 was considered to be a very rugged plane and to be the most advanced of its time, and was built decades before technological progress in safety to air travel.

## Conclusions

Based on the analysis conducted, we can draw the following conclusions for this project:

1. Decrease in crashes and fatalities: The analysis reveals a notable decrease in the number of airplane crashes and fatalities over time. Despite the increase in the number of passengers, the aviation industry has managed to improve safety measures and protocols, resulting in a decline in the frequency and severity of incidents.
2. Positive trend in air travel safety: The consistent reduction in the number of incidents and fatalities suggests that air travel has become safer over the years. This conclusion is supported by both absolute numbers and relative measures, such as the ratio of fatalities to the total number of accidents.
3. Continuous improvement: While the analysis demonstrates positive trends in air travel safety, it is important to emphasize the need for ongoing efforts to further enhance safety standards. The aviation industry should continue to invest in research, technology, training, and collaborative initiatives to maintain and improve the already achieved safety levels.

In conclusion, the analysis indicates that air travel has indeed become safer over time. The combination of decreasing crash rates, declining fatalities, and the implementation of robust safety measures demonstrates the industry's commitment to prioritizing passenger safety. However, it is crucial to remain vigilant and continuously strive for improvement to ensure the highest level of safety in air transportation.