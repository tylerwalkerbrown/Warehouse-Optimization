# Warehouse Optimization
 
## What are the best distribution centers for OCF Products in the US?

This is the map of the orders within the United States with the hue set to the items. In red is Winter Rye, which is the highest-selling product that the ecommerce store has in its inventory. With these coordinates, we wanted to create a script that has the ability to group by the product to get the centroids for each product, so we can establish where to send items.

![orders](https://user-images.githubusercontent.com/94020684/221389677-f7aac8d2-d2ae-46e3-af70-4935f8ef104f.png)

This is what we got for a couple of the product centroids. This is a dynamic map within Python that can display the centroids by the products that you have in the inventory. We did this by performing a k-means ML task that allowed us to get the averages of two k clusters. The reason that two clusters were chosen is because the business wanted it to be two to get two different warehouses per product.

![centroids](https://user-images.githubusercontent.com/94020684/221389670-767d40a3-b63b-4b34-8b96-484be892a83f.png)

## Next Steps 

With the centroids established, I had to obtain the locations of the Amazon warehouses. For this, I web scraped the addresses and ran it through Geopy, which allowed me to get the latitude and longitude of the warehouses. With the warehouse locations, I then took the centroids of the data and got the distances of each one to then group by each centroid to get the minimum distance, which is the closest warehouse. This can then be seen in a table as shown below.

![image](https://user-images.githubusercontent.com/94020684/221389941-51c6ce44-8418-4299-9ece-e430a1e8183a.png)

## Analysis of Customers 
- Explore distributions 
- Summary Stats 
- Feature Engineering
- Buying Habits 
- Hypothesis Chi2
- Residual Analysis
- Simple Linear

# Summary Stats

The first thing we did was create a table of descriptive statistics that gave us insights into what type of earners are buying our products. To collect data on suspected income, I used Zillow's API to loop through addresses and append a dictionary created in Python. Below, you can see the table that may be a little inconsistent but serves a general purpose. Winter Rye was spotted first as the highest amount sold, as we saw in the map. The other thing that was noticed was the low earners for the tapping category.

![Screen Shot 2023-02-25 at 10 14 37 PM](https://user-images.githubusercontent.com/94020684/221390327-39618074-4666-4ba6-af24-ea417b9d8f13.png)

Here is a plot of the population densities broken up into deciles and arranged by male and female. This was interesting because we found opposite distributions. For men, we found that most purchases are done in the urban area, whereas for females, they tend to have a higher rate of purchasing in rural or suburban areas.

![image](https://user-images.githubusercontent.com/94020684/221390436-b47958f8-72f4-467f-9cf7-0cd410b85606.png)

Now looking at the distribution of incomes between females and males, you can notice that there is a spike down around $50k for men, causing the mean income to be lower for men. In contrast, females have a higher density higher. Females seem to have higher density outliers in the data, which is also causing the male's average to be lower than females. You can also notice how there is a very large number of men compared to women among the customers.

![image](https://user-images.githubusercontent.com/94020684/221390467-50ed33de-8060-4332-a708-d0d06a7db43a.png)

Bar plot of men vs women.

![image](https://user-images.githubusercontent.com/94020684/221390519-08bc90d7-3bc0-494c-ae6f-d0e7c299690b.png)

## Buying Habits
Females purchase bulbs at almost 5 times the rate than men do and corn gluten three times as much. Most of the categories are < 2% with the biggest sellers being winter rye (accounts for around 71% of units sold) and greensand around 13%.

quantity
item              gender
20-20-20          male       0.102354
Alfalfa           female     0.204708
Aluminum Sulfate  male       0.511771
Buckwheat         female     0.102354
                  male       0.102354
Corn Gluten       female     2.456499
                  male       0.307062
Flower Bulbs      female     2.354145
                  male       0.716479
Greensand         female     7.778915
                  male       5.936540
Oyster Shell      female     0.511771
                  male       2.149437
Tapping           female     0.716479
                  male       4.196520
Winter Rye        female    34.800409
                  male      37.052201
                  
                  
With this data I wanted to test to see if these is any major difference between the habits of the shoppers we get to the store. For this I did a chi2 test where I tested the items purchased and gender to see if there was a difference. The first test I conducted was of the whole sample which gave me these results: 

- Chi-squared test statistic = 125.14
- P-value = 0.00000000
- Degrees of freedom = 20
- There is sufficient evidence to reject the null hypothesis at the 95.0% confidence level.The association between Gender and Item Purchased is significant.

After I saw that I then retested using an even amount of males and females in a random sample. This came back with the results I exceptec where there is no real disparity between the two groups. 

- Chi-squared test statistic = 5.24
- P-value = 0.3870
- Degrees of freedom = 5
- There is not sufficient evidence to reject the null hypothesis at the 95.0% confidence level.The association between Gender and Item Purchased is not significant.

