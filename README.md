# E-commerce-data-analysis
<br>
What will Olist's future sales look like? From which kind of customer and from which region will they occur?
<br>
Moreover, which regions are the most valuable to the company in terms of total customers and total sales?
<br>

# Business Problem
<br>
Managers at Olist need to understand future demand in number and geography in order to properly allocate capital across their operations.
This analysis seeks to analyze sales data across Brazils' states to drive actionable insight. My method will consist of 3 objectives:
<br>

1. Geospatial Analysis
<br>
2. Segmentation Analysis
<br>
3. Time Series Forecasting of Sales
<br>
Finally, I will provide recommendations on where to allocate capital to best position the firm to provide value for its customers.

# The Data
![HRhd2Y0](https://user-images.githubusercontent.com/87211473/195154331-b8d622e2-62b9-4de6-9be5-753a248d9b47.png)
<br>

The data schema above visualizes the data sets we will be analyzing. Foreign keys are indicated by the arrows.
<br>
https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce
# Recency, Frequency, Monetary Clustering
RFM analysis examines customers across 3 characteristics: recency, frequency, and monetary value.
<br>

1. Recency: how recent a customer purchased
<br>

2. Frequency: how frequent a customer purchases
<br>

3. Monetary: how valuable the customer purchases are

To this end, I will now create data frames to look at each characteristic.
<br>
Frequency does not seem to add any meaningful signal for our clusters, as most customers have a frequency of 1. The model returned 5 clusters:
<br>

<img width="417" alt="Screen Shot 2022-10-11 at 9 58 50 AM" src="https://user-images.githubusercontent.com/87211473/195154087-d0fec69d-495c-45fd-bfa2-2d70580fe8be.png">
<br>

0. Middle of the road monetary value with similar recency to cluster. These customers are similar to cluster 1, but have much higher average monetary value. These customers represent our second largest cluster by customer count, and second most valuable customer segment as a percentage of sales revenue.
<br>

1. Low monetary value with relatively high recency. As the largest of our clusters, these individuals purchase about once a year with relatively low order value. They are the largest customer segment by count and as a precentage of sales revenue.
<br>

2. High monetary value with with relatively low recency. On an individual basis, these people represent our most valuable customers. They have highest average order value and have purchased the most recently.
<br>

3. Outlier customer who purchased a significantly large amount a long time ago. Infering from the massive order value, this customer is probably some kind of business. This customer does not fit into the other segments, so they stand alone.
<br>

4. Middle-high monetary value with lower recency. These customers' monetary values sit between clusters 0 and 2, with the second lowest recency out of all our clusters. They order with higher payment values, and also ordered more recently than our other customer segments (excluding segment 2).
<br>
Overall, our clusters reveal an underlying problem in Olist's customer base: <b>low customer life-time value (LTV)</b>. According to our model, customers do not come back to purchase again often (frequency). Olist is failing to build meaningful relationships with their customers, resulting in lower LTV. This has serious implications on profitability. Given the often razor thin margins of e-commerce, Olist may have negative customer LTV. This means that Olist loses money on the average customer they service. Recommendations to Olist managers will attempt to address this issue and increase customer LTV.

# Geospatial Analysis
How do customers, sales, delivery times, and more vary across the regions of Brazil? This section seeks to visualize the geography of our ecommerce data.
## Customer Count

![newplot (1)](https://user-images.githubusercontent.com/87211473/195154736-5e6d7309-a756-42ff-87ab-8f87624aa6d8.png)
<br>
Sao Paulo, Minas Gereis, and Rio de Janeiro hold the majority of customers. Sao Paulo appears to be the center of operations for Olist; the state boasts 48.7K customers. This is significantly higher than any other region. More rural areas in the north appear to have much fewer customers than the more urban southeast.
## Review Score
![newplot](https://user-images.githubusercontent.com/87211473/195154835-89cf4341-4b93-44e2-9e69-c0e06c47d422.png)
<br>
Review scores are at or above 4.0 in the south. The middle and north of the country experience lower review scores, probably due to the more rural and remote deliveries.
## Delivered
![newplot (5)](https://user-images.githubusercontent.com/87211473/195155078-b4706a99-27a5-43be-90af-3609f4632b8f.png)
<br>
Delivery rates are fairly consistent (>90%) across the country. RR stands out at 88%, indicating this northern rural region has delivery issues. 

## Seller Count

![newplot (4)](https://user-images.githubusercontent.com/87211473/195155140-aab02c74-d35f-47d1-ae4f-4ea313422008.png)
<br>
Correlating with customer count, sellers are also concentrated in the south of the country. Sao Pualo holds a vast majority of sellers at 82.6K. For sellers, Sao Paulo is the most important region.
## Sales Revenue
![newplot (3)](https://user-images.githubusercontent.com/87211473/195155224-09fe42f4-28a4-4ab6-b38a-3e771ef5ebf4.png)
<br>
Again, the urban centers of Sao Paulo, Rio de Janerio, and Minas Gereis show the largest numbers. A majority of revenue comes from these three regions. Revenue drops as one progresses north through the country.
## Freight Value

![newplot (2)](https://user-images.githubusercontent.com/87211473/195155299-45a74fb4-c3ef-409b-80ef-7ea246be6876.png)
<br>
Freight value is much higher for Sao Pualo, Rio, and Minas Gereis. This coincides with the customer count examined earlier. The South east appears to be a bulk of Olist's freight value.
# Time Series Forecasting of Demand: Customer and Payment Value
<br>

<img width="783" alt="Screen Shot 2022-10-11 at 10 26 10 AM" src="https://user-images.githubusercontent.com/87211473/195159227-8de7e571-270f-4789-b0ae-af7e45f47b99.png">


<br>

Preliminary visualization of our weekly sales data shows a sudden drop to zero in sales. The model may not capture the sudden drop in a train-test split. Validation will not be as clear in this situation due to the outlier event.
<br>
<img width="198" alt="Screen Shot 2022-10-11 at 10 14 09 AM" src="https://user-images.githubusercontent.com/87211473/195157128-aa785025-0512-4eed-9e1d-af404cc7a313.png">
<br>
Average weekly sales revenue stands at 188014.48(BRL). However, the standard deviation of sales revenue = 134951.3(BRL), which is a relatively high. The volatility in sales data is expected, given our previous visualization.
<br>
## Baseline Time Series Forecasts

<img width="448" alt="Screen Shot 2022-10-11 at 10 21 03 AM" src="https://user-images.githubusercontent.com/87211473/195158214-34c26510-4faa-4f05-8a6a-86ac15f16a17.png">
<img width="461" alt="Screen Shot 2022-10-11 at 10 16 17 AM" src="https://user-images.githubusercontent.com/87211473/195157752-aa24f8c1-cd6f-4edc-814d-b4b241165b40.png">
<br>
Model returned 4 AR terms, 1 MA term, and 1 sigma term. AIC was minimized to 2088.818 using the auto_arima package's stepwise search.
<br>
Unusually, our data shows weekly sales dropping off a cliff to zero. This "outlier" event causes some difficulty in our SARMIAX modeling.
<br>

Splitting the data into training and test sets results in the model predicting inaccuratley over the test set. Basically, a 80/20 train-test split results in a SARMIAX model that completely misses the sudden downturn to zero sales. This is because the training data alone does not indicate or suggest such a drastic drop in sales to zero.
<br>

In fact, a quick google search of Olist 2018 revenue shows no sign of a drop to zero sales. Therefore, this anomaly is probably the result of data collection issues. It is most likely that the data collection of sales revenue was not fully or properly recorded in the dataset provided.
<br>

Nevertheless, data collection is outside the scope of this project. Therefore, I will re-train the model on the entire dataset. This should yield a better picture of future sales, since the training will take into account the sudden drop in sales that plagues our model validation.
## Final Time Series Forecasts
<img width="425" alt="Screen Shot 2022-10-11 at 10 22 43 AM" src="https://user-images.githubusercontent.com/87211473/195158517-3ff4ef5b-f61b-4a20-87dd-45a922fe5d1b.png">

<img width="437" alt="Screen Shot 2022-10-11 at 10 23 37 AM" src="https://user-images.githubusercontent.com/87211473/195158628-855b1737-f754-4ee9-842b-a8df1c868817.png">
<br>
Model returned 2 AR terms, 1 sigma term, and 2 MA terms (2, 1, 2). AIC was minimized to 2623.873 through auto_arima package's stepwise search.

<br>
The model trained on the entire dataset is visualized above with the 95% confidence interval of the predictions shaded in grey. The model predicts a bounce back of sales, which stabilize around 147K.
<br>

However, the prediction line should not be considered alone. The confidence interval of the prediction provides a range that weekly predictions should fall into according to the model. The lower side of the interval indicates zero or near zero sales. The upper side indicates a possible return to healthier sales numbers. That being said, confidence intervals do not represent an "upper" situation vs. a "lower" situation. They simply represent a range that the model is 95% confident the true value of the prediction lies within.


# Business Recommendations: Capital Allocations, Customer Lifetime Value, and Reccuring Revenue
## Geospatial Recommendations
1.  <b>Invest in building out operations in Bahia, a region close to our hub of operations in the south with the third largest population in Brazil (after SP, MG)</b>. According to our geospatial analysis, Bahia has the potential to become one of Olist's core geographies. The region already has healthy traction in sales, freight value, and delivery rates. Moreover, Bahia's proximity to Olist's hub of operations in Sao Paulo allows for an easier transfer of transportation assets and personel. Managers should focus on increasing sales from the region, along with increasing the number of sellers. More local sellers in Bahia should maintain healthier delivery times and strong delivery rates. Bahia is not as dense as other Olist core geographies, so local sellers is important for more efficent deliveries.
<br>

2. <b>Invest in operations in Paraná. Similar to Bahia, Paraná has a large population with close proximity to our hub of operations</b>. Sales, freight values, and seller count suggest that Paraná could also become a core geography for Olist. While Paraná has a lower total population than Bahia, Paraná is nearly twice as dense. For Olist, this means less average distanced traveled for delivery, as customers will be more concentrated.
<br>

These recommendations are aligned with the goal of growing sales revenue and seller counts across southern Brazil. Southern Brazil has multiple important population centers surrounding Olist's hub of operations in Sao Paulo. Building out operations in the south should be a first priority. Thinking more broadly, Olist's capital allocations should be concentrated in the south and move north towards the northeast population centers as the southern markets mature.

## Clustering Recommendations
1.  <b>Create targeted upsell recommendations for customers during checkout in order to increase average order value</b>.
Our largest customer segment (cluster 0 at 83K customers) has a meager BR $143 average order value (AOV). By providing relevant, targeted upsells using a recommendation model, Olist managers will increase AOV and drive more profitability across cluster 0. The recommendation upsell model should be implemented in browser during checkout, as well as emailed in a preprogrammed, post-purchase email flow.
<br>
The email flow should be structured as follows:
<br>
>Post Purchase "Thank You" plus reccomendations
<br>
>"You forgot these" reminder with recommendations
<br>
>"Order now and save X%" with recommendations (introduce some urgency, final push for purchasing)
<br>

2. <b>Build out an SMS list to recapture customers and increase customer lifetime value</b>. Olist can collect phone numbers as a part of the checkout process, or test browser pop-ups that ask for phone numbers and emails. Open rates for SMS marketing communications are significnatly higher than regular email. Successful SMS campaigns can reach open rates of up to 90%, while email open rates usually sit around 30%. Consumers can enjoy a more personal touchpoint with the Olist brand via SMS.
<br>
Periodic SMS campaigns offering discounts, announcing new product offerings, or promoting events (holiday sales, black friday, etc.) should increase the frequency of buyers, resulting in an increase of customer lifetime value. However, SMS campaigns should not exceed 4-6 texts per month. We do not want our customers to interpret our SMS communications as spam, so the frequency should not exceed the prescribed limit.
<br>

Overall, these two recommendations seek to address the underlying, existential problem revealed by our clustering: low customer lifetime value. Targeted email upsells alongside SMS campaigns should increase the frequency of buying, as well as the average order value. Metrics of evaluation include the average order value of our largest customer segment (cluster 0), and the frequency of buying across all our clusters.

## Time Series Analysis Recommendations
1. <b>Build out an Olist paid membership program in order to provide more stable, reccuring monthly revenue</b>. Olist's sales revenue over the examined period had multiple drastic fluctutations, including a sudden drop to zero. Olist memberships could provide some predictability and stability in Olist's revenue structure. This will give managers more stable cashflow, allowing them to make more informed decisions on capital allocation. Relying on wildly swinging sales complicates a manager's ability to make effective decisions on growth, hiring, scaling, etc.

# Limitations and Next Steps
The next step in executing on the recommendations provided would be a comprehensive review of the Paraná and Bahia regions. Financial and logistics information should be compiled and analyzed to ascertain the feasability of investing more heavily in these regions. Analysis should review historic return on invested capital in those regions, as well as model the performance of future investments. Does Olist have the logistics in place to handle more capacity? Do investments in these regions make sense at the current cost of capital? Is it better to buy or build the systems needed to increase revenue?
<br>

Second, the success of our customer lifetime value campaigns should be monitored and evaluated. Relevant success metrics include average order value, frequency, recency, and customer lifetime value. Meaningful lift in these metrics would signal success.

# Repository Structure
├── README.md <- The top-level README for reviewers of this project
├── EcommerceDataAnalysis.ipynb <- Narrative documentation of analysis in Jupyter notebook
├── Presentation_nontechnical.pdf <- PDF version of project presentation
