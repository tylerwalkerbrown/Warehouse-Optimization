# Warehouse Optimization
 
## What are the best distribution centers for OCF Products in the US?


This is the map of the orders within the United States with hue set to the items. In red is Winter Rye which is the highest selling product that the ecomemrce store has in its inventory. With these coordinate we wanted to create a script that has the ability to group by the product to get the centroids for each product so we can establish where to sent items.

![orders](https://user-images.githubusercontent.com/94020684/221389677-f7aac8d2-d2ae-46e3-af70-4935f8ef104f.png)

This is what we got for a couple of the products centroids. This is a dynamic mape within python that can display the centroids by the producst that you have in the inventory. We did this by performing a k-mean ML task that allowed us top get the averages of two k clusters. The reason thast two clusters were chosen is because the business wanted it to be two to get two different warehouses per product.

![centroids](https://user-images.githubusercontent.com/94020684/221389670-767d40a3-b63b-4b34-8b96-484be892a83f.png)

## Next Steps 

With the centroids established I had to obtain the locations of the Amazon warehouses. For this I web scraped the addresses and ran it thorugh geopy that allowed me to get the latitude and longitude of the warehouses. With the warehouse locations I then took the centroids of the data and got the distances of each one to then group by each centroids to get the minimum distance which is the closes warehouse. This then is able to be seen in a table as sen below.

![image](https://user-images.githubusercontent.com/94020684/221389941-51c6ce44-8418-4299-9ece-e430a1e8183a.png)

## Analysis of Customers 
- Explore distributions 
- Summary Stats 
- Feature Engineering
- Buying Habits 
- Hypothesis Chi2
- Residual Analysis
- Simple Linear
