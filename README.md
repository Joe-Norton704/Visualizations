# Visualizations
Here’s a Power BI dashboard I built this evening. In this project I explored the raw data in SQL Server. I then used multiple JOINs and wrapped them in a CTE to move the data I wanted over to Power BI. My dashboard will allow users to extract insights about seasonality, revenue, and discounts. 

SQL code:
--Brining tables together CTE.
WITH hotels as (
SELECT * FROM DBO.['2018$']
UNION
SELECT * FROM DBO.['2019$']
UNION
SELECT * FROM DBO.['2020$'])
-- Using join to bring together hotel data and market segment data.
SELECT DISTINCT * 
FROM hotels
LEFT JOIN dbo.market_segment$
	ON hotels.market_segment = market_segment$.market_segment
LEFT JOIN dbo.meal_cost$
	ON meal_cost$.meal = hotels.meal;
