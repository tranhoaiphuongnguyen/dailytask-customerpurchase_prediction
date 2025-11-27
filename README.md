# Will this customer purchase your product?

**Timeframe:** January 2023 – July 2024  
**Location:** United States  
**Dataset size:** 10,746 customers  
**Tools:** Python (NumPy, Pandas, SciPy, Matplotlib, Seaborn)

## Project overview
This project analyses online shopping behaviour during November and December, the busiest shopping months of the year.  
The goal is to understand how new and returning customers behave differently, what browsing patterns drive purchase decision, and how a marketing campaign could improve conversions.

The analysis focuses on three main questions:
1. How do purchase rates differ between new and returning customers?  
2. Which browsing behaviours (page durations) are most correlated?  
3. What is the probability that a new marketing campaign achieves its target sales?

The goal is to translate data patterns into actionable marketing insights and quantifiable business outcomes.

This project was inspired by the [DataCamp Real World Project – *Will This Customer Purchase Your Product?*](https://app.datacamp.com/learn/projects/2470), with extended analysis, visualisations and business insights.

The datasets used in this analysis can be found [here](online_shopping_session_data.csv).  
The Python code can be found [here](Pythoncode.ipynb).  

---

## Dataset description

The dataset includes 10,746 sessions recorded between January 2023 and July 2024, covering both new and returning customers across the US.

| Column | Description |
|--------|--------------|
| `Administrative`, `Administrative_Duration` | Number and duration of visits to administrative pages |
| `Informational`, `Informational_Duration` | Number and duration of visits to informational pages |
| `ProductRelated`, `ProductRelated_Duration` | Number and duration of visits to product pages |
| `BounceRates`, `ExitRates` | Website behavioural metrics |
| `PageValues` | Average page value in the session |
| `SpecialDay`, `Weekend`, `Month` | Contextual and seasonal features |
| `CustomerType` | Type of visitor (Returning or New) |
| `Purchase` | Whether a purchase occurred (1 = Yes, 0 = No) |

---

## Methodology

The analysis follows a structured workflow:
1. Data cleaning and preparation 
 - Duplicates removed, data types corrected, categorical values standardised.  
 - Focused on sessions from November–December to capture peak-season behaviour.
     
2. Exploratory Data Analysis (EDA)  
 - Calculated purchase rates by customer type.  
 - Correlation matrix created for browsing time metrics.  
 - Statistical simulation performed using binomial probability.
     
3. Visualisation  
 - Charts created using `matplotlib` and `seaborn` for clarity and interpretability.

---

## Results and insights

### Purchase rate by customer type

| Customer type | Purchase rate |
|----------------|----------------|
| New customer | 27.3% |
| Returning customer | 19.6% |

![](visualisation/purchase_rate.png)

An analysis of online shopping sessions during the peak months of November and December shows a clear difference in purchase likelihood between new and returning customers. New customers converted at an average rate of 27.3%, while returning customers converted at only 19.6%.

Although returning visitors are generally expected to have higher purchase intent due to their familiarity with the brand, the data suggests otherwise. This may indicate that the company’s holiday campaigns and promotions are particularly effective at attracting first-time buyers, while returning users may be browsing more cautiously, comparing offers, checking for discounts, or waiting for better deals before committing to a purchase.

From a marketing perspective, the stronger conversion performance among new customers reflects effective acquisition strategies, but also highlights weaker retention. Strengthening re-engagement efforts, such as personalised product recommendations, loyalty incentives, or targeted remarketing, could help improve conversion rates among returning shoppers.


### Correlation between page durations (Returning customers)

The strongest relationship was observed between Administrative_Duration and ProductRelated_Duration, with a correlation coefficient of 0.42.

| Page duration pair | Correlation |
|--------------------|-------------|
| Administrative ↔ ProductRelated | 0.42 |
| Informational ↔ ProductRelated | 0.37 |
| Administrative ↔ Informational | 0.26 |

![](visualisation/correlation_timespent.png)

The analysis shows how returning customers spent their time across different types of pages on the website during November and December. The strongest relationship appears between time spent on administrative or account-related pages and time spent on product pages. This means that when returning customers are actively managing their accounts or moving through transactional steps, they also tend to spend more time reviewing product details. In practical terms, these users are likely browsing with a clear intention to purchase, taking time to evaluate items before making a decision.

In contrast, the connections involving informational or general content pages are noticeably weaker. This suggests that returning customers do not rely heavily on general site information during their shopping experience.

Overall, the results indicate that returning visitors behave in a focused, purpose-driven way. They primarily interact with pages that directly support the purchasing process, rather than engaging in casual or exploratory browsing.


### Probability of campaign success

A hypothetical marketing campaign was designed to increase returning customers’ purchase rate by 15%. 
A binomial probability model was used to estimate the likelihood of achieving at least 100 purchases out of 500 sessions.

| Metric | Value |
|--------|--------|
| Baseline Purchase Rate | 0.196 |
| Adjusted Rate (+15%) | 0.225 |
| Sessions Simulated | 500 |
| Probability ≥ 100 Purchases | 91.9% |

![](visualisation/binomialdistribution_returningcustomers.png)

The analysis of the binomial probability distribution shows the likelihood of achieving at least 100 purchases out of 500 sessions from returning customers after their purchase rate increases by 15%. The result is a probability of about 91.9%, which means it is very likely that the campaign will meet or even surpass the target of 100 sales. The expected average outcome sits at around 110 purchases, so most scenarios fall safely above the goal.

From a business standpoint, this suggests that the marketing campaign directed at returning customers is highly encouraging. The improvement in conversion rate has a strong positive effect on expected sales, indicating that investing in re-engagement and loyalty-focused initiatives can generate meaningful returns during peak shopping periods.

---

## Key findings

**Acquisition outperformed retention**  
New customers converted at a higher rate, reflecting the success of holiday campaigns in attracting new visitors.

**Returning customers are deliberate browsers**  
Their time distribution suggests intentional research before buying, offering opportunities for targeted product recommendations.

**Retention marketing pays off**  
A 15% increase in conversion among returning users can achieve campaign success with 91.9% certainty.

**Behavioural patterns reveal intent**   
Duration correlations can help identify high-intent users and tailor personalised engagement strategies.

---

## Business implications

- Optimise promotions for new users while designing personalised loyalty campaigns for returning customers.  
- Use page duration metrics to segment visitors by intent, prioritising follow-up actions for high-engagement sessions.  
- Measure campaign ROI through probabilistic models instead of simple averages to better capture uncertainty.
