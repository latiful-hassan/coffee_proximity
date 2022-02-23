# coffee_proximity
**Context**

- A coffee company need assistance in deciding where to prioritise building new stores to ensure that customers are never more that 0.5 miles away from one of their locations

**Task**

- Using the supplied store data create maps for the following:
  * All current store locations - shwoing monthly turnover and number of months the store has been operation
  * Calculate the distance between stores and hightlight the sotres whicha re more tha 0.5 miles from another branch

**Techniques & Process**

- Connect to data
- Use *Longitude* and *Latitude* to create map
- Applied *Monthly Turnover* in colour shelf
- Applied *Months Open* in size shelf
- Applied *Store ID* in detail shelf
- Used the company's logo as a custom shape:

![](https://github.com/latiful-hassan/coffee_proximity/blob/main/coffee_proximity_screenshots/coffee_proximity_map.png)

- To calculate distance between stores we will need to join the data to itself where *Store ID* is ***NOT*** equal:

![](https://github.com/latiful-hassan/coffee_proximity/blob/main/coffee_proximity_screenshots/store_id_join.png)

- We will use the ***Great-Circle Distance*** formula for our calculation in a calculated field:
  * 3959 * ACOS (
    SIN(RADIANS([Latitude])) * SIN(RADIANS([latitude (Sheet11)])) +
    COS(RADIANS([Latitude])) * COS(RADIANS([latitude (Sheet11)])) * COS(RADIANS([longitude (Sheet11)]) - RADIANS([Longitude]))
    )
- Created another calculated field with an **IIF** statement to evaluate which stores are too far:
  * IIF(MIN([Distance]) > 0.5, "Yes", "No")
- The **Too Far** calculated field is applied to colour and **Distance** to size:

![](https://github.com/latiful-hassan/coffee_proximity/blob/main/coffee_proximity_screenshots/coffee_proximity_map_with_distance.png)

- Used **Mapbox** to add a customer map:

![]()

**Analysis & Insights**

-
